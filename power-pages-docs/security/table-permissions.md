---
title: Configuring table permissions
description: Learn how to set and manage table permissions.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/27/2022
ms.author: ndoelman
ms.reviewer:
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Configuring table permissions

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE[powerapps-info](../includes/cc-powerapps-info.md)]

Access to Dataverse records is automatically restricted in Power Pages when using forms, lists, Liquid, the Portals Web API, and other components accessing Dataverse tables.

To allow access to Dataverse records in Power Pages sites, you will need to configure **Table permissions** and associate the table permissions to [web roles](create-web-roles.md). 

## How to configure table permissions

You can create table permissions using the following methods:
- when configuring a list or a form on a page
- from the Setup workspace
- Using the Portals Management app

### Adding table permissions from a list or form

1. In design studio, navigate to the page containing the list or form component.

1. Select the form or list component, and then select **Permissions**.

1. The Table permissions panel will appear, you can manage existing permissions or create a new table permission.

    :::image type="content" source="media/table-permissions/add-table-permission-form.png" alt-text="Adding a table permission from a form in design studio.":::

### Adding table permissions from Setup workspace

1. In design studio, select **Setup workspace**.

1. In the **Security** section, select **Table permissions** to add and modify table permissions.

    :::image type="content" source="media/table-permissions/table-permission-setup.png" alt-text="Adding a table permission from the Setup workspace.":::

### Adding table permissions from Portals Management app

1. In design studio, select the ellipses (**...**) from the toolbelt and select **Portal Management**.

    :::image type="content" source="media/table-permissions/launch-portals-management-app.png" alt-text="Launch Portals Management app.":::

1. In the Portal Management app, choose **Table Permissions** in the **Security** section.

:::image type="content" source="media/table-permissions/pma-table-permissions.png" alt-text="Access table permissions using the Portals Management app.":::

## Available access types

Portals Studio shows four different **Access types**. Depending on the access type you choose, the selected table permission and privileges apply to the users from the selected roles for the following records.

1. **Global access** - Applies the selected table permission and privileges to the users from the selected roles for *all records*.
1. **Contact access** - Applies the selected table permission and privileges to the users from the selected role *associated to the signed-in user*.
1. **Account access** - Applies the selected table permission and privileges to the users from the selected role *associated to the signed-in user's account*.
1. **Self access** - Applies the selected table permission and privileges to the users from the selected role *for only their own Contact record*.

> [!NOTE]
> **Parent access type** is only available in the Portal Management app. Instead of creating a table permission with the access type of **Parent**, directly add child permission to existing table permissions when using the design studio.

## Configure table permissions

In this section, you'll learn how to create, view, edit, and deactivate/activate or delete table permissions.

### Create table permissions

1. Select **New permission**.

1. Enter table permission name.

1. Select a table.

1. Select an access type. More information: [Available access types](#available-access-types)

1. If you select the **Contact** or **Account** access type, select the relationship between the Contact/Account and the table you selected for the permission.

    :::image type="content" source="media/table-permissions/contact-account-access-type.png" alt-text="Contact or Account access type.":::

    > [!NOTE]
    > If you don't have any relationships available for the selected table, you can select **New relationship** to create a new relationship.

1. Select the privileges that you want to grant.

1. Select **Add roles** to add the roles that this table permission will apply to.

    > [!TIP]
    > If you have not created a web role yet, select **Manage roles** from the roles flyout to open the Portal Management app and create roles.

1. Select **Save**.

    :::image type="content" source="media/table-permissions/table-permission-example.png" alt-text="The add a video menu with a url pre-filled.":::

### View table permissions

1. In design studio, select **Setup workspace**.

1. In the **Security** section, select **Table permissions** to view table permissions.

    :::image type="content" source="media/table-permissions/edit-table-permissions.png" alt-text="List of existing table permissions.":::

1. To group or filter table permissions, select a view (List/Group by roles/Group by table/Group by state), or enter a table permission name in the filter text box.

    :::image type="content" source="media/table-permissions/group-table-permissions.png" alt-text="Group or filter table permissions.":::

    > [!NOTE]
    > - When you group table permissions by role, table, or state, the permissions are listed as a flat structure without the parent-child relationships for configured permissions.
    > - You can only filter for parent table permissions, not child permissions.

1. To sort the table permissions, select a column at the top in the list of table permissions.

### Edit table permissions

1. In design studio, select **Setup workspace**.

1. In the **Security** section, select **Table permissions** to view table permissions.

1. Select the table permission that you want to edit, alternatively, you can also select more commands (**...**) option, and then choose **Edit**.

1. Change table permission details, such as the name, table, access type, privileges, and applicable roles. More information: [Create table permissions](#configure-table-permissions).

1. Select **Save**.

### Deactivate/activate or delete table permissions

A deactivated table permission becomes ineffective. You can activate a deactivated table permission later. When a table permission is deactivated, its child table permissions remain active but are not in effect due to the ineffective parent table permission. You can deactivate child permissions separately.

When a table permission is deleted, it also deletes all associated child permissions.

To deactivate/activate or delete a table permissions:

1. In design studio, select **Setup workspace**.

1. In the **Security** section, select **Table permissions** to view table permissions.

1. Select the table permission that you want to deactivate/activate or delete.

1. Select the more commands option (**...**) and choose **Deactivate** or **Delete**.

1. Confirm when prompted.

## Configure child permissions

To add a child permission to an existing table permission:

1. In design studio, select **Setup workspace**.

1. In the **Security** section, select **Table permissions** to view table permissions.

1. Select the table permission that you want to add the child permission to. In the table permissions property panel, select the **Child permissions** tab and choose **New**. Alternatively, you can also select the more commands option (**...**), and then choose **Add child permission**.

1. Create the child permission with the following details:

    1. Name for the child permission
    
    1. Table that the child permission is for
    
    1. Relationship between the table for primary table permission, and the selected table for the child permission
    
    1. Privileges for the child permissions
    
    1. Roles (These are inherited from the parent table permission. To add/remove roles, edit the parent table permission instead.)

1. Select **Save**.

To view, edit, deactivate/activate, or delete child permissions using portals Studio, follow the steps explained in the earlier section to [configure table permissions](#configure-table-permissions).

## Additional considerations

The configuration of table permissions is subject to the following additional considerations and rules:

### Parent table permission missing a web role associated to its child

When you have a child permission associated with one or more web roles missing from the parent permissions, you'll see the following error while editing the child permissions:

> One or more roles applied to this permission aren't available to its parent table permission. Modify roles in either permissions.

For example, a child table permission shows the below message when the parent table permission doesn't have the *Marketing* web role associated, even though the child permission is still associated.

:::image type="content" source="media/table-permissions/missing-webrole-parent.png" alt-text="Parent table permission missing one or more web roles associated to child table permission.":::

To fix this problem, add the *Marketing* web role to the parent table permission, or remove the *Marketing* web role from the child table permission.

### Table permissions without any web roles associated

For a table permission to take effect, it has to be associated to one or more web roles. Users that belong to web roles are granted the privileges you select for the associated table permission.

The following message shows when you try to save a table permission without any web role associated.

:::image type="content" source="media/table-permissions/table-permission-without-webrole.png" alt-text="Saving a table permission without any associated web role.":::

### See also

[Assign table permissions](assign-table-permissions.md)<br>
[Tutorial: Display data securely on your site](../getting-started/tutorial-display-data-securely.md)
