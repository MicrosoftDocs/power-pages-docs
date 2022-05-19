---
title: Assign table permissions
description: Assign table permissions to web roles.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/19/2022
ms.author: ndoelman
ms.reviewer:
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Assign table permissions

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Table permissions are assigned to [web roles](create-web-roles.md) to allow members of the web role access to the table specified.

1. Using the [design studio](../getting-started/use-design-studio.md), select **Setup** workspace.

1. Select the table permission to which you want to assign a web role.

1. In the **Roles** section, select **+ Add roles** and choose the roles to be assigned to the table permission. You can select multiple roles.

    :::image type="content" source="media/table-permissions/assign-web-role.png" alt-text="Adding web roles to the specific table permission.":::

1. Select **Save**.

1. If the web role does not appear, you can select **Manage roles** to open the [Portal Management app](../configure/portal-management-app.md) to create web roles.

    >[!NOTE]
    >Once you have created the web role, you will need to select **Sync** in the design studio as well as refresh your browser to view your new roles in table permissions side panel.

More information on creating web roles and assigning site users (contacts), go to: [Create web roles](create-web-roles.md).

### See also

[Configure table permissions](table-permissions.md)<br>
[Tutorial: Display data securely on your site](../getting-started/tutorial-display-data-securely.md)
