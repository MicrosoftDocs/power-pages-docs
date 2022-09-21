---
title: "Tutorial: Add custom CSS to your site"
description: Learn how to add custom CSS to your Power Pages sites.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 08/04/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---
# Tutorial: Add custom CSS to your site

The [style workspace](tutorial-style-site.md) allows you to edit some of the theme features of your site, such as fonts and colors; however, you may wish to apply your own custom CSS themes.

You can create your own theme by defining a custom CSS file and uploading it to your site.  

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Upload a custom CSS file

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- A custom theme created using your favorite CSS editor.

> [!NOTE]  
> Any custom theme you create must be compatible with Bootstrap v3.

## Add custom CSS to your site

1. Create or download a custom theme and save as a .CSS file.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Open up the **Styling** workspace.

1. Select a theme and select the **...** (ellipses) and select **Manage CSS**.

    :::image type="content" source="media/tutorial/manage-css.png" alt-text="Open the manage CSS panel from Styling workspace.":::

1. In the **Custom CSS** section, select **Upload** and choose your custom CSS file. You can only upload one CSS file at a time, but multiple files can be uploaded. If multiple CSS files update the same attribute, the attributes in the CSS file at the bottom of the list will apply. You can adjust the order of your custom CSS files.

1. Select **Preview** to view the custom theme on your site.

1. You can disable, or move the order of your custom CSS files.

    :::image type="content" source="media/tutorial/css-order.png" alt-text="Disable or move the order of the CSS file.":::

> [!NOTE]
>
> To completely remove the custom theme; delete or de-activate the web file record in the [Portal Management app](../configure/portal-management-app.md).
