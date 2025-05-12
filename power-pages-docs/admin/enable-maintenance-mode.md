---
title: Maintenance mode for a website
description: Learn how to enable maintenance mode with your Power Pages website.
author: neerajnandwana-msft

ms.topic: concept-article
ms.custom: 
ms.date: 03/16/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---

# Maintenance mode for a website

There might be times when your website is under scheduled maintenance or is down because of temporary outage. When a customer accesses the website during maintenance, unpredictable behavior and intermittent unavailability might be experienced. 

As a website administrator, you can configure your site to display a proper message to customers whenever a maintenance activity is going on (for example, "Solution packages are being upgraded.") You can benefit from this capability by enabling the maintenance mode on your website. When the maintenance mode is enabled, a message is displayed, and the customers are restricted from browsing any webpages except the `<website URL>/_services/about` page.

:::image type="content" source="media/maintenance-mode/maintenance-page.png" alt-text="Default maintenance mode page.":::

## Enable maintenance mode

You can enable maintenance mode on your website to provide a consistent message, instead of dealing with unpredictable behavior when your website is under scheduled maintenance. This capability will provide a better experience for your users.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Select the site for which you want to enable maintenance mode, select **Manage** from the main menu.

1. Select **Site Actions** and then **Enable maintenance mode**.

    :::image type="content" source="media/maintenance-mode/enable-maintenance-mode.png" alt-text="Enable maintenance mode.":::

1. In the **Enable maintenance mode** panel, enter the following values:
    - **Select page to be used when maintenance mode is enabled**: Select one of the following values:

        - **Default page**: Select this value if you want the default page to be displayed when maintenance mode is enabled. By default, this option is selected.

        - **Custom page**: Select this value if you want a custom HTML page to be displayed when maintenance mode is enabled.

    - **Custom page URL**: This field is enabled only when you select the option to display a custom HTML page.

        > [!IMPORTANT]
        > Read the [custom maintenance page considerations](#considerations-for-custom-maintenance-page) before using custom maintenance page.
 
1. Select **Enable**. While maintenance mode is being enabled, the website restarts and is unavailable for a few minutes. 

### Considerations for custom maintenance page

- Ensure the page URL you provide is publicly accessible.
- The custom maintenance page uses IFrame to display the page. So, the page shouldn't contain the `x-frame-options:SAMEORIGIN` response header, else the page won't load.
- Don't host custom maintenance page on a Power Pages site. If a website is unavailable (for reasons such as data migration, solution upgrade, an outage, or any other maintenance activity), the custom maintenance page hosted on the same website won't be accessible.
- If the custom maintenance page is inaccessible publicly, or if you host the page on a Power Pages site where custom maintenance mode is enabled, the default maintenance page is used instead. The page also shows the following note for the administrators:

    `Note for administrators: The custom page for maintenance mode could not be displayed due to configuration errors.`

## Configure or disable maintenance mode

After enabling maintenance mode for your website, you can update the maintenance mode settings and choose a different page.

You can also choose to disable maintenance mode on your website when the scheduled maintenance of your website is complete. Your  users can now browse and access all web pages as usual.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Select the site for which you want to disable or update maintenance mode, select **Manage** from the main menu.

1. Select **Site Actions** and then **Configure or Disable maintenance mode**.

1. Modify the settings as required, and select **Update**. For example, you might choose to display the default page if you've selected to display the custom page earlier.

1. To disable maintenance mode, select **Disable**. While maintenance mode is being updated or disabled, the website restarts and is unavailable for a few minutes.

### See also

[Power Pages maintenance and troubleshooting](/training/modules/portals-maintenance-troubleshooting/)

