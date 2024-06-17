---
title: Add an image
description: Learn how to add images to your Power Pages site.
author: ckwan-ms
ms.topic: conceptual
ms.custom: 
ms.date: 06/11/2024
ms.subservice:
ms.author: ckwan 
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
    - ckwan-ms
    - DanaMartens
---

# Add an image

Use the image component to add images to your portal page.

To add an image:

1. Open the [design studio](use-design-studio.md) to edit the content and components of your page.

1. Select the page you want to edit.

1. Select the section you want to add the image component to.

1. Hover over any editable canvas area, then select the **Image** icon from the component panel.

    :::image type="content" source="media/common/component-options.png" alt-text="The add component menu options.":::

1. You can now upload an image, use an external URL, or use template images (if available).

    | Option | Description |
    | ----------- | ----------- |
    | Upload image | Select this option if you want to select an existing image or upload a new one. If you want to select a previously uploaded image, choose it from the **Select image** list. To upload a new image, select **Upload image**. All the uploaded images are included in the image library, which you can select again through the **Select image** list. |
    | External URL | Select this option if you want to upload an image from an external URL. Enter the URL in the **External URL** field. Only secured links are accepted—that is, **https://** is mandatory. If you have images stored in your content delivery network, you can provide the link in this field. |

## Format an image

To format your image, select it and a menu with editing options will appear:

- Select a new image
- Configure the alignment
- Add a link to the image
- Access more options
- Duplicate the image, move it up, move it down, or delete it

:::image type="content" source="media/add-image/edit-image.png" alt-text="Editing options for images in the design studio.":::

> [!TIP]
> Power Fx is now available to use with different Power Pages components including images. Use Power Fx to dynamically set values based on the result of an expression. For more information, go to [Use Power Fx in Power Pages (preview)](../configure/power-fx.md).

### Add a link to an image

To add a link to your image:

1. Choose the **link icon** from the editing options above the image.
1. Select a radio button to **Link to a URL** or **Link to a page**.
    - If you're linking to a URL, fill in the text field.
    - If you're linking to a page, select the page from the drop down.
1. Select the **OK** button.

Once the link is created, you can select the **link icon** to edit or remove the link.

### Adjust image size

Options to adjust the size of your image are located under **More options**. To access these options:

1. Select the **gear icon** from the editing options above the image to access the **More options** window.
1. Update the height and width fields.
1. Select the **OK** button.

### Add alt text to an image

1. Select the **gear icon** from the editing options above the image to access the **More options** window.
1. Update the alt text field.
1. Select the **OK** button.

## Storing images in Power Pages design studio

By default, images in Power Pages sites are stored beneath the Home page.

### Change image storage location

To change the location where your images will be stored

1. Select the image button for any image component.
1. Choose **Advanced Options** in the bottom-left corner of the **Add an image** dialog.
1. Select the page to store all newly updated images beneath.

    > [!TIP]
    > - This only applies to newly updated images. If you want to change the parent page for an existing image, re-upload the image after changing this setting.
    > -  If you want to prevent, direct access to images, store them beneath a restricted page and set the image files to inherit the page's permissions. More information: [Page permissions in Power Pages](../security/page-security.md)

### View image storage location

To see the parent page of your images in design studio

1. Select the Image button for any image component.
1. Locate the parent age in Grid or List view.
