---
title: Set up the Facebook provider
description: Learn how to set up Facebook as the OAuth 2.0 identity provider for use with sites you create with Microsoft Power Pages.
ms.date: 09/10/2024
ms.topic: how-to
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Set up the Facebook provider

Facebook is one of the [OAuth 2.0 identity providers](oauth2-provider.md) you can use to [authenticate visitors](configure-site.md) to your Power Pages site. OAuth 2.0&ndash;based identity providers require a *client ID*, *client secret*, and sometimes a *redirect or reply URL*. This article describes the following steps:

- [Set up Facebook in Power Pages](#set-up-facebook-in-power-pages)
- [Create an app registration in Facebook](#create-an-app-registration-in-facebook)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)

## Set up Facebook in Power Pages

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. To the right of **Facebook**, select **More Commands** (**&hellip;**) > **Configure** or select the provider name.

1. Leave the provider name as it is or change it if you like.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

1. Select **Open Facebook**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an app registration in Facebook

[Register an application in Facebook](https://developers.facebook.com/docs/development/create-an-app) with your site's reply URL as the redirect URL.

> [!NOTE]
> If you [use or add a custom domain name](../../admin/add-custom-domain.md) or [change your site's base URL](/power-apps/maker/portals/admin/change-base-url), you must set up your identity provider to use the correct reply URL. The Facebook app uses the reply URL to redirect users to your website after authentication.

### Create an app in Facebook

1. Sign in to the [Facebook Developers App Dashboard](https://developers.facebook.com/apps).

1. Select **Create App**.

1. Select **Consumer** as the app type, and then select **Continue**.

1. Enter the name of your app and an email address where you can receive developer notifications from Facebook.

1. Select **Create App**.

    If prompted, accept Facebook platform policies and complete an online security check.

1. Open the **Settings** > **Basic** tab and enter the following details:

    - (Optional) **App Domains**; for example, `contoso.powerappsportals.com`
    - (Optional) **Privacy Policy URL**: The URL of your organization's privacy policy, which must be accessible anonymously
    - **User Data Deletion**: The callback URL or the instructions URL for user data deletion
    - An appropriate **App Purpose**

1. Select **Add Platform**, select **Website**, and then paste the reply URL [you copied](#set-up-facebook-in-power-pages).

1. Select **Save Changes**.

1. In the left side panel, select **Add Products**.

1. Select **Set Up** for **Facebook Login**, and then select **Web**.

1. Select **Save**.

1. Under **Facebook Login**, select **Settings**.

1. In **Valid OAuth redirect URIs**, paste the reply URL [you copied](#set-up-facebook-in-power-pages).
​
1. Select **Save Changes**.

### Publish the app

1. In the left side panel, select **Settings**.

1. In the notification that starts with "Your app has Standard Access to public_profile," select **Get Advanced Access**.

    You can also select **App Review** in the left side panel, and then select **Permissions and Features**.

1. Select **Get Advanced Access** for **public_profile**.

1. Confirm the change.

    If prompted, accept Facebook platform policies and complete an online security check.

1. At the top of the page, select **Live** for the **App Mode**.

1. When prompted, select **Start checkup**.

1. Review and confirm the data use certification, certify the compliance policies, and then select **Submit**.

1. At the top of the page, select **Live** for the **App Mode**.

1. Select **Settings** > **Basic**.

1. Copy the **App ID** and **App Secret**.

## Enter site settings in Power Pages

1. Return to the Power Pages **Configure identity provider** page you left earlier.

1. Under **Configure site settings**, paste the following values:

    - **Client ID​**: Paste the **App ID** [you copied](#publish-the-app).
    - **Client secret**: Paste the **App Secret** you copied.

[Optional additional settings for OAuth 2.0 identity providers](oauth2-settings.md)

### See also

[Set up site authentication](configure-site.md)
