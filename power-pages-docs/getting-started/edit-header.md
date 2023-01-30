---
title: Edit site header
description: Learn how to make changes to the header of your Power Pages site.
author: clromano
ms.topic: conceptual
ms.custom: 
ms.date: 1/30/2023
ms.subservice:
ms.author: clromano 
ms.reviewer: kkendrick
contributors:
    - clromano
    - ProfessorKendrick
---

# Edit site header

Makers can establish their Power Pages site's brand by modifying their site's header using the Edit site header feature. Using this feature, makers can:

- Update the site's title and logo.
- Provide accessible alt text for logo images.
- Change colors and fonts to reflect their organization's branding.
- Preview their site's responsive layout.

From the Pages workspace, hover over the header component and select the **Edit Site Header button**.

:::image type="content" source="media/edit-header/edit-site-header-button.png" alt-text="The Edit Site Header button, which appears when you hover over the header inside Pages workspace.":::

Editing options will appear within a pop-up window inside the Pages workspace.

## Title and logo

In the **Title + logo** section of the Edit site header pop-up window, makers can modify their site's title and update or remove the site logo.  

:::image type="content" source="media/edit-header/edit-site-header.png" alt-text="Title and logo options inside the Edit site header pop-up window.":::

- Enter your text in the text box under the **Site title label** to edit the site's title.
- Use the **toggle switch** next to the **Site logo label** to remove the logo from the header completely.
- Select the **Upload image button** under the **Site logo label** and follow the prompts to add the image of your choice.  
- Use the text box under the **Alt text label** to provide alternative text for your site logo.  

## Styling

To style your header, select the **Styling menu option** from the side navigation links inside the Edit site header pop-up window.

### Update brand colors

Makers can choose from various options to add brand colors to their site's header.

:::image type="content" source="media/edit-header/edit-site-header-styling.png" alt-text="Styling options in the Edit site header pop-up window.":::

- Choose the colors for your site's header by selecting each of the circles under the **Brand colors label**.
- Select the colored square next to the **Header background label** to choose which brand color will serve as your header's background.
- Choose the **>** symbol next to **Title** and **Site Navigation** below the **Fonts label** to expand the section and choose a weight, font, color, and size for each element.

## Layout

To preview your site's responsive layout, select the **Layout menu option** from the side navigation links inside the Edit site header pop-up window.

:::image type="content" source="media/edit-header/edit-site-header-layout.png" alt-text="Layout options in the Edit site header pop-up window.":::

- Use the **+** and **-** controls to modify the display size.

## Customize the site header

The header contains three underlying content snippets, which use [Liquid](../configure/liquid-overview.md). 

|Content snippet         |Liquid syntax                        |
|------------------------|-------------------------------------|
|Site name               |```{{ snippets['Site name'] }}```        |
|Logo URL                |```{{ snippets['Logo URL'] }}```         |
|Logo alt text           |```{{ snippets['Logo alt text'] }}```   |

For more information on content snippets, see [Content snippets](../configure/content-snippets.md).

When customizing the header, makers must also update the Liquid code in the content snippets. Changes won't reflect in studio until the attribute values are updated appropriately. 

>[!NOTE]
> If the values for any of these snippets aren't modified, makers will see the following message in the studio:<br />```Your updates may not show on the site because of customizations to the code made by someone in your org.```<br />For information on how to update the Liquid code and resolve this issue, see [Modifying the header in Portal Management App](../known-issues.md#modifying-the-header-in-portal-management-app).

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
