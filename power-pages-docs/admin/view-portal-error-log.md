---
title: View error logs
description: Learn how to view Power Pages website error logs and store them in your Azure Blob storage account.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/02/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# View website error logs

Website administrators and developers use Power Pages to create websites for their customers. Developers often debug issues while developing the website. To help debug, you can access detailed error logs for any issues on your website. There are multiple ways that you can get error logs for your website.

> [!TIP]
> To learn about the roles required to perform tasks in this article, read [Admin roles required for portal administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles).

## Custom error

If any server-side exception occurs on your website, a customized error page with a user-friendly error message is shown by default. To configure the error message, see [Display a custom error message](#display-a-custom-error-message).

However, it's better to see the ASP.NET detailed error page, also known as *Yellow Screen of Death* (YSOD), for debugging purposes. The detailed error page helps you to get the full stack of server errors.

:::image type="content" source="media/view-error-log/ysod.png" alt-text="Yellow Screen of Death.":::

To enable YSOD, you need to [disable custom errors](#disable-custom-error) on your website.

> [!NOTE]
> It is advisable to only disable custom errors when you are in the development phase and enable custom errors once you go live.

More information on custom error: [Displaying a Custom Error Page](/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### Disable custom error

You can disable custom errors on Power Pages websites to display the detailed exception message if any server-side exception occurs in your website.

1. Open the [Power Platform admin center](aka.ms/ppac).

1. Under the **Resources** section select **Power Pages sites**.

1. Select your website.

1. From the **Site Actions** menu, select **Disable custom errors**.

1. Select **Disable** in the confirmation message. While custom errors are being disabled, the website restarts and will be unavailable. 

### Enable custom error

You can enable custom errors on websites to display a professional-looking page instead of YSOD. This page provides meaningful information if any exception occurs in the application.

1. Open the [Power Platform admin center](aka.ms/ppac).

1. Under the **Resources** section select **Power Pages sites**.

1. Select your website.

1. From the **Site Actions** menu, select **Enable custom errors**.

1. Select **Enable** in the confirmation message. While custom errors are being enabled, the website restarts and will be unavailable. 

> [!NOTE]
> - If you change the instance that your website is connected to, the custom errors setting is set to enabled. You must disable the custom errors again, if required.
> - You must not enable or disable custom errors when the instance that your website is connected to is being changed; otherwise an error message appears.

### Display a custom error message

You can configure your portal to display a professional-looking custom error instead of a generic error.

To define a custom error, use the content snippet `Portal Generic Error`. The content defined in this snippet is shown on the error page. This content snippet isn't available out-of-the-box and you must create it. The content snippet **Type** can be **Text** or **HTML**. To create or edit the content snippet, see [Customize content by using content snippets](/power-apps/maker/portals/configure/customize-content-snippets).

> [!NOTE]
> If liquid code is written in the content snippet, it will be skipped and not rendered.

When you enable custom errors, the message appears in the following structure on the error page:

\<`Content Snippet`\> <br>
\<`Error ID` \><br>
\<`Date and time`\><br>
\<`Portal ID`\>

Below is an example of a custom error message, using a content snippet of type HTML:

This is a custom error, file a support ticket with screenshot of error by clicking here

:::image type="content" source="media/view-error-log/custom-error-message.png" alt-text="Custom error message.":::

> [!NOTE]
> If the portal cannot retrieve a content snippet because it can't connect to Microsoft Dataverse or if the snippet is not available in Dataverse, an error message appears.

## Access portal error logs

After developing and publishing the portal, you still need to be able to access portal logs to debug issues reported by your customers. To access the logs, configure your portal to send all application errors to an Azure Blob storage account that you own. By accessing portal error logs, you can respond to customer queries efficiently because you have details of the issue. To get portal error logs into your Azure Blob storage, you must enable diagnostic logging from the Power Apps portals admin center.

> [!NOTE]
> If you change the Dataverse instance that your portal is connected to, diagnostic logging is disabled. You must enable diagnostic logging again.

### Enable diagnostic logging

1. Open [Power Apps portals admin center](admin-overview.md).

2. Go to **Portal Actions** > **Enable diagnostic logging**.

   > [!div class=mx-imgBorder]
   > ![Enable diagnostic logging.](../media/enable-diagnostic-logging.png "Enable diagnostic logging")

3. In the **Enable diagnostic logging** window, enter the following values:

   - **Connection String of Azure Blob Storage service**: URL of the Azure Blob Storage service to store the portal error logs. The maximum length of the URL is 2048 characters. If the URL is longer than 2048 characters, an error message appears. More information on connection string: [Configure Azure Storage connection strings](/azure/storage/common/storage-configure-connection-string)
   - **Select retention period**: Duration to keep the portal error logs in blob storage. The error logs are deleted after the selected duration. You can select one of the following values:
     - One day
     - Seven days
     - 30 days
     - 60 days
     - 90 days
     - 180 days
     - Always

   By default, the retention period is 30 days.
  
   > [!div class=mx-imgBorder]
   > ![Enable diagnostic logging window.](../media/enable-diagnostic-logging-window.png "Enable diagnostic logging window")

4. Select **Configure**.

Once diagnostic logging is configured, a new **telemetry-logs** blob container is created in your Azure storage account and the logs are written into the blob files stored in the container. The following screenshot shows the **telemetry-logs** blob container in Azure Storage Explorer:

> [!div class=mx-imgBorder]
> ![Azure blog storage account.](../media/azure-blob-storage.png "Azure blog storage account")

When diagnostic logging is enabled successfully, the following action becomes available:
- **Update diagnostic logging configuration**: Allows you to update or remove diagnostic logging configuration for the portal.
- **Disable diagnostic logging**: Allows you to disable diagnostic logging configuration for the portal.
 
### Update diagnostic logging

1. Open [Power Apps portals admin center](admin-overview.md).

2. Go to **Portal Actions** > **Update diagnostic logging configuration**.

   > [!div class=mx-imgBorder]
   > ![Update diagnostic logging configuration.](../media/update-diagnostic-logging.png "Update diagnostic logging configuration")

3. In the Update diagnostic logging configuration window, enter the following values:
   - **Do you want to update the Connection string of the Azure Blob Storage service?**: Allows you to specify whether to update the connection string of the Azure Blob Storage service. By default, it's selected.
   - **Connection String of Azure Blob Storage service**: URL of the Azure Blob Storage service to store the portal error logs. The maximum length of the URL can be 2048 characters. If the URL is longer than 2048 characters, an error message appears. This field is displayed only if the **Do you want to update the Connection string of the Azure Blob Storage service?** check box is selected. More information on connection string: [Configure Azure Storage connection strings](/azure/storage/common/storage-configure-connection-string)
   - **Select retention period**: Duration to keep the portal error logs in blob storage. The error logs are deleted after the selected duration. You can select one of the following values:
     - One day
     - Seven days
     - 30 days
     - 60 days
     - 90 days
     - 180 days
     - Always

   By default, the retention period is 30 days.

   > [!div class=mx-imgBorder]
   > ![Update diagnostic logging configuration window.](../media/update-diagnostic-logging-window.png "Update diagnostic logging configuration window")

4. Select **Update**.

### Disable diagnostic logging

1. Open [Power Apps portals admin center](admin-overview.md).

2. Go to **Portal Actions** > **Disable diagnostic logging**.

   > [!div class=mx-imgBorder]
   > ![Disable diagnostic logging.](../media/disable-diagnostic-logging.png "Disable diagnostic logging")

3. Select **Disable** in the confirmation message.

## Display plugin error

Another scenario that often occurs while developing a portal is an error generated by custom plug-ins and business logic written in your Dataverse environment. These errors can generally be accessed by [disabling custom errors](#disable-custom-error) or [enabling diagnostic logging](#enable-diagnostic-logging). In some cases, it's faster to display these errors directly on the portal to diagnose the issue faster. You can accomplish this by configuring your portal to display custom plugin errors from Dataverse on your portal screen.

To display custom plugin errors, create the site setting `Site/EnableCustomPluginError` and set its value to True. The custom plugin errors will be displayed on the screen instead of a generic error. The error will display only the message part of the plugin error and not the complete stack trace.

Following are the screens where custom plugin errors will appear: 
- List 
    - Retrieval of records 
- Basic form 
    - Retrieve 
    - Create/Update, and so on 
- Multistep forms 
    - Retrieve 
    - Create/Update, and so on

If the site setting isn't present, then it will be treated as false by default and plugin errors won't render.

### See also

[Power App portal maintenance and troubleshooting](/training/modules/portals-maintenance-troubleshooting/)


