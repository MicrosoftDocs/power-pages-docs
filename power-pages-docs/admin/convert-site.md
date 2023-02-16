---
title: Convert a website
description: Learn how to convert a website to different lifecycle stages.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 02/15/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Convert a website

As explained in the [portal lifecycle](/power-apps/maker/portals/admin/portal-lifecycle) topic in the Power Apps documentation, a Power Pages website goes through different stages. You can convert a website from one stage to another, depending on what conversion is allowed, and whether the environment has the required license, or capacity.

## Convert a website from trial to production

You can convert a trial website to a production website from the notifications displayed in the **Power Pages sites** section in the Power Platform admin center.

> [!NOTE]
> You must be assigned one of the following roles to convert a website from trial to production:
> - Global administrator
> - System administrator
>
> More information: [Admin roles required for portal administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles)

When you open the **Power Pages sites** section for your website in the [Power Platform admin center](admin-overview.md) you'll see the notification about the trial expiration.

:::image type="content" source="media/power-platform-admin-center/admin-center-convert-notif.png" alt-text="Text used by screen readers.":::

To convert your website from trial to production:

1. In the notification, select **Convert** or in the **Site Details** section select **Convert to Production**.

    :::image type="content" source="media/power-platform-admin-center/trial-to-prod-confirm.png" alt-text="Trial to production confirmation.":::

    > [!NOTE]
    > You will also have the option to turn on the [content delivery network](/power-apps/maker/portals/configure/configure-cdn) option for your website.


1. Select **Confirm**.

> [!IMPORTANT]
> Once the website has been converted to production, you should ensure that the website is appropriately licensed with the appropriate subscription plans corresponding to the expected user volume. Not having appropriate licenses assigned can result in degraded performance. For information on how to allocate licenses, see [Allocate or change capacity in an environment](/power-platform/admin/capacity-add-on#allocate-or-change-capacity-in-an-environment).

### See also

- [Power Pages licensing FAQ](/power-platform/admin/powerapps-flow-licensing-faq#power-pages)

