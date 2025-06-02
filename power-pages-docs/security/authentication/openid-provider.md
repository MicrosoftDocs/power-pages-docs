---
title: Set up an OpenID Connect provider
description: Learn how to set up an OpenID Connect provider for use with sites you create with Microsoft Power Pages.
ms.date: 05/28/2025
ms.topic: how-to
author: DanaMartens
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
    - nageshbhat-msft
ms.custom: bap-template
---

# Set up an OpenID Connect provider

[OpenID Connect](https://openid.net/connect/) identity providers are services that conform to the [Open ID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html). OpenID Connect introduces the concept of an *ID token*. An ID token is a security token that allows a client to verify the identity of a user. It also gets basic profile information about users, known as *claims*.

OpenID Connect providers [Azure AD B2C](azure-ad-b2c-provider.md), [Microsoft Entra ID](openid-settings.md), and [Microsoft Entra ID with multiple tenants](openid-settings.md#allow-multitenant-microsoft-entra-authentication) are built into Power Pages. This article explains how to add other OpenID Connect identity providers to your Power Pages site.

## Supported and unsupported authentication flows in Power Pages

- Implicit grant
  - This flow is the default authentication method for Power Pages sites.
- Authorization code
  - Power Pages uses the *client_secret_post* method to communicate with the identity server's token endpoint.
  - The *private_key_jwt* method to authenticate with the token endpoint isn't supported.
- Hybrid (restricted support)
  - Power Pages requires *id_token* to be present in the response, so *response_type* = *code token* isn't supported.
  - The hybrid flow in Power Pages follows the same flow as implicit grant, and uses *id_token* to directly sign in users.
- Proof Key for Code Exchange (PKCE)
  - PKCE&ndash;based techniques to authenticate users aren't supported.

> [!NOTE]
> Changes to your site's authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the site. To see the changes immediately, restart the site in the [admin center](../../admin/admin-overview.md).

## Set up the OpenID Connect provider in Power Pages

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. Select **+ New provider**.

1. Under **Select login provider**, select **Other**.

1. Under **Protocol**, select **OpenID Connect**.

1. Enter a name for the provider.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an app registration in the identity provider

1. Create and register an application with your identity provider using the reply URL [you copied](#set-up-the-openid-connect-provider-in-power-pages).

1. Copy the application or client ID and the client secret.

1. Find the application's endpoints and copy the **OpenID Connect metadata document** URL.

1. Change other settings as needed for your identity provider.

## Enter site settings in Power Pages

Return to the Power Pages **Configure identity provider** page you left earlier and enter the following values. Optionally, change the [**additional settings**](#additional-settings-in-power-pages) as needed. Select **Confirm** when you're finished.

- **Authority**: Enter the authority URL in the following format: `https://login.microsoftonline.com/<Directory (tenant) ID>/`, where *<Directory (tenant) ID>* is the directory (tenant) ID of the application [you created](#create-an-app-registration-in-the-identity-provider). For example, if the directory (tenant) ID in the Azure portal is `aaaabbbb-0000-cccc-1111-dddd2222eeee`, then the authority URL is `https://login.microsoftonline.com/aaaabbbb-0000-cccc-1111-dddd2222eeee/​`.

- **Client ID​**: Paste the application or client ID of the application [you created](#create-an-app-registration-in-the-identity-provider).

- **Redirect URL**: If your site uses a custom domain name, enter the custom URL; otherwise, leave the default value. Be sure the value is exactly the same as the redirect URI of the application [you created](#create-an-app-registration-in-the-identity-provider).

- **Metadata address**: Paste the OpenID Connect metadata document URL [you copied](#create-an-app-registration-in-the-identity-provider).

- **Scope**: Enter a space-separated list of scopes to request using the OpenID Connect `scope` parameter. The default value is `openid`.

    The `openid` value is mandatory. [Learn about other claims you can add](openid-settings.md#set-up-additional-claims).

- **Response type**: Enter the value of the OpenID Connect `response_type` parameter. Possible values include `code`, `code id_token`, `id_token`, `id_token token`, and `code id_token token`. The default value is `code id_token`.

- **Client secret**: Paste the client secret from the provider application. It might also be referred to as an *app secret* or *consumer secret*. This setting is required if the response type is `code`.

- **Response mode**: Enter the value of the OpenID Connect *response_mode* parameter. It should be `query` if the response type is `code`. The default value is `form_post`.

- **External logout**: This setting controls whether your site uses federated sign-out. With federated sign-out, when users sign out of an application or site, they're also signed out of all applications and sites that use the same identity provider. Turn it on to redirect users to the federated sign-out experience when they sign out of your website. Turn it off to sign users out of your website only.

- **Post logout redirect URL**: Enter the URL where the identity provider should redirect users after they sign out. This location should be set appropriately in the identity provider configuration.

- **RP initiated logout**: This setting controls whether the relying party&mdash;the OpenID Connect client application&mdash;can sign out users. To use this setting, turn on **External logout**.

### Additional settings in Power Pages

The additional settings give you finer control over how users authenticate with your OpenID Connect identity provider. You don't need to set any of these values. They're entirely optional.

- **Issuer filter**: Enter a wildcard-based filter that matches on all issuers across all tenants; for example, `https://sts.windows.net/*/`. If you are using a Microsoft Entra ID auth provider, the issuer URL filter would be `https://login.microsoftonline.com/*/v2.0/`.

- **Validate audience**: Turn on this setting to validate the audience during token validation.

- **Valid audiences**: Enter a comma-separated list of audience URLs.

- **Validate issuers**: Turn on this setting to validate the issuer during token validation.

- **Valid issuers**: Enter a comma-separated list of issuer URLs.

- **Registration claims mapping​** and **Login claims mapping**: In user authentication, a *claim* is information that describes a user's identity, like an email address or date of birth. When you sign in to an application or a website, it creates a *token*. A token contains information about your identity, including any claims that are associated with it. Tokens are used to authenticate your identity when you access other parts of the application or site or other applications and sites that are connected to the same identity provider. *Claims mapping* is a way to change the information that's included in a token. It can be used to customize the information that's available to the application or site and to control access to features or data. *Registration claims mapping* modifies the claims that are emitted when you register for an application or a site. *Login claims mapping* modifies the claims that are emitted when you sign in to an application or a site. [Learn more about claims mapping policies](/azure/active-directory/develop/reference-claims-mapping-policy-type).

    User information can be provided in two ways:

  - **ID Token Claims** – Basic user attributes like first name or email are in the token.
  - **UserInfo Endpoint** – A secure API that returns detailed user information after authentication.

  To use the UserInfo endpoint, create a [Site Setting](/power-apps/maker/portals/configure/configure-site-settings) named **Authentication/OpenIdConnect/{ProviderName}/UseUserInfoEndpointforClaims** and set the value to **true**.

  Optionally, create a site setting named **Authentication/OpenIdConnect/{ProviderName}/UserInfoEndpoint** and set the value to the UserInfo endpoint URL. If you don't provide this setting, Power Pages tries to find the endpoint from OIDC metadata.

  **Error handling**:
  
  - If the endpoint URL isn't set and Power Pages can't find it in metadata, sign in continues and logs a warning.
  - If the URL is set but isn't accessible, sign in continues with a warning.
  - If the endpoint returns an authentication error (like 401 or 403), sign in continues with a warning that includes the error message.

  **Mapping syntax:**

  To use UserInfo claims in login or registration claim mappings, use this format:

  fieldName = userinfo.claimName

  If UseUserInfoEndpointforClaims isn't enabled, mappings that use the `userinfo.` prefix are ignored.

- **Nonce lifetime**: Enter the lifetime of the nonce value, in minutes. The default value is 10 minutes.

- **Use token lifetime**: This setting controls whether the authentication session lifetime, such as cookies, should match that of the authentication token. If you turn it on, this value overrides the **Application Cookie Expire Timespan** value in the **Authentication/ApplicationCookie/ExpireTimeSpan** site setting.

- **Contact mapping with email**: This setting determines whether contacts are mapped to a corresponding email address when they sign in.

  - **On**: Associates a unique contact record with a matching email address and automatically assigns the external identity provider to the contact after the user successfully signs in.
  - **Off**

> [!Note]
> The *UI_Locales* request parameter is sent automatically in the authentication request and is set to the language selected on the portal.

## Other authorization parameters

You can use the following authorization parameters, but you don't set them within the OpenID Connect provider in Power Pages:

- **acr_values**: The acr_values parameter lets identity providers enforce security assurance levels like multifactor authentication (MFA). It lets the app indicate the required authentication level.

  To use the acr_values parameter, create a [site setting](../../configure/configure-site-settings.md) named **Authentication/OpenIdConnect/{ProviderName}/AcrValues** and set the value you need. When you set this, Power Pages includes the acr_values parameter in the authorization request.

- **Dynamic authorization parameters**: Dynamic parameters let you tailor the authorization request for different usage contexts, like embedded apps or multiple tenant scenarios.

  - **Prompt parameter**:

    This parameter controls whether the sign-in page or consent screen appears. To use it, add a customization to send it as a query string parameter to the ExternalLogin endpoint.

    **Supported values**:

    - none
    - login
    - consent
    - select_account

    **URL format**:

    `{PortalUrl}/Account/Login/ExternalLogin?ReturnUrl=%2F&provider={ProviderName}&prompt={value}`

    Power Pages sends this value to the identity provider in the prompt parameter. 

  - **Login hint parameter**:
  
    This parameter lets you pass a known user identifier, like an email, to prefill or bypass sign-in screens. To use it, add a customization to send it as a query string parameter to the ExternalLogin endpoint.

    **URL format**:

    `{PortalUrl}/Account/Login/ExternalLogin?ReturnUrl=%2F&provider={ProviderName}&login_hint={value}`

    This helps when users are already signed in through another identity, like Microsoft Entra ID or Microsoft account (MSA), in the same session.

- **Custom authorization parameters**: Some identity providers support proprietary parameters for specific authorization behavior. Power Pages lets makers set up and pass these parameters securely. To use these parameters, add a customization to send them as query string parameters to the ExternalLogin endpoint.

  Create a [site setting](../../configure/configure-site-settings.md) named **Authentication/OpenIdConnect/{Provider}/AllowedDynamicAuthorizationParameters** and set the value to a comma-separated list of parameter names, like param1,param2,param3.

  **Example URL format**:

  `{PortalUrl}/Account/Login/ExternalLogin?ReturnUrl=%2F&provider={ProviderName}&param1=value&param2=value&param3=value`

  If any of the params (param1 or param2 or param3) isn't in the list of allowed parameters, Power Pages ignores it.

  This setting defines a list of custom parameters that can be sent in the authorization request.

  **Behavior**

  - Pass parameters in the query string of the ExternalLogin endpoint.
  - Power Pages includes only parameters in the list in the authorization request.
  - Default parameters like prompt, login_hint, and ReturnUrl are always allowed and don't need to be listed.

  **Example URL format**:

  `{PortalUrl}/Account/Login/ExternalLogin?ReturnUrl=%2F&provider={ProviderName}&custom_param=value`

  If custom_param isn't in the list of allowed parameters, Power Pages ignores it.

### See also

[Set up an OpenID Connect provider with Azure Active Directory (Azure AD) B2C](azure-ad-b2c-provider.md)  
[Set up an OpenID Connect provider with Microsoft Entra ID](openid-settings.md)  
[OpenID Connect FAQs](openid-faqs.md)
