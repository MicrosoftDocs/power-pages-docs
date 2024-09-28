---
title: Cache invalidation
description: Learn about Site Checker diagnostics results for cache invalidation issues.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/06/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - dileepsinghmicrosoft
---

# Cache invalidation

In this article, you'll learn about Site Checker diagnostics results for cache invalidation issues.

## Website isn't displaying updated data from Microsoft Dataverse environment

Any data displayed on the website is rendered from the website cache. This cache gets updated whenever data in the Dataverse environment is updated. However, this process can take up to 15 minutes. If changes are made in the metadata table of the website (for example, webpages, web files, content snippets, or site settings), it's recommended to clear the cache manually or restart the website from the Power Platform admin center. For information on how to clear the cache, see [Server-side cache in portals](/power-apps/maker/portals/admin/clear-server-side-cache). 

However, if you're seeing stale data for a long period of time in non-website metadata tables, it could be because of one of the following issues.

### Tables not enabled for cache invalidation

If you're seeing stale data only for certain tables and not everything, this can be because the change tracking metadata isn't enabled on that specific table.

If you run the Site Checker (self-service diagnostic) tool, it will list the Object Type Code of all the tables that are referenced on the website that aren't enabled for change tracking. You can browse your metadata by following the steps outlined at [Browse the metadata for your organization](/dynamics365/customerengagement/on-premises/developer/browse-your-metadata).

If you're experiencing stale data issues in any of these tables, you can enable change tracking by using Power Apps or Dynamics 365 API. For more information, see [Enable change tracking for a table](/dynamics365/customerengagement/on-premises/developer/use-change-tracking-synchronize-data-external-systems#enable-change-tracking-for-an-entity).

### Organization not enabled for change tracking

Apart from each table being enabled for change tracking, organizations on the whole have to be enabled for change tracking as well. An organization is enabled for change tracking when a website provisioning request is submitted. However, this can break if an organization is restored from an old database or reset. To fix this issue:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under the **Resources** section, select **Power Pages sites**.

1. Select the your website.

1. When the site page opens, from the main menu, select **Shut down this site**. On the prompt, select **Stop**.

1. From the main menu, select **Start this site**. On the prompt, select **Start**.

### I'm getting a "Page Not Found" error and the page content is different from the default Page Not Found site marker or web page

You may see a *Page Not Found* error message that appears different from the default error page content on the **Page Not Found** site marker and webpage.

This *Page Not Found* error appears if: 

- The default **Page Not Found** site marker is configured incorrectly.
- The default **Page Not Found** site marker is deleted.
- The default **Page Not Found** webpage is deleted.

To resolve this error, ensure that you have the default site marker named **Page Not Found** present and configured correctly. If the site marker is present and correctly configured, check if the **Page Not Found** webpage is selected for the site marker or whether the **Page Not Found** webpage is present or not.

For steps to create a site marker for **Page Not Found**, go to [An active Page Not Found site marker isn't available for this website](site-checker-configuration-issues.md#an-active-page-not-found-site-marker-isnt-available-for-this-website).

For steps to check site marker configuration and ensure it points to the correct webpage, go to [The Page Not Found site marker isn't pointing to any webpage](site-checker-configuration-issues.md#the-page-not-found-site-marker-isnt-pointing-to-any-webpage).

For steps to change the site marker to point to the correct **Page Not Found** webpage, go to [The Page Not Found site marker is pointing to a deactivated webpage](site-checker-configuration-issues.md#the-page-not-found-site-marker-is-pointing-to-a-deactivated-webpage).

### See also

[Run Site Checker](site-checker.md)
