---
title: Set up an OpenID Connect provider with Microsoft Entra ID
description: Learn how to set up an OpenID Connect identity provider with Microsoft Entra ID use with sites you create with Microsoft Power Pages.
ms.date: 02/07/2025
ms.topic: how-to
author: DanaMartens
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
    - nageshbhat-msft
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# Set up an OpenID Connect provider with Microsoft Entra ID

Microsoft Entra is one of the OpenID Connect identity providers you can use to [authenticate visitors](configure-site.md) to your Power Pages site. Along with Microsoft Entra ID, multitenant Microsoft Entra ID, and Azure AD B2C, you can use any other provider that conforms to the [Open ID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html).

This article describes the following steps:

- [Set up Microsoft Entra in Power Pages](#set-up-microsoft-entra-in-power-pages)
- [Create an app registration in Azure](#create-an-app-registration-in-azure)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)
- [Allow multitenant Microsoft Entra authentication](#allow-multitenant-microsoft-entra-authentication)

> [!NOTE]
> Changes to your site's authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the site. To see the changes immediately, restart the site in the [admin center](../../admin/admin-overview.md).

## Set up Microsoft Entra in Power Pages

Set Microsoft Entra as an identity provider for your site.

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. Select **+ New provider**.

1. Under **Select login provider**, select **Other**.

1. Under **Protocol**, select **OpenID Connect**.

1. Enter a name for the provider; for example, *Microsoft Entra ID*.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

    Don't close your Power Pages browser tab. You return to it soon.

## Create an app registration in Azure

[Create an app registration in the Azure portal](/azure/active-directory/develop/quickstart-register-app) with your site's reply URL as the redirect URI.

1. Sign in to the [Azure portal](https://portal.azure.com).

1. Search for and select **Azure Active Directory**.

1. Under **Manage**, select **App registrations**.

1. Select **New registration**.

1. Enter a name.

1. Select one of the [**Supported account types**](/azure/active-directory/develop/quickstart-register-app) that best reflects your organization requirements.

1. Under **Redirect URI**, select **Web** as the platform, and then enter the reply URL of your site.

    - If you're using your site's default URL, paste the reply URL [you copied](#set-up-microsoft-entra-in-power-pages).
    - If you're using a custom domain name, enter the custom URL. Be sure to use the same custom URL for the redirect URL in the settings for the identity provider on your site.

1. Select **Register**.

1. Copy the **Application (client) ID**.

1. To the right of **Client credentials**, select **Add a certificate or secret**.

1. Select **+ New client secret**.

1. Enter an optional description, select an expiration, and then select **Add**.

1. Under **Secret ID**, select the **Copy to clipboard** icon.

1. Select **Overview** and then select **Endpoints** at the top of the page.

1. Find the **OpenID Connect metadata document** URL and select the copy icon.

1. In the left side panel, under **Manage**, select **Authentication**.

1. Under **Implicit grant**, select **ID tokens (used for implicit and hybrid flows)**.

1. Select **Save**.

## Enter site settings in Power Pages

Return to the Power Pages **Configure identity provider** page you left earlier and enter the following values. Optionally, change the [**additional settings**](#additional-settings-in-power-pages) as needed. Select **Confirm** when you're finished.

- **Authority**: Enter the authority URL in the following format: `https://login.microsoftonline.com/<Directory (tenant) ID>/`, where *<Directory (tenant) ID>* is the directory (tenant) ID of the application [you created](#create-an-app-registration-in-azure). For example, if the directory (tenant) ID in the Azure portal is `aaaabbbb-0000-cccc-1111-dddd2222eeee`, then the authority URL is `https://login.microsoftonline.com/aaaabbbb-0000-cccc-1111-dddd2222eeee/​`.

- **Client ID​**: Paste the application or client ID of the application [you created](#create-an-app-registration-in-azure).

- **Redirect URL**: If your site uses a custom domain name, enter the custom URL; otherwise, leave the default value. Be sure the value is exactly the same as the redirect URI of the application [you created](#create-an-app-registration-in-azure).

- **Metadata address**: Paste the OpenID Connect metadata document URL [you copied](#create-an-app-registration-in-azure).

- **Scope**: Enter `openid email`.

    The `openid` value is mandatory. The `email` value is optional; it ensures that the user's email address is automatically filled in and shown on the profile page after the user signs in. [Learn about other claims you can add](openid-settings.md#set-up-additional-claims).

- **Response type**: Select `code id_token`.

- **Client secret**: Paste the client secret from the application [you created](#create-an-app-registration-in-azure). This setting is required if the response type is `code`.

- **Response mode**: Select `form_post`.

- **External logout**: This setting controls whether your site uses federated sign-out. With federated sign-out, when users sign out of an application or site, they're also signed out of all applications and sites that use the same identity provider. Turn it on to redirect users to the federated sign-out experience when they sign out of your website. Turn it off to sign users out of your website only.

- **Post logout redirect URL**: Enter the URL where the identity provider should redirect users after they sign out. This location should be set appropriately in the identity provider configuration.
- **RP initiated logout**: This setting controls whether the relying party&mdash;the OpenID Connect client application&mdash;can sign out users. To use this setting, turn on **External logout**.

### Additional settings in Power Pages

The additional settings give you finer control over how users authenticate with your Microsoft Entra identity provider. You don't need to set any of these values. They're entirely optional.

- **Issuer filter**: Enter a wildcard-based filter that matches on all issuers across all tenants; for example, `https://sts.windows.net/*/`.

- **Validate audience**: Turn on this setting to validate the audience during token validation.

- **Valid audiences**: Enter a comma-separated list of audience URLs.

- **Validate issuers**: Turn on this setting to validate the issuer during token validation.

- **Valid issuers**: Enter a comma-separated list of issuer URLs.

- **Registration claims mapping​** and **Login claims mapping**: In user authentication, a *claim* is information that describes a user's identity, like an email address or date of birth. When you sign in to an application or a website, it creates a *token*. A token contains information about your identity, including any claims that are associated with it. Tokens are used to authenticate your identity when you access other parts of the application or site or other applications and sites that are connected to the same identity provider. *Claims mapping* is a way to change the information included in a token. It can be used to customize the information that's available to the application or site and to control access to features or data. *Registration claims mapping* modifies the claims that are emitted when you register for an application or a site. *Login claims mapping* modifies the claims that are emitted when you sign in to an application or a site. [Learn more about claims mapping policies](/azure/active-directory/develop/reference-claims-mapping-policy-type).

- **Nonce lifetime**: Enter the lifetime of the nonce value, in minutes. The default value is 10 minutes.

- **Use token lifetime**: This setting controls whether the authentication session lifetime, such as cookies, should match that of the authentication token. If you turn it on, this value overrides the **Application Cookie Expire Timespan** value in the **Authentication/ApplicationCookie/ExpireTimeSpan** site setting.

- **Contact mapping with email**: This setting determines whether contacts are mapped to a corresponding email address when they sign in.

  - **On**: Associates a unique contact record with a matching email address and automatically assigns the external identity provider to the contact after the user successfully signs in.
  - **Off**

> [!Note]
> The *UI_Locales* request parameter is sent automatically in the authentication request and is set to the language selected on the portal.

## Set up additional claims

1. Enable [optional claims in Microsoft Entra ID](/azure/active-directory/develop/active-directory-optional-claims#configuring-directory-extension-optional-claims).

1. Set **Scope** to include the additional claims; for example, `openid email profile`.

1. Set the **Registration claims mapping** additional site setting; for example, `firstname=given_name,lastname=family_name`.

1. Set the **Login claims mapping** additional site setting; for example, `firstname=given_name,lastname=family_name`.

In these examples, the first name, last name, and email addresses supplied with the additional claims become the default values in the profile page in the website.

> [!NOTE]
> Claims mapping is supported for text and boolean data types.

## Allow multitenant Microsoft Entra authentication

To allow Microsoft Entra users to authenticate from any tenant in Azure, not just from a specific tenant, [change the Microsoft Entra application registration](/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant#update-registration-to-be-multi-tenant) to multitenant.

You also need to set **Issuer filter** in your provider's [additional settings](#additional-settings-in-power-pages).

### See also

[OpenID Connect FAQs](openid-faqs.md)