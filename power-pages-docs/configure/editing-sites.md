---
title: Power Pages design studio and Power Apps portals Studio
description: Learn about how sites created in Power Apps can be edited in Power Pages design studio.
author: ankitavish

ms.topic: conceptual
ms.custom: 
ms.date: 10/11/2022
ms.subservice:
ms.author: avishwakarma
ms.reviewer: kkendrick
contributors:
    - ankitavish
    - nickdoelman
    - ProfessorKendrick
---

# Power Pages design studio and Power Apps portals Studio

> [!NOTE]
> Effective November 2023, legacy Power Pages studio is deprecated. Use Power Pages [design studio](design-build-overview.md) to edit your websites instead.

There are two experiences for editing Power Pages and Power Apps portals sites.

- The new [Power Pages design studio](../getting-started/create-manage.md).
- The legacy [Power Apps portals Studio](/power-apps/maker/portals/portal-designer-anatomy). 

From the Power Pages home page, you can open sites in design studio [created using Power Pages](../getting-started/create-manage.md) and sites [created using Power Apps](/power-apps/maker/portals/create-portal). 

You can open sites created using Power Apps using portals Studio or the new design studio. Sites created using Power Pages by default open in Power Pages design studio.

When you select a site in the Power Apps maker portal created using Power Apps, you will be given the option to open the site using the portal Studio or to open in Power Pages design studio.

:::image type="content" source="media/editing-sites/select-editor.png" alt-text="Editing site from Power Apps maker portal.":::

## Features not available in the Power Pages design studio

The Power Apps portals Studio has the following features that aren't part of the Power Pages design studio:

- [Web template code editing](/power-apps/maker/portals/work-with-templates)
- [Breadcrumbs](/power-apps/maker/portals/add-breadcrumb)
- [Custom menus](/power-apps/maker/portals/add-custom-menu)
- [Content snippet editing](/power-apps/maker/portals/configure/customize-content-snippets)

> [!NOTE]
> Please see [How to: Embed a chatbot on a webpage](../guidance/integrate-pva.md) on how to embed a chatbot on a Power Pages site.

## Components added in design studio

Power Pages design studio has new capabilities that aren't available in the Power Apps portals Studio. If you customize a site in the Power Pages design studio and open the site in Power Apps portals Studio, the following components won't be configurable:  

- [Videos](../getting-started/add-video.md) 
- [Buttons](../getting-started/add-button.md)
- [Spacers](../getting-started/add-spacer.md)
- [Text](../getting-started/add-text.md)
- [Images](../getting-started/add-image.md)
- [Basic forms](../getting-started/add-form.md)
- [Multistep forms](../getting-started/multistep-forms.md)

> [!TIP]
> When customizing sites created through Power Pages, we recommend that you use Power Pages design studio instead of Power Apps portals Studio.

## Styling and themes

New themes and styling options introduced in the [Styling workspace](../getting-started/style-site.md) of the Power Pages design studio can't be customized using the [themes editor](/power-apps/maker/portals/theme-overview) in the Power Apps portals Studio.

### Editing themes created in Power Apps portals Studio

If you're using the Styling workspace with a site that had a theme applied using Power Apps portals Studio, you'll encounter the following behaviors;

- The Styling workspace will show the theme as a **Custom theme**.
- All the existing preset themes are available.
- Once you choose and save a new theme, you won't be able to revert to the original theme.
- In Pages workspace, text items won't support **title** and **small text** styles.
- Buttons won't support styling options.
- For the background color, you can use the color picker but not the color palette.

:::image type="content" source="media/editing-sites/portal-theme.png" alt-text="Editing theme created in Power Apps portals Studio.":::

> [!TIP]
> To utilize the richer styling options of design studio, we recommend you select and apply one of the preset themes to your site.

### Editing custom themes

A common method of styling a site is to upload a custom CSS file using the [Portals Management app](portal-management-app.md).

There are also three CSS files added to all sites by default;
- bootstrapmin.css
- theme.css
- portalbasictheme.css

The display order of the custom CSS file should be higher than the **theme.css** and **bootstrapmin.css** files and lower than the **portalbasictheme.css** and the default display order shouldn't be modified.

**portalbasictheme.css** > *custom.css* > **theme.css** > **bootstrapmin.css**

If the display order has been modified, or the default CSS files have been disabled, you'll encounter the following behaviors;

- The Styling workspace will show the theme as a **Custom theme**.
- The existing preset themes won't be available.
- In Pages workspace, text items won't support **title** and **small text** styles.
- Buttons won't support styling options.
- For the background color, you can use the color picker but not the color palette.

:::image type="content" source="media/editing-sites/custom-theme.png" alt-text="Editing custom theme uploaded in the Portals Management app.":::

> [!TIP]
> To utilize the richer styling options of design studio, we recommend that all three of the default CSS files are enabled (**portalbasictheme.css**, **theme.css**, and **bootstrapmin.css**) and in the correct display order. You can then select and apply one of the preset themes to your site.

> [!WARNING]
> It is not recommended to deactivate, delete or change the display order of any of the default CSS files (bootstrap.min.css, theme.css, or portalbasictheme.css). You will see an error in the design studio.</br>
> :::image type="content" source="media/manage-css/update-css-pma.png" alt-text="Update CSS files using the Portals Management app."::: </br>

#### Resolving display order

In order to restore the display order of the default CSS files, follow these steps:

1. Open the **Portal management app** and in the **Content** section, locate **Web Files**.

1. Locate the following web files and update the **display** order appropriately. You can use any values as long as the display order values are **portalbasictheme.css** > *custom.css* > **theme.css** > **bootstrapmin.css**. 

    | File | Display order |
    | - | - |
    | bootstrap.min.css | 8 |
    | theme.css | 9 |
    | *custom.css* | 10, 11, etc. |
    | portalbasictheme.css | 15 |

    :::image type="content" source="media/editing-sites/display-order.png" alt-text="Create a Power Pages site.":::

1. Select **Save** to update the web file record.

For information on how to upload a custom CSS file, see [upload CSS files](manage-css.md#upload-css-files).

