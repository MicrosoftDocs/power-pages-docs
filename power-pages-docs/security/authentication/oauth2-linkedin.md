---
title: Set up the LinkedIn provider
description: Learn how to set up LinkedIn as the OAuth 2.0 identity provider for use with sites you create with Microsoft Power Pages.
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

# Set up the LinkedIn provider

LinkedIn is one of the [OAuth 2.0 identity providers](oauth2-provider.md) you can use to [authenticate visitors](configure-site.md) to your Power Pages site. OAuth 2.0&ndash;based identity providers require a *client ID*, *client secret*, and sometimes a *redirect or reply URL*. This article describes the following steps:

- [Set up LinkedIn in Power Pages](#set-up-linkedin-in-power-pages)
- [Create an app registration in LinkedIn](#create-an-app-registration-in-linkedin)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)

## Set up LinkedIn in Power Pages

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. To the right of **LinkedIn**, select **More Commands** (**&hellip;**) > **Configure** or select the provider name.

1. Leave the provider name as it is or change it if you like.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

1. Select **Open LinkedIn**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an app registration in LinkedIn

Register an application in LinkedIn with your site's reply URL as the redirect URL.

> [!NOTE]
> If you [use or add a custom domain name](../../admin/add-custom-domain.md) or [change your site's base URL](/power-apps/maker/portals/admin/change-base-url), you must set up your identity provider to use the correct reply URL. The LinkedIn app uses the reply URL to redirect users to your website after authentication.

1. In the LinkedIn developer portal, select **My apps**, and then select **Create app**.

1. Enter the name of the app and the URL of your organization's LinkedIn page to associate with the app.

1. Upload a graphic file to use as the logo that visitors see when they authenticate with the app.

1. Select **I have read and agree to these terms**, and then select **Create app**.

1. On the app page, select the **Auth** tab.

1. Under **Authentication keys**, copy the **Client ID**, and then reveal and copy the **Client Secret**.

1. Under **OAuth 2.0 settings**, select the pencil icon.

1. Select **+ Add redirect URL**, paste the reply URL [you copied](#set-up-linkedin-in-power-pages), and then select **Update**.

## Enter site settings in Power Pages

1. Return to the Power Pages **Configure identity provider** page you left earlier.

1. Under **Configure site settings**, paste the following values:

    - **Client ID​**: Paste the **Client ID** [you copied](#create-an-app-registration-in-linkedin).
    - **Client secret**: Paste the **Client Secret** you copied.

[Optional additional settings for OAuth 2.0 identity providers](oauth2-settings.md)

### See also

[Set up site authentication](configure-site.md)
