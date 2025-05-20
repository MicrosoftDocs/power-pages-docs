---
title: Manage forum access permissions
description: Learn about managing forum access permissions in Power Pages.
author: murugesh1985
ms.topic: how-to
ms.custom: 
ms.date: 2/20/2025
ms.subservice: 
ms.author: murugeshs
ms.reviewer: danamartens
contributors: nageshbhat-msft
---

# Manage forum access permissions

Forum Access Permission is a security rule that can be assigned to a particular forum and web role that can restrict particular users from viewing the forum or granting particular users the ability to moderate a forum within the webpages. To create, edit, or delete forum access permissions:

1. Sign in to Power Pages.

1. Go to **Community** > **Forum Access Permissions**.

    :::image type="content" source="media/forum-access-permission.png" alt-text="Forum access permission":::

1. To create a new forum access permission, select **New**.

1. To edit an existing permission, select the permission name.

1. Enter appropriate values in the fields.

1. Select **Save & Close**.

    :::image type="content" source="media/edit-forum-access-permission.png" alt-text="Edit forum access permission":::

> [!NOTE]
> A web role must be assigned for the rule to apply for users associated with the given role. See [Provide access to external audiences](../../security/external-access.md).

## Permission attributes

The table below explains the forum access permission attributes used by Power Pages.

|Name     |Description                                                                        |
|---------|-----------------------------------------------------------------------------------|
|Name     |A name used for reference within Microsoft Dataverse.                              |
|Forum    |The [forum threads](manage-forum-threads.md) associated with the permission.       |
|Right    |The permission settings are:<br /><ul><li>**Restrict Read**: Prevents viewing of the forum for users unless in a web role associated with the rule.</li><li>**Grant Change**: Allows a user in a web role associated with the rule to moderate the forum. Grant Change takes precedence over Restrict Read.</li></ul>                                                                 |

> [!NOTE]
> Starting with Power Pages site version 9.7.1.34, default read access on the forum is turned off. Makers need to configure Forum Access Permission with 'Restrict Read' to provide access.

### See also

- [Setup and manage forums](setup-manage-forums.md)  
- [Manage forum threads](manage-forum-threads.md)  
- [Create forum posts](create-forum-posts.md)  
- [Subscribe to alerts](subscribe-alerts.md)  
