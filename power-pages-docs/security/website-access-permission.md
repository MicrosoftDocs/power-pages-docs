---
title: Create website access permissions
description: Learn how to create and associate website access permissions to elements in a Power Pages site.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 3/3/2023
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
---

# Create website access permissions

Website Access Permissions is a permission set, associated with a [web role](create-web-roles.md), that permits front-side editing of the various content managed elements within the website other than just web pages. The permission settings determine which components can be managed in the site.

| Name                         | Description                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| Manage Content Snippets      | Allows the editing of Snippet controls.                                                          |
| Manage Site Markers          | Allows the editing of hyperlinks that use Site Markers                                           |
| Manage Web Link Sets         | Allows the editing of [web link sets](/power-apps/maker/portals/configure/manage-web-links), including adding an removing web links from a web link set. |
| Preview Unpublished Entities | Allows the viewing of portal-exposed tables that have a publishing state of Draft.             |
|||

To create a website access permission and add it to a web role:

1. Open the [Portal Management app](../configure/portal-management-app.md).

2. Go to **Portals** > **Website Access Permissions**.

3. Select **New**.

4. Under **General**, enter name, website, and select the required permissions.

5. Under **Web Roles**, select **Add Existing Web Role**, and add the web role to associate the permission with.

6. Save the changes.

