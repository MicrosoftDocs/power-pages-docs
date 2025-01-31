---
title: Create new sites with Bootstrap version 5
description: Learn how to enable Bootstrap version 5 in your environment to take advantage of new features and updates that make creating responsive, customized Power Pages sites even easier.
ms.topic: how-to
ms.date: 11/13/2024
author: ankitavish
ms.author: avishwakarma
ms.reviewer: dmartens
contributors:
  - DanaMartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:11/16/2023
  - bap-template
---

# Create new sites with Bootstrap version 5

[Bootstrap version 5](https://getbootstrap.com/docs/5.0/getting-started/introduction/) offers new features, like CSS Flexbox and responsive layout that make creating more responsive customized Power Pages sites even easier.

> [!IMPORTANT]
>
> Site creation with Bootstrap version 5 is only supported with the [enhanced data model](../admin/enhanced-data-model.md).

Power Platform environments and Power Pages sites use Bootstrap version 3 by default. To start creating new sites with Bootstrap version 5, you need to enable the [enhanced data model](../admin/enhanced-data-model.md) in your environment. Once the setting is enabled, all new sites created in the environment use Bootstrap version 5.

## Supported templates

You can [migrate](migrate-bootstrap.md) any of your existing Bootstrap version 3 sites to version 5 regardless of the template that was used to create them. For creation of new sites with Bootstrap version 5, the following templates are supported:

- [Blank page template](../templates/blank.md)
- [Starter layout templates](../templates/starter-layout.md)
- [Application processing template](../templates/building-permit.md)
- [Program registration template](../templates/after-school.md)
- [Schedule and manage meetings template](../templates/book-a-meeting.md)
- [Frequently Asked Questions template (preview)](../templates/frequently-asked-questions.md)

## Set up Bootstrap version 5

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. In the left side panel, select **Environments**, and then select your environment.

1. On the **Resources** tile, select **Power Pages sites**.

1. If not already, turn on **Switch to enhanced data model (preview)** and confirm when prompted.

You can view and edit Power Pages sites that you create with Bootstrap version 5 just as you did with version 3.

## Next steps

- [Customize webpages with design studio page editor](../getting-started/customize-pages.md)

### See also

- [Migrate existing sites to Bootstrap version 5](migrate-bootstrap.md)
- [Bootstrap overview](bootstrap-overview.md)
- [Manage CSS files](manage-css.md)
- [Set up Bootstrap version 5 with Power Pages (video)](https://youtu.be/rQe34jyVROQ?feature=shared)
