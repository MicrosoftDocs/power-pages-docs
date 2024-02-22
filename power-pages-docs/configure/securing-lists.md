---
title: Securing lists
description: Learn how to secure lists on Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 02/23/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
    - ProfessorKendrick
---

# Securing lists

To secure a list, you must configure [table permissions](../security/table-permissions.md) for the table for which records are being displayed.

Starting with release [9.3.7.x](/power-platform/released-versions/portals/portalupdate1), newly created websites will have table permissions enforced for all lists irrespective of the **Enable Table Permissions** setting.

> [!NOTE]
> The changes described above also apply to sites [converted](/power-apps/maker/portals/admin/convert-portal) from trial to production.

To configure anonymous access explicitly, use proper [table permissions](../security/table-permissions.md), and relate to the **Anonymous Users** web role or a custom web role with **Anonymous Users Role** option.

Securing your list will ensure that users only see the records they have permissions for. 

Securing data related to specific users (or their related accounts) is accomplished by adding a relationship between the table and either the *contact* or *account* table whereby only portal users that have a relationship to these records will be able to access the data using the table permission type of *Account* or *Contact*, and the setting up appropriate privileges and associating [web roles](../security/create-web-roles.md) to the table permission.

Good website design requires that if a user's role doesn't have permissions for the table (that is, there will never be a situation where they should see any records), they shouldn't have access to the page at all. Ideally, the page should also be protected by using [Page permissions](../security/page-security.md).

If you want to display the records level actions that are applicable to the signed in user, you must set the value of **EntityList/ShowRecordLevelActions** site setting to **true**. 

For example, there are two users: Preston and Teddy. Preston has contact level all access on the *case* table, whereas Teddy has global read access. If a list is created to show all the *case* records, Preston would see all actions (**View**, **Edit**, and **Delete**) on the records that are related their contact. On other records, they would only see the **View** action. On the other hand, Teddy would only see the **View** action on all records.

If the **EntityList/ShowRecordLevelActions** site setting is set to **false** and the table has multiple permissions, all the record level actions are visible. But, when a user tries to perform an action without authorization, an error is displayed.

### See also

- [Lists overview](lists.md)
- [Portal Management app](portal-management-app.md)  
- [Redirect to a new URL](add-redirect-url.md)
