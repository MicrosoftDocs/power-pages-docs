---
title: Transfer ownership of a Power Pages site
description: Learn how Power Pages site ownership transfer moves a site's primary owner between tenant members using the Edit Details panel in the Power Platform admin center.
author: shwetamurkute
ms.author: apsinhar
ms.reviewer: smurkute
ms.date: 10/13/2026
ms.topic: how-to
---

# Transfer ownership of a Power Pages site

Transfer ownership of a Power Pages site when responsibility for managing the site moves to another user in your organization. The new owner becomes the primary owner of the site.

Depending on the site's permissions and configuration, the previous owner might lose access to the site.

> [!IMPORTANT]
> You can't automatically undo an ownership transfer. To restore the previous owner, an authorized administrator must transfer ownership back to that user.

## Prerequisites

Before you transfer site ownership, ensure that:

- You are the website app owner and have any one of the following roles:
    - System administrator
    - Dynamics 365 administrator
    - Power Platform administrator
- You have access to the [Power Platform admin center](https://aka.ms/ppac). 
- The new owner is an enabled Microsoft Entra user with a **Member** user type. 

To learn more about the roles required, see [Admin roles required for website administrative tasks](admin-roles.md).

> [!IMPORTANT]
> Websites on [Power Platform managed identity](../security/identity-provisioning.md) model don't need web app ownership as a prerequisite for initiating transfer. For other portals, if you don't see the ownership transfer option, check whether you're the web app owner. Learn more in [Add an Owner to an Application Using Microsoft Graph](/troubleshoot/entra/entra-id/users-groups-entra-apis/add-owner-for-application-microsoft-graph).

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

To view ownership transfer activity in Microsoft Purview, see [View Power Pages activity logs in Microsoft Purview](/power-platform/admin/activity-logging-auditing/activity-logs-power-pages#explore-power-pages-activities).

### See also

- [Admin roles required for website administrative tasks](admin-roles.md).
- [Manage website authentication key](manage-auth-key.md).  
