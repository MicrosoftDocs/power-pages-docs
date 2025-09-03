---
title: Build and distribute progressive web apps
description: Configure a site as a progressive web app.
author: DanaMartens
ms.topic: how-to
ms.date: 11/13/2024
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - ankitavish
    - tapanm-msft
    - DanaMartens
ms.custom:
  - sfi-image-nochange
---

# Build and distribute a progressive web app

Use Power Pages design studio to configure your progressive web app (PWA). You can enable or disable PWA capability. You can customize PWA settings and prepare to create an app package to publish to respective device stores if you choose.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Choose your site and select **Edit**.

1. In the design studio, select **Set up** workspace and then select **Progressive web application**.

    :::image type="content" source="media/progressive-web-apps/pwa-setup-workspace.png" alt-text="Launch progressive web application from Set up workspace.":::

1. Select **Enable PWA**.

    :::image type="content" source="media/progressive-web-apps/enable-pwa.png" alt-text="Enable progressive web app from Set up workspace.":::

## Brand your app

You can create your own branded PWA by using the customization options to change the app name, starting page, color, and more.

> [!NOTE]
> On iOS devices, icons for the PWA will be shown as thumbnails and the customized splash screen won't be displayed.

1. In the design studio, select **Progressive web app**.

1. Update the following PWA settings for your site.
  
    | **Setting** | **Description** |
    |-------------------------|-------------------------|
    | Title | The name of the portal PWA that appears on the mobile device and in the app store. |
    | Description | The description of the PWA that appears on the mobile device and in the app store. |
    | Starting page of the app | The start page for the site when it opens through the PWA. |
    | Splash screen background | The background color for the splash screen when the PWA is loaded. |
    | App icon | The icon for the app that appears on the mobile device and in the app store.<br>**Note:** Supports .jpg, .jpeg, .png formats with a maximum upload size of 5 MB. Size of icon must be 512 &times; 512 pixels. |
      
    > [!NOTE]
    > Depending on your browser, it might take a few moments for it to reflect your changes. After customizing the PWA, select **Preview** to clear the cache of your site.

## Define offline behavior

PWA offers support for a smooth navigation experience when the device being used is offline or disconnected from the internet. You can choose the pages within your site that are available offline (read-only), and a message page for the rest of the portal capabilities that aren't enabled for offline access.

### Configure offline pages for the portal PWA

1. In the design studio, in the **Set up** workspace, select **Progressive web application**.

1. Under **More settings**, select **Define offline pages**.

    :::image type="content" source="media/progressive-web-apps/pwa-define-offline-pages.png" alt-text="Selecting pages for offline mode." :::

1. Select the pages that you want to enable users to access when they use the PWA offline.

    :::image type="content" source="media/progressive-web-apps/select-offline-pages.png" alt-text="Managing offline pages." :::

> [!NOTE]
> When configuring offline access for PWA pages, be sure to consider the storage limitations for user devices. When the storage requirement for offline PWA access exceeds the available storage on the device, the entire portal will be unavailable for offline access. We recommend that you test the user experience of offline access and only cache the pages that will be most helpful and important to your users. Remember that offline pages can only show information; pages that are connected to Microsoft Dataverse that contain forms to fill out or run queries won't work while offline.

### Set up an offline message page

When a device is offline, the page you configure as the offline message page appears when users try to access pages that aren't enabled for offline access.

1. In the design studio, select **Pages** workspace.

1. Select **Default offline page**.

1. Customize the page.

> [!NOTE]
> - You can't change the **Title** or **Partial URL** ("*/default-offline-page*") fields for the offline page. A default offline page will be shown to users if the offline page is missing.
> - Depending on your browser, it might take a few moments for it to reflect your changes. After customizing the offline PWA experience, select **Preview** to clear the cache of your site.

### Test your site in offline mode

After you [enable offline pages](#define-offline-behavior), you can use a mobile device in offline mode and browse through different pages that are enabled for offline access.

1. Browse to your site by using a web browser on your mobile device in online mode.

1. Select **Add to Home screen** or a similar option. For example, on an Android device, the option might be **+ Add to** > **App screen**.

    :::image type="content" source="media/progressive-web-apps/add-to-home.png" alt-text="Adding the PWA to the home page on a mobile device." border="false":::

    > [!NOTE]
    > This action downloads portal pages that have been enabled for offline browsing. This might take a while, depending on network bandwidth and the size of the pages that were selected for offline browsing.

1. Enable offline mode in your mobile device.

1. Open your portal from the home screen. You see a notification at the top reminding you that you're browsing in offline mode. If you select any pages that aren't enabled for offline browsing, the offline message appears.

    :::image type="content" source="media/progressive-web-apps/pwa-offline.png" alt-text="Read-only page in offline mode for a PWA app.":::   :::image type="content" source="media/progressive-web-apps/not-connected.png" alt-text="Not connected to the internet page in PWA app." :::

## Distribute your app

You can distribute your app either by using a browser or through an app store.

### Distribute your app by using a browser

After your portal is enabled as a PWA, your users can pin the Power Pages site as an app to the home screen on their device. This option is supported on all platforms (Android, iOS, Chromebook, and Windows) in addition to all form factors (mobile, desktop, and tablet).

The following graphics illustrate the user experience of adding a portal to the home screen by using the browser that installs the portal as a PWA.

:::image type="content" source="media/progressive-web-apps/site-to-pwa.png" alt-text="A sequence of images, the first image shows a portal open in a browser on a mobile device. The next image shows the menu command Add to Home screen. In the next image, the user is prompted to install the app. The last image shows the app with its custom background and branding, operating as a native mobile app." border="false":::

Android and iOS each offer a different method for browser-based installation.

### Distribute your app through an app store

Progressive web apps can also be distributed through app stores for Android, iOS, and Windows. This distribution is done by creating an app package and publishing the app to the respective app store. For creating the app packages, we partner with [PWABuilder](https://www.pwabuilder.com/), which provides a platform to generate application packages for various app stores.

To create an app package, go to **Set up** workspace in the design studio. Under **App package**, select **Create app package**.

:::image type="content" source="media/progressive-web-apps/open-pwa-builder.png" alt-text="Opening PWA Builder to create an app package in portals Studio." border="false":::

This takes you to [the PWA Builder website](https://www.pwabuilder.com/) where you can create an app package for various app stores. The package you create by using PWA Builder contains:

- An app package for the PWA to be used in its respective app store.

- A step-by-step document about publishing the app.

For more details, go to the [PWA resource hub](https://blog.pwabuilder.com/).

For iOS, PWABuilder provides support for generating the app store package. For more information, see [package for the App Store](https://docs.pwabuilder.com/#/builder/app-store).

For Windows, see [package for the Microsoft Store](https://docs.pwabuilder.com/#/builder/windows?id=publishing-pwas-to-the-microsoft-store).

#### Other considerations for Android

For the Android platform, you can also update the Android certificate with the **Update the Android certificate** option.

:::image type="content" source="media/progressive-web-apps/update-android-certificate.png" alt-text="Menu item in portals Studio to update the Android certificate." border="false":::

Update the title and the SHA-256 certificate fingerprint to update the digital asset links file (assetlinks.json) that proves ownership of your PWA.

:::image type="content" source="media/progressive-web-apps/android-certificate.png" alt-text="Updating the Android certificate details.":::

### See also

[Overview of sites as progressive web apps](progressive-web-apps.md)</br>
[Overview of Progressive Web Apps (PWAs)](/microsoft-edge/progressive-web-apps-chromium/)<br>
[Build and distribute a progressive web app (video)](https://youtu.be/Pzs8zTXy8kI?feature=shared)
