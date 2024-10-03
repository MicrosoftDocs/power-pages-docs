---
title: Update the Dynamics 365 instance for your Power Pages site
description: Learn how to update the Dynamics 365 instance for your Power Pages site.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 08/27/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---

# Update the Dynamics 365 instance for your Power Pages site

You can use the Power Platform admin center to update the Dynamics 365 instance for your website.

> [!IMPORTANT]
> When changing the Dynamics 365 instance for your site, ensure that the new instance is from the same [region](/power-platform/admin/regions-overview) as the current instance. Changing the Dynamics 365 instance for Power Pages across regions isn't supported.

1. Open the [Power Platform admin center](admin-overview.md).
    1. You can open the admin center from the **Set up** workspace of your site.
    1. You can also directly open the [Power Platform admin center](https://aks.ms/ppac) and then select **Power Pages sites** from the **Resources** tab.
    1. Select the website and then choose **Manage**.

1. Select the **...** (ellipse) option that appears between the **Site Actions** and **Switch to Classic**.

1. Select **Manage Dynamics 365 Instance**.

    :::image type="content" source="media/power-platform-admin-center/manage-Dynamics365-instance.svg" alt-text="Text used by screen readers.":::

1. Select **Update Dynamics 365 Instance**.

    :::image type="content" source="media/power-platform-admin-center/update-dynamics365-instance.svg" alt-text="Update your Dynamics 365 instance.":::

1. Select your existing instance and portal.

    :::image type="content" source="media/power-platform-admin-center/select-dynamics365-instance.svg" alt-text="Select your Dynamics 365 instance":::

1. Select **OK**.

1. Select **Submit** to confirm.

    :::image type="content" source="media/power-platform-admin-center/submit-selection.svg" alt-text="Submit Dynamics 365 solution update.":::

    You'll see a confirmation that the update request is in progress.

The update might take a while after you select **Submit**. More information: [Upgrade site](upgrade-site.md)

> [!NOTE]
> You may be required to [reload SSL certificates](/power-apps/maker/portals/admin/manage-ssl-certificates) after you have updated the Dynamics 365 instance.

## See also

- [Upgrade a website](upgrade-site.md) 
- [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation) 
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)
