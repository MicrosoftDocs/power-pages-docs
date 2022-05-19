---
title: Configure web roles in Power Pages
description: Learn how to configure web roles.
author: nickdoelman

ms.topic: conceptual
ms.custom: 
ms.date: 05/19/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Configure web roles

[!INCLUDE[powerapps-info](../includes/cc-powerapps-info.md)]

In order for authenticated users to be given access to [table permissions](table-permissions.md) or [restricted pages](page-security.md), they must first be assigned to a web role.

Configuration and assignment of web roles is done through the [Portal Management app](../configure/portal-management-app.md). 

1. To access the Portal Management app, in the design studio, select the ellipsis (**...**) from the toolbelt, and then select **Portal Management**.

:::image type="content" source="media/table-permissions/launch-portals-management-app.png" alt-text="Open the Portal Management app.":::

1. Select **Web Roles** in the **Security** section.

1. Select **New**.

1. Enter appropriate values in the fields.

    :::image type="content" source="media/web-role/create-web-role.png" alt-text="Create a web role.":::

1. Select **Save**.

## Attributes and relationships

The table below explains the Web Role attributes used by portals.

| Name                     | Description                                                                                                                                                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                     | The descriptive name of the Web Role                                                                                                                                                                                                            |
| Website                  | The associated website                                                                                                                                                                                                                          |
| Description              | An explanation of the Web Role's purpose. Optional.                                                                                                                                                                                             |
| Authenticated Users Role | Boolean. If set to true, this will be the default web role for authenticated users (see below). Only one Web Role with the Authenticated Users Role attribute set to true should exist for a given website. All authenticated user automatically get permissions defined in this role. |
| Anonymous Users Role     | Boolean. If set to true, this will be the default web role for unauthenticated users (see below). Only one Web Role with the Anonymous Users Role attribute set to true should exist for a given website. This will be the default web role for unauthenticated users. The Anonymous Users Role will only respect Table Permissions.| 
|| 

Now that the Web Role has been created, you will be able to configure it to meet your needs via various permissions, rules, and associations.

- **Optional default web role for authenticated users**: By enabling the **Authenticated Users Role**, it will become the default web role for all users. This role is commonly used to provide a predetermined access for users that are not associated to any other roles. Keep in mind that users can have multiple web roles, but there can only be one Authenticated Users web role for authenticated users.
- **Optional default web role for unauthenticated users**: The **Anonymous Users Role** is intended to be used with Table Permissions. It will not respect any other rules or permissions. By enabling the "Anonymous Users Role" it will become the default web role for all users. There can only be one Anonymous Users web role for unauthenticated users.

## Assign users to web roles

You can assign site users to web roles from either the contact record or the web role record.

### From the web role

1. In the **Security** section, select **Web Roles**.

1. Locate and open the web role record that you want to assign site users to.

1. Select the **Related** tab and select **Contacts**.

1. Select **Add Existing Contact**. 

1. From the side panel, search and select the contacts (site users) that you want to assign to the web role.

1. Select **Add**.

    :::image type="content" source="media/web-role/assign-users.png" alt-text="Assign users to a web role.":::

1. The users now have access to the resources specified by the web role.

### From the contact

1. In the **Security** section, select **Contacts**.

1. Locate and open the contact record that you want to assign the web role to.

1. Select the **Related**.

1. Select **Web Roles**.

1. Select **Add Existing Web Role**.

1. From the side panel, search and select the web roles you want to assign to the contact (site user).

1. The site users now have access to the resources specified by the web role.

### See also

[Configure table permissions](table-permissions.md)</br>
[Assign table permissions](assign-table-permissions.md)</br>
[Tutorial: Display data securely on your site](../getting-started/tutorial-display-data-securely.md)