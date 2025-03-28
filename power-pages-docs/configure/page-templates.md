---
title: Create and manage page templates
description: Learn how to create and manage page templates in Power Pages.
author: DanaMartens

ms.topic: conceptual
ms.custom: 
ms.date: 04/12/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Create and manage page templates

While web pages are nodes in your website's sitemap which represent content accessible to website users, page templates point to either the actual .aspx pages or to the [web templates](web-templates.md) which provide a means to maintain a consistent look and feel of the structure of your website content. 

When creating a new web page for your website, whether through the [design studio](../getting-started/create-manage.md) or using the [Portals Management app](portal-management-app.md), you must select a page template (also known as page layout) which will present the webpage's layout and functionality to users of the website.

A page template will determine whether the webpage will use an .aspx page or a web template for its layout as well as determining if the webpage will render the website header and footer.

## Manage page templates

Creating a new page template is necessary to point to a new or existing web template that has been developed as a custom page layout. See [Tutorial: Add custom page layout to your site](../getting-started/tutorial-add-custom-page-layout.md) for a complete tutorial on creating custom page layouts.

1. Open the [Portal Management app](portal-management-app.md).

2. Go to **Websites** > **Page Templates**.

3. To create a new page template, select **New**.

4. To edit an existing page template, select the page template name.

5. Enter appropriate values in the fields.

6. Select **Save & Close**.

### Page template attributes

|Name |Description |
|-----|--------|
|Name    |Name of the template used for reference.   |
|Website   |The associated website.   |
|Type   |The type of the template, which controls how the template will determine what to render.<ul><li>**Rewrite**: Will use the rewrite URL field to render a given ASP.NET template.</li><li>**Web Template**: Will use the web template field to render a given Web Template.</li></ul>   |
|Rewrite URL   | Path of the physical ASP.NET .aspx page which will be rendering the content.<br> This field is displayed only if **Rewrite URL** is selected from the **Type** list. You can only point to default .aspx pages. |
|Web Template   | A reference to a web template to that will be used to render this template.<br>This field is displayed only if **Web Template** is selected from the **Type** list.  |
|Is Default   |If 'Yes' then the template will be the default assigned to the dropdown in the client-side editing tools.   |
|Table Name   |The page table type that this template expects to render. This will be use by the front-side editing system to present only appropriate template choices to content authors.<br>Usually, this will be Web Page (adx_webpage), but may be another portal table, such as Forum, Forum Thread, Blog, or Blog Post.   |
|Description  |A description of this template. |
|||


