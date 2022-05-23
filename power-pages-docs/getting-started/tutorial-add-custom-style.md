---
title: "Tutorial: Add custom CSS to your site"
description: Learn how to add custom CSS to your Power Pages sites.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 05/24/2022
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
> * Create a web file record
> * Upload a custom CSS file

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- A custom theme created using your favorite CSS editor.

> [!NOTE]  
> Any custom theme you create must be compatible with Bootstrap v3.

## Add custom CSS to your site

This video provides an overview of the steps to add custom CSS to your site.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4XYen]

1. Create or download a custom theme and save as a .CSS file.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In the **design studio**, choose **...** and then select **Portal Management**. You'll need to use the Portal Management app to create a web file record and attach your custom CSS file.

    :::image type="content" source="media/tutorial/portal-management-app.png" alt-text="Selecting the ellipse directs you to a menu where you can choose the portal management app.":::

1. In the **Portal Management app**, scroll to the **Content** section and select **Web Files**.

1. From **Active Web Files** screen, select **New**.

    :::image type="content" source="media/tutorial/new-web-file.png" alt-text="The + New menu option from the Active Web Files page in the Portal Management app.":::

1. Fill in the required fields. 

    |Field  |Value  |
    |---------|---------|
    |Name     |Type in a name.         |
    |Website     |Select the web site to which the theme will be applied. Put your cursor in the field and hit enter on your keyboard to display a list of available options.         |
    |Parent Page    |Select **Home**. Put your cursor in the field and hit enter on your keyboard to display a list of available options.           |
    |Partial URL    |Type in the name you chose for the **Name** field followed by .css.         |
    |Publishing State| Put your cursor in the field and hit enter on your keyboard to display a list of available options.  |
    | Display Order | (Scroll down to view this field) Set to a high value (100) to ensure that you CSS is the final theme applied. |

    :::image type="content" source="media/tutorial/web-file-css.png" alt-text="Fillable fields for New Web Files.":::

1. Select **Save**.

1. Select the **Notes** tab.

    :::image type="content" source="media/tutorial/notes.png" alt-text="The notes menu option for a web file in the Portal Management app.":::

1. Select the **Paperclip icon**.

1. Select your CSS file to attach to the note.

1. Select **Add Note**

1. Select **Save**.

1. Go back to the **design studio** to preview the css on your site. If you select the **Styling** workspace, you should see **Custom CSS** as the selected theme. 

    :::image type="content" source="media/tutorial/custom-style-preview.png" alt-text="Viewing the custom style in design studio.":::

1. Select **Preview** to view the custom theme on your site.

> [!NOTE]
> To remove the custom theme; delete or de-activate the web file record in the [Portal Management app](../configure/portal-management-app.md).
