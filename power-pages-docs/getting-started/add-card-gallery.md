---
title: Add a card gallery (preview)
description: Explore how to add, style, and configure a Card gallery in Power Pages sites using design studio and Liquid code.
author: pranita225
ms.topic: conceptual
ms.date: 05/23/2024
ms.author: prpadalw
ms.reviewer: kkendrick
contributors:
  - ProfessorKendrick
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:05/23/2024
---
# Add a card gallery (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

A Card gallery is a data control used to display data in Power Pages sites in card gallery format. Card gallery is bound to a table and view. 

> [!IMPORTANT]
>
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

To add a Card gallery:

1. Open the design studio to edit the content and components of the site.

1. Go to the Pages workspace.

1. Select the page you want to edit.

1. Select the section you want to add the form component to.

1. Hover over any editable canvas area, then select the Card gallery icon from the component panel.

Choose from any of the four available layouts. You can also choose from existing card galleries if they're available.

## Configure your card gallery's data source

To configure your card gallery's data source, select an existing table and corresponding view.

Bind each Card gallery element (image, title, description, button, text hyperlink) to a view column.

> [!NOTE]
> 
>For button and hyperlink elements, two configurations are required: name and url. Both configurations must be bound to a view column.

You can rearrange each element's position by selecting and sliding.

### Supported column types

For each element, specific data types are supported.

| **Data type**                     | **Element**                             |
|-----------------------------------|-----------------------------------------|
| Text (single line of text)        | Title, Button name, Text hyperlink name |
| Text Area (multiple lines of text) | Description                             |
| Email                             | NA                                      |
| URL                               | Button URL, Text hyperlink URL          |
| Phone                             | Title, Description                      |
| Whole number                      | Title, Description                      |
| Decimal                           | Title, Description                      |
| Rich Text                         | Description                             |
| Look up                           | Title                                   |
| File - Image                      | Image                                   |
| Date only                         | Title, Description                      |
| Date and time                     | Title, Description                      |

## Style and configure your card gallery in design studio

You can [style your card gallery](customize-pages.md#edit-components) by configuring style properties at the gallery, card, and element level.

### Search filtering

Turn on/off the **Enable search** toggle to add or remove search filtering.

### Preview your card gallery

After Card gallery is configured, you can see the preview on canvas with sample data. 

>[!NOTE]
> You must [set table permissions](../security/table-permissions.md) to allow site visitors to view and interact with your card gallery.

## Edit card gallery with Liquid

You can also use Liquid code to edit your card gallery.

### Add a placeholder

To add new Card gallery placeholder without any data binding or configuration, use the following liquid tag:

```Liquid
{% codecomponent name:Pages.CardGallery %}
```

### Add to an existing card gallery

To add an existing Card gallery, use the Liquid tag with relevant Card gallery id:

```Liquid
{% codecomponent name:Pages.CardGallery id: '3d29615c-1bbe-4bf9-a97b-19d7318d1341' %}
```


