---
title: Using solutions with Power Pages
description: Learn how to solutions in Power Pages.
author: gitanjalisingh33msft
ms.topic: conceptual
ms.custom: 
ms.date: 04/19/2023
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - gitanjalisingh33msft
    - neerajnandwana-msft
---

# Using solutions with Power Pages (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Using solutions with Power Pages allows you to contain and transport all website configuration using standard Power Platform [solutions](/power-platform/alm/solution-concepts-alm). You can combine all website and Dataverse components into a single solution artifact and participate in advanced ALM capabilities to deploy websites to destination environments using managed solutions. 

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisites

To try this feature, you'll require two Power Platform environments that have the enhanced data model enabled, one designated as the source and the other as the target. See [Power Pages enhanced data model](../getting-started/enhanced-data-model.md) to enable the enhanced data model for an environment.

Each environment will required a site that is created using the new data model. See [create a website with an enhanced data model](../getting-started/enhanced-data-model.md#create-a-website-with-an-enhanced-data-model).

## Add Power Pages site and components to a solution

1. From the Power Pages home page, select the **Solutions** tab.

:::image type="content" source="media/solutions/power-pages-home-solutions.png" alt-text="Solutions on Power Pages home page.":::

1. Create a new solution using the new solution command on the command bar. Fill in the solution details and select **Create** to create the new solution. 

1. Navigate to the solution.

1. From the **Add Existing menu**, select **Site**.

    :::image type="content" source="media/solutions/add-to-solution.png" alt-text="Add site to a solution.":::

1. From the Add existing sites panel, select site(s) and choose Add.

> [!NOTE]
> The process will add all of the site components to the solution.

## Add website components

As you create and add new components to your website, you can add them to your solution containing the website.

> [!NOTE]
> New website components are not automatically added to a solution containing a site. You will need to add any new website components to a solution following the steps below.

1. From the Power Pages home page, go to the **Solutions** area.

1. Select the solution to which you want to add components.

1. Select **Add existing** > **More** > **Other** > **Site Component**.
 
1. From the **Add existing Site component** panel, select the site components and select **Add** to add them to the solution.

Alternatively, you can add the required components to your site.

1. In the solution, select the **Site**.

1. From the main menu, choose **Advanced** and then select **Add required objects**.

1. A panel will appear, select **OK** to continue. After a few moments you will see a message that the required objects have been successfully added to the solution.

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

## Frequently asked questions: 

### What is best practice when you're migrating a Power Pages website using solutions? 

Refer to [Overview of application lifecycle management with Microsoft Power Platform](/power-platform/alm/overview-alm) for best practices.

### After importing site configuration data in a managed solution I edited my website in the target environment. I don't see any new changes when I import managed solutions from my source environment.

Editing the site configuration data in the target environment is discouraged as it will result in the creation of an unmanaged layer and changes from the source won't reflect in the target. To fix it in the target environment user needs to remove the unmanaged solution layer. See [Solution layers](/power-platform/alm/solution-layers-alm) for more information.

## See Also
- [Power Pages enhanced data model](../getting-started/enhanced-data-model.md)

