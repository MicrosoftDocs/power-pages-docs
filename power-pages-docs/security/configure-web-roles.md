---
title: Configure web roles in Power Pages
description: Learn how to configure web roles.
author: nickdoelman

ms.topic: conceptual
ms.custom: 
ms.date: 05/24/2022
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Configure web roles

Before you grant authenticated users access to [table permissions](table-permissions.md) or [restricted pages](page-security.md), they must first be assigned to a web role.

Configure and assign web roles using the [Portal Management app](../configure/portal-management-app.md). 

1. To access the Portal Management app, navigate to the design studio. 

1. Select the ellipsis (**...**) from the tool belt, and then select **Portal Management**.

    :::image type="content" source="media/table-permissions/launch-portals-management-app.png" alt-text="Open the Portal Management app.":::

1. Select **Web Roles** in the **Security** section.

1. Select **New**.

1. Enter appropriate values in the fields.

    :::image type="content" source="media/web-role/create-web-role.png" alt-text="Create a web role.":::

1. Select **Save**.

## Attributes and relationships

The table below explains the web role attributes used by Power Pages.

| Name                     | Description                                                                                                                                                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                     | The descriptive name of the web role                                                                                                                                                                                                            |
| Website                  | The associated website                                                                                                                                                                                                                          |
| Description              | An optional explanation of the web role's purpose.                                                                                                                                                                                            |
| Authenticated Users Role | Boolean. If set to true, this web role is the default for authenticated users (see below). Websites should only have one web role with the *Authenticated Users Role* attribute set to true. 
| Anonymous Users Role     | Boolean. If set to true, this web role is the default for unauthenticated users (see below). Websites should only have one Web Role with the *Anonymous Users Role* attribute set to true. The *Anonymous Users Role* will only respect table permissions.| 
|| 

### Optional default web roles

Now that the web role has been created, you can configure it to meet your needs via various permissions, rules, and associations.

#### Authenticated users

Enabling the **Authenticated Users Role** makes it the default web role for all users. This role is commonly used to provide a predetermined access for users that aren't associated to any other roles. Keep in mind that users can have multiple web roles, but there can only be one Authenticated Users web role for authenticated users.

#### Unauthenticated users

The **Anonymous Users Role** is intended to be used with table permissions. It will not respect any other rules or permissions. Enabling the *Anonymous Users Role* makes it the default web role for all users. There can only be one Anonymous Users web role for unauthenticated users.

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

The users now have access to the resources specified by the web role.

### From the contact

1. In the **Security** section, select **Contacts**.

1. Locate and open the contact record that you want to assign the web role to.

1. Select the **Related**.

1. Select **Web Roles**.

1. Select **Add Existing Web Role**.

1. From the side panel, search and select the web roles you want to assign to the contact (site user).

The site users now have access to the resources specified by the web role.

### See also

[Configure table permissions](table-permissions.md)</br>
[Assign table permissions](assign-table-permissions.md)</br>
[Tutorial: Display data securely on your site](../getting-started/tutorial-display-data-securely.md)