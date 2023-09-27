---
title: Enable Bootstrap version 5 in your environment (preview)
description: Learn how to enable Bootstrap version 5 in your environment(preview).
author: ankitavish 
ms.topic: conceptual
ms.custom: 
ms.date: 09/27/2023
ms.subservice:
ms.author: avishwakarma 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Enable Bootstrap version 5 in your environment (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

You can add new functionality to your site, like CSS Flexbox and responsive layout, using [Bootstrap version 5](https://getbootstrap.com/docs/5.0/getting-started/introduction/).

Power Platform environments and existing Power Pages sites by default use Bootstrap version 3. Follow the steps in this article to enable Bootstrap version 5 for your environment before you create new sites. After the setting is enabled, new sites created in the selected environment will start using Bootstrap version 5.

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This feature is in the process of rolling out, and may not be available in your region yet.
> - Bootstrap version 5 is only supported in enhanced data model environments. More information: [Enable the enhanced data model in an environment](../admin/enhanced-data-model.md#enable-the-enhanced-data-model-in-an-environment)
> - You can migrate existing sites from using Bootstrap version 3 to use Bootstrap version 5, or create new sites after enabling the above setting.

To enable Bootstrap version 5 in your environment:

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. Select **Environments** and choose the environment that you want to use the Bootstrap version 5 upgrade with.

1. From the **Resources tile**, select **Power Pages sites**.

1. From the toolbar, set the **Switch to enhanced data model (preview)** toggle to **On**.

1. From the toolbar, set the **Enable Bootstrap version 5 for new sites (preview)** toggle to **On**.

These actions install the packages needed for Bootstrap version 5. After the setting is enabled, create new sites with the [templates that support Bootstrap version 5](#supported-templates).

Viewing and editing experiences for Power Pages sites created with Bootstrap version 5 remain unchanged. More information: [Edit your site](../getting-started/customize-pages.md), [Customize your site](../configure/bootstrap-overview.md#customize-bootstrap)

## Supported templates

The following templates are supported for Bootstrap version 5:

- [Blank page template](../templates/blank.md)
- [Starter layout templates](../templates/starter-layout.md)
- [Application processing template](../templates/building-permit.md)
- [Program registration template](../templates/after-school.md)
- [Schedule and manage meetings template](../templates/book-a-meeting.md)

## Next steps

[Migrate existing sites to Bootstrap version 5 (preview)](migrate-bootstrap.md)

### See also

- [Bootstrap overview](bootstrap-overview.md)
- [Manage CSS files](manage-css.md)
