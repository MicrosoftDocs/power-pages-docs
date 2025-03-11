---
title: Set up the Twitter provider
description: Learn how to set up Twitter as the OAuth 2.0 identity provider for use with sites you create with Microsoft Power Pages.
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

# Set up the Twitter provider

Twitter is one of the [OAuth 2.0 identity providers](oauth2-provider.md) you can use to [authenticate visitors](configure-site.md) to your Power Pages site. OAuth 2.0&ndash;based identity providers require a *client ID*, *client secret*, and sometimes a *redirect or reply URL*. This article describes the following steps:

- [Set up Twitter in Power Pages](#set-up-twitter-in-power-pages)
- [Create an app registration in Twitter](#create-an-app-registration-in-twitter)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)

## Set up Twitter in Power Pages

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. To the right of **Twitter**, select **More Commands** (**&hellip;**) > **Configure** or select the provider name.

1. Leave the provider name as it is or change it if you like.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

1. Select **Open Twitter**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an app registration in Twitter

[Register an application in Twitter](https://developer.twitter.com/en/docs/apps/overview) with your site's reply URL as the redirect URL.

> [!NOTE]
> If you [use or add a custom domain name](../../admin/add-custom-domain.md) or [change your site's base URL](/power-apps/maker/portals/admin/change-base-url), you must set up your identity provider to use the correct reply URL. The Twitter app uses the reply URL to redirect users to your website after authentication.

1. Sign in to [Twitter Application Management](https://apps.twitter.com/).

1. Select **Create New App**.

1. Enter the name of your app and a brief description.

1. Enter your site's URL.

1. In **Callback URL**, paste the reply URL [you copied](#set-up-twitter-in-power-pages).

1. Select **Create your Twitter application**.

1. Select **Create my access token**.

1. Select the **Keys and Access Tokens** tab.

1. Copy the **Consumer Key (API Key)** and **Consumer Secret (API Secret)**.

## Enter site settings in Power Pages

1. Return to the Power Pages **Configure identity provider** page you left earlier.

1. Under **Configure site settings**, paste the following values:

    - **Client ID​**: Paste the **Consumer Key** [you copied](#create-an-app-registration-in-twitter).
    - **Client secret**: Paste the **Consumer Secret** you copied.

[Optional additional settings for OAuth 2.0 identity providers](oauth2-settings.md)

### See also

[Set up site authentication](configure-site.md)
