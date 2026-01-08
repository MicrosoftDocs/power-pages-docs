---
title: Configure a site with Content Delivery Network
description: Learn how to configure a site with Content Delivery Network.
author: nageshbhat-msft

ms.topic: how-to
ms.date: 01/05/2026
ms.subservice: 
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - nageshbhat-msft
ms.custom:
  - sfi-image-nochange
---

# Content Delivery Network

A *content delivery network* is a distributed network of servers that can efficiently deliver web content to users. Content delivery networks store cached content on edge servers in point-of-presence (POP) locations that are close to users to minimize latency.

:::image type="content" source="media/configure-cdn/cdn-diagram.png" alt-text="Screenshot of a diagram of the world showing Content Delivery Network servers on three different continents. Each server connects to users who are on, or near to, the continent the server is located on.":::

When you enable Content Delivery Network on your portal, static content&mdash;like images, scripts, and style sheet files used to design your portal website&mdash;are stored and served from the Content Delivery Network server closest to your location.  

> [!NOTE]
> - You need to be a [website administrator](/power-apps/maker/portals/admin/portal-admin-roles#required-roles-and-permissions) to enable Content Delivery Network. This feature is available for Power Pages. If you're using the legacy Add-on license, you can't enable Content Delivery Network. Trial websites aren't supported by Content Delivery Network. 
> - [Restricting website access by IP address](../admin/ip-address-restrict.md) on a site is currently not supported using Content Delivery Network.
> - This service isn't available in Singapore Local, China and the UAE region.

## Enable Content Delivery Network for a production website

Content Delivery Network is available for production Power Pages. Follow these steps to enable it:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which you want to enable Content Delivery Network.

1. Under Performance and Protection, turn on the **Content Delivery Network** toggle switch.

    :::image type="content" source="media/configure-cdn/manage-cdn.svg" alt-text="Screenshot of the enable cdn toggle switch in the on position.":::

    It might take a few minutes to provision Content Delivery Network.

> [!NOTE]
> When you add a custom domain name for a Content Delivery Network-enabled site, Power Pages uses Azure Front Door–managed TLS certificates to enforce HTTPS for custom domains. These certificates are created with a lifetime validity of 6 months and are auto-renewed 45 days before the expiration date.

## Enable Content Delivery Network while converting trial to production

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which you want to convert to production and enable Content Delivery Network.

1. On the site details page, select **Convert To Production** in the **Site Details** section.

1. Select the **Enable the Content Delivery Network** checkbox.

1. Select **Confirm**.

    :::image type="content" source="media/configure-cdn/trial-conversion.gif" alt-text="Screenshot of the message confirming you want to enable Content Delivery Network while converting trial to production.":::

## Disable Content Delivery Network

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which you want to disable Content Delivery Network.

1. Under **Performance and Protection**, turn off the **Content Delivery Network** toggle switch.

    :::image type="content" source="media/configure-cdn/manage-cdn.svg" alt-text="Screenshot of the enable Content Delivery Network toggle switch in the on position.":::

It might take a few minutes to de-provision the Content Delivery Network.

## Clear the Content Delivery Network cache

Static website contents are stored on Content Delivery Network servers across geographical locations. You can clear the cached content by using the **Purge cache** command. This action clears the cache from the Content Delivery Network server and the portal website.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which you want to purge the Content Delivery Network cache.

1. Select **Purge Cache**.

    :::image type="content" source="media/configure-cdn/purge-cache.png" alt-text="Screenshot of the Purge Cache button.":::

## Static file configuration

Static files are cached based on the file name extensions stored in the *Web files* table in the Portal Management app. By default, Content Delivery Network caches files that have the extensions *css, js, png, svg, jpg, ico, woff2, gif, ttf, woff, eot, otf, tts, jpeg, 7z, mp3,* and *mp4* on the edge server. A maker can override the default list by updating the site settings.

1. Open the [Portal Management app](portal-management-app.md).

1. Go to **Site Settings** in the **Website** section.

1. In the **ContentDeliveryNetwork/FileExtensions** site setting, update or add to the list of file name extensions you want to be cached.

    :::image type="content" source="media/configure-cdn/cdn-files.png" alt-text="Screenshot of the list of files to be cached.":::

## Static page configuration

When a site contains static pages, all users see the same information, which eliminates the need to load the content from the server each time. Instead, it can be served from the nearest server to reduce the request roundtrip. 

To configure static pages for caching:

1. Go to the **Set up** workspace.

1. Under **General**, select **Site performance**.

1. Select the static web pages you want to enable for caching.

    :::image type="content" source="media/configure-cdn/select-pages-to-cache.png" alt-text="Screenshot of the Site performance page including the ability to select which pages to cache.":::

    Choose the appropriate page that doesn’t contain any dynamic content. Different icons represent each type of page to help in the selection process. From a data perspective, there are four types of pages:

    - **Static pages**: These pages don't contain dynamic data components, and the content doesn't change based on the user. It's safe to enable caching for these pages.

    - **Pages with dynamic components – recommended for caching**: These pages might have some dynamic components, but it's still safe to enable caching. Ensure to purge the cache after any of these records are updated. Pages might contain the following components:

        - Ads
        - Polls  
        - Forums
        - Events
        - Blogs
        - Ideas
        - Knowledge articles

        > [!NOTE]
        > CDN cache is automatically refreshed every hour. Even if you have not manually purged the CDN cache, it will fetch the updated content after one hour.

    - **Pages with dynamic components – not recommended for caching**: These pages might contain components like basic forms or web forms in update/read-only mode or fetch XML, which displays dynamic data. It isn't recommended to enable caching for these pages, as end users might see stale data.

    - **Pages not available for caching**: Authenticated pages aren't available for caching and can't be selected for this purpose.

    > [!IMPORTANT]
    > - CDN caching is available only for anonymous users. If you enable caching for a static page accessed by authenticated users, the page will be served from the application server, not from the CDN cache.
    > - CDN cache and browser cache are different. When a user requests a page for the first time and that page is enabled for CDN caching, the page will be served from the application server and stored in the CDN cache. If the browser settings allow, the page will also be stored locally. The next time the same user accesses the page, it will be served from the browser cache. If another user accesses the same page, it will be served from the CDN cache.

1. Save changes.

### When to use caching for static pages

Caching of static pages is recommended in the following scenarios:

- Anonymous users access your site.

- The web page doesn’t contain any dynamic content.

- The site isn't in development.

The following list of actions always serves the pages from the server instead of from the cache:

- An authenticated user accesses any page.

- A maker accesses the site using the Preview button from studio.

- Developer tools are opened and disable cache is checked.

- You select <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>R</kbd> (hard refresh).

## Frequently Asked Questions

**How can I verify if the request is being served from the cache?**

1. Open Developer Tools (F12 or right-click on the page and select "Inspect").

1. Go to the **Network** tab.

1. Reload the page.

1. Select a resource/page request to see headers and caching details.

If the page is served from the cache, you get an x-cache response header of TCP_HIT.

## Privacy notice

Enabling the Content Delivery Network service stores your site files and pages on servers across multiple geographical locations and delivers them from the server closest to your site visitors. When a user requests the webpage of the site, the nearest Content Delivery Network server in the Microsoft global network receives the request and forwards it to the back-end application server. Static page responses are cached on the Content Delivery Network server. Subsequent requests to webpages are delivered from the cached content on the Content Delivery Network server, and dynamic page content is forwarded and delivered from the application server.

> [!NOTE]
> Only webpages that can be accessed by anonymous users are stored on Content Delivery Network servers; authenticated files are always delivered from the application server. An administrator can configure the list to be stored on servers based on their file name extensions.

A website administrator can disable the Content Delivery Network at any given point to stop the service, and all the files cached on the Content Delivery Network servers are removed.  

Content Delivery Network is powered by [Azure Front Door](/azure/frontdoor/standard-premium/overview) to provide a fast, reliable, and modern cloud content delivery network.

> [!NOTE]
> For more information about other Azure service offerings, go to the  [Microsoft Azure Trust Center](https://azure.microsoft.com/support/trust-center/).
