---
title: Edit header
description: Learn how to customize the header for your Power Pages site.
author: clromano
ms.topic: conceptual
ms.custom: 
ms.date: 1/19/2023
ms.subservice:
ms.author: clromano 
ms.reviewer: kkendrick
contributors:
    - clromano
    - ProfessorKendrick
---

# Edit header

Makers can establish their site’s brand using the header. Using the **Edit Site Header** button, makers can update the following elements: 

- Site title 
- Site logo
- Site navigation

## Edit the site title

## Edit the site logo

## Update site navigation

Makers can choose to use the out of the box header or customize their header following the steps outlined here.  More information: [Considerations for editing the header](#considerations-for-editing-the-header)

## Establish styling options for the header

### Select a color palette

### Select a background color

## Considerations for editing the header

The Edit site header contains three underlying content snippets. For more information on content snippets, see INSERT LINK HERE.

|Content snippet         |Liquid syntax                        |
|------------------------|-------------------------------------|
|Site name               |```{{ snippets['Site name'] }}```        |
|Logo URL                |```{{ snippets['Logo URL'] }}```         |
|Logo alt text           |```{{ snippets['Logo alt text'] }}```   |

When customizing the header, makers must also update the Liquid code in the content snippets. Changes won't reflect in Studio until the attribute values are updated appropriately. If the values aren't modified, makers will see the following message in the studio:

INSERT MESSAGE TEXT HERE

For information on how to update the Liquid code and resolve this message, see INSERT LINK HERE.

FOR KNOWN ISSUES:
Sample solution to resolve the issue: 

Open the Mobile Header in PMA (Portal Management App) (or the corresponding content snippet being used for the header) 

Update the source code with values for each 

```html
<a href="~/">
    {% if snippets['Logo URL'] %}
        <img src="{{ snippets['Logo URL'] }}" alt="{{ snippets['Logo alt text'] }}" style="width: auto; height: 32px; margin: 0 10px;">
    {% endif %} 
    {% if snippets['Site name'] %}
        <h1 class="siteTitle">{{ snippets['Site name'] }}</h1>
    {% endif %}
</a> 
```

### See also

[Add text](add-text.md)<br />
[Add button](add-button.md)<br />
[Add image](add-image.md)<br />
[Add video](add-video.md)<br />
[Add spacer](add-spacer.md)<br />
[Add Power BI](add-power-bi.md)<br />
[Add list](add-list.md)<br />
[Add form](add-form.md)<br />
[Add IFrame](add-iframe.md)<br />
[Add multistep form](multistep-forms.md)<br />
[Edit code with Visual Studio Code for the Web](../configure/visual-studio-code-editor.md)<br />
[Structure site map](structure-site.md)<br />
