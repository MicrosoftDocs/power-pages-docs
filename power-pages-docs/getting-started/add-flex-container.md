---
title: Add flex containers
description: Add flex containers to your page in Power Pages.
author: 
ms.topic: conceptual
ms.date: 05/14/2024
ms.author: 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Flex Container

Flex Container is a layout component that can be used to design and build section layouts. It allows for grouping of components such as buttons, text, images, and nesting of containers.

**Add a Flex Container component**

1.  Open the [design studio](https://learn.microsoft.com/en-us/power-pages/getting-started/use-design-studio) to edit the content and components of your page.

2.  Select the page you want to edit.

3.  Select the section you want to add the flex container component to.

4.  Hover over any editable canvas area, then select the **flex Container** component from the component panel.

![A screenshot of a computer Description automatically generated](media/image1.png)

5.  After adding the flex container, add components like button and text to it and create a group of components. Styling and configure the flex container by adding a background image and/or changing its flex properties.

![A screenshot of a computer Description automatically generated](media/image2.png)

**Edit a flex container**

After a flex container control is added, selecting the flex container control will open the properties bar where you can configure its properties.

| **Property** | **Description** |
|-------------------------|-------------------------|
| Design | Change the following flex container properties:</br><ul></br><li>[Direction](https://www.w3schools.com/css/css3_flexbox_container.asp#flex-direction)</li></br><li>[Justify](https://www.w3schools.com/css/css3_flexbox_container.asp#justify-content)</li></br><li>[Align items](https://www.w3schools.com/css/css3_flexbox_container.asp#align-items)</li></br><li>[Align content](https://www.w3schools.com/css/css3_flexbox_container.asp#align-content)</li></br><li>[Align self](https://www.w3schools.com/css/css3_flexbox_items.asp#align-self)</li></br><li>[Gap](https://www.w3schools.com/cssref/css3_pr_gap.php)</li></br><li>[Flex grow](https://www.w3schools.com/css/css3_flexbox_items.asp#flex-grow)</li></br><li>[Flex shrink](https://www.w3schools.com/css/css3_flexbox_items.asp#flex-shrink)</li></br><li>[Flex basis](https://www.w3schools.com/css/css3_flexbox_items.asp#flex-basis)</li></br><li>[Flex order](https://www.w3schools.com/css/css3_flexbox_items.asp#order)</li></br></ul> |
| Edit background | Change the color of the background according to the color palette for the selected styling template. You can also add a background image and adjust the size and position. |
| Change direction and alignment | Align and change direction of content in the flex container. |
| Others | Choose an option to duplicate the section, move it up or down within the page, or delete the section entirely. |


**Flex container code conventions**

Makers can add flex containers in the html of the webpage. In order for Design Studio to recognize and allow canvas editing of custom flexbox divs, the CSS class "**ppFlexContainer**" needs to be applied.

&lt;div class="row sectionBlockLayout text-start" style="display: flex; flex-wrap: wrap; margin: 0px; min-height: auto; padding: 8px;"&gt;

&lt;div class="container" style="padding: 0px; display: flex; flex-wrap: wrap;"&gt;

&lt;div class="col-lg-12 columnBlockLayout" style="flex-grow: 1; display: flex; flex-direction: column; min-width: 250px; word-break: break-word;"&gt;

&lt;div class="ppFlexContainer"&gt;

&lt;button type="button" class="button1"&gt;Button&lt;/button&gt;

&lt;button type="button" class="button1"&gt;Button&lt;/button&gt;

&lt;/div&gt;

&lt;/div&gt;

&lt;/div&gt;

&lt;/div&gt;

Without this class, Studio will not recognize the custom divs as Flex Container components, and they will not be editable within Studio.

**Sample layouts built with flex container**

1.  Cards – example on slide 10 [Section Layouts - Jan 2024.pptx](https://microsoft-my.sharepoint-df.com/:p:/p/ckwan/EY0v0Ybw0PBMhp34mviH66MBTHqUKswdFrjdboUGTkmDkA?e=VVaRbG)

2.  Overlapping grids – example on slide 11 [Section Layouts - Jan 2024.pptx](https://microsoft-my.sharepoint-df.com/:p:/p/ckwan/EY0v0Ybw0PBMhp34mviH66MBTHqUKswdFrjdboUGTkmDkA?e=VVaRbG)

3.  Split screen layout – example on slide 12 [Section Layouts - Jan 2024.pptx](https://microsoft-my.sharepoint-df.com/:p:/p/ckwan/EY0v0Ybw0PBMhp34mviH66MBTHqUKswdFrjdboUGTkmDkA?e=VVaRbG)
