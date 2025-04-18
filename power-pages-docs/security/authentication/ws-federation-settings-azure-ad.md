---
title: Set up a WS-Federation provider with Microsoft Entra ID
description: Learn how to set up a WS-Federation identity provider with Microsoft Entra ID use with sites you create with Microsoft Power Pages.
ms.date: 09/24/2024
ms.topic: how-to
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
    - nageshbhat-msft
ms.custom: bap-template
---
# Set up a WS-Federation provider with Microsoft Entra ID

Microsoft Entra is one of the WS-Federation identity providers you can use to [authenticate visitors](configure-site.md) to your Power Pages site. You can use any provider that conforms to the WS-Federation specification.

This article describes the following steps:

- [Set up Microsoft Entra in Power Pages](#set-up-microsoft-entra-in-power-pages)
- [Create an app registration in Azure](#create-an-app-registration-in-azure)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)

> [!NOTE]
> Changes to your site's authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the site. To see the changes immediately, restart the site in the [admin center](../../admin/admin-overview.md).

## Set up Microsoft Entra in Power Pages

Set Microsoft Entra as an identity provider for your site.

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. Select **+ New provider**.

1. Under **Select login provider**, select **Other**.

1. Under **Protocol**, select **WS-Federation**.

1. Enter a name for the provider; for example, *Microsoft Entra ID*.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

    Don't close your Power Pages browser tab. You'll return to it soon.

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
    - If you're using a custom domain name, enter the custom URL. Be sure to use the same custom URL for the assertion service consumer URL in the settings for the identity provider on your site.

1. Select **Register**.

1. Select **Endpoints** at the top of the page.

1. Find the **Federation metadata document** URL and select the copy icon.

1. In the left side panel, select **Expose an API**.

1. To the right of **Application ID URI**, select **Add**.

1. If you're using a custom domain name, enter your site URL. Otherwise, leave the auto-generated URI. You'll need to [change the app ID URI](#update-app-id-uri-in-site-settings) in your site settings to match.

    Due to a recent update, the app ID URI must be the auto-generated URI or a verified custom domain name.

1. Select **Save**.

1. In a new browser tab, paste the federation metadata document URL you copied earlier.

1. Copy the value of the `entityID` tag in the document.

## Enter site settings in Power Pages

Return to the Power Pages **Configure identity provider** page you left earlier and enter the following values. Optionally, change the [**additional settings**](#additional-settings-in-power-pages) as needed. Select **Confirm** when you're finished.

- **Metadata address**: Paste the federation metadata document URL [you copied](#create-an-app-registration-in-azure).

- **Authentication type**: Paste the `entityID` value [you copied](#create-an-app-registration-in-azure).

- **Service provider realm**: Enter your site's URL.

- **Assertion service consumer URL**: If your site uses a custom domain name, enter the custom URL; otherwise, leave the default value, which should be your site's reply URL. Be sure the value is exactly the same as the redirect URI of the application [you created](#create-an-app-registration-in-azure).

### Additional settings in Power Pages

The additional settings give you finer control over how users authenticate with your SAML 2.0 identity provider. You don't need to set any of these values. They're entirely optional.

- **Sign-out reply**: Enter the URL to return to after the user signs out.

- **Validate audience**: Turn on this setting to validate the audience during token validation.

- **Valid audiences**: Enter a comma-separated list of audience URLs.

- **WHR**: Enter the home realm of the identity provider. This value sets the WS-Federation sign-in request [`whr` parameter](/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation). If this setting is empty, the `whr` parameter isn't included in the request.

- **Contact mapping with email**: This setting determines whether contacts are mapped to a corresponding email address when they sign in.

  - **On**: Associates a unique contact record with a matching email address and automatically assigns the external identity provider to the contact after the user successfully signs in.
  - **Off**

### Update app ID URI in site settings

If you're using the auto-generated URI for the app ID URI, you'll need to change the value in your site settings.

1. Open the Portal Management app and go to **Site Settings**.

1. Change the value of the site setting **Authentication/WsFederation/WSFederation_1/Wtrealm** to the auto-generated app ID URI.

1. Select **Save**.

### See also

[Set up a WS-Federation provider](ws-federation-provider.md)  
[Set up a WS-Federation provider with AD FS](ws-federation-settings.md)