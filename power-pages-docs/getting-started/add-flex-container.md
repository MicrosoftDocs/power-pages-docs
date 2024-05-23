---
title: Add flex containers
description: Add flex containers to your page in Power Pages.
author: ckwan-ms
ms.topic: conceptual
ms.date: 05/23/2024
ms.author: ckwan 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Flex container

Flex Container is a layout component that can be used to design and build section layouts. It allows for grouping of components such as buttons, text, images, and nesting of containers.

## Add a flex Container component

1. Open the [design studio](use-design-studio.md) to edit the content and components of your page.

1. Select the page you want to edit.

1. Select the section you want to add the flex container component to.

1. Hover over any editable canvas area, then select the **flex container** component from the component panel.

Add components like [button](add-button.md) and [text](add-text.md) to your flex container to create a group of components. 

You can also style and configure the flex container by adding a [background image](add-image.md) and changing its [flex properties](#flex-properties).

## Edit a flex container

After a flex container is added, select the flex container control to open the properties bar to configure your flex properties.

### Flex properties

| **Property** | **Description** |
|-------------------------|-------------------------|
| Design |  |
| Edit background | Change the color of the background according to the color palette for the selected styling template. You can also add a background image and adjust the size and position. |
| Change direction and alignment | Align and change direction of content in the flex container. |
| Others | Choose an option to duplicate the section, move it up or down within the page, or delete the section entirely. |

## Flex container code conventions

You can also add flex containers directly to the html of your webpage. 
In order for design studio to recognize and allow canvas editing of custom flexbox divs, the CSS class "**ppFlexContainer**" needs to be applied.

>[!IMPORTANT] 
> Without the **ppFlexContainer** class, design studio doesn't recognize the custom divs as flex container components, and they can't be edited in design studio.

```
<div class="row sectionBlockLayout text-start" style="display: flex; flex-wrap: wrap; margin: 0px; min-height: auto; padding: 8px;>
    <div class="container" style="padding: 0px; display: flex; flex-wrap: wrap;>
        <div class="col-lg-12 columnBlockLayout" style="flex-grow: 1; display: flex; flex-direction: column; min-width: 250px; word-break: break-word;>
            <div class="ppFlexContainer">
                <button type="button" class="button1">
                    &gt;Button&lt;
                </button>
                <button type="button" class="button1">
                    &gt;Button&lt;
                </button>
            </div>
        </div>
    </div>
</div>
```



