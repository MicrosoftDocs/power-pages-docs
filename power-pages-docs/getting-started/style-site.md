---
title: Style your Power Pages site
description: Learn how to style your Power Pages site.
author: ckwan-ms
ms.topic: how-to
ms.custom: 
ms.date: 07/04/2023
ms.subservice:
ms.author: ckwan
ms.reviewer: danamartens
contributors:
    - ankitavish
    - rob-moyer
---

# Style your pages site

Power Pages contains a robust set of themes and tools to use to style your site. Choose from several preset themes that you can apply to your portal.  Use these themes as a starting point and apply further customization with the styling menu.

The **Styling** workspace lets you apply global site styles. You can apply corporate branding updates, and review the changes in the preview on the right side of the app window. Styling offers 13 preset themes. For each theme, you can customize the color palette, background color, font styles, button styles, and section margins.

1. Open the [design studio](use-design-studio.md).

1. On the left pane, select **Styling**.

    :::image type="content" source="media/style-site/styling-workspace.png" alt-text="GUI with the Styling workspace menu option selected.":::

    Notice the list of themes in the Styling workspace. You can further customize specific elements, such as the site's colors and fonts, from the Styling menu. Power Pages offers basic fonts and more than 30 Google Fonts for you to choose from.

1. Select one of the preset themes to see how the style is reflected on the canvas workspace to the right. 

    - Each theme has its own color palette.

    - You can adjust the styling menu to make adjustments to each theme. Text options include font, weight, size, and color.

1. Choose between **Save Changes** or **Discard Changes** after you make your edits.

    A modified theme is noted next to the theme name unless or until a theme is reset to preserve changes.

## Resetting a theme

To reset a theme to its original state, select the ellipsis (**...**) and then select the **Reset to default** option.

:::image type="content" source="media/style-site/reset-default.png" alt-text="GUI with the reset to default option highlighted.":::

## Viewing your page

To see the full page in the design studio, select the full page icon.

:::image type="content" source="media/style-site/full-page.png" alt-text="GUI with the full page icon highlighted.":::

To see the site as it appears in production, select the preview icon.

:::image type="content" source="media/style-site/preview-icon.png" alt-text="GUI with the preview icon highlighted.":::

You can also use the viewport selector to choose from web, tablet, and mobile views of the workspace.  

## Theme mapping

Each color on the palette maps to a specific element on the page. The preset theme consists of nine colors and three slots for user-selected colors. If you customize elements, the mapping isn't correct until the theme is reset.  

To add a new color or to change an existing color, select the plus sign (**+**) in the color palette and choose your color using the color picker, hexadecimal value, or RGB values.

:::image type="content" source="media/style-site/color-picker.png" alt-text="The color picker feature within portals.":::

After a new color is added to the color palette, it can be used to color components in the context menu.

> [!NOTE]
> For sites created using Power Pages prior to September 23, 2022 there is a known issue related to themes. More information: [Adjusting the background color for your Power Pages site](../known-issues.md#adjusting-the-background-color-for-your-power-pages-site)

## Undo/redo

You can select the **Undo** and **Redo** icons in the **Styling** workspace to revert theme updates for all the scenarios related to changing a current selected theme.

1. You can apply the undo/redo options on any style settings for the selected theme including the **reset to default** theme from the more menu (**...**) options. 

1. When switching to a new theme, you're prompted with a dialog to save or discard for any unsaved changes. The undo/redo stack is cleared upon choosing either of the actions. 

### What is the expected experience of undo/redo? 

The **Undo** and **Redo** options only support changes that you make in the **Styling** workspace. Your action history is immediately cleared when navigating to a different workspace or switching to a different theme. 

By design, some general design studio actions aren't supported, such as:

- Syncing, saving, previewing, zooming, resizing the canvas, navigating between workspaces and webpages, and uploading media and CSS files. 

- Switching to a different theme, saving a newly selected theme without any style changes. 

- **Custom CSS** panel actions such as **upload**, **enable/disable**, move file **up/down** in the priority order. 

## See also

- [Use design studio](use-design-studio.md)
- [Create and design pages](first-page.md)  
- [Customize pages](customize-pages.md)
