---
title: Manage websites from the Power Platform admin center
description: Learn about Power Pages admin settings in the Power Platform admin center.
author: vamseedillimsft

ms.topic: conceptual
ms.custom: 
ms.date: 07/17/2023
ms.subservice: 
ms.author: vamseedilli
ms.reviewer: kkendrick
contributors:
    - vamseedillimsft
    - neerajnandwana-msft
    - nickdoelman
---

# Manage websites from the Power Platform admin center

You can now use the Power Platform admin center to manage websites in your tenant. You can also see information such as how many days are left before a trial website expires. For more information about Power Pages licensing, go to the [licensing FAQ](/power-platform/admin/powerapps-flow-licensing-faq#power-pages). For more information about the Power Platform admin center, go to [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation).

You can manage websites in the Power Platform admin center in two ways:

- Manage all websites for the current tenant from **Resources** > **Power Pages sites**.
- Manage websites for a specific environment from **Environments**.

## Manage all websites for a tenant

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. On the left pane, select **Resources**, and then select **Power Pages sites**.

    :::image type="content" source="media/power-platform-admin-center/website-lists.png" alt-text="List of websites in a tenant.":::

1. Select a website.

1. Select the ellipse **...**, and then select **Manage**.<br>or<br>Select the website, and then select **Manage** at the top of the page.

From here you can configure website details, for more information go to [site details](admin-overview.md#site-details).

Selecting on any of the cards in the header will filter the lists to the chosen website type.

You can export a list of website information by selecting the **Export to csv** button.

>[!NOTE]
> You can only view the list of websites from the environments you are a system administrator for. If you are a service administrator (D365 administrator or Power Platform administrator), you can view the list of all websites in your tenant.

## Manage all websites for an environment

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. On the left pane, select **Environments**.

1. Hover over and select the hyperlinked environment name to open the environment details.

1. On the right side of the screen, under **Resources**, select **Power Pages sites**.

    :::image type="content" source="media/power-platform-admin-center/environment-info.png" alt-text="Power Platform environment details.":::

1. You'll see a list of websites installed in the selected environment.

1. Select the ellipse (**...**), and then select **Manage**.<br>or<br>Select the site, and then select **Manage** from the top of the page.

To configure website details, see [site details](admin-overview.md#site-details).

## Website types in the admin center

The following table describes the different types of websites that are listed in the Power Platform admin center.

| Type                |Description                                                           |
|---------------------|----------------------------------------------------------------------|
| Production          | A production website based on a capacity-based license.               |
| Trial (*n* days)    | A trial website based on a capacity-based license, with _n_ days remaining until suspension. |
| Production (add-on) | A production website based on an add-on license.     |
| Trial (add-on)      | A trial website based on an add-on license.          |

## Website status in the admin center

A website can have the following status: *Configured*, *Suspended*, or *Not configured*. The following table describes each state.

| Status         |  Description    |
|----------------|-----------------|
| Configured     | This website has been configured to an environment.     |
| Suspended      | This website has been suspended because its trial period is over. It will be deleted in seven days, unless it's converted to a production website. |
| Not configured | This website is ready to be configured to an environment.   |

## Next steps

[Configure site details](admin-overview.md#site-details)

### See also

- [Manage website security from the admin center (preview)](admin-center-security.md)
- [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation)
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)  
- [Upgrade a website](upgrade-site.md)
