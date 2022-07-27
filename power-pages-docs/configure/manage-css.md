---
title: Manage CSS files in Power Pages
description: Learn how to upload CSS files in the design studio
author: ankitavish
ms.topic: conceptual
ms.custom: 
ms.date: 07/27/2022
ms.subservice:
ms.author: avishwakarma
ms.reviewer: ndoelman
contributors:
    - ankitavish
    - nickdoelman
    - ProfessorKendrick
---

# Manage CSS files

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Cascading Style Sheets (CSS) allows you to control the formatting and styling of your site. 

By default, new Power Pages sites have *bootstrap.min.css*, *theme.css* and *portalbasictheme.css* files available. 

You can modify the style using the [Styling workspace](../getting-started/style-site.md) or you can upload your own custom CSS files. 

When you upload a new CSS file, it will be available as a web file in the [Portal Management app](portal-management-app.md).

## Entry Point to Manage CSS:

Edit the site to open it in Power Pages Studio.

-   Select 'Manage CSS' option under more options in Styling Workspace. 

:::image type="content" source="media/manage-css/manage-css.png" alt-text="Manage CSS files using design studio.":::

## Manage and Upload CSS:

-   Under 'Manage CSS'.

-   You'll see list of default css files – bootstrapmin.css, theme.css and portalbasictheme.css.

-   NOTE – Files at bottom take higher precedence.

-   To Upload CSS – Click on 'Upload'

:::image type="content" source="media/manage-css/upload-css.png" alt-text="Upload CSS files using design studio.":::

-   You can upload .css files of size upto 1mb.

-   Once css is uploaded the preview will reflect on right side.

-   The uploaded css files will be applicable for all themes.

## More options for CSS:

-   Move up/down or disable css using more options.

-   NOTE – Files at bottom take higher precedence. 

:::image type="content" source="media/manage-css/css-order.png" alt-text="Order of precedence for CSS files.":::

## Edit CSS:

-   Edit CSS is currently not supported. We are working on bringing this capability for Power Pages soon.

## Architecture:

-   Please note that custom css is at lower priority then portalbasictheme.css and higher than theme.css, this is to encourage customizing styles using style panel for out of box styling options provided in style panel.

-   Note –We recommend Custom CSS should be used to format styles which aren't provided out of box in style pane.

## Error Scenario:

-   If any default css file is deactivated, deleted or priority order is tweaked from Portal Management app, this error will show.

-   Go to Portal management app and reverse the changes done.

:::image type="content" source="media/manage-css/update-css-pma.png" alt-text="Update CSS files using the Portals Management app.":::