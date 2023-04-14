---
title: Enhanced data model
description: Learn how to use the enhanced data model in Power Pages site.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 04/12/2023
ms.subservice:
ms.author: nenandw 
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - neerajnandwana-msft
    - gitanjalisingh33msft
---

# Enhanced data model

The enhanced data model for Power Pages provides the following benefits:

- improved site performance
- faster provisioning of websites
- allow website configuration to be contained in solutions to provide smoother ALM experiences.
- automatic updates of Power Pages enhancements, bug fixes, and updates

## ​​Enable environment for enhanced data model  

Follow these steps to enable the new data model for a specific environment.  

1. Open the [Power Platform admin center](https://aka.ms/ppac)

1. Select **Environments**

1. Select the environment that you want to enable the new data model. 

1. Select **Power Pages sites** under the **Resources** tile. 

1. Select the **Upgrade to modern data model for new sites** switch from the tool bar.  

:::image type="content" source="media/enhanced-data-model/switch-to-enhanced-data-model.png" alt-text="Switch to enhanced data model.":::

This will start installation of the **Power Pages Core** package. You'll see a message once completed.

:::image type="content" source="media/enhanced-data-model/packages-installed.png" alt-text="Updated packages installed.":::

You can opt out from new data model site creation by disabling the **Upgrade to modern data model for new sites** option from top tool bar. 

## Update enhanced data model packages 

When new data model packages (**Power Pages Core**) updates are available, you'll see a message in the Power Platform admin center.

Select the package and then select **Update** to install the latest packages. 

The **Update** option will be enabled once the new package is available. See [Update the Power Pages solution](../admin/update-solution.md#view-package-details). 

## Create a website with an enhanced data model 

You can create a new site using Power Pages home page with the new data model once it's enabled for an environment.

> [!NOTE]
> The new site will be created using the new data model only if it is supported by the selected template. Currently, only the [Blank template](../templates/blank.md) supports the new data model.

Create site using **Blank template** using the new data model:

1. Navigate to the [Power Pages](https://aka.ms/mpp) home page.

1. Select the **Create a site** button.  

1. Select **Blank template** and select **Choose this template** to create your site.

1. Fill in the required information and select **Done**.  

You'll be redirected to the Power pages home page, and the new site will appear in the **My sites** list. You can edit the site using Power Pages design studio when the site is ready.

## See list of new data model sites 

You can see the newly created site from the Power Pages home.

The new data model sites are at functional parity, so there are no UI indicators to differentiate between new data model and existing data model sites; however, you can identify the difference by opening the **Power Pages Management** application as the new data model application name will be **Power Pages Management** instead **Portals Management** application. 

:::image type="content" source="media/enhanced-data-model/power-pages-management.png" alt-text="Power Pages Management app.":::

You can view a list of the available sites in the Power Pages home page **Active sites** section. This list shows sites that are created on the new data model and the existing data model, whether the environment has been enabled for the new data model or not.

## Editing newly created site on new data model  

Site that is created on new data model will have functional parity with classic data model and users can use [Power Pages design studio](use-design-studio.md) or [Power Pages management application](../configure/portal-management-app.md) for customization.  

## Edit site using the Power Pages design studio

Users can select **Edit** option from the Power Pages home page site card to open the design studio and edit the site.

> [!NOTE]
> Editing new data model site using design studio will work same as existing data model site without any functionality gaps.  

## Edit site using the Power Pages Management app

Users can select the **Portals management app** option from the Power Pages home site card to open the **Power Pages management** application.  Select **…** followed by **Portal management**.

> [!NOTE]
> The new data model comes with new UCI model-driven Power App application with name **Power Pages management.** You will need to use this application for advanced customizations which are not available using the Power Pages design studio.  

You can also open the **Power Pages Management** application from Power Pages design studio. Select **…** followed by **Portal management**. 

The **Power Pages Management** application allows you to make advance customizations unavailable in the design studio.

:::image type="content" source="media/enhanced-data-model/edit-site-power-pages-management.png" alt-text="Edit website using Power Pages Management app.":::

## See also

[Using solutions with Power Pages](../configure/power-pages-solutions.md)