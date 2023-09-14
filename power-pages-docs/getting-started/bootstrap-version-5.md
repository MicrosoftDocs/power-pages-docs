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

These actions install the packages needed for Bootstrap version 5. Once the instal is complete, you'll see the following message: "All your new sites will be created using Bootstrap v5, where you can access new studio templates and increase security. Your current sites will continue to remain in Bootstrap v3. Since this is a preview feature, it's recommended that you enable this for test environments. Learn more"

Now sites you create in this environment will use Bootstrap version 5.

## Create a site with Bootstrap version 5

Once Bootstrap version 5 is enabled for an environment, you can [create a site](create-manage.md) in Power Pages design studio. Begin by selecting the [Microsoft Dataverse environment](/power-platform/admin/environments-overview) you enabled for Bootstrap 5. When you create your site, choose a [supported template](#templates-supported-for-bootstrap-version-5).

## Edit your Bootstrap version 5 site

Use Power Pages design studio to [edit your site](customize-pages.md) or use the Portal management application to [customize your site](../configure/bootstrap-overview.md#customize-bootstrap).

## View your Bootstrap version 5 sites

Go to the [Power Pages](https://make.powerpages.microsoft.com/) home page to view a list of your active sites. This list shows which version of Bootstrap each site was created on.

## Supported templates for Bootstrap version 5

The following templates are supported for Bootstrap 5:

- [Blank page template](../templates/blank.md)
- [Starter layout templates](../templates/starter-layout.md)
- [Application processing template](../templates/building-permit.md)
- [Program registration template](../templates/after-school.md)
- [Schedule and manage meetings template](../templates/book-a-meeting.md)

## Opt out of Bootstrap version 5

You can opt out of Bootstrap version 5 site creation by disabling the **Enable Bootstrap version 5 for new sites (preview)** option from top tool bar in Power Pages design studio.

