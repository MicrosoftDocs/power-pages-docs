---
title: "Tutorial: Add a multistep form to your page"
description: Learn how to add multistep forms to your Power Pages.
author: pranita225
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 11/04/2022
ms.subservice:
ms.author: prpadalw 
ms.reviewer: ndoelman
contributors:
    - pranita225
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Add a multistep form to your page

Multistep forms are a powerful way to collect and update information in Microsoft Dataverse from a page.  

Multistep forms provide additional features as compared to regular forms:

- Allows data collection or update process to be broken up over multiple steps.
- Provides interactive conditions to direct a user down different paths of data updates.
- Session tracking allows a user to pick up where they left off when following a data update process.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create Dataverse tables, views, and forms to use in your multistep form
> * Add a multistep form to a web page
> * Configure table permissions for multistep forms
> * Add a condition and redirect step to a multistep form

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- Complete the [Add and design a page](tutorial-add-webpage.md) tutorial.
- Complete the [Display data securely on pages](tutorial-display-data-securely.md) tutorial.
- Complete the [Add a form to a page](tutorial-add-form-to-page.md) tutorial.

> [!NOTE]
> When creating a multistep form, it is important to plan the steps first.  This will make the configuration process easier.  Establish the individual steps and any conditional branches to the multistep process.

## Create an multistep form 

In the steps below, we'll create an multistep form, this example follows a simple process to apply for a scholarship, but the concepts can be applied to other business processes. 

Here is an outline of the sample steps:

| Step | Description |
| - | - |
| 1 | Select the scholarship to apply for and enter the applicants name. |
| 2 | Fill in details about the applicant. |
| 3 | Gather some additional details. Later in the tutorial, we will make this step conditional on information from step 2. |
| 4 | Collect final sign-off consent from the user. |

### Create Dataverse tables and forms to use in the multistep form

We will need to store our information of our process in Dataverse tables. For each step of the process that requires a user to create or update columns on a Dataverse record, you will need to have a corresponding Dataverse form.

We will create two tables for our process, *Scholarships* and *Applications*. For more information on how to create Dataverse tables, see [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md)

Create two tables with the following properties:

>[!NOTE] 
> The following tables are just examples, feel free to create tables to match your own business processes:

#### Scholarship

| Column name | Column data type |
| - | - |
| Scholarship Name | Text (rename *name* column) |
| Description | Multiple lines of text |
| Application Opens | Date and time |
| Application Deadline | Date and time |

#### Application

| Column name | Column data type |
| - | - |
| Applicant name | Text (rename *name* column) |
| Scholarship | Lookup (related table - scholarship table created earlier) |
| Class Level | Choice (choices: Junior, Senior) |
| Consent | Yes/No |
| Cost of Tuition | Currency |
| Degree Type | Choice (choices: Masters, Bachelor )
| Fulltime | Yes/No |
| Major | Text |
| Other Scholarships | Multiple lines of text |

Once you have created the tables, you will need to create forms for each step of your process. A good practice is to name your forms to correspond to each step of your multistep process.

See [How to create and modify Dataverse forms by using the Data workspace](../configure/data-workspace-forms.md) on how to create Dataverse forms.

Create the following four forms;

| Form name | Columns on form |
| - | - |
| Application Step 1 | Scholarship, Applicant name |
| Application Step 2 | Scholarship (read-only), Applicant name (read-only), |
| Application Step 3 ||
| Application Step 4 ||





:::image type="content" source="media/tutorial/advanced-form.gif" alt-text="Animation that shows the working advanced form in action.":::

Follow the steps to create an advanced form in the Portals Management app and add it to a page in the design studio.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In the design studio, use the Data workspace to create/edit forms to use in each step of your process.

    :::image type="content" source="media/tutorial/advanced-forms-create-step-forms.png" alt-text="Active Advanced Forms inside the Portal Management App.":::

    > [!TIP]
    > - Create a form for each step that requires data to created or updated. Alternatively, you can create a series of form tabs for each step.
    > - To display columns in the advanced form but not allow users to update, configure the columns to be read-only when creating the forms.

1. Publish your forms.

1. Advanced form configuration is done in the **Portal Management app**. Select the ellipses **...** from the left toolbar, and select **Portal Management**.

1. In the Portal Management app, locate **Advanced forms** in the **Content** section. Create a new Advanced forms record.

1. Specify the configurations.

    - **Name** can be anything descriptive.
    - Set the **Website** is your website (press **Enter** to view list of sites).
    - **Start Step** will be blank for now, we'll set the start step later in the tutorial.
    - Set **Authentication required** to **Yes** (this will required your users sign in to the site to use the advanced form).
    - Set **Start new session on load** to **No** (this will allow your users to pick up where they left off in the advanced form steps).
    - Set **Multiple records per user permitted** to **Yes** (this will allow your users to use the advanced form multiple times to create multiple submissions).
    
    Optionally, you can enable the **Progress Indicator** (scroll down) to show users their progress when filling out a form. 
    
    :::image type="content" source="media/tutorial/advanced-form-config.png" alt-text="New Advanced Form configurations.":::

1. Select **Save**.

### Add advanced form steps

1. In the **Advanced form steps tab**, create a **new Advanced form step record**.
        
    :::image type="content" source="media/tutorial/new-advanced-form-steps.png" alt-text="New advanced form steps menu option in Portal Management app.":::

1. Specify the configurations.

    - Set **Type** to **Load Form**.
    - Select the **Target Table name** from the drop-down menu.

    :::image type="content" source="media/tutorial/advanced-form-step-config.png" alt-text="Configurations for the new advanced form step in Portal Management app.":::

1. Select the **Form Definition** tab where we'll add more configuration.

    :::image type="content" source="media/tutorial/advanced-form-step-details.png" alt-text="Details for the advanced form step in Portal Management app.":::

1. Set the **Mode** to **Insert**. This means that this step will *create* a new record in the table as part of the process.

1. Scroll down the page and select the **Form Name** from the drop-down menu.
    
    > [!NOTE]
    > If you created a form with a set of tabs for each step, select the appropriate **Tab Name** for the step.

1. Scroll down the page and select the **Portal User Lookup Column** from the drop-down menu. This will associate the currently signed-in user with the record being created. The table will need to have a lookup field to the contact table.

#### Adding edit steps to your advanced form

You can edit existing records in advanced forms. These may be a record you created earlier in the process. For example, we created a record in the first step, and now we want to collect some additional information in a subsequent step.

1. In the **Advanced form steps tab**, create a **new Advanced form step record**.
        
    :::image type="content" source="media/tutorial/new-advanced-form-steps.png" alt-text="New advanced form steps menu option in Portal Management app.":::

1. Specify the configurations.

    - Set **Type** to **Load Form**.
    - Select the **Target Table name** from the drop-down menu.

1. Select the **Form Definition** tab where we'll add more configuration.

    :::image type="content" source="media/tutorial/advanced-form-edit-step.png" alt-text="Advanced form steps edit step.":::

    - Set the **Mode** to **Edit** as we're now updating a record.
    - Choose the form (and if necessary, the tab) where the user will be editing or adding data to an existing record.
    - Set the **Source Type** to **Result From Previous Step**. This step will provide the GUID of the record we need to edit as part of the step. There are other options to specify the source record.
    - When the **Source Type** is **Result From Previous Step**, we need to specify the step in the process that will indicate which record is being edited.

1. Select **Save**

#### Adding conditions to your advanced form

If you need to add conditional logic to your advanced form, identify the condition by adding the Dataverse column logical name and the evaluation you want to perform. The logical name of a column can be found by viewing the column configuration in [Data workspace](../configure/data-workspace-tables.md).

In the steps below, we'll check to see if an applicant is pursuing a Masters degree. If a user is pursuing an advanced degree, they'll be directed to extra steps. Other applicants will skip that step.

1. In the **Advanced form steps tab**, create a **new Advanced form step record**.

    :::image type="content" source="media/tutorial/new-advanced-form-steps.png" alt-text="New advanced form steps menu option in Portal Management app.":::

1. Specify the configurations.

    - Set **Type** to **Condition**.
    - Select the **Target Table name** from the drop-down menu.
    :::image type="content" source="media/tutorial/advanced-form-type-condition.png" alt-text="Set configurations for an advanced form step of type condition.":::

1. Select the **Condition** tab and enter the condition using the logical column name and a value.

    :::image type="content" source="media/tutorial/advanced-form-specify-condition.png" alt-text="Text entry field for a condition on an advanced form step.":::

1. Select **Save**

Repeat the instructions outlined until you've created the number of steps needed for your business process.

In the example, we have created the following steps for the scenario of applying for a scholarship.

| Step | Type | Mode | Details | 
| - | - | - | - | 
| Choose Scholarship | Load Form | Insert | <ul><li>Creates an application record</li><li>User chooses scholarship</li></ul> |  
| Application Details | Load Form | Edit | <ul><li>User adds details to application</li><li>User fills in degree type choices that will be used to determine condition in next step.</li></ul> | 
| Check Degree Type | Condition | | <ul><li>Evaluates degree type choices using column logical name.</li><li>Next step is Master degree information if *true* or Consent step if *false*.</li></ul> |
| Master Degree Information | Load Form | Edit | <ul><li>Allows user to fill in additional information if they selected a degree type of *Master* in a previous step, this step is skipped if degree type selected was *Bachelor*.</li></ul>  |
| Consent | Load Form | Edit | <ul><li>Allows user to choose consent field and ends process.</li></ul> |

## Link the steps

Once the steps have been created, you'll need to first go back and specify the start step and link all the steps you created previously.

1. Open the Advanced Form record.

1. Choose the appropriate Advanced form step for **Start Step**

    :::image type="content" source="media/tutorial/advanced-form-set-steps.png" alt-text="Entering in start step.":::

1. For each step, ensure the **Next Step** is populated, except for the last step.

    :::image type="content" source="media/tutorial/advanced-form-link-steps.png" alt-text="Link the steps.":::

1. Conditional steps will have two targets, the step if the evaluation has passed and a step if the evaluation hasn't passed.

    :::image type="content" source="media/tutorial/advanced-form-condition-passed.png" alt-text="Condition passed in the step.":::

    :::image type="content" source="media/tutorial/advanced-form-condition-failed.png" alt-text="Condition failed in the step.":::

1. With conditions, the multiple steps may lead to a step, some of which may **not** have been surfaced to the user. The **Record Source** should be set to a previous step earlier in the process that the user would have interacted with. This is to make sure that the record being updated is identified. 

    :::image type="content" source="media/tutorial/advanced-form-previous-step.png" alt-text="Previous step, not last step.":::

## Table permissions

Ensure that you've created all the appropriate [table permissions](../security/table-permissions.md) for the tables where records are being created, modified or associated with (for example, populating a lookup). 

## Add configuration options

Advanced forms can be configured for different behaviors, set default values, and specialized user controls. In the following example, we'll replace a lookup column with drop-down control as it would provide a better experience for a user.

1. In the **Portal Management app**, choose **Advanced form**, then in the **Advanced Form Steps** tab, select the appropriate step.

    :::image type="content" source="media/tutorial/advanced-form-choose-scholarship.png" alt-text="Select the Choose Scholarship step from the Advanced form menu.":::

1. In the **Related tab**, choose **Metadata**.

    :::image type="content" source="media/tutorial/advanced-form-metadata.png" alt-text="Advanced form metadata.":::

1. Choose **New Advanced Form Metadata**.

:::image type="content" source="media/tutorial/advanced-forms-add-new.png" alt-text="Add new advanced form metadata.":::

1. Set the **Attribute Logical Name**.

    :::image type="content" source="media/tutorial/advanced-form-scholarship-name.png" alt-text="Attribute Logical Name field set to Scholarship Name.":::

1. Scroll down to **Control Style** and set the **Style** to **Render Lookup as a Dropdown**.

    :::image type="content" source="media/tutorial/advanced-form-render-dropdown.png" alt-text="The Style set to Render Lookup as Dropdown under New Advanced Form Metadata.":::

## Add an advanced form to a page

Now that we've created an advanced form in the Portal Management app, we can now add it to a page in our site.

We'll need to use the code editor to add a [Liquid](../configure/liquid-overview.md) tag to the page to show the advanced form.

1. Open the design studio and **Add a page** or edit a page to which you want to add the advanced form.

    :::image type="content" source="media/tutorial/advanced-form-add-page.png" alt-text="Add a new page pop-up.":::

1. Open the **code editor** by selecting the **</>** at the top of canvas.  

    :::image type="content" source="media/tutorial/advanced-form-code-editor.png" alt-text="Code editor icon in design studio.":::

1. Select the code editor icon, and in between the ```<div></div>``` tags, enter in the following Liquid code snippet:

    ```{% webform name: '<name of advanced form>' %}```

    For example, if your advanced form name was *Scholarship Application* then the code would be:

    ```{% webform name: 'Scholarship Application' %}```

    :::image type="content" source="media/tutorial/advanced-form-code.png" alt-text="Adding an advanced form.":::

1. Select **Save**.

1. Select **Preview**.

1. Sign-in to your site.

1. Fill in and test your form.

    :::image type="content" source="media/tutorial/advanced-form-rendering.png" alt-text="Viewing advanced form on a web page.":::

1. You can view the information collected and updated in your advanced form by going to the [Data workspace](../configure/data-workspace-tables.md?#table-designer) table designer, selecting the table, and viewing the data.

## Next steps

Advance to the next article to learn how to configure site authentication to allow users to sign in using Azure AD B2C.

> [!div class="nextstepaction"]
> [Configure site authentication](tutorial-setup-site-authentication.md)
