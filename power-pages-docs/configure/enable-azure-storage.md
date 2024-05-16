---
title: Enable Azure storage
description: Learn how to enable Azure storage for Power Pages to take advantage of the greater file storage capability of Azure.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 3/13/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - GitanjaliSingh33msft
    - nageshbhat-msft
    - ProfessorKendrick
---

# Enable Azure Storage

Azure Storage integration for Power Pages enables you to take advantage of the greater file storage capability of Azure, using the same interface and providing the same user experience as for default file attachments. This feature is supported for web files, basic forms, and multistep forms.

You must create a storage account with **Resource manager** as the deployment model. More information: [Create an Azure storage account](/azure/storage/common/storage-account-create?tabs=azure-portal).

After the storage account is running, Power Pages require certain global settings that tell the application how to locate your storage account. In the Portal Management app, go to **Settings** > **New**, and add a new setting named **FileStorage/CloudStorageAccount**.

Azure storage integration only works with **Notes** configured in basic form metadata. Azure Blob as a storage is not used if you use **Portal Comments** that can be setup using **Timeline**. Though portal comments also provide capability for files to be uploaded as attachments, these files are only stored in Microsoft Dataverse.
 
> [!NOTE]
> - You must enable attachments for the table in Microsoft Dataverse first before using this feature. More information: [Create a table](/power-apps/maker/data-platform/data-platform-create-entity)
> - The maximum file upload size is 125 MB.

To locate the value for FileStorage/CloudStorageAccount, you must get a connection string from your Azure portal.

1. Sign in to your Azure portal.

1. Navigate to your storage account.

1. Select **Access Keys**.

1. In the resulting panel, locate the field labeled **Connection String**. Select the **Copy** icon next to the field for which you need to copy the value, and then paste that value into your new setting:

    :::image type="content" source="media/enable-azure-storage/primary-connection-string-azure-storage.png" alt-text="Primary connection string value.":::
    
    :::image type="content" source="media/enable-azure-storage/portal-site-setting-cloud-storage-account.png" alt-text="Portal setting for your cloud storage account.":::

## Specify the storage container

If you do not already have an Azure Blob container in your storage account, you must add one by using your Azure portal.

In the [Portal Management app](portal-management-app.md), in the **Website** section go to **Settings** > **New**, and add a new setting named **FileStorage/CloudStorageContainerName**, using the name of your container as the value.

## Add CORS rule

You must add cross-origin resource sharing (CORS) rule on your Azure Storage account as follows, otherwise you will see the regular attachment icon rather than the cloud icon:

- **Allowed origins**: Specify your domain. For example, `https://contoso.crm.dynamics.com` <br /> Ensure the allowed origin doesn't have trailing `/`. For example, `https://contoso.crm.dynamics.com/` is incorrect.
- **Allowed verbs**: GET, PUT, DELETE, HEAD, POST
- **Allowed headers**: Specify the request headers that the origin domain may specify on the CORS request. For example, x-ms-meta-data\*, x-ms-meta-target\*, or \* to allow all.
- **Exposed headers**: Specify the response headers that may be sent in the response to the CORS request and exposed by the browser to the request issuer. For example, x-ms-meta-\*, or \* to allow all.
- **Maximum age (seconds)**: Specify the maximum amount time that a browser should cache the preflight OPTIONS request. For example, 200.

CORS rule example:

:::image type="content" source="media/enable-azure-storage/portals-cors-azure.png" alt-text="Text used by screen readers.":::

More information: [CORS support for the Azure Storage Services](/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services).

## Add site settings

Add the following site settings from **Portals** > **Site Settings**. More information: [Manage portal site settings](/power-apps/maker/portals/configure/configure-site-settings) 

|Name|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|Provide the same connection string as provided for the FileStorage/CloudStorageAccount setting.|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

## Configure basic or multistep forms 

To view and add attachments stored in Azure on basic and multistep forms on your site, you will need to [configure notes as attachments](configure-notes.md) as well as add [basic form](configure-notes.md#notes-configuration-for-basic-forms) or [multistep form](configure-notes.md#notes-configuration-for-multistep-forms) metadata with the **File Attachment Location** set to **Azure Blob Storage**.

You can then add attachments to records on web pages.

Attachments uploaded via the site will be stored in Azure.

To view and access the attachments in a model-driven app (including Dynamics 365 apps) you will need [add a web resource to enable uploading attachments to Azure Storage](add-web-resource.md).

### See also

[Add web resource](add-web-resource.md)
[Configure notes](configure-notes.md)

