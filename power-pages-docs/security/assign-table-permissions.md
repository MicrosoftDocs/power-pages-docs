---
title: Assign table permissions
description: Assign table permissions to web roles.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 11/14/2022
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Assign table permissions

Table permissions are assigned to [web roles](create-web-roles.md) to allow members of the web role access to data stored in Dataverse [tables](../configure/data-workspace-tables.md).

1. Using the [design studio](../getting-started/use-design-studio.md), select **Set up** workspace.

1. In the **Security** section, select **Table permissions**.

1. Select the table permission you want to assign for a web role.

1. In the **Roles** section, select **+ Add roles** and choose the roles you wish to assign to the table permission. You can select multiple roles.

    :::image type="content" source="media/table-permissions/assign-web-role.png" alt-text="Adding web roles to the specific table permission.":::

    > [!NOTE]
    > When Anonymous Users are granted access to a table, any user who visits the site can access data.  
    > More information: 

1. Select **Save**.

1. If the web role doesn't appear, select **Manage roles** to open the [Portal Management app](../configure/portal-management-app.md) to create web roles.

    > [!NOTE]
    > Once you have created the web role, select **Sync** in the design studio and refresh your browser to view your new roles in the table permissions side panel.

## Notifications for the Anonymous users web role

If the Anonymous users web role is selected, notifications will display in the design studio and in the table permissions workspace.

Your data is visible to anyone.  If you don't want that, change the table permissions so they aren't anonymous.

Additionally, flags are displayed in the Table Permissions workspace for all tables with Anonymous Users enabled.

ADD IMAGE HERE

To revoke the Anonymous users access, follow the steps to assign table permissions and remove the checkmark next to the Anonymous users web role.

### See also

[Configure table permissions](table-permissions.md)<br />
[Create web roles](create-web-roles.md) <br />
[Tutorial: Display data securely on your site](../getting-started/tutorial-display-data-securely.md)
