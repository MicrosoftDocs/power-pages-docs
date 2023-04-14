---
title: Using solutions with Power Pages
description: Learn how to solutions in Power Pages.
author: gitanjalisingh33msft
ms.topic: conceptual
ms.custom: 
ms.date: 04/14/2023
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - gitanjalisingh33msft
    - neerajnandwana-msft
---

# Using solutions with Power Pages

Using solutions with Power Pages allows to contain and transport all website configuration using standard Power Platform solutions.

## Prerequisites

To try this feature, you'll require two Power Platform environments that have the enhanced data model enabled, one designated as the source and the other as the target. See [Power Pages enhanced data model](../getting-started/enhanced-data-model.md) to enable the enhanced data model for an environment.

Each environment will required a site that is created using the new data model. See [create a website with an enhanced data model](../getting-started/enhanced-data-model.md#create-a-website-with-an-enhanced-data-model).

## Add Power Pages site and its component to a solution

1. From the Power Pages home page, select the **Solutions** tab.

:::image type="content" source="media/solutions/power-pages-home-solutions.png" alt-text="Solutions on Power Pages home page.":::

1. Create a new solution using the new solution command on the command bar. Fill in the solution details and select **Create** to create the new solution. 

1. Navigate to the solution.

1. From the **Add Existing menu**, select **Site**.

    :::image type="content" source="media/solutions/add-to-solution.png" alt-text="Add site to a solution.":::

1. From the Add existing sites panel, select site(s) and choose Add.

> [!NOTE]
> The process will add all of the site components to the solution.

## Export solution from source environment

Select the solution and choose **Export solution** from the main menu. See [Solution Concepts](/power-platform/alm/solution-concepts-alm) for more information on importing and exporting solutions.

## Import solution to destination environment.

1. Select **Import solution** from the top toolbar.

1. Browse to the location of the exported solution, select the file and choose open.

1. Select **Next**.

1. Select **Import**.

Once the solution is imported, it will appear under solutions list.

> [!NOTE]
> If the solution is unmanaged, select **Publish all customizations** in the destination environment.

## Binding enhanced data model website record to a site

1. Navigate to the [Power Platform admin center](https://aka.ms/ppac)

1. Select the destination environment

1. Select **Power Pages sites** from the **Resources** section.

1. Select the destination site, select the ellipse (…) and choose **Manage** to display the site details page.

1. Choose the **Edit** button from the **Site Details** section and select the imported site record in the **Website Record** dropdown, then choose Save.

:::image type="content" source="media/solutions/link-site.png" alt-text="Text used by screen readers.":::

1. Choose **Site Actions**, and then **Restart site**.

Now your destination site is updated with data from source environment site.

## See Also
- [Power Pages enhanced data model](../getting-started/enhanced-data-model.md)

