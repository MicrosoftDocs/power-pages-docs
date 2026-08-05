---
title: Rotate SSL certificates for Power Pages sites
description: Learn Power Pages SSL certificate rotation concepts, including API endpoints, PFX requirements, and the three-stage flow to secure your custom domain.
author: RitGan
ms.author: ritwikganni
ms.reviewer: smurkute
ms.date: 08/05/2026
ms.topic: concept-article
---

# Rotate SSL certificate for your sites

SSL certificate rotation for Power Pages websites is a process that replaces an existing SSL certificate bound to a custom domain with a new one by chaining two Power Platform APIs. This concept explains the components, requirements, and API surface involved in an end-to-end certificate rotation flow for a Power Pages website.

Rotation is performed against the Power Platform API (service version `2024-10-01`) and consists of three logical stages which are acquiring a delegated OAuth2 access token, uploading a `.pfx` certificate to obtain its thumbprint, and binding that thumbprint to the target custom domain.

## Prerequisites

- **Environment ID**: The Power Platform environment ID hosting the website.
- **Website ID**: The Power Pages website unique identifier (ID).
- **Custom domain (host name)**: Web address that replaces the default Power Pages URL with your organization's own branded domain name, for example, `site.contoso.com`.
- **PFX file + password**: A password-protected `.pfx` file that meets the certificate requirements.
- **App registration**: A Microsoft Entra ID app (client ID/secret) that can acquire a token for `https://api.powerplatform.com`.

## Certificate requirements

The SSL certificate used for rotation must meet all of the following requirements:

- Signed by a trusted certificate authority.
- Exported as a password-protected PFX file.
- Contains a private key that's at least 2048 bits long.
- Contains all intermediate certificates in the certificate chain.
- Must be SHA2 enabled; SHA1 support is being removed from popular browsers.
- PFX file is encrypted with AES-256 encryption.
- Contains an Extended Key Usage for server authentication (OID = 1.3.6.1.5.5.7.3.1).

## Rotation flow overview

The end-to-end rotation flow consists of three sequential stages. Each stage produces an artifact that the next stage consumes.

1. **Security**: acquire a delegated (user) OAuth2 access token
1. **Upload certificate**: upload the `.pfx` file and capture the returned thumbprint
1. **Update SSL binding**: bind the uploaded certificate (by thumbprint) to the custom domain

## Security

Authentication uses Microsoft Entra ID OAuth2 to get a delegated access token for the Power Platform API.

| Property | Value |
|----|----|
| Type | oauth2 |
| Flow | implicit |
| Authorization URL | `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.powerplatform.com` |

## Upload certificate API

The upload API accepts a multipart form containing the `.pfx` file and its password. It returns the uploaded certificate's thumbprint. The thumbprint is required by the SSL binding stage.

**Endpoint**

```
POST https://api.powerplatform.com/powerpages/environments/{environmentId}/websites/{id}/certificates?api-version=2024-10-01&certType={certType}
```

### URI parameters

| Name | In | Required | Type | Description |
|----|----|----|----|----|
| environmentId | path | True | string | The environment ID. |
| id | path | True | string | Website unique identifier (ID). |
| certType | query | True | string | Type of certificate, such as SSL. |
| api-version | query | True | string | The API version. |

### Request body

Media type: `multipart/form-data`

| Name | Required | Type | Description |
|----|----|----|----|
| file | True | file (.pfx) | SSL certificate file. |
| password | True | string | Password for the PFX file. |

### Responses

| Name | Type | Description |
|----|----|----|
| 200 OK | string | Success - uploaded certificate thumbprint |
| 400 Bad Request | ErrorMessage | Bad Request |
| 401 Unauthorized | ErrorMessage | Unauthorized |
| 404 Not Found | ErrorMessage | Not Found |
| 500 Server error | ErrorMessage | Server error |

### PowerShell example

`curl.exe` sends `multipart/form-data` uploads because it reliably handles the multipart body and file streaming. To avoid exposing the certificate password through process arguments, include it in the form body instead of the command line.

```powershell
function Invoke-CertUpload {
    param(
        [string]$BaseUrl,
        [string]$EnvironmentId,
        [string]$WebsiteId,
        [string]$ApiVersion,
        [string]$CertPath,
        [SecureString]$CertPassword,
        [string]$DelegatedToken
    )

    Write-Host "Uploading certificate ..."

    $certUploadUrl = "$BaseUrl/powerpages/environments/$EnvironmentId" +
                     "/websites/$WebsiteId" +
                     "/certificates?api-version=$ApiVersion&certType=SSL"

    $tempFile = [System.IO.Path]::GetTempFileName()
    $statusCode = & curl.exe --silent --request POST `
        --max-time 120 `
        --url $certUploadUrl `
        --header "authorization: Bearer $DelegatedToken" `
        --header "user-agent: PowerShell/CertRotation" `
        --form "file=@$CertPath" `
        --form "password=$([Runtime.InteropServices.Marshal]::PtrToStringAuto(
            [Runtime.InteropServices.Marshal]::SecureStringToBSTR($CertPassword)))" `
        --output $tempFile `
        --write-out "%{http_code}"

    if ($LASTEXITCODE -eq 28) { throw "Certificate upload timed out after 2 minutes." }

    $uploadResponse = [PSCustomObject]@{
        StatusCode = [int]$statusCode
        Content    = Get-Content $tempFile -Raw
    }
    Remove-Item $tempFile -ErrorAction SilentlyContinue

    if ($uploadResponse.StatusCode -eq 200) {
        $responseText = $uploadResponse.Content
        if ([string]::IsNullOrWhiteSpace($responseText)) {
            throw "Certificate upload failed: HTTP 200 but response body is empty."
        }
        $thumbprint = $responseText.Trim('"')
        Write-Host "Uploaded certificate, cert thumbprint: $thumbprint"
        return $thumbprint
    } else {
        throw "Certificate upload failed: HTTP $($uploadResponse.StatusCode). Response: $($uploadResponse.Content)"
    }
}
```

## SSL binding API

The SSL binding API associates an uploaded certificate (identified by thumbprint) with a custom domain on the website. It creates the binding if it doesn't exist, or updates it if it does.

**Endpoint**

```
POST https://api.powerplatform.com/powerpages/environments/{environmentId}/websites/{id}/sslBindings?api-version=2024-10-01&hostName={hostName}&thumbprint={thumbprint}
```

### URI parameters

| Name | In | Required | Type | Description |
|----|----|----|----|----|
| environmentId | path | True | string | The environment ID. |
| id | path | True | string | Website unique identifier (ID). |
| hostName | query | True | string | Custom domain for which SSL binding needs to be created or updated. |
| thumbprint | query | True | string | SSL certificate thumbprint (returned by the upload step). |
| api-version | query | True | string | The API version. |

### Responses

| Name | Type | Description |
|----|----|----|
| 200 OK | boolean | `true` means SSL binding created or updated successfully |
| 400 Bad Request | ErrorMessage | Bad Request |
| 401 Unauthorized | ErrorMessage | Unauthorized |
| 404 Not Found | ErrorMessage | Not Found |
| 500 Server error | ErrorMessage | Server error |

### PowerShell example

```powershell
function Invoke-SslBinding {
    param(
        [string]$BaseUrl,
        [string]$EnvironmentId,
        [string]$WebsiteId,
        [string]$ApiVersion,
        [string]$HostName,
        [string]$Thumbprint,
        [string]$DelegatedToken
    )
    Write-Host "Binding SSL certificate ..."
    $sslBindUrl = "$BaseUrl/powerpages/environments/$EnvironmentId" +
                  "/websites/$WebsiteId" +
                  "/sslBindings?api-version=$ApiVersion" +
                  "&hostName=$HostName" +
                  "&thumbprint=$Thumbprint"

    $tempFile = [System.IO.Path]::GetTempFileName()
    $bindStatusCode = & curl.exe --silent --request POST `
        --max-time 120 `
        --url $sslBindUrl `
        --header "authorization: Bearer $DelegatedToken" `
        --header "content-type: application/json" `
        --header "user-agent: PowerShell/CertRotation" `
        --data "{}" `
        --output $tempFile `
        --write-out "%{http_code}"

    if ($LASTEXITCODE -eq 28) { throw "SSL binding timed out after 2 minutes." }

    $bindResponse = [PSCustomObject]@{
        StatusCode = [int]$bindStatusCode
        Content    = Get-Content $tempFile -Raw
    }
    Remove-Item $tempFile -ErrorAction SilentlyContinue

    if ($bindResponse.StatusCode -eq 200) {
        Write-Host "SSL binding succeeded."
    } else {
        throw "SSL binding failed: HTTP $($bindResponse.StatusCode). Response: $($bindResponse.Content)"
    }
}
```

## API reference summary

| API | Method & Endpoint | Script Function |
|----|----|----|
| [Upload certificate](/rest/api/power-platform/powerpages/websites/upload-certificate) | `POST /powerpages/environments/{environmentId}/websites/{id}/certificates?certType=SSL` | `Invoke-CertUpload` |
| [Update SSL binding](/rest/api/power-platform/powerpages/websites/add-ssl-binding-by-portal) | `POST /powerpages/environments/{environmentId}/websites/{id}/sslBindings?hostName={hostName}&thumbprint={thumbprint}` | `Invoke-SslBinding` |

Learn more about API in [Websites](/rest/api/power-platform/powerpages/websites).

## Error model

Error responses (400, 401, 404, and 500) share a common shape composed of an `ErrorMessage` wrapping an `Error` object, which can include additional `Details` entries.

### ErrorMessage

| Name | Type | Description |
|----|----|----|
| error | Error | |

### Error

| Name | Type | Description |
|----|----|----|
| code | string | Error code |
| details | Details[] | |
| message | string | Error message |
| target | string | Target parameter |

### Details

| Name | Type | Description |
|----|----|----|
| code | string | Error code |
| message | string | Error message |
| target | string | Target parameter |