---
title: Enhanced view filter for lists
description: Learn how to configure an enhanced view filter for lists on a website.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 04/10/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - sandhangitmsft
---

# Enhanced view filter for lists

You can use table permissions if you want to secure records.  If you want to filter records based on the current portal user’s context, you can configure a filter on the underlying model-driven view definition used by the list using the [Data workspace](data-workspace-views.md). This feature supports filtering of the current user, user's parent account, or website at any depth. Build the view filter to match any single contact record and the code will replace its value with the actual value at runtime&mdash;no need to assign values to fields in the Filter Conditions section.

- The control will find all condition elements where uitype="contact" and set the value to the actual value of the current website user's contact ID.
- The control will find all condition elements where uitype="account" and set the value to the actual value of the current website user's parent account ID.
- The control will find all condition elements where uitype="adx_website" and set the value to the actual value of the current website ID.

### Example View Filter Criteria

The following image shows an arbitrary contact assigned to a filter condition, this contact happens to be a stub 'dummy' contact but this could be any contact record. The ID of this record will be replaced by the actual value of the ID of the user viewing the page. If the user isn't logged in, no records will be returned. This provides greater flexibility in filtering the data based on the user and website contextually.

:::image type="content" source="media/lists/entity-list-view-filter-criteria.png" alt-text="Example view filter criteria.":::

> [!NOTE]
> If you are filtering by current website user's contact or parent account then it is recommended that you associate a [page permission](../security/page-security.md) to the web page to force the user to sign in. You would need to create a [web role](../security/create-web-roles.md). Configure page permissions and associate the web role. This will force users to be signed in to view the page and therefore allow the data to be filled accordingly.

### See also

- [Lists overview](lists.md)
- [Portal Management app](portal-management-app.md)  
- [Redirect to a new URL](add-redirect-url.md)


