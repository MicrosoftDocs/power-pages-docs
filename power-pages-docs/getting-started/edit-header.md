---
title: Edit site header
description: Learn how to make changes to the header of your Power Pages site.
author: clromano
ms.topic: how-to
ms.custom: bap-template
ms.date: 03/20/2023
ms.subservice:
ms.author: clromano 
ms.reviewer: kkendrick
contributors:
    - clromano
    - ProfessorKendrick
---

# Edit site header

Edit your site's header to apply your brand to your Power Pages site. You can:

- Update the site title and add your organization's logo.
- Provide alt text for logo images.
- Change colors and fonts.
- Preview the site's responsive layout.

In the Pages workspace, hover over the header component and select **Edit site header**. Editing options appear in a window in the Pages workspace.

:::image type="content" source="media/edit-header/edit-header-button.png" alt-text="Screenshot of the Edit site header button, which appears when you hover over the header in the Pages workspace.":::

## Title and logo

Change your site's title and change or remove the logo in the **Title + logo** section of the header editing window. You can also [customize them using Liquid code](#customize-the-title-and-logo-using-liquid).

:::image type="content" source="media/edit-header/title-logo.png" alt-text="Screenshot of the title and logo options in the header editing window.":::

- Enter the title of the site in the box under **Site title**.
- To use a different logo, select **Upload image** and follow the prompts to select an image file.  
- Enter alt text for the logo image in the box under **Alt text**.  
- To remove the logo from the header completely, turn off the **Site logo** toggle.

### Customize the title and logo using Liquid

The header consists of three [content snippets](../configure/content-snippets.md), which use the [Liquid](../configure/liquid-overview.md) markup language.

|Content snippet         |Liquid syntax                        |
|------------------------|-------------------------------------|
|Site name               |```{{ snippets['Site name'] }}```        |
|Logo URL                |```{{ snippets['Logo URL'] }}```         |
|Logo alt text           |```{{ snippets['Logo alt text'] }}```   |

If the title and logo are changed in the code, those changes override any changes you make in the header editing window. When these changes prevent your edits, the following message displays: `Your updates may not show on the site because of customizations to the code made by someone in your org.`

[Modify the header in the Portal Management app](../known-issues.md#modifying-the-header-in-portal-management-app) to make the header code match your changes in the header editing window.

## Styling

Change your header's style in the **Styling** section of the header editing window.

> [!TIP]
> You can also customize your header's styling by editing your site's [CSS files](../configure/manage-css.md).  

### Brand colors

:::image type="content" source="media/edit-header/styling.png" alt-text="Screenshot of styling options in the header editing window.":::

- Select the circles under **Brand colors** to change the colors your site's header uses.
- Select the square to the right of **Header background** to change the background color of the header.
- Select **>** to the right of **Title** and **Site Navigation** to change the type characteristics of the site title and navigational elements.

## Layout

Preview your site's responsive layout in the **Layout** section of the header editing window.

:::image type="content" source="media/edit-header/layout.png" alt-text="Screenshot of layout options in the header editing window.":::

- Use the **+** and **-** controls to change the display size.

### See also

[Add text](add-text.md)  
[Add button](add-button.md)  
[Add image](add-image.md)  
[Add video](add-video.md)  
[Add spacer](add-spacer.md)  
[Add Power BI](add-power-bi.md)  
[Add list](add-list.md)  
[Add form](add-form.md)  
[Add Iframe](add-iframe.md)  
[Add multistep form](multistep-forms.md)  
[Edit code with Visual Studio Code for the Web](../configure/visual-studio-code-editor.md)  
[Structure site map](structure-site.md)  
