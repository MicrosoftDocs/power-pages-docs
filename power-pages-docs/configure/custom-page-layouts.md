---
title: Custom page layouts in Power Pages
description: Learn how to create custom page layouts in Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 09/01/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
---

# Custom page layouts in Power Pages

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

When you create a new web page using the design studio, you need to select a page layout. The Pages workspace provides a set of pre-configured page layouts.

:::image type="content" source="media/custom-page-layouts/select-page-layout.png" alt-text="Selecting the page layout.":::

You can also create your own custom page layouts using HTML, Liquid, JavaScript and CSS.

## Create a custom page layout

To create a custom page, you'll need to follow these steps:

- Create a web template containing the code
- Create a corresponding page template

### Creating a web template

The web template will contain your code for your layout. This can be a combination of Liquid, HTML, CSS, and JavaScript. 

Web templates can be included in other content or combined with other templates to build a modular system of templates when building web applications.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In the **design studio**, choose **...** and then select **Portal Management**. You'll need to use the Portal Management app to create a web template record and enter in your custom code.

    :::image type="content" source="media/custom-page-layouts/portal-management-app.png" alt-text="Selecting the ellipse directs you to a menu where you can choose the portal management app.":::

1. In the **Portal Management app**, scroll to the **Content** section and select **Web Templates**.

1. From **Active Web Templates** screen, select **New**.

    :::image type="content" source="media/custom-page-layouts/new-web-template.png" alt-text="The + New menu option from the Active Web Templates page in the Portal Management app.":::

1. Fill in the required fields. 

    |Field  |Value  |
    |---------|---------|
    | Name | Type in a name. |
    | Website | Select the web site to which the theme will be applied. Put your cursor in the field and hit enter on your keyboard to display a list of available options. |
    |Source  | The source code of your web template, this is typically a combination of Liquid, HTML, CSS, and JavaScript. You will create the code based on your requirements. |
    | MIME Type | (Scroll down to view this field)  |

    :::image type="content" source="media/custom-page-layouts/custom-web-template.png" alt-text="Fillable fields for New Web Files.":::

1. Select **Save**.
