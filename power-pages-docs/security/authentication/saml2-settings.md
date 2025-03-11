---
title: Set up a SAML 2.0 provider with AD FS
description: Learn how to set up a SAML 2.0 identity provider with Active Directory Federation Services (AD FS) for use with sites you create with Microsoft Power Pages.
ms.date: 09/10/2024
ms.topic: how-to
author: sandhangitmsft
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Set up a SAML 2.0 provider with AD FS

Active Directory Federation Services (AD FS) is one of the SAML 2.0 identity providers you can use to [authenticate visitors](configure-site.md) to your Power Pages site. You can use any provider that conforms to the [SAML 2.0 specification](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html).

This article describes the following steps:

- [Set up AD FS in Power Pages](#set-up-ad-fs-in-power-pages)
- [Create an AD FS relying party trust](#create-an-ad-fs-relying-party-trust)
- [Finish setting up the provider](#finish-setting-up-the-provider)

> [!IMPORTANT]
> The steps for setting up AD FS might vary depending on the version of your AD FS server.

## Set up AD FS in Power Pages

Set AD FS as an identity provider for your site.

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. Select **+ New provider**.

1. Under **Select login provider**, select **Other**.

1. Under **Protocol**, select **SAML 2.0**.

1. Enter a name for the provider.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an AD FS relying party trust

You can also [use a PowerShell script to perform these steps](#configure-ad-fs-using-powershell).

1. In Server Manager, select **Tools**, and then select **AD FS Management**.

1. Expand **Service**.

1. In the right side panel, select **Add Claim Description**.

1. Enter the following values:

    - **Display name**: *Persistent Identifier*

    - **Claim identifier**: *urn:oasis:names:tc:SAML:2.0:nameid-format:persistent*

    - Select both **Publish this claim description in federation metadata**&hellip; options.

1. Select **OK**.

1. Select **Trust Relationships** > **Relying Party Trusts**.

1. Select **Add Relying Party Trust**.

1. Select **Start**.

1. Select **Enter data about the relying party manually**, and then select **Next**.

1. Enter a name; for example, *https://portal.contoso.com/*.

1. Select **Next**.

1. Select **AD FS 2.0 profile**, and then select **Next**.

1. On the **Configure Certificate** page, select **Next**.

1. Select **Enable support for the SAML 2.0 WebSSO protocol**.

1. Under **Relying party SAML 2.0 SSO service URL**, enter the reply URL [you copied](#set-up-ad-fs-in-power-pages). AD FS requires that the website run HTTPS, not HTTP.

1. Select **Next**.

1. On the **Configure Identifiers** page, enter your site's URL, and then select **Add**.

    You can add more identities for each additional relying party website if needed. Users can authenticate using any available identities.

1. Select **Next**.

1. On the **Configure Multi-factor Authentication Now?** page, select **I do not want to configure multi-factor authentication settings for this relying party trust at this time**.

1. On the **Choose Issuance Authorization Rules** page, select **Permit all users to access this relying party**, and then select **Next**.

1. Review the trust settings, and then select **Next**.

1. Select **Close**.

1. In **Edit Claim Rules**, select one the following tabs, depending on the trust you're editing and in which rule set you want to create the rule:

    - **Acceptance Transform Rules**
    - **Issuance Transform Rules**
    - **Issuance Authorization Rules**
    - **Delegation Authorization Rules**

1. Select **Add Rule**.

1. In the **Claim rule template** list, select **Transform an Incoming Claim**, and then select **Next**.

1. Enter or select the following values:

    - **Claim rule name**: *Transform Windows account name to Name ID*

    - **Incoming claim type**: **Windows account name**

    - **Outgoing claim type**: **Name ID**

    - **Outgoing name ID format**: **Persistent Identifier**

1. Select **Pass through all claim values**.

1. Select **Finish**, and then select **OK**.

## Finish setting up the provider

After you set up the AD FS relying party trust:

1. [Create an app registration in Azure](saml2-settings-azure-ad.md#create-an-app-registration-in-azure).

1. [Enter site settings in Power Pages](saml2-settings-azure-ad.md#enter-site-settings-in-power-pages).

## Identity provider&ndash;initiated sign-in

AD FS supports the [identity provider&ndash;initiated single sign-on (SSO)](/azure/active-directory/manage-apps/configure-saml-single-sign-on) profile of the [SAML 2.0 specification](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline). For the service provider website to respond properly to the identity provider's SAML request, you must encode the [`RelayState`](/archive/blogs/askds/ad-fs-2-0-relaystate) parameter.

The basic string value to encode in the SAML `RelayState` parameter must be in the format `ReturnUrl=/content/sub-content/`, where `/content/sub-content/` is the path to the page you want to go to on the service provider website. You can specify the path to any valid page on the website. The string value is encoded and placed in a container string of the format `RPID=&lt;URL encoded RPID&gt;&RelayState=&lt;URL encoded RelayState&gt;`. This entire string is once again encoded and added to another container of the format `<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> encoded RPID/RelayState&gt;`.

For example, given the service provider path `/content/sub-content/` and the relying party ID `https://portal.contoso.com/`, follow these steps to construct the URL:

- Encode the value `ReturnUrl=/content/sub-content/` to get `ReturnUrl%3D%2Fcontent%2Fsub-content%2F`

- Encode the value `https://portal.contoso.com/` to get `https%3A%2F%2Fportal.contoso.com%2F`

- Encode the value `RPID=https%3A%2F%2Fportal.contoso.com%2F&RelayState=ReturnUrl%3D%2Fcontent%2Fsub-content%2F` to get `RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F`

- Prepend the AD FS identity provider&ndash;initiated SSO path to get the final URL `https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F`

You can use the following PowerShell script to construct the URL. Save the script to a file named `Get-IdPInitiatedUrl.ps1`.

```powershell

<#
.SYNOPSIS 
Constructs an IdP-initiated SSO URL to access a website page on the service provider.
.PARAMETER path
The path to the website page.
.PARAMETER rpid
The relying party identifier.
.PARAMETER adfsPath
The AD FS IdP initiated SSO page.
.EXAMPLE
PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"
#>
param
(
[parameter(mandatory=$true,position=0)]
$path,
[parameter(mandatory=$true,position=1)]
$rpid,
[parameter(position=2)]
$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx
)
$state = ReturnUrl=$path
$encodedPath = [uri]::EscapeDataString($state)
$encodedRpid = [uri]::EscapeDataString($rpid)
$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")
$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid
Write-Output $idpInitiatedUrl
```

## Configure AD FS using PowerShell

Instead of adding a relying party trust in AD FS manually, you can run the following PowerShell script on the AD FS server. Save the script to a file named `Add-AdxPortalRelyingPartyTrustForSaml.ps1`. After the script executes, continue to [configure the site settings in Power Pages](#finish-setting-up-the-provider).

```powershell
<# 
.SYNOPSIS
Adds a SAML 2.0 relying party trust entry for a website.
.PARAMETER domain
The domain name of the website.
.EXAMPLE
PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com
#>
param
(
[parameter(Mandatory=$true,Position=0)]
$domain,
[parameter(Position=1)]
$callbackPath = /signin-saml2
)
$VerbosePreference = Continue
$ErrorActionPreference = Stop
Import-Module adfs
Function Add-CrmRelyingPartyTrust
{
param (
[parameter(Mandatory=$true,Position=0)]
$name
)
$identifier = https://{0}/ -f $name
$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)
$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }
$issuanceTransformRules = @'
@RuleTemplate = MapClaims
@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim
c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]
=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");
@RuleTemplate = LdapClaims
@RuleName = Send LDAP Claims
c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]
=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);
'@ -f $identityProviderValue
$issuanceAuthorizationRules = @'
@RuleTemplate = AllowAllAuthzRule
=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);
'@
Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules
}
# add the 'Identity Provider' claim description if it is missing
[!INCLUDE[cc-pages-ga-banner](../../../includes/cc-pages-ga-banner.md)]
if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {
Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true
}
# add the website relying party trust
[!INCLUDE[cc-pages-ga-banner](../../../includes/cc-pages-ga-banner.md)]
Add-CrmRelyingPartyTrust $domain
```

### See also

[Set up a SAML 2.0 provider](saml2-provider.md)  
[Set up a SAML 2.0 provider with Microsoft Entra ID](saml2-settings-azure-ad.md)  
[SAML 2.0 FAQ](saml2-faqs.md)