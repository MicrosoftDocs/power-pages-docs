---
title: Use OAuth 2.0 implicit grant flow in your Power Pages site
description: Learn how to make client-side calls to external APIs and secure them using OAuth 2.0 implicit grant flow in your Power Pages site.
ms.date: 08/27/2024
ms.topic: how-to
author: gitanjalisingh33msft
ms.author: gisingh
ms.reviewer: danamartens
contributors:
    - GitanjaliSingh33msft
    - dileepsinghmicrosoft
    - nabha-msft
ms.custom: sfi-ropc-nochange
---

# Use OAuth 2.0 implicit grant flow in your Power Pages site

This feature allows a customer to make client-side calls to external APIs and secure them using OAuth implicit grant flow. It provides an endpoint to obtain secure id tokens. These tokens will contain user identity information to be used by external APIs for authorization following OAuth 2.0 implicit grant flow. The identity information of a signed-in user is passed in a secured manner to the external AJAX calls, which helps developers to pass authentication context and will also help users secure their APIs.

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

You can also get a token by making a post request to the `<portal_url>/_services/auth/token` endpoint. The token endpoint supports the following parameters:

| Parameter   | Required? | Description                             |
|---------------|-----------|---------------------------------------|
| client_id      | No       | A string that is passed when making a call to the endpoint. You must ensure that the client ID is [registered](#register-client-id-for-implicit-grant-flow). Otherwise, an error is displayed. Client ID is added in claims in the token as `aud` and `appid` parameter and can be used by clients to validate that the token returned is for their app.<br />The maximum length is 36 characters. Only alphanumeric characters and hyphen are supported. |
| state       | No        | A value included in the request that also is returned in the token response. It can be a string of any content that you want to use. Usually, a randomly generated, unique value is used to prevent cross-site-request forgery attacks.<br />The maximum length is 20 characters.              |
| nonce   | No        | A string value sent by the client that is included in the resulting ID token as a claim. The client can then verify this value to mitigate token replay attacks. The maximum length is 20 characters.      |
| response_type         | No        | This parameter supports only `token` as a value, allowing your app to immediately receive an id token from the endpoint without making a second request to the endpoint.                               |
|||

> [!NOTE]
> Even though `client_id`, `state`, and `nonce` parameters are optional, it is recommended to use them in order to make sure your integrations are secure.

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
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "aaaa0000-bb11-2222-33cc-444444dddddd" }
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
|||

## Sample code

You can use the following sample code to get started with using OAuth 2.0 Implicit Grant with Power Pages APIs.

### Use Power Pages OAuth token with an external Web API

This sample is an ASP.NET based project and is used to validate the ID token issued by Power Pages. The complete sample can be found here: [Use Power Pages OAuth token with an external Web API](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample).

### Token Endpoint sample

This sample shows how you can use the getAuthenticationToken function to fetch an ID token using the Token endpoint in Power Pages. The sample can be found here: [Token Endpoint sample](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js).
