---
title: Site design templates
description: The site design templates provide basic building blocks for you to create custom sites.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 10/07/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Site design templates

The site design templates provide building blocks for you to create custom sites. Each site design template has different layout, images, and colors that can be used as-is or customized to meet your needs.

:::image type="content" source="media/site-design.png" alt-text="Site design templates.":::

## Makers

Makers are able to use the design studio to modify the templates for their specific needs.

The following are the pages, forms, and customizable tables provided in each site design template. These components can be modified to align with your specific project needs.

### Pages

All site design templates contain the following pages.

| **Page**       | **Description**                         |
|----------------|-----------------------------------------|
| Home page      | Customer homepage                       |
| Subpages       | Customer pages with standard components |
| Contact us     | Contains a feedback form                |
| Search results | Contains a keyword-based search         |

### Forms and tables

The templates use the following forms linked to Dataverse tables.

| Table    | Table form name\*      | Page form name\*\* |
|----------|------------------------|--------------------|
| Feedback | simple contact us form | Contact us         |

*\* The form name as it appears associated to the table in data workspace.*

*\*\* The form name as it appears when added to a page as a component.*

### Table information

| Table name | Schema name | Description   |
|------------|-------------|---------------|
| Feedback   | Feedback    | Feedback form |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns. For custom code editing, use the [Microsoft Power Platform CLI](../configure/cli-tutorial.md) to download the site metadata, and use Visual Studio Code to view and modify the source code.

### See also

[Tutorial: Add a page to your Power Pages site](../getting-started/tutorial-add-webpage.md)  
[Create and design pages](../getting-started/first-page.md)
