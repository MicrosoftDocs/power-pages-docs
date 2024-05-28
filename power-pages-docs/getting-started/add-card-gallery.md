---
title: Add a card gallery (preview)
description: Explore how to add, style, and configure a Card gallery in Power Pages sites using design studio and Liquid code.
author: pranita225
ms.topic: conceptual
ms.date: 05/28/2024
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

A card gallery is a data control, bound to a table and view, used to display data in Power Pages sites in card gallery format. 

> [!IMPORTANT]
>
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

To add a card gallery:

1. Open the [design studio](use-design-studio.md) to edit the content and components of the site.

    >[!TIP]
    >
    > You can also [add a card gallery using code](#add-a-card-gallery-using-code).

1. Go to the **Pages** workspace.

1. Select the page you want to edit.

1. Select the section you want to add the card gallery to.

1. Hover over any editable canvas area, then select the **Card gallery** icon from the component panel.
    
    :::image type="content" source="media/add-card-gallery/card-gallery-component.png" alt-text="A screenshot of the card gallery component with the Card gallery design button displayed in the top left corner.":::

## Choose a layout

Select the **Card gallery design** button to choose from any of the four available layouts.

:::image type="content" source="media/add-card-gallery/card-gallery-design.png" alt-text="A screenshot of the card gallery design options in design studio. The card gallery design button, located in the top left corner of the component, is emphasized and the design options display in a window in front of the component.":::

You can also choose from existing card galleries if they're available.

## Configure your card gallery's data source

To configure your card gallery's data source:

1. Select the **Card gallery design** button and choose **Data**.

    :::image type="content" source="media/add-card-gallery/card-gallery-design-data.png" alt-text="A screenshot of the Card gallery design options for Data in design studio.":::
 
1. Select an existing table from the **Data source** lookup field.
1. Select a corresponding view from the **View** dropdown.
1. For each card gallery element (image, title, description, button, text hyperlink), choose the **Select data** option to bind it to a view column.

    > [!NOTE]
    > 
    >For button and hyperlink elements, two configurations are required: name and url. Both configurations must be bound to a view column.

Disable the toggle switch next to any element you don't wish to include.

You can rearrange each element's position by selecting the icon to the left of the toggle switch and dragging the element to the desired position.

### Supported column types

For each element, specific data types are supported.


|**Element**  |**Data type(s)** |
|---------|---------|
|Title     |Text (single line of text)<br />Phone<br />Whole Number<br />Decimal<br />Look up<br />Date only<br />Date and time         |
|Description     |Rich Text<br />Text Area (multiple lines of text)<br />Phone<br />Whole Number<br />Decimal<br />Date only<br />Date and time         |
|Image    |File - Image        |
|Button    |Button label - Text (single line of text)<br />Button URL - URL         |
|Text Hyperlink   |Text Hyperlink label: Text (single line of text)<br />Text Hyperlink URL: URL         |

## Style and configure your card gallery

You can [style your card gallery](customize-pages.md#edit-components) by configuring style properties at the gallery, card, and element level.

### Search filtering

Turn on/off the **Enable search** toggle to add or remove search filtering.

### Preview your card gallery

After your card gallery is configured, you can see the preview on canvas with sample data. 

>[!NOTE]
> You must [set table permissions](../security/table-permissions.md) to allow site visitors to view and interact with your card gallery.

## Add a card gallery using code

You can also use [Liquid](../configure/liquid/liquid-overview.md) to edit your card gallery.

### Add a new card gallery

To add a new card gallery without any data binding or configuration, use the following liquid tag:

```Liquid
{% codecomponent name:Pages.CardGallery %}
```

### Add an existing card gallery

To add an existing card gallery, use the Liquid tag and replace `{your card gallery id}` with the id for the existing card gallery:

```Liquid
{% codecomponent name:Pages.CardGallery id: '{your card gallery id}' %}
```




