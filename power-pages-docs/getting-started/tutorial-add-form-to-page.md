---
title: "Tutorial: Add a form to your page"
description: Learn how to add forms with code components to your Power Pages.
author: shwetamurkute
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 11/17/2026
ms.subservice:
ms.author: bipuldeora 
ms.reviewer: 
contributors:
    - pranita225
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

This video provides an overview of the steps to create a form.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=4c80269b-496c-4de7-9383-2e64f6c7b823]

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In the **data workspace**, select the **Feedback table** and choose the **Forms tab**.

    :::image type="content" source="media/tutorial/feedback-table.png" alt-text="The forms menu option for the feedback table in the data workspace.":::

1. Select **+ New form** to open the form editor.

    :::image type="content" source="media/tutorial/new-form.png" alt-text="The + New form menu tile inside the forms menu item.":::

1. Fill in the details.

    * Give the form a name. You can also add a description if you'd like one.
    * Select **Create**.

        :::image type="content" source="media/tutorial/new-form-details.png" alt-text="Create a new form field.":::

1. Modify the form using the **Add field** menu option, or by dragging and dropping existing fields to reorder them.

1. Select **Publish form**.

    :::image type="content" source="media/tutorial/publish-form.png" alt-text="Publish form button inside the data workspace.":::

1. Select **Back**.

    :::image type="content" source="media/tutorial/back-form.png" alt-text="The back menu option.":::

The form will appear in the list of forms for that table.

### See also

* [Add Form](add-form.md)
* [How to create and modify Dataverse forms using data workspace](../configure/data-workspace-forms.md)

## Add code components

Code components can be added to Dataverse forms to allow advanced interaction with specific data fields. For example, we can enable rich text editing capabilities to a multi-line text field on a form.

1. In the **Data workspace**, select the **Feedback table** and choose the **Forms tab**.

1. Select the form you created earlier.

1. Select the **Comments** field on the form.

1. In the right-hand section, choose **Components** and select the **Rich Text Editor** control.

    :::image type="content" source="media/tutorial/rich-text-editor.png" alt-text="The Rich Text Editor Control option in Add component.":::

1. Select **Done**.

The form now has a code component linked to the field. 

## Add a form to a page

Add a form to collect information from site visitors and save it in Microsoft Dataverse. You can describe the form you need to Copilot or select an existing Dataverse form.

Open your site in the Power Pages design studio, and then use either of the following methods. After you add the form, review its table permissions and preview the page.

This video provides an overview of the steps to add a form to a page.

> [!VIDEO 314d2bf3-0b7e-4a1c-9536-eba3ad594bfd]

### Create a form with Copilot

Describe the information you want to collect, and then use Copilot to generate and refine the form. In this example, you create a volunteer sign-up form.

1. In the **Pages** workspace, select the page where you want to add the form.

2. In the section where you want the form to appear, select **Form** from the component bar.

3. Under **Describe a form to create it**, enter a description of the form. For example:

   > A volunteer sign-up form for trail days, with name, email, preferred weekday, and a comments box.

4. Select the arrow in the prompt box to generate the form.

5. Review the generated form in the preview.

6. To change the form, enter a request under **Do you want to make any changes?**, and then select the arrow. For example:

   > Add a phone number field.

7. Review the updated form, and then select **OK** to add it to the page.

> [!NOTE]
> Copilot results can vary. Review the generated fields and collect only the personal data you need for the form's purpose.

### Add an existing Dataverse form

Select a form from a Dataverse table instead of generating one with Copilot. In this example, you use the **Feedback** form from the **Feedback** table.

1. In the **Pages** workspace, select the page where you want to add the form.

2. In the section where you want the form to appear, select **Form** from the component bar.

3. Under **Other ways to get started**, select **New form**.

4. In the **Add a form** dialog, under **Choose a table**, select **Feedback**.

5. Under **Select a form**, select **Feedback**, or select the form you created previously for that table.

6. In **Name your copy of the selected form**, enter a descriptive name, such as **Visitor feedback**.

7. Select **OK** to add the form to the page.

### Configure table permissions

Table permissions determine which site visitors can submit information. Review the permissions for the table used by your form. The following steps use the **Feedback** table permission shown in this example.

1. Select the form on the page, and then select **Permissions** on the form toolbar.

2. In the **Table permissions** pane, select **Feedback**.

3. On the **Basic** tab, confirm that **Table** is set to **Feedback**.

4. For this example, set **Access type** to **Global access**.

5. Under **Permission to**, select **Create** so visitors can submit new records.

6. Under **Roles**, select **Add roles**, and then select **Anonymous Users** and **Authenticated Users** to allow submissions from visitors who aren't signed in and visitors who are signed in.

7. Close the role selector, and then select **Save**.

> [!IMPORTANT]
> Include **Anonymous Users** only if you want visitors who aren't signed in to submit the form. Grant only the permissions your form needs. For this example, visitors need **Create**, not **Read**, **Update**, or **Delete**.

### Preview the form

Preview the page to check how the form appears to site visitors.

1. Close the permissions pane, and then select **Preview** in the design studio.

2. Select **Desktop** to open the site in a new tab.

3. Review the form on the page and confirm that the expected fields appear.

## Enable code components on form fields

This video provides an overview of the steps to configure the rich text editor control on a form.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=3975f527-e192-45af-9df1-ac8c7d3a5bb3]

If a Dataverse form field has been configured to use a code component using the Data workspace or a model-driven app, you can enable the code component to be used when a form is used on a webpage.

To enable a code component:

1. Select the **Edit code component** button from the menu.

1. Switch the **Enable custom component field** toggle switch to the on position.

Custom components are now enabled for that field.

1. From the design studio, select **Preview** and navigate to your page.

1. The form should show the rich text editor controls on the field.

    :::image type="content" source="media/tutorial/feedback-form-richtext.png" alt-text="Feedback form with rich text editor control on comments.":::

## Enable attachments on forms

This video shows how you can enable attachments on forms.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=92101405-5ecf-4267-90bc-f4d2adca0a2a]

Users can upload an attachment with form submission.

To enable attachments on a form:

1. Add a form or edit an existing form.

1. In the **Add a form** modal, choose **Attachments** from the left panel. 

    - Configure the following options:
        - Turn on/off the **Enable attachments** toggle.
        - Turn on/off the **Attachment is required** toggle.
        - Turn on/off the **Allow multiple files** toggle.
        - Max file size allowed

> [!NOTE]
> The following file types are allowed:
>   - All
>   - Audio
>   - Document
>   - Image
>   - Video
>    - Specific (comma separated values)

:::image type="content" source="media/add-form/attach-file.png" alt-text="Menu options for enabling attachments on a form.":::

Once configured, the file upload placeholder will show in the canvas. 

:::image type="content" source="media/add-form/form-with-attachment.png" alt-text="Form with attachment option enabled.":::

## Next steps

Next, learn how to create a multi-step (advanced) form to your page.
> [!div class="nextstepaction"]
> [Add a multi-step form to a page](tutorial-add-multi-step-form.md)
