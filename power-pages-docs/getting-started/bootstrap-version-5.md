---
title: Create Power Pages sites with Bootstrap version 5 (preview)
description: Learn how to create Power Pages sites with Bootstrap version 5.
author: 
ms.topic: conceptual
ms.custom: 
ms.date: 09/11/2023
ms.subservice:
ms.author: 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Create Power Pages sites with Bootstrap version 5 (preview)

You can add new functionality to your site, like CSS Flexbox and responsive layout, using Bootstrap version 5.

>[!NOTE]
> Bootstrap version 5 is only supported in enhanced data model environments. More information: [Enable the enhanced data model in an environment](https://learn.microsoft.com/power-pages/admin/enhanced-data-model#enable-the-enhanced-data-model-in-an-environment)

## Enable an environment for Bootstrap version 5

To enable Bootstrap version 5 support for a specific environment:

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. Select **Environments** and choose the environment that you want to use the Bootstrap version 5 upgrade with.

1. From the **Resources tile**, select **Power Pages sites**.

1. From the toolbar, set the **Switch to enhanced data model** toggle to the **on** position.

1. From the toolbar, set the **Enable Bootstrap version 5 for new sites (preview)** toggle to the **on** position. 

These actions install the packages needed for Bootstrap version 5. Now sites you create in this environment will use Bootstrap version 5.

## Create a site with Bootstrap version 5

Once Bootstrap version 5 is enabled for an environment, you can create new Bootstrap version 5 sites in Power Pages design studio.

To create a site using Bootstrap version 5:

1. Navigate to the Power Pages home page.

1. Select the **Create a site** button and choose a [supported template](#templates-supported-for-bootstrap-version-5).

1. Select **Choose this template** to create your site.

1. Fill in the required information and select **Done**. 

Once you've completed these steps, you're redirected to the Power pages home page and your new site appears in the **My sites** list. You can edit the site using the Power Pages design studio once the site is ready.

## Edit your Bootstrap version 5 site

You can use Power Pages studio to edit your site or the Portal management application to customize your site just like you can with Power Pages sites created using Bootstrap version 3.

More information: [Customize Bootstrap](../configure/bootstrap-overview.md#customize-bootstrap)

## View your Bootstrap version 5 sites

You can view a list of your Power Pages sites in the Power Pages home page **My Sites** section. This list shows sites that are created on Bootstrap v3 and Bootstrap version 5 whether the environment has been enabled for Bootstrap version 5 or not.

## Supported templates for Bootstrap version 5

The following templates are supported for Bootstrap 5:

- [Blank page template](../templates/blank.md)
- [Starter layout templates](../templates/starter-layout.md)
- [Application processing template](../templates/building-permit.md)
- [Program registration template](../templates/after-school.md)
- [Schedule and manage meetings template](../templates/book-a-meeting.md)

## Opt out of Bootstrap version 5

You can opt out of Bootstrap version 5 site creation by disabling the **Enable Bootstrap version 5 for new sites (preview)** option from top tool bar.

