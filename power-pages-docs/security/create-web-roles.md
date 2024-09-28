---
title: Create and assign web roles
description: Learn how to use web roles to manage permissions on sites you create with Microsoft Power Pages.
ms.date: 11/06/2023
ms.topic: how-to
author: gitanjalisingh33msft
ms.author: gisingh
ms.reviewer: danamartens
contributors:
ms.custom: bap-template
---

# Create and assign web roles

A web role is basically a collection of permissions to the content of your site. Before you can grant authenticated users access to [restricted tables](table-permissions.md) or [restricted pages](page-security.md), you need to assign them to a web role.

Use the [Portal Management app](../configure/portal-management-app.md) to create and assign web roles.

## Create a web role

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, scroll down to **Security** and select **Web Roles**.

1. Select **New**.

1. Enter or select a **Name**, the **Website** to associate with the role, and an optional **Description**.

1. Select whether authenticated or unauthenticated users should [have this role by default](#default-web-role-for-authenticated-or-anonymous-users). The default for both is **No**.

    - If *authenticated* users should have this role by default, select **Yes** for **Authenticated Users Role**. A website should have only one web role that's the default role for authenticated users.
    - If *unauthenticated* users should have this role by default, select **Yes** for **Anonymous Users Role**. A website should have only one web role that's the default role for unauthenticated users. The **Anonymous Users Role** respects only table permissions.

1. Select **Save**.

### Default web role for authenticated or anonymous users

If you set **Authenticated Users Role** to **Yes**, the web role is the default role for all users. This role is commonly used to provide predetermined access for users who aren't assigned any other roles. Keep in mind that users can have multiple web roles, but a site can have only one Authenticated Users web role for authenticated users.

If you set **Anonymous Users Role** to **Yes**, the web role is the default role for all users. This role is intended to be used with table permissions. It doesn't respect any other rules or permissions. A site can have only one Anonymous Users web role for unauthenticated users.

## Assign users to web roles

You can assign site users to web roles from either the contact record or the web role record. However, if your site uses the [enhanced data model](../admin/enhanced-data-model.md), then assign web roles [from the contact under the enhanced data model](#from-the-contact-enhanced-data-model).

### From the web role

1. In the Portal Management app, select **Security** > **Web Roles**.

1. Select a web role.

1. Select the **Related** tab, and then select **Contacts**.

1. Select **Add Existing Contact**.

1. Search for and select the site users to assign to the web role.

1. Select **Add**, and then select **Save**.

### From the contact

1. In the Portal Management app, select **Security** > **Contacts**.

1. Select a contact.

1. Select the **Related** tab, and then select **Web Roles**.

1. Select **Add Existing Web Role**.

1. Search for and select the web roles to assign to the site user.

1. Select **Add**, and then select **Save**.

### From the contact (enhanced data model)

1. In the Power Pages Management app, select **Security** > **Contacts**.

1. Select a contact.

1. Select the **Portal Contact (Enhanced Form)**

1. In the **General** tab, scroll down to the **Web Roles** section and select **Add Existing Web Role**.

    :::image type="content" source="media/web-role/web-role-enhanced.png" alt-text="Screenshot of assigning a web role under the enhanced data model.":::

1. Search for and select the web roles to assign to the site user.

1. Select **Add**, and then select **Save**.

### See also

[Set table permissions](table-permissions.md)  
[Assign table permissions](assign-table-permissions.md)  
[Tutorial: Display data securely on your site](../getting-started/tutorial-display-data-securely.md)
