---
title: "Tutorial: Add a form to your page"
description: Learn how to add forms with code components to your Power Pages.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 5/24/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Add a form to your page

Power Pages allows you to add form components to a page to allow your users to be able to create, edit, or view Microsoft Dataverse records.

Forms on pages are created from Microsoft Dataverse table forms.

This tutorial shows you how to create and add a form to your page, capture rich information through code components, and configure form actions when the information in the form is submitted.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create a form
> * Add code components
> * Add a form to a page
> * Configure code options

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- Complete the [Add and design a page](tutorial-add-webpage.md) tutorial.
- Complete the [Display data securely on pages](tutorial-display-data-securely.md) tutorial.

## Create a form

This video will provide an overview of the following steps.
<!--embed video
> [!VIDEO https://www.microsoft.com/videoplayer/embed/ZZZZZZ]
-->
[!INCLUDE[cc-video-coming-soon](../includes/cc-video-coming-soon.md)]

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In the **data workspace**, select the **Feedback table** and choose the **Forms tab**.

    :::image type="content" source="media/tutorial/feedback-table.png" alt-text="Theforms menu option for the feedback table in the data workspace.":::

1. Select **+ New form** to open the form editor.

    :::image type="content" source="media/tutorial/new-form.png" alt-text="The + New form menu tile inside the forms menu item.":::

1. Fill in the details.
 
    - Give the form a name. You can also add a description if you'd like one.
    - Select **Create**.
    
        :::image type="content" source="media/tutorial/new-form-details.png" alt-text="Create a new form field.":::

1. Modify the form using the **Add field** menu option, or by dragging and dropping existing fields to reorder them.

1. Select **Publish form**.

    :::image type="content" source="media/tutorial/publish-form.png" alt-text="Publish form button inside the data workspace.":::

1. Select **Back**.

    :::image type="content" source="media/tutorial/back-form.png" alt-text="The back menu option.":::

The form will appear in the list of forms for that table.

### See also
- [Add Form](add-form.md)
- [How to create and modify Dataverse forms using data workspace](../configure/data-workspace-forms.md)

## Add code components

Code components can be added to forms to allow advanced interaction with specific data fields. For example, we can enable rich text editing capabilities to a multi-line text field on a form.

This video will provide an overview of the following steps.
<!--embed video
> [!VIDEO https://www.microsoft.com/videoplayer/embed/ZZZZZZ]
-->
[!INCLUDE[cc-video-coming-soon](../includes/cc-video-coming-soon.md)]

1. In the **data workspace**, select the **Feedback table** and choose the **Forms tab**.

1. Select the form you created earlier.

1. Select the **Comments** field on the form.

1. In the right-hand section, choose **Components** and select the **Rich Text Editor** control.

    :::image type="content" source="media/tutorial/rich-text-editor.png" alt-text="The Rich Text Editor Control option in Add component.":::

1. Select **Done**.

The form now has a code component linked to the field. 

## Add a form to a page

The following steps provide details on how to add your form to a page.

This video provides an overview of the steps to add a form to a page.
<!--embed video
> [!VIDEO https://www.microsoft.com/videoplayer/embed/ZZZZZZ]
-->
[!INCLUDE[cc-video-coming-soon](../includes/cc-video-coming-soon.md)]

1. Open a Power Pages site in the design studio.

1. Choose the **+ icon** next to **Main Navigation** to add a new page.

1. Fill in the details.
    - Give the page a name.
    - Choose the **Start from Blank template**.
    - Select **Add**.
    
    :::image type="content" source="media/tutorial/add-page.png" alt-text="Details for your new page.":::
    
1. Select **Form** from the component bar.

    :::image type="content" source="media/tutorial/form-icon.png" alt-text="THe form icon from the component bar.":::

1. Select **+ New form**.

    :::image type="content" source="media/tutorial/add-a-form.png" alt-text="Add a form window.":::

1. Fill in the details.
    - Select the **Feedback table**.
    - Select the form you created previously.
    - Select **Ok**.
    
    :::image type="content" source="media/tutorial/add-form-details.png" alt-text="Details for Add a Form":::

1. Select the **Permissions** button.

    :::image type="content" source="media/tutorial/permissions.png" alt-text="The permissions button.":::

1. Select **Feedback permissions**.

    - Ensure the **Create privilege** is checked and that **Anonymous** and **Authenticated** web roles are linked.
    
    :::image type="content" source="media/tutorial/web-roles-feedback.png" alt-text="Options for setting feedback permissions."::: 
 
1. Select **Preview page**.

    :::image type="content" source="media/tutorial/preview-icon.png" alt-text="Preview icon.":::

## Configure form options

Earlier we enabled the rich text editor component on the comments field in our form. In order for the rich text editor to render on the page, we need to add some metadata. 

This video will provide an overview of the following steps.
<!--embed video
> [!VIDEO https://www.microsoft.com/videoplayer/embed/ZZZZZZ]
-->
[!INCLUDE[cc-video-coming-soon](../includes/cc-video-coming-soon.md)]

1. In the design studio, open a page with a form component and select the form you previously created.

1. Select the **Form** button.

    :::image type="content" source="media/tutorial/form-menu-bar.png" alt-text="Form menu bar options.":::

1. Select the **Data section**.  Select **Open Portal Management app**.  You'll be directed to the form metadata record.

    :::image type="content" source="media/tutorial/form-data-tab.png" alt-text="The form data tab.":::

1. Select the **Basic form metadata** tab.

1. Choose **New basic form metadata**.

    :::image type="content" source="media/tutorial/form metadata.png" alt-text="New Form Metadata tab.":::

    - Choose **Attribute** for the Type.
    - Choose **Comments** for the Attribute Logical Name.
    - Choose **Code component** for the control style.

    :::image type="content" source="media/tutorial/form-metadata-choices.png" alt-text="Choosing values for form metadata.":::

1. Select **Save**.

1. From the design studio, select **Preview** and navigate to your page.

1. The form should show the rich text editor controls on the field.

    :::image type="content" source="media/tutorial/feedback-form-richtext.png" alt-text="Feedback form with rich text editor control on comments.":::

## Next steps

Next, learn how to create a multi-step (advanced) form to your page.
> [!div class="nextstepaction"]
> [Add a multi-step form to a page](tutorial-add-multi-step-form.md)

