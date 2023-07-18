---
title: Use OAuth 2.0 implicit grant flow in your Power Pages site
description: Learn how to make client-side calls to external APIs and secure them using OAuth 2.0 implicit grant flow in your Power Pages site.
ms.date: 3/20/2023
ms.topic: how-to
author: gitanjalisingh33msft
ms.author: gisingh
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - GitanjaliSingh33msft
    - dileepsinghmicrosoft
    - nickdoelman
    - ProfessorKendrick
ms.custom:
  - bap-template
  - ai-gen-docs
content_well_notification: 
  - AI-contribution
---

# Use OAuth 2.0 implicit grant flow in your Power Pages site
<!-- EDITOR'S NOTE: When I looked up information about the OAuth 2.0 implicit grant flow, I found documentation stating the implicit flow shouldn't be used. See https://oauth.net/2/grant-types/implicit/. Should we at least mention this warning in our article? -->
<!-- EDITOR'S NOTE: Please include in the introduction an explanation of what benefit the implicit grant flow offers a maker and in what scenarios it should be considered. -->
<!-- EDITOR'S NOTE: Please restructure this article so that it follows a logical sequence of actions and so that the headings give a good overview of the contents when scanned. As it is, the article reads like a random collection of steps and possibly related information. This article is in a section that's meant for makers/citizen devs, not pro devs. I'm fairly knowledgeable, but I'm so lost that I can't even begin to edit this. -->

The OAuth 2.0 implicit grant flow is a way to get tokens from an authorization server without backend servers exchanging credentials. It returns tokens directly from the /authorize endpoint instead of the /token endpoint. It was designed for applications that access APIs only while the user is present.

Here's an example of an authentication path with standard OAuth 2.0 and OAuth 2.0 implicit grant:

:::row:::
    :::column:::
        OAuth 2.0
    :::column-end:::
    :::column:::
        OAuth 2.0 implicit grant
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        1. A user visits a website and clicks on the "Sign in with Google" button.
        2. The website redirects the user to Google's authorization server.
        3. The user logs in to their Google account and is asked to grant permission to the website.
        4. If the user grants permission, Google sends an authorization code back to the website.
        5. The website sends this authorization code to Google's token server along with its client ID and secret.
        6. Google verifies the authorization code and sends an access token back to the website.
        7. The website can now use this access token to make requests on behalf of the user.
    :::column-end:::
    :::column:::
        1. A user visits a website and clicks on the "Sign in with Google" button.
        2. The website redirects the user to Google's authorization server.
        3. The user logs in to their Google account and is asked to grant permission to the website.
        4. If the user grants permission, Google sends an access token back to the website directly from the /authorize endpoint instead of the /token endpoint.
        5. The website can now use this access token to make requests on behalf of the user.
    :::column-end:::
:::row-end:::

OAuth 2.0 implicit grant flow supports [token](#token-endpoint-details) endpoints that a client can call to get an ID token.

## Custom certificates

Use the [Power Platform admin center](/power-apps/maker/portals/admin/manage-custom-certificates) to upload the custom certificate. After uploading the custom certificate, you need to update site settings as below: 

1. Go to the [Portal Management app](../configure/portal-management-app.md) and in the **Website** section, select **Site Settings**. 

1. To create a new setting, select **New**. 

1. To edit an existing setting, select **CustomCertificates/ImplicitGrantflow**. 

1. Specify values:
    - **Name:** CustomCertificates/ImplicitGrantflow 
    - **Website:** The associated website 
    - **Value:** Copy the thumbprint of the uploaded custom certificate from the Manage custom certificate screen and paste it here. The value will indicate which certificate will be used for implicit grant flow. 
1. Select **Save & Close**.

## Token endpoint details

You can also get a token by making a post request to the `/token` endpoint. The URL for token endpoint is: `<portal_url>/_services/auth/token`. The token endpoint supports the following parameters:

| Parameter   | Required? | Description                             |
|---------------|-----------|---------------------------------------|
| client_id      | No       | A string that is passed when making a call to the authorize endpoint. You must ensure that the client ID is [registered](#register-client-id-for-implicit-grant-flow). Otherwise, an error is displayed. Client ID is added in claims in the token as `aud` and `appid` parameter and can be used by clients to validate that the token returned is for their app.<br />The maximum length is 36 characters. Only alphanumeric characters and hyphen are supported. |
| redirect_uri      | No       | URL of the website where authentication responses can be sent and received. It must be registered for the particular `client_id` used in the call and should be exactly the same value as registered.            |
| state       | No        | A value included in the request that also is returned in the token response. It can be a string of any content that you want to use. Usually, a randomly generated, unique value is used to prevent cross-site-request forgery attacks.<br />The maximum length is 20 characters.              |
| nonce   | No        | A string value sent by the client that is included in the resulting ID token as a claim. The client can then verify this value to mitigate token replay attacks. The maximum length is 20 characters.      |
| response_type         | No        | This parameter supports only `token` as a value, allowing your app to immediately receive an access token from the authorize endpoint without making a second request to the authorize endpoint.                               |
|||

> [!NOTE]
> Even though `client_id`, `redirect_uri`, `state`, and `nonce` parameters are optional, it is recommended to use them in order to make sure your integrations are secure.

### Successful response

The token endpoint returns state and expires_in as response headers, and token in the form body.

### Error response

The error in a token endpoint is returned as a JSON document with the following values:

- **Error ID**: Unique identifier of the error.
- **Error message**: A specific error message that can help you identify the root cause of an authentication error.
- **Correlation ID**: A GUID that is used for debugging purposes. If you have enabled diagnostic logging, correlation ID would be present in server error logs.
- **Timestamp**: Date and time when the error is generated.

The error message is displayed in the default language of the signed-in user. If the user isn't signed in, a sign-in page is displayed for the user to sign in. 
For example, an error response looks as follows:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## Validate ID token

Just getting an ID token isn't sufficient to authenticate the user; you must also validate the token's signature and verify the claims in the token based on your app's requirements. The public token endpoint provides the public key of the site, which can be used to validate the signature of the token provided by the website. The URL for public token endpoint is: `<portal_url>/_services/auth/publickey`.

## Turn implicit grant flow on or off

By default, implicit grant flow is enabled. If you want to turn off implicit grant flow, set the value of the **Connector/ImplicitGrantFlowEnabled** site setting to **False**.

If this site setting isn't available in your website you must [create a new site setting](/power-apps/maker/portals/configure/configure-site-settings) with the appropriate value.

## Configure token validity

By default, the token is valid for 15 minutes. If you want to change the validity of token, set the value of the **ImplicitGrantFlow/TokenExpirationTime** site setting to the required value. The value must be specified in seconds. The maximum value can be 1 hour, and the minimum value must be 1 minute. If an incorrect value is specified (for example, alphanumeric characters), the default value of 15 minutes is used. If you specify a value more than the maximum value or less than the minimum value, the maximum and minimum values are used respectively, by default.

For example, to set the token validity to 30 minutes, set the value of the **ImplicitGrantFlow/TokenExpirationTime** site setting to **1800**. To set the token validity to 1 hour, set the value of the **ImplicitGrantFlow/TokenExpirationTime** site setting to **3600**.

## Register client ID for implicit grant flow

You must register the client ID with the website for which this flow is allowed. To register a client ID, you must create the following site settings:

|Site setting|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|The valid client ID values that are allowed for this site. The values must be separated by a semicolon and can contain alphanumeric characters and hyphens. The maximum length is 36 characters.|
|ImplicitGrantFlow/{ClientId}/RedirectUri|The valid redirect URIs that are allowed for a specific client ID. The values must be separated by a semicolon. The URL provided must be of a valid web page of the website.|
|||

## Sample code

You can use the following sample code to get started with using OAuth 2.0 Implicit Grant with Power Pages APIs.

### Use Power Pages OAuth token with an external Web API

This sample is an ASP.NET based project and is used to validate the ID token issued by Power Pages. The complete sample can be found here: [Use Power Pages OAuth token with an external Web API](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample).

### Token Endpoint sample

This sample shows how you can use the getAuthenticationToken function to fetch an ID token using the Token endpoint in Power Pages. The sample can be found here: [Token Endpoint sample](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js).

