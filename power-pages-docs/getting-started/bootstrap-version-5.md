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

Now you can create new websites and migrate existing websites in Power Pages using Bootstrap version 5. You can also migrate your existing websites running on Bootstrap v3 to version 5 using the PAC CLI based migration tool provided by Power pages. The Bootstrap upgrade for Power Pages enables you to use new components including CSS Flexbox and responsive layout.

Sites created with Bootstrap version 5 have functional parity with Bootstrap version 3; however, you may notice some minor changes between the two. Changes include UX improvements like spacing, icons, edges of components like buttons, text etc.

>[!NOTE]
> Bootstrap version 5 is supported in only environments which are on "enhanced data model". Follow these Steps to enable enhanced data model [link](https://learn.microsoft.com/en-us/power-pages/admin/enhanced-data-model#enable-the-enhanced-data-model-in-an-environment)

## Enable environment for Bootstrap version 5

Follow these steps to enable Bootstrap version 5 support for a specific environment.

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. Select **Environments.**

1. Choose the environment that you want to use the Bootstrap version 5 upgrade with.

1. Select the **Power Pages sites** under the **Resources** tile.

1. Select the **Switch to enhanced data model** switch from the tool bar and toggle on

1. Select the **Enable Bootstrap version 5 for new sites (preview)** switch from the tool bar switch from the tool bar and toggle on. This installs the packages needed for Bootstrap version 5.

1. Now sites created will be on Bootstrap version 5.

## Create a site with Bootstrap version 5

You can create a new site using the Power Pages home page with Bootstrap version 5 once it's enabled for an environment.

To create a site using Bootstrap version 5:

1. Navigate to the Power Pages home page.

1. Select the **Create a site** button and choose a [supported template](#templates-supported-for-bootstrap-version-5).

1. Select **Choose this template** to create your site.

1. Fill in the required information and select **Done**. You're redirected to the Power pages home page, and the new site appears in the **My sites** list. You can edit the site using the Power Pages design studio when the site is ready.

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

