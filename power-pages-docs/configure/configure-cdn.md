---
title: Configure a site with Content Delivery Network
description: Configure a site with Content Delivery Network
author: nageshbhat-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/07/2023
ms.subservice: 
ms.author: nabha
ms.reviewer: kkendrick
contributors:
    - nageshbhat-msft
    - nickdoelman
    - ProfessorKendrick
---

# Content Delivery Network

A *content delivery network* is a distributed network of servers that can efficiently deliver web content to users. Content delivery networks store cached content on edge servers in point-of-presence (POP) locations that are close to users, to minimize latency.

:::image type="content" source="media/configure-cdn/cdn-diagram.png" alt-text="Diagram of the world showing Content Delivery Network servers on three different continents. Each server connects to users who are on, or near to, the continent the server is located on.":::

When you enable Content Delivery Network on your portal, static content&mdash;like images, scripts, and style sheet files used to design your portal website&mdash;will be stored and served from the Content Delivery Network server closest to your location.  

> [!NOTE] 
> - You need to be a [website administrator](/power-apps/maker/portals/admin/portal-admin-roles#required-roles-and-permissions) to enable Content Delivery Network. This feature is available for Power Pages. If you're using the legacy Add-on license, you can't enable Content Delivery Network. Trial websites aren't supported for Content Delivery Network. 
> - [Restricting website access by IP address](../admin/ip-address-restrict.md) on a site is currently not supported with using Content Delivery Network.
> - This service is not available in Government Community Cloud (GCC), Government Community Cloud (GCC High), Department of Defense (DoD), and UAE region.

## Enable Content Delivery Network for a production website 

Content Delivery Network is available for production Power Pages. The steps below detail how to enable it.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which want to enable Content Delivery Network.

1. Under Performance and Protection, turn on the **Content Delivery Network** toggle switch.

    :::image type="content" source="media/configure-cdn/manage-cdn.png" alt-text="The enable cdn toggle switch in the on position.":::

    It might take a few minutes to provision Content Delivery Network.

## Enable Content Delivery Network while converting trial to production 

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which want to convert to production and enable Content Delivery Network.

1. On the site details page, select **Convert To Production** in the **Site Details** section.

1. Select the **Enable the Content Delivery Network** checkbox. 

1. Select **Confirm**.
    
    :::image type="content" source="media/configure-cdn/trial-conversion.gif" alt-text="Message confirming you want to enable Content Delivery Network while converting trial to production.":::

## Disable Content Delivery Network 

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which want to disable Content Delivery Network.

1. Under **Performance and Protection**, turn off the **Content Delivery Network** toggle switch.

    :::image type="content" source="media/configure-cdn/manage-cdn.png" alt-text="The enable cdn toggle switch in the on position.":::

It might take a few minutes to de-provision Content Delivery Network.

## Clear the Content Delivery Network cache 

Static website contents are stored on Content Delivery Network servers across geographical locations. You can clear the cached content by using the **Purge cache** command. This action clears the cache from the Content Delivery Network server and the portal website. 

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which want to purge the Content Delivery Network cache.

1. Select **Purge Cache**.

    :::image type="content" source="media/configure-cdn/purge-cache.png" alt-text="The Purge Cache button.":::

## Cache configuration 

Static files are cached based on the file name extensions stored in the **Web files** table in the Portal Management app. By default, Content Delivery Network caches files that have the extensions *css, js, png, svg, jpg, ico, woff2, gif, ttf, woff, eot, otf, tts, jpeg, 7z, mp3,* and *mp4* on the edge server. A maker can override the default list by updating the site settings. 

1. Open the [Portal Management app](portal-management-app.md).

1. Go to **Site Settings** in the **Website** section.

1. In the **ContentDeliveryNetwork/FileExtensions** site setting, update or add to the list of file name extensions you want to be cached. 

    :::image type="content" source="media/configure-cdn/cdn-files.png" alt-text="List of files to be cached.":::

## Privacy notice 

Enabling the Content Delivery Network service stores your site files on servers across multiple geographical locations and delivers the files from the server closest to your site visitors. When a user makes a request to the webpage of the site, the nearest Content Delivery Network server in the Microsoft global network receives the request and forwards it to the back-end application server. Static files in the page response are cached on the Content Delivery Network server. Subsequent requests to static files of the webpage are delivered from the cached content on the Content Delivery Network server, and dynamic page content is forwarded and delivered from the application server.

> [!NOTE] 
> Only files that are part of a webpage that can be accessed by anonymous users are stored on Content Delivery Network servers; authenticated files are always delivered from the application server. An administrator can configure the  list of static files to be stored on servers based on their file name extensions.

A website administrator can disable Content Delivery Network at any given point to stop the service, and all the files cached on the Content Delivery Network servers will be removed.  

Content Delivery Network is powered by [Azure Front Door](/azure/frontdoor/standard-premium/overview) to provide a fast, reliable, and modern cloud content delivery network.

> [!NOTE] 
> For more information about other Azure service offerings, go to the  [Microsoft Azure Trust Center](https://azure.microsoft.com/support/trust-center/).


