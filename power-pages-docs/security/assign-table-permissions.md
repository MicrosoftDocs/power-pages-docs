---
title: Assign table permissions
description: Assign table permissions to web roles.
ms.date: 07/25/2024
ms.topic: how-to
author: gitanjalisingh33msft
ms.author: gisingh
ms.reviewer: danamartens
contributors:
ms.custom: bap-template
---

# Assign table permissions

Table permissions assigned to [web roles](create-web-roles.md) allow members of the web role to access data that's stored in Dataverse [tables](../configure/data-workspace-tables.md).

> [!IMPORTANT]
> When the [Anonymous users web role](#anonymous-users-web-role) is granted access to a table, any user who visits the site can access the data in the table.

1. In your Power Pages site, select **Security** > **Table permissions**.

1. Select the **ellipse (...)** next to the table you wish to assign permissions to and choose **Edit**.

1. Select the role or roles to assign the table permission to.

    If the web role isn't listed, select **Manage roles** to open the [Portal Management app](../configure/portal-management-app.md). Create the role and save it. Return to the design studio and select **Sync**, then refresh the browser page. Start again at step 2.

1. Select **Save**.

## Anonymous users web role

If you add the Anonymous users web role to a table permission, the data in the table is visible to anyone.

>[!TIP]
> If your [site visibility](site-visibility.md) is set to public, an icon appears next to the site name in the design studio and the following message is displayed: *The data displayed in your site can be seen by anyone. If that's not what you want, change or eliminate the "Anonymous" role in your table permissions.*  

To restrict access to your site's data, follow the [steps to assign table permissions](#assign-table-permissions) and clear the checkmark next to the **Anonymous users** web role.

### See also

[Set table permissions](table-permissions.md)  
[Create web roles](create-web-roles.md)  
[Tutorial: Display data securely on your site](../getting-started/tutorial-display-data-securely.md)
