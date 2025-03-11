---
title: Set up a WS-Federation provider
description: Learn how to set up a WS-Federation provider for use with sites you create with Microsoft Power Pages.
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

# Set up a WS-Federation provider

To allow users to authenticate to your Power Pages site, you can add a WS-Federation&ndash;compliant security token service provider such as Microsoft Entra or a single Active Directory Federation Services (AD FS) server. This article describes the following steps:

- [Set up the WS-Federation provider in Power Pages](#set-up-the-ws-federation-provider-in-power-pages)
- [Create an app registration in the identity provider](#create-an-app-registration-in-the-identity-provider)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)

> [!NOTE]
> Changes to your site's authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the site. To see the changes immediately, restart the site in the [admin center](../../admin/admin-overview.md).

## Set up the WS-Federation provider in Power Pages

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. Select **+ New provider**.

1. Under **Select login provider**, select **Other**.

1. Under **Protocol**, select **WS-Federation**.

1. Enter a name for the provider.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an app registration in the identity provider

1. Create and register an application with your identity provider using the reply URL [you copied](#set-up-the-ws-federation-provider-in-power-pages).

1. Find the application's endpoints and copy the **Federation metadata document** URL.

1. In a new browser tab, paste the federation metadata document URL you copied.

1. Copy the value of the `entityID` tag in the document.

## Enter site settings in Power Pages

Return to the Power Pages **Configure identity provider** page you left earlier and enter the following values. Optionally, change the [**additional settings**](#additional-settings-in-power-pages) as needed. Select **Confirm** when you're finished.

- **Metadata address**: Paste the federation metadata document URL [you copied](#create-an-app-registration-in-the-identity-provider).

- **Authentication type**: Paste the `entityID` value [you copied](#create-an-app-registration-in-the-identity-provider).

- **Service provider realm**: Enter your site's URL.

- **Assertion service consumer URL**: If your site uses a custom domain name, enter the custom URL; otherwise, leave the default value, which should be your site's reply URL. Be sure the value is exactly the same as the redirect URI of the application [you created](#create-an-app-registration-in-the-identity-provider).

### Additional settings in Power Pages

The additional settings give you finer control over how users authenticate with your WS-Federation identity provider. You don't need to set any of these values. They're entirely optional.

- **Sign-out reply**: Enter the URL to return to after the user signs out.

- **Validate audience**: Turn on this setting to validate the audience during token validation.

- **Valid audiences**: Enter a comma-separated list of audience URLs.

- **WHR**: Enter the home realm of the identity provider. This value sets the WS-Federation sign-in request [`whr` parameter](/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation). If this setting is empty, the `whr` parameter isn't included in the request.

- **Contact mapping with email**: This setting determines whether contacts are mapped to a corresponding email address when they sign in.

  - **On**: Associates a unique contact record with a matching email address and automatically assigns the external identity provider to the contact after the user successfully signs in.
  - **Off**

### See also

[Set up a WS-Federation provider with Microsoft Entra ID](ws-federation-settings-azure-ad.md)  
[Set up a WS-Federation provider with AD FS](ws-federation-settings.md)