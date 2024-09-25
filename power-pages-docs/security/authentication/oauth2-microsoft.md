---
title: Set up the Microsoft provider
description: Learn how to set up Microsoft as the OAuth 2.0 identity provider for use with sites you create with Microsoft Power Pages.
ms.date: 09/10/2024
ms.topic: how-to
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Set up the Microsoft provider

Microsoft is one of the [OAuth 2.0 identity providers](oauth2-provider.md) you can use to [authenticate visitors](configure-site.md) to your Power Pages site. OAuth 2.0&ndash;based identity providers require a *client ID*, *client secret*, and sometimes a *redirect or reply URL*. This article describes the following steps:

- [Set up Microsoft in Power Pages](#set-up-microsoft-in-power-pages)
- [Create an app registration in Azure](#create-a-microsoft-app-registration-in-azure)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)

## Set up Microsoft in Power Pages

Set Microsoft as an identity provider for your site.

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. To the right of **Microsoft**, select **More Commands** (**&hellip;**) > **Configure** or select the provider name.

1. Leave the provider name as it is or change it if you like.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

1. Select **Open Microsoft**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create a Microsoft app registration in Azure

[Register an application](/azure/active-directory/develop/quickstart-register-app) with your site's reply URL as the redirect URI.

> [!NOTE]
> If you [use or add a custom domain name](../../admin/add-custom-domain.md) or [change your site's base URL](/power-apps/maker/portals/admin/change-base-url), you must set up your identity provider to use the correct reply URL. The Microsoft app uses the reply URL to redirect users to your website after authentication.

1. In the Azure portal, select **New registration**.

1. Enter a name.

1. Select one of the **Supported account types** that best reflects your organization requirements.

1. Under **Redirect URI**, select **Web** as the platform, and then paste the reply URL [you copied](#set-up-microsoft-in-power-pages) over the example in the box.

1. Select **Register**.

1. Copy the **Application (client) ID**.

1. To the right of **Client credentials**, select **Add a certificate or secret**.

1. Select **+ New client secret**.

1. Enter an optional description, select an expiration, and then select **Add**.

1. Under **Secret ID**, select the **Copy to clipboard** icon.

## Enter site settings in Power Pages

1. Return to the Power Pages **Configure identity provider** page you left earlier.

1. Under **Configure site settings**, paste the following values:

    - **Client ID​**: Paste the **Application (client) ID** [you copied](#create-a-microsoft-app-registration-in-azure).
    - **Client secret**: Paste the **Secret ID** you copied.

[Optional additional settings for OAuth 2.0 identity providers](oauth2-settings.md)

### See also

[Set up site authentication](configure-site.md)
