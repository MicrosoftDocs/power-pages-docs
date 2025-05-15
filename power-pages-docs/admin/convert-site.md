---
title: Convert a website
description: Learn how to convert a website to different lifecycle stages.
author: neerajnandwana-msft

ms.topic: how-to
ms.custom: 
ms.date: 09/06/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---

# Convert a website

As explained in the [Power Pages lifecycle](lifecycle.md) topic, a Power Pages website goes through different stages. You can convert a website from one stage to another, depending on what conversion is allowed, and whether the environment has the required license, or capacity.

## Convert a website from trial to production

You can convert a trial website to a production website from the notifications displayed in the **Power Pages sites** section in the Power Platform admin center.

> [!NOTE]
> You must be assigned one of the following roles to convert a website from trial to production:
> - System administrator
> - Power Platform administrator
> - Dynamics 365 administrator
>
> More information: [Admin roles required for portal administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles)

When you open the **Power Pages sites** section for your website in the [Power Platform admin center](admin-overview.md) you'll see the notification about the trial expiration.

:::image type="content" source="media/power-platform-admin-center/admin-center-convert-notification.svg" alt-text="Convert notification.":::

To convert your website from trial to production:

1. In the notification, select **Convert** or in the **Site Details** section select **Convert to Production**.

    :::image type="content" source="media/power-platform-admin-center/trial-to-prod-confirm.png" alt-text="Trial to production confirmation.":::

    > [!NOTE]
    > - You will also have the option to turn on the [content delivery network](/power-apps/maker/portals/configure/configure-cdn) option for your website.
    > - You cannot convert a website on a developer environment to a production website.

1. Select **Confirm**.

> [!IMPORTANT]
> Once the website has been converted to production, you should ensure that the website is appropriately licensed with the appropriate subscription plans corresponding to the expected user volume. Not having appropriate licenses assigned can result in degraded performance. For information on how to allocate licenses, see [Allocate or change capacity in an environment](/power-platform/admin/capacity-add-on#allocate-or-change-capacity-in-an-environment).


## Convert an existing website to capacity-based model

You can convert your existing Power Pages license to [capacity-based licensing model](/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing). To change your portal license to capacity-based model:

> [!TIP]
> To learn about the roles required to perform this task, read [Admin roles required for portal administrative tasks](admin-roles.md).

## [New admin center](#tab/new)
1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select **Manage**, then **Power Pages**, and select the site with *Add-on* as its **Type**.
1. Select **Change License**, and then **Confirm**.
:::image type="content" source="media/convert-site/new_admin_capacity_license.png" alt-text="Convert license to capacity based in new admin center" lightbox="media/convert-site/new_admin_capacity_license.png":::

## [Classic admin center](#tab/classic)
1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select **Resources**, then **Power Pages sites**, and select the site with *Add-on* as its **Type**.
1. Select **Change License**, and then **Confirm**.
:::image type="content" source="media/convert-site/old_admin_capacity_license.png" alt-text="Convert license to capacity based in old admin center" lightbox="media/convert-site/old_admin_capacity_license.png":::
---

Consider the following before changing your Power Pages license:

- Your website will restart and won't be available for a few minutes during license conversion. You might need to schedule this for a downtime period for business users.
- Your environment must have an appropriate [license](/power-platform/admin/powerapps-flow-licensing-faq#portals) available and assigned before you convert the license.
- You must have administrative privileges to convert the license.
- Only production environments can be converted from an existing license to a capacity-based license. If you have a [trial environment](/power-platform/admin/trial-environments), you must convert it to a production environment first.

## Considerations for conversion of add-on portals

The following sections describe the conditions that apply to portals that were [provisioned by using the portal add-on plan](/power-apps/maker/portals/provision-portal-add-on).

### Trial add-on portal

A trial add-on portal expires after 30 days. An expired portal is suspended for seven days. The portal is deleted after the suspension period ends. A trial add-on portal can still be converted to a production portal during the period when it has either been configured to an environment or suspended.

### Production add-on portal

A production add-on portal expires at the end of the purchased license period. The suspension period for a production add-on portal can vary depending on the license plan you purchased. The portal is deleted after the suspension period ends. You can extend the license of a production add-on portal while the portal is in a configured or suspended state. If it has been suspended, the portal can be converted to a configured state after you extend the license period.

> [!IMPORTANT]
> - To avoid functionality loss by having your portal suspended or deleted, ensure that you've extended the license period in a timely manner, well before expiry.
> - When converting a production add-on portal using a [custom domain](add-custom-domain.md) to a Power Pages website (current licensing model), you may need to reconfigure your custom domain settings. Ensure that you [update your custom domain name](add-custom-domain.md) as part of the conversion process in this situation.

### Suspended add-on portal

Portal [provisioned using portal add-on plan](/power-apps/maker/portals/provision-portal-add-on) purchased earlier is suspended at the end of expiration. This expiration period is 30 days for trial portals while it may vary for an add-on portal in production with a purchased license. Suspended trial portal is deleted after 7 days while suspension period may vary for production portal.

### Delete add-on portal

Follow the steps in [Delete a website](delete-website.md) to delete a portal that was provisioned by using a previously purchased, portal add-on plan.

### See also

- [Understand lifecycle of a portal](/power-apps/maker/portals/admin/portal-lifecycle) 
- [Portal application lifecycle management](/training/modules/extend-power-app-portals/2-portal-application-lifecycle)
- [Power Pages FAQ](../faq.yml)
- [Power Pages licensing FAQ](/power-platform/admin/powerapps-flow-licensing-faq#power-pages)

