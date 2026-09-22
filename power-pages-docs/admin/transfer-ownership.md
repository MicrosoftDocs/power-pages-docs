---
title: Transfer ownership of a Power Pages site
description: Learn how Power Pages site ownership transfer moves a site's primary owner between tenant members using the Edit Details panel in the Power Platform admin center.
author: shwetamurkute
ms.author: apsinhar
ms.reviewer: smurkute
ms.date: 09/21/2026
ms.topic: how-to
---

# Transfer ownership of a Power Pages site

Transfer ownership of a Power Pages site when responsibility for managing the site moves to another user in your organization. The new owner becomes the primary owner of the site.

Depending on the site's permissions and configuration, the previous owner might lose access to the site.

> [!IMPORTANT]
> You can't automatically undo an ownership transfer. To restore the previous owner, an authorized administrator must transfer ownership back to that user.

## Prerequisites

Before you transfer site ownership, ensure that:

- You have any one of the following roles:
    - Website owner who is a System administrator as well
    - Dynamics 365 administrator
    - Power Platform administrator
- You have access to the [Power Platform admin center](https://aka.ms/ppac). 
- The new owner is an enabled Microsoft Entra user with a **Member** user type. 

To learn more about the roles required, see [Admin roles required for website administrative tasks](admin-roles.md).

## Transfer site ownership

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the left navigation pane, select **Manage**, and then select **Power Pages**.
1. Select the Power Pages site that you want to update.
1. On the **Site Details** page, select **Edit**.
    :::image type="content" source="media/transfer-ownership/power-pages-site-details-page.png" alt-text="Power Pages site details page showing site information before editing.":::
1. In the **Owner** field, remove the current owner and search for the new owner.
    :::image type="content" source="media/transfer-ownership/edit-details-panel-owner.png" alt-text="Edit Details panel showing the editable Owner field with the current owner.":::
1. Select the new owner, and then select **Save**.
1. Review the confirmation message, and then select **Transfer**.

When the transfer finishes, the selected user becomes the primary owner of the site. Verify that the new owner can access and manage the site.


### See also

- [Admin roles required for website administrative tasks](admin-roles.md).
- [Manage website authentication key](manage-auth-key.md).
