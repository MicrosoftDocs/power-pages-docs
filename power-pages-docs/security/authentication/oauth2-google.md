---
title: Set up the Google provider
description: Learn how to set up Google as the OAuth 2.0 identity provider for use with sites you create with Microsoft Power Pages.
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

# Set up the Google provider

Google is one of the [OAuth 2.0 identity providers](oauth2-provider.md) you can use to [authenticate visitors](configure-site.md) to your Power Pages site. OAuth 2.0&ndash;based identity providers require a *client ID*, *client secret*, and sometimes a *redirect or reply URL*. This article describes the following steps:

- [Set up Google in Power Pages](#set-up-google-in-power-pages)
- [Create an app registration in Google](#create-an-app-registration-in-google)
- [Enter site settings in Power Pages](#enter-site-settings-in-power-pages)

## Set up Google in Power Pages

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. To the right of **Google**, select **More Commands** (**&hellip;**) > **Configure** or select the provider name.

1. Leave the provider name as it is or change it if you like.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

1. Select **Open Google**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an app registration in Google

[Register an application in Google](https://cloud.google.com/apigee/docs/api-platform/publish/creating-apps-surface-your-api) with your site's reply URL as the redirect URL.

> [!NOTE]
> If you [use or add a custom domain name](../../admin/add-custom-domain.md) or [change your site's base URL](/power-apps/maker/portals/admin/change-base-url), you must set up your identity provider to use the correct reply URL. The Google app uses the reply URL to redirect users to your website after authentication.

### Add the API

1. Open the [Google Developers Console](https://console.developers.google.com/).

1. Create or open an API project.

1. In the left side panel, select **APIs & Services**.

1. Select **+ Enable APIs and Services**.

1. Search for and enable **Google People API**.

   > [!IMPORTANT]
   > [Google+ API](https://developers.google.com/people/legacy) is deprecated. We strongly recommend that you migrate to [Google People API](https://developers.google.com/people).

### Set up your consent screen

If you already have a consent screen for your website's top-level domain, skip to [Add credentials](#add-credentials). If your site has a consent screen but you haven't added the top-level domain, skip to [Enter your top-level domain](#enter-your-top-level-domain).

1. In the left side panel, select **Credentials**.

1. Select **Configure consent screen**.

1. Select the **External** user type.

1. Select **Create**.

1. Enter the name of the application and select your organization's user support email address.

1. Upload a logo image file if necessary.

1. Enter the URLs of your site's home page, privacy policy, and terms of service, if applicable.

1. Enter an email address where Google can send you developer notifications.

### Enter your top-level domain

1. Under **Authorized domains**, select **+ Add Domain**.

1. Enter your site's top-level domain; for example, `powerappsportals.com`.

   > [!TIP]
   > Use `microsoftcrmportals.com` if you haven't [updated your domain name](/power-apps/maker/portals/admin/update-portal-domain). If your site uses a [custom domain name](/power-apps/maker/portals/admin/add-custom-domain), enter it instead.

1. Select **Save and Continue**.

### Add credentials

1. In the left side panel, select **Credentials**.

1. Select **Create credentials** > **OAuth client ID**.

1. Select **Web application** as the application type.

1. Enter a name to identify your OAuth Client; for example, `Web sign-in`.

    This name is for internal use only and isn't shown to users.

1. Under **Authorized JavaScript origins**, select **+ Add URI**.

1. Enter your site's URL; for example, `https://contoso.powerappsportals.com`.

1. Under **Authorized redirect URIs**, select **+ Add URI**.

1. Enter your site's URL followed by `/signin-google`; for example, `https://contoso.powerappsportals.com/signin-google`.

1. Select **Create**.

1. In the **OAuth client created** window, select the copy icons to copy the **Client ID** and **Client secret**.

1. Select **OK**.

## Enter site settings in Power Pages

1. Return to the Power Pages **Configure identity provider** page you left earlier.

1. Under **Configure site settings**, paste the following values:

    - **Client ID​**: Paste the **Client ID** [you copied](#add-credentials).
    - **Client secret**: Paste the **Client secret** you copied.

[Optional additional settings for OAuth 2.0 identity providers](oauth2-settings.md)

### See also

[Set up site authentication](configure-site.md)
