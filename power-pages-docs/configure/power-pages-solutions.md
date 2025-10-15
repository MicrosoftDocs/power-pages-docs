---
title: Use solutions with Power Pages
description: Learn how to use solutions with Power Pages.
author: gitanjalisingh33msft
ms.topic: how-to
ms.date: 09/09/2024
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - gitanjalisingh33msft
    - neerajnandwana-msft
ms.custom:
  - sfi-image-nochange
---

# Use solutions with Power Pages

By using solutions with Power Pages, you can contain and transport all website configurations through standard Microsoft Power Platform [solutions](/power-platform/alm/solution-concepts-alm). Combine all website and Dataverse components into a single solution artifact, and then take advantage of advanced application lifecycle management (ALM) capabilities to deploy websites to destination environments by using managed solutions.

## Prerequisites

You'll need to enable enhanced data model to use solutions with Power Pages. More information: [Power Pages enhanced data model](../admin/enhanced-data-model.md)

## Add Power Pages site and components to a solution

1. Open the [Power Pages home page](https://aka.ms/mpp).
1. Select the **Solutions** tab.

    :::image type="content" source="media/solutions/power-pages-home-solutions.png" alt-text="Screenshot that shows the Solutions tab on the Power Pages home page.":::

1. On the toolbar at the top of the page, select **New solution**. Fill in the solution details, and then select **Create** to create the solution.
1. Go to the new solution.
1. On the **Add existing** menu, select **Site**.

    :::image type="content" source="media/solutions/add-to-solution.png" alt-text="Screenshot that shows the Site command on the Add existing menu.":::

1. In the **Add existing sites** panel, select one or more sites, and then select **Next**.
1. Choose the components to include:
    - To add all related components, select **Include all objects**.
    - To select specific components, choose **Edit objects** and select the items you want.
    - To remove all selected components, select **Clear all objects**.
1. When you're ready, select **Add** to include the site and its components in the solution.

> [!NOTE]
> - If the **Site** command doesn't appear on the **Add existing** menu, your environment doesn't include any websites that were created by using the [enhanced data model](../admin/enhanced-data-model.md#create-a-website-by-using-the-enhanced-data-model).
> - This process adds all the site components to the solution.
> - Dataverse system tables associated with site components won't be added to the solution automatically, you need to add them using add existing tables.

## Add website components

As you create new components and add them to your website, you can add them to the solution that contains the website.

> [!NOTE]
> New website components aren't automatically added to the solution that contains a site. You must use the following procedure to add them.

1. On the Power Pages home page, select the **Solutions** tab.
1. Select the solution that you want to add components to.
1. On the **Add existing** menu, select **More** \> **Other** \> **Site Component**.
1. In the **Add existing Site component** panel, select the site components, and then select **Add** to add them to the solution.

Alternatively, you can add the required components to your site.

1. In the solution, select the site.
1. On the main menu, select **Advanced**, and then select **Add required objects**.
1. In the panel that appears, select **OK** to continue. After a few moments, you'll receive a message that the required objects have been successfully added to the solution.

> [!NOTE]
> When you use the Add Website Components feature, all site components are added to the solution, not just the ones you select. This happens because our configuration is set to automatically include all related and dependent components in a solution. There isn't a workaround available at the moment, but we plan to address this limitation. A fix is expected to be released soon.

## Export the solution from the source environment

Select the solution, and then select **Export solution** on the main menu. For more information about how to import and export solutions, go to [Solution Concepts](/power-platform/alm/solution-concepts-alm).

## Import the solution into the target environment

1. On the toolbar at the top of the page, select **Import solution**.
1. Browse to the location of the exported solution, select the file, and then select **Open**.
1. Select **Next**.
1. Select **Import**.

After the solution is imported, it appears in the solution list.

> [!NOTE]
> If the solution is unmanaged, select **Publish all customizations** in the destination environment.

## Reactivate the site in the target environment

After the website has been transferred to the target environment, you must reactivate it.

1. In the target environment, on the Power Pages home page, select **Inactive sites**. The website that you transferred to the environment should be listed.
1. Select **Reactivate**.

    :::image type="content" source="../admin/media/migrate-portal-config/reactivate-website.png" alt-text="Screenshot that shows the Reactivate button on the Inactive sites section of the Power Pages home page.":::

1. You can specify the reactivated website's name and create a web address, or you can leave the default values.
1. Select **Done**.

The target environment should reflect the website updates from the source environment. From now on, you should be able to transfer the configuration from your source environment to the target environment by transferring the website configuration data.

## Bind the record for an enhanced data model website to a site

The following steps show how you can update an existing website by using the configuration from the source environment.

1. Open the [Power Platform admin center](https://aka.ms/ppac).
1. Select the destination environment.
1. In the **Resources** section, select **Power Pages sites**.
1. Select the destination site, select the ellipsis (**…**), and then select **Manage** to open the site details page.
1. In the **Site Details** section, select **Edit**. Select the imported site record in the **Website Record** dropdown list, and then select **Save**.

    :::image type="content" source="media/solutions/link-site.svg" alt-text="Screenshot of the imported site record selected in the Website Record dropdown list.":::

1. Select **Site Actions**, and then select **Restart site**.

Your destination environment site is now updated with data from the source environment site.

> [!NOTE]
> You can't use the [Power Pages Management app](portal-management-app.md) to delete a website configuration that is part of a managed solution. To remove the website, delete the managed solution.

## Frequently asked questions

### What is the best practice for migrating a Power Pages website by using solutions?

For best practices, go to [Overview of application lifecycle management with Microsoft Power Platform](/power-platform/alm/overview-alm).

### After I imported site configuration data in a managed solution, I edited my website in the target environment. Why don't I see any new changes when I import managed solutions from my source environment?

We recommend that you don't edit the site configuration data in the target environment. Otherwise, an unmanaged solution layer is created, and the target environment won't reflect changes from the source environment. To fix this issue in the target environment, you must remove the unmanaged solution layer. For more information, go to [Solution layers](/power-platform/alm/solution-layers-alm).

## See also

- [Enhanced data model](../admin/enhanced-data-model.md)
- [Power Platform CLI solution support for Power Pages](../configure/power-platform-cli-solution-management.md)
