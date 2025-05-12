---
title: Delete a website
description: Learn how to delete a website.
author: neerajnandwana-msft

ms.topic: how-to
ms.custom: 
ms.date: 03/17/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---

# Delete a website

A Power Pages website consists of the following components:

- **Power Pages website host**: The website host is the code that forms the actual website, which runs as an Azure web application.

- **Website configuration**: The website configuration in the Dataverse environment that defines components such as *Websites*, *Webpages*, *Content Snippets* and *Web Roles* records.

- **Power Pages solutions**: Solutions that are installed in the Dataverse environment and contain the metadata tables for any website.

**To delete a website**, you must delete the **website host** and then the **website configuration**.

You can delete your website host, which will delete all the hosted resources associated with it. Then you can provision the website again using the same configuration data.

It is important to note that deleting your **website host** doesn't remove the configuration or solutions present in your instance and they will remain as is.

You can delete a completely configured website, or a website for which provisioning or updating of an instance has failed.

> [!TIP]
> To learn about the roles required to perform this task, read [Admin roles required for website administrative tasks](admin-roles.md).

To delete a **website host**:

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site that you want to delete. Select **Manage** from the main menu.

1. From the **Site Actions** menu, select **Delete this site**.

    :::image type="content" source="media/delete-site/delete-site.png" alt-text="Delete site.":::

1. Select **OK**.

> [!NOTE]
> - If you don't have appropriate permissions on an associated Microsoft Entra application, an error is displayed. You must contact the global administrator for the appropriate permissions.
> - If you delete a website and provision a new website using the same configuration, you must add website application ID of the new website to the **Portal Power BI Embedded service** Microsoft Entra security group. For more information, read [Set up Power BI integration](/power-apps/maker/portals/admin/set-up-power-bi-integration#create-security-group-and-add-to-power-bi-account).
 
- To delete **website configuration**, delete the corresponding website record for the website you want to delete using the [Portal Management app](../configure/portal-management-app.md).

If you want, you can also delete **Power Pages solutions**. Deleting the solutions is not required to create a new website with clean configuration. However, you may need to delete the solutions for other reasons such as a business requirement to not have any more websites in a specific environment.

## Troubleshooting

If a website delete request could not be submitted, an error is displayed. In this case, you must close and reopen the Power Platform admin center, and try to delete the website again. If the issue persists, contact Microsoft support.
