---
title: Use flex containers to group and align components
description: Explore the versatility of Flex Container, a layout component for grouping elements like buttons and images, with customizable properties.
author: ckwan-ms
ms.topic: how-to
ms.date: 05/23/2024
ms.author: ckwan
ms.reviewer: danamartens
contributors:
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:05/23/2024
---

# Use flex containers to group and align components

Flex Container is a layout component that helps you design and build section layouts on your web page. You can use flex containers to group components such as buttons, text, images, and other containers.

## Add a flex container

To add a flex container to your web page:

1. Open the [design studio](use-design-studio.md) to edit the content and components of your page.

1. Select the page you want to edit.

1. Select the section where you want to add the flex container component.

1. Hover over any editable canvas area, then select the **flex container** component from the component panel.

You can create a group of components by adding other components, like [buttons](add-button.md) and [text](add-text.md), to your flex container.

You can also style and configure your flex container.

## Edit a flex container

After you add a flex container, select the flex container control to open the properties bar to edit your flex container.

| **Property** | **Description** |
|-------------------------|-------------------------|
| Design |  Change your [design properties](#design-properties) to customize your flex container's appearance. |
| Edit background | Change the color of the background according to the color palette for the selected styling template. You can also add a background image and adjust the size and position. |
| Change direction and alignment | Align and change the direction of content in the flex container. |
| Others | Duplicate the section, move it up or down within the page, or delete the section entirely. |

### Design properties

The following design properties are configurable in design studio:

:::row:::
    :::column span="":::
        - [Direction](https://www.w3schools.com/css/css3_flexbox_container.asp#flex-direction)
        - [Justify](https://www.w3schools.com/css/css3_flexbox_container.asp#justify-content)
        - [Align items](https://www.w3schools.com/css/css3_flexbox_container.asp#align-items)
        - [Align content](https://www.w3schools.com/css/css3_flexbox_container.asp#align-content)
    :::column-end:::
    :::column span="":::
        - [Align self](https://www.w3schools.com/css/css3_flexbox_items.asp)
        - [Gap](https://www.w3schools.com/cssref/css3_pr_gap.php)
        - [Flex grow](https://www.w3schools.com/css/css3_flexbox_items.asp)
    :::column-end:::
    :::column span="":::
        - [Flex shrink](https://www.w3schools.com/css/css3_flexbox_items.asp)
        - [Flex basis](https://www.w3schools.com/css/css3_flexbox_items.asp)
        - [Flex order](https://www.w3schools.com/css/css3_flexbox_items.asp)
    :::column-end:::
:::row-end:::

## Add flex containers in HTML

You can also add flex containers directly to your web page's HTML with [Visual Studio Code for the Web (preview)](../configure/visual-studio-code-editor.md#edit-web-page-code-from-pages-workspace).

To make the design studio recognize and allow canvas editing of custom flexbox divs, apply the CSS class "**ppFlexContainer**" to them.

>[!IMPORTANT] 
> Without the **ppFlexContainer** class, design studio doesn't recognize the custom divs as flex container components, and you can't edit them in design studio.

```html
<div class="row sectionBlockLayout text-start" style="display: flex; flex-wrap: wrap; margin: 0px; min-height: auto; padding: 8px;">
    <div class="container" style="padding: 0px; display: flex; flex-wrap: wrap;">
        <div class="col-lg-12 columnBlockLayout" style="flex-grow: 1; display: flex; flex-direction: column; min-width: 250px; word-break: break-word;">
            <div class="ppFlexContainer">
                <button type="button" class="button1">Button</button>
                <button type="button" class="button1">Button</button>
            </div>
        </div>
    </div>
</div>
```

## Build custom layouts

You can use multiple flex containers to build custom layouts. Here are just a few examples of what you can do.

### Set up card layout

 >[!VIDEO https://learn-video.azurefd.net/vod/player?id=3579f326-dab0-406a-893e-767d026e4c98]

### Set up floating cards

 >[!VIDEO https://learn-video.azurefd.net/vod/player?id=f8afb160-81d1-4c66-8cfe-119f3dbfa061]
