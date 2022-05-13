---
title: "Tutorial: Add a form to your page"
description: Learn how to add forms to your Power Pages.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 5/13/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Add a form to your page

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create a form
> * Add code components
> * Add a form to a page
> * Configure code options

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).

## Create a form

In this video, we'll create a form using the Data workspace.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4VDev]

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

1. Open the maker studio and select the form you created previously.
1. Select the **Comments** field on the form.
    :::image type="content" source="media/tutorial/comments.png" alt-text="The comments field on the form.":::
1. In the right-hand section, choose **Components** and select the **Rich Text Editor** control.
    :::image type="content" source="media/tutorial/rich-text-editor.png" alt-text="The Rich Text Editor Control option in Add component.":::
1. Select **Done**.
    :::image type="content" source="media/tutorial/done.png" alt-text="The done button.":::

The form now has a code component linked to the field.

## Add a form to a page

1. Open a Power Pages site in the maker studio.
1. Choose the **+ icon** next to **Main Navigation** to add a new page.
    :::image type="content" source="media/tutorial/plus-icon.png" alt-text="Add a new page.":::
1. Fill in the details.
    - Give the page a name.
    - Choose the **Start from Blank template**.
    - Select **Add**.
    :::image type="content" source="media/tutorial/add-page.png" alt-text="Add a new page.":::
    
1. Select **Form** from the component bar.
1. Select **+ New form**.
1. Select the **Feedback table**.
1. Select the form you created previously.
1. Select the **Permissions** button.
1. Select **Feedback permissions**.
1. Ensure the **Create privilege** is checked and that **Anonymous** and Authenticated web roles are linked.
1. Select **Preview page**.
1. Add some data, then enter the captcha code.
1. Select **Submit**.

## Configure form options

1. In the maker studio, open a page with a form component and choose the Form button.
1. Specify the table and Dataverse form.
1. Select the **Data tab** to create a record, update an existing record, or specify as read-only.
1. Select the **On Submit tab** to enable your page to show a success message or redirect to a webpage or URL.
1. Select the **Data section**.  Select **Open Portal Management app**.
1. Select **Basic form metadata**.
1. Choose **New basic form metadata**.
1. Choose **Attribute** for the type.
1. Choose **Comments** for the column.
1. Choose **Code component** for the control style.
1. Select **Save**.

## Next steps

Advance to the next article to learn how to create a multi-step (advanced) form to your page.
> [!div class="nextstepaction"]
> [Next steps](tutorial-add-multi-step-form.md)

