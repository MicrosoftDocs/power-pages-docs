---
title: Manage SharePoint documents
description: Learn how to manage SharePoint documents in Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 03/20/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
---

# Manage SharePoint documents

Microsoft Dataverse supports integration with SharePoint Online that enables you to use the document management capabilities of SharePoint from within Dataverse. Power Pages supports uploading and displaying documents to and from SharePoint directly on a basic form or multistep form on a website. This feature allows website users to view, download, add, and delete documents from a webpage. Website users can also create subfolders to organize their documents.

> [!NOTE]
> - Document management works only with SharePoint Online.
> - Document management is supported with server-based integration.

To work with the document management capabilities of SharePoint from within Dataverse, you must:

1. [Enable document management functionality for your environment](#step-1-enable-document-management-functionality-in-model-driven-apps)

1. [Set up SharePoint integration from Power Platform admin center](#step-2-set-up-sharepoint-integration-from-power-platform-admin-center)

1. [Enable document management for tables](#step-3-enable-document-management-for-tables)

1. [Configure the appropriate form in Power Apps documents](#step-4-configure-the-appropriate-form-to-display-documents)

1. [Create appropriate table permission and assign it to the appropriate web role](#step-5-create-appropriate-table-permission-and-assign-it-to-the-appropriate-web-role)

## Step 1: Enable document management functionality in model-driven apps

You must enable the document management functionality in model-driven apps by using server-based SharePoint integration. Server-based SharePoint integration allows model-driven apps and SharePoint to perform a server-to-server connection. The default SharePoint site record is used by Power Pages. For information on how to enable document management functionality in model-driven apps, see [Set up model-driven apps to use SharePoint Online](/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online).

> [!NOTE]
> The instructions may refer to Dynamics 365 Customer Engagement apps, you can enable SharePoint Online to integrate with Dataverse without Dynamics 365 apps enabled.

## Step 2: Set up SharePoint integration from Power Platform admin center

To use the document management capabilities of SharePoint, you must enable SharePoint integration from the Power Platform admin center.

### Enable SharePoint integration

> [!NOTE]
> You must be a global administrator to perform to enable SharePoint integration.

1. Open the [Power Platform admin center](../admin/admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to enable SharePoint integration. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to enable SharePoint integration.
    
    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to enable SharePoint integration. Select **Manage** from the main menu.

1. On the site information page, in the **Services** section, select the **SharePoint Integration** control to the **Yes** position.

    :::image type="content" source="media/sharepoint/power-platform-admin-center.png" alt-text="Enable SharePoint.":::

1. Select **Enable** in the confirmation window. This setting will enable the website to communicate with SharePoint. While the SharePoint integration is being enabled, the website will restart and will be unavailable for a few minutes. A message appears when SharePoint integration is enabled.

### Disable SharePoint integration

> [!NOTE]
> You must be a global administrator to perform to disable SharePoint integration.

1. Open the [Power Platform admin center](../admin/admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to disable SharePoint integration. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to disable SharePoint integration.
    
    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to enable SharePoint integration. Select **Manage** from the main menu.

1. On the site information page, in the **Services** section, select the **SharePoint Integration** control to the **No** position.

1. Select **Disable** in the confirmation window. Turning off this setting will disable communication with SharePoint. During the process, the website will restart and will be unavailable for a few minutes. A message appears when SharePoint integration is disabled.

Enabling or disabling the SharePoint integration will update the Microsoft Entra application for the website and add or remove the required SharePoint permissions, respectively. You'll also be redirected to provide your consent for the changes to be made in the Microsoft Entra application. 

:::image type="content" source="media/sharepoint/sharepoint-integration-consent.png" alt-text="Disable SharePoint integration consent screen.":::

If you don't provide your consent:

- Enabling or disabling the SharePoint integration won't be complete and an error message will display.

- Your out-of-the-box Microsoft Entra sign-in on the website won't work.


## Step 3: Enable document management for tables
You must enable document management for tables to store documents related to table records in SharePoint. For information on how to enable document management for tables, see [Enable SharePoint document management for specific tables](/power-platform/admin/enable-sharepoint-document-management-specific-entities).

## Step 4: Configure the appropriate form to display documents

### Dataverse forms configuration

You'll need to configure the Dataverse form by adding a subgrid component that will allow you to work with related documents on a webpage.

Identify the table and the corresponding form where you want to use document management capabilities. 

Open the [Data workspace form designer](data-workspace-forms.md) for the table you want to use for document management capabilities.

:::image type="content" source="media/sharepoint/configure-form.png" alt-text="Configure form for documents.":::

1. Select **Add component**

1. Select the **Subgrid** component.

1. For **Table**, choose **Document Locations**.

1. For **Default view**, Select **Active Document Locations**

1. Select **Done**.

You can specify name and label as per your requirement. Save and publish the form once the subgrid is added and configured.

> [!NOTE]
> Document management must be enabled for the table for which you edit the form. More information: [Enable document management for tables](#step-3-enable-document-management-for-tables)

### Power Pages configuration

Configure either a [form](../getting-started/add-form.md) component or [multistep form](../getting-started/multistep-forms.md) component to a webpage using the Dataverse form with the subgrid you created earlier. 

The **Data from this form** setting on the **Data** tab of the form configuration must be set to **Updates an existing record** to be able to upload files.

> [!NOTE]
> File uploading requires the parent table record to exist. If the **Data from this form** setting is **Creates a new record**, the document upload will not work because the parent table record is not created until the form is submitted.

## Step 5: Create appropriate table permission and assign it to the appropriate web role

Two table permission records are required to establish the necessary access to view and upload documents.

1. Go to the **Set up** workspace and select **Table permissions**.
1. Create a **Table permission** record specifying the **Table** used in the basic form or multistep form configured previously. 
1. Select a **Access type** and access type relationship that is appropriate to the behavior of the form that you want.
1. Enable **Read** and **Append to** privileges to allow read access to documents and optionally enable **Write** privilege to allow document uploads. 
1. Under **Roles**, select an appropriate webrole.
1. In the **Child permissions** tab, select **+ New**
1. Give the permission a **Name** (can be anything).
1. Select the **Document Location** as the table.
1. Select the **Relationship**
1. Select **Permissions**
    - The minimum privileges to allow read access to documents are **Read**, **Create**, and **Append**. 
    - Include **Write** privileges for document upload access. 
    - Include **Delete** to allow deletion of a document.
1. Select **Save**

> [!NOTE]
> A corresponding child table permission on the **Document Location** table needs to be created for each instance of the parent table permission record that exists on the table of the table or multistep form where documents need to be shown.

The form on the webpage will show a listing of files and folders. Depending on table permissions, there will the ability to **Add files**, **New folder**, and **Delete**.

:::image type="content" source="media/sharepoint/sharepoint-documents-webpage.png" alt-text="SharePoint document storage on a page.":::

## Configure file upload size

By default, the file size is set to 10 MB. However, you can configure the file size to a maximum of 50 MB by using the site setting `SharePoint/MaxUploadSize`.

## Maximum file download size

We recommend limiting the size of the individual files available for download to 250 MB or less. If you use portals to download larger files from SharePoint, the operation may time out after a couple of minutes.

### See also

[Document management with SharePoint](/training/modules/portals-integration/2-sharepoint)