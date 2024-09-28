---
title: Set website access permissions
description: Learn how to create and associate website access permissions to elements in sites you create with Microsoft Power Pages.
ms.date: 07/21/2023
ms.topic: how-to
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - nickdoelman
    - sandhangitmsft
ms.custom: bap-template
---

# Set website access permissions

Website access permissions allow front-end editing of content-managed elements other than web pages. They're a set of permissions that are associated with a [web role](create-web-roles.md). The permission settings determine which site elements can be edited.

| Name | Description |
| --- | --- |
| Manage Content Snippets | Allows the editing of snippet controls. |
| Manage Site Markers | Allows the editing of hyperlinks that use site markers. |
| Manage Web Link Sets | Allows the editing of [web link sets](/power-apps/maker/portals/configure/manage-web-links), including adding and removing links from a web link set. |
| Preview Unpublished Entities | Allows the viewing of tables that have a publishing state of Draft. |

Use the [Portal Management app](../configure/portal-management-app.md) to create and assign website access permissions.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, scroll down to **Security** and select **Website Access Permissions**.

1. Select **New**.

1. On the **General** tab, enter or select the **Name**, the **Website** to associate with the permissions, and the permissions to apply.

1. Select the **Web Roles** tab, select **Add Existing Web Role**, and add a web role to associate with the permission.

1. Select **Save & Close**.
