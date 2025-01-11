---
title: "Tutorial: Add custom CSS to your site"
description: Learn how to add custom CSS to your Power Pages sites.
author: ankitavish
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 02/21/2023
ms.subservice:
ms.author: avishwakarma 
ms.reviewer: danamartens
contributors:
    - ankitavish
---
# Tutorial: Add custom CSS to your site

The [Styling workspace](tutorial-style-site.md) allows you to edit some of the theme features of your site, such as fonts and colors; however, you may apply your own custom CSS themes.

You can create your own theme by defining a custom CSS file and uploading it to your site.  

In this tutorial, you'll learn how to:

> [!div class="checklist"]
> * Upload a custom CSS file
> * Edit CSS in Visual Studio Code for the Web

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- A custom theme file created using your favorite CSS editor.

> [!NOTE]  
> Any custom theme you create must be compatible with Bootstrap v3.

## Add custom CSS to your site

The following video shows you how to apply custom CSS code to your site.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=13703cfb-4427-4106-ba30-e6ebba47ca95]

In this example, we'll add some custom CSS files that will allow us to add shadow effects to buttons on our website. You can use your own custom CSS file or use the sample provided.

1. To create a sample, in your favorite CSS editor, create the **button_shadow.css** custom theme file and save.

    ```css
    .button1 {
    box-shadow: 0 9px 18px 0 #333333, 0 8px 24px 0 #333333;
     }
    ```

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select the site to which you want to add the custom theme and choose **Edit**.

1. Open up the **Styling** workspace.

1. Select a theme and select the **...** (ellipses), and then select **Manage CSS**.

    :::image type="content" source="media/tutorial/manage-css.png" alt-text="Open the manage CSS panel from Styling workspace.":::

1. In the **Custom CSS** section, select **Upload** and choose your custom CSS file. You can only upload one CSS file at a time, but multiple files can be uploaded. If multiple CSS files update the same attribute, the attributes in the CSS file at the bottom of the list will apply. You can adjust the order of your custom CSS files.

1. You should immediately see the results of the updates on the pages canvas.

    :::image type="content" source="media/tutorial/button-shadow.png" alt-text="Button shadow effect from uploaded CSS file.":::

1. You can disable or move the order of your custom CSS files. The file listed last will take precedence over the others.

    :::image type="content" source="media/tutorial/css-order.png" alt-text="Disable or move the order of the CSS file.":::

1. You can edit a CSS file directly by selecting the ellipses (**...**) and  then selecting **Edit code**. This step will open the [Visual Code for the Web](../configure/visual-studio-code-editor.md) editor. Select **CTRL-S** to save your changes. 

    :::image type="content" source="media/tutorial/edit-css-vscode.png" alt-text="Edit the CSS file in Visual Studio Code for the Web.":::

1. Select **Sync** in the design studio to update the CSS and view the changes.

1. Select **Preview** to view the custom theme on your site.

> [!NOTE]
>
> To completely remove the custom theme delete  the web file record in the [Portal Management app](../configure/portal-management-app.md).
