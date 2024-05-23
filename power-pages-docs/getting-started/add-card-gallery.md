---
title: Add a card gallery
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
# Add a card gallery

A Card gallery is a data control used to display data in Power Pages sites in card gallery format. Card gallery is bound to a table and view. 

To add a Card gallery:

1. Open the design studio to edit the content and components of the site.

1. Go to the Pages workspace.

1. Select the page you want to edit.

1. Select the section you want to add the form component to.

1. Hover over any editable canvas area, then select the Card gallery icon from the component panel.

1. You can choose either to create a new Card gallery or use add one (if a maker created one previously). If you choose to create a new one, you can select any one of the four available layouts. After this, you need to select an existing table and corresponding view to configure the data source.

1. You can bind each Card gallery element namely, image, title, description, button, text hyperlink, to a view column.

1. Each element's position can be rearranged by selecting and sliding it.

1. For button and hyperlink elements, two configurations are required - name and url. Both name and url also need to be bound to view column.

1. For each element, specific column types are supported as given below:

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

## Style a card gallery

1. Select on the styling tab in toolbar

1. Set the styling properties. Styling properties can be configured at the Gallery, Card, and Element level (Style)

1. Turn on/off the Enable search toggle to add/remove search filtering

After Card gallery is configured, you can see the preview on canvas with sample data. Like all other data controls, set permissions to allow site visitors to view and interact with Card gallery. For more information, see [Configuring table permissions](../security/table-permissions.md).

## Edit card gallery with Liquid

To configure Card gallery using code:

1. To add new Card gallery placeholder, without any data binding or configuration use the following liquid tag:

{% codecomponent name:Pages.CardGallery %}

1. To add an existing Card gallery, use the Liquid tag with relevant Card gallery id:

{% codecomponent name:Pages.CardGallery id: '3d29615c-1bbe-4bf9-a97b-19d7318d1341' %}


