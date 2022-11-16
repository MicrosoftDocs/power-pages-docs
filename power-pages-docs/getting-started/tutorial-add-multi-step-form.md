---
title: "Tutorial: Add a multistep form to your page"
description: Learn how to add multistep forms to your Power Pages.
author: pranita225
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 11/16/2022
ms.subservice:
ms.author: prpadalw 
ms.reviewer: ndoelman
contributors:
    - pranita225
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Add a multistep form to your page

Multistep forms are a powerful way to collect and update information in Microsoft Dataverse from a page and provide additional features as compared to regular forms:

- Allows data collection or update process to be broken up over multiple steps.
- Provides interactive conditions to direct a user down different paths of data updates.
- Session tracking allows a user to pick up where they left off when following a data update process.

:::image type="content" source="media/tutorial-multistep-forms/multistep-form.gif" alt-text="Animation that shows the working multistep form in action.":::

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
> When creating a multistep form, it is important to plan the steps first. This will make the configuration process easier. Establish the individual steps and any conditional branches to the multistep process.

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

We will need to store our information of our process in Dataverse tables. For each step of the process that requires a user to create or update columns on a Dataverse record, you will need to have a corresponding Dataverse form for each step.

We will create a Dataverse table called *Applications* for our process. For more information on how to create Dataverse tables, see [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md)

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select a site where you want to add a multistep form and select **Edit**. 

1. In the design studio, select the **Data** workspace.

1. Create a Dataverse table called *Applications* with the following properties:

    > [!TIP] 
    > - For more information on how to create Dataverse tables, see [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md)
    > - The following table is just an example, feel free to create tables to match your own business processes.

    | Column name | Column data type |
    | - | - |
    | Applicant name | Text (rename *name* column) |
    | Scholarship | Choice (example choices: *American Architect Scholarship*,*Foreign Language Scholarship*,*Women in STEM Scholarship*,*Future Design Leaders Scholarship*) |
    | Class Level | Choice (choices: *Junior*, *Senior*) |
    | Consent | Yes/No |
    | Cost of Tuition | Currency |
    | Degree Type | Choice (choices: *Masters*, *Bachelor* )
    | Fulltime | Yes/No |
    | Major | Text |
    | Other Scholarships | Multiple lines of text |

    :::image type="content" source="media/tutorial-multistep-forms/create-table.png" alt-text="Creating a table to use with multistep forms in Data workspace.":::


1. Once you have created the tables, you will need to create forms for each step of your process. 

    > [!TIP]
    > - See [How to create and modify Dataverse forms by using the Data workspace](../configure/data-workspace-forms.md) on how to create Dataverse forms.
    > - A good practice is to name your forms to correspond to each step of your multistep process.
    > - To display columns in the form but not allow users to update, configure the columns to be read-only when creating the forms.

    Create the following four forms and arrange the columns on the form. As each form is created, select **Publish form**.

    | Form name | Columns on form |
    | - | - |
    | Application Step 1 | Scholarship, Applicant name |
    | Application Step 2 | Scholarship (read-only), Applicant name (read-only), Degree Type, Major, Fulltime, Class Level, Stem |
    | Application Step 3 | Scholarship (read-only), Applicant name (read-only), Cost of Tuition, Other Scholarships |
    | Application Step 4 | Scholarship (read-only), Applicant name (read-only), Consent |

    :::image type="content" source="media/tutorial-multistep-forms/create-forms.png" alt-text="Creating forms to use with multistep forms in Data workspace.":::

1. You should now have a series of forms to use in your multistep process.

    :::image type="content" source="media/tutorial-multistep-forms/dataverse-forms.png" alt-text="A list of forms in the Data workspace.":::

### Add a multistep form component to a page

Now that we have our table and forms, we can create a multistep form on a webpage.

1. Go to the **Pages** workspace and add a new page or edit an existing page. For more information on creating webpages, see [Create and design pages](first-page.md).

1. Select the **Multistep form** from the selection of components.

1. If other multistep forms exist on your site, you will be given the option to add them to your page. We will create a new multistep form for our tutorial, Select **+ New multistep form** from the dialog. Otherwise, proceed to the next step.

1. You will see the **Add a multistep** form window. Enter in **Application** (or other name) for the **Form name**. Select **OK**.

1. There will be no steps in the form. Select **+ Add the first step** to add the first step.

    :::image type="content" source="media/tutorial-multistep-forms/add-multistep-form.png" alt-text="A blank multistep form added to a webpage.":::

1. In the **Add step** window, enter in **Application Step 1** as the **Step name**, select **Application** (or whatever you named your table) in the **Choose a table** field, and select **Application Step 1** in the **Select a form** field.

1. Choose the **More options** side tab and note that the **Data from this form:** option is automatically set to **Create a new record**. In our example for the first step we will be creating a new Dataverse record. Note that in subsequent steps we will be modifying a record and this option will be different. 

1. Select **OK**.

1. Select **+ Add step**.

1. In the **Add step** window, enter in **Application Step 2** as the **Step name**, the **Application** table (or whatever table you choose earlier) should be already selected in the **Choose a table** field, and select **Application Step 2** in the **Select a form** field.

1. Choose the **More options** side tab and note that the **Data from this form:** option is automatically set to **Update an existing record**. In our example for the second step will continue to add details to the Dataverse record created in the first step.

    > [!NOTE]
    > Depending on your unique processes, you may be creating or updating Dataverse records at different steps in the process.

1. Select **OK**

1. Continue to add the remaining two steps, **Application Step 3** and **Application Step 4** following the instructions above.

    :::image type="content" source="media/tutorial-multistep-forms/add-steps.png" alt-text="Adding steps to the multistep form.":::

### Edit field properties

You can modify some of the field properties on your multistep form in the design studio. Let's make a field required, update the label and add a description.

1. Select a field on the multistep form component on the page.

1. Select **Edit field**.

1. In the **Edit field** window, change the **Field label** to another value. Select **Make this field required** and select **Show a description**. Enter some instructions in the **Description** field.

    :::image type="content" source="media/tutorial-multistep-forms/edit-field.png" alt-text="Editing field properties.":::

1. Select **OK**.

### Add table permission

By default visitors to the site will not be able to access the multistep form. In our example, we would only want to allow authenticated users to fill in the multistep form.

For new forms, a banner will appear prompting you to add permissions. If you have already configured permissions for the table used in your multistep form, you can select the ellipse (**...**)

1. Select **+ New permission**.

1. The table permission is provided a name, the table selected and the **Access type** set to **Global access** by default. The **Write** and **Create** permissions will be selected so site visitors can use the form.

1. Select **+ Add roles** and select **Authenticated Users** as the default role. 

    :::image type="content" source="media/tutorial-multistep-forms/add-table-permissions.png" alt-text="Adding table permissions to the application table.":::

1. Select **Save**.

## Testing your multistep form

At this point you can try out your multistep form.

1. Select **Preview**, followed by **Desktop**.

1. When the home page appears, select **Sign in** and sign in with a site user. See [Provide access to external audiences](../security/external-access.md) for more information.

1. Select the page where you placed your multistep form component.

1. If you encounter any issues, review the configuration in design studio and review each step.

1. Once you have successfully submitted the form, return to the design studio.

1. Select **Data**, then select the **Application** table (or whatever you had named your table) and confirm that you can see that records were created using the multistep form process.

## Add conditional and redirect steps to your multistep form

If you need to add conditional logic to your multistep form, you first need to identify the condition by adding the Dataverse column logical name and the evaluation you want to perform. The logical name of a column can be found by viewing the column configuration in [Data workspace](../configure/data-workspace-tables.md).

In our example below, we'll check to see if an applicant is pursuing a Masters degree. If a user is pursuing an advanced degree, they'll be directed to extra steps. Other applicants will skip that step. Feel free to add a condition based on your own business processes.

We will add a redirect step at the end of the process to navigate the user back to the home page.

Conditional and redirect steps are configured in the [Portal Management app](../configure/portal-management-app.md).

1. In the design studio, on the multistep form, select the dropdown listing all the steps of the multistep form, choose the **Portal Management App** link.

    :::image type="content" source="media/tutorial-multistep-forms/portal-management-app.png" alt-text="Launch Portal Management app.":::

1. You should be in the Portal Management app in the metadata record for your multistep form. Select the **Form Steps** tab.

1. Select **+ New Form Step**.

1. Give the step a name (e.g. *Check degree type*).

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







1. You can view the information collected and updated in your advanced form by going to the [Data workspace](../configure/data-workspace-tables.md?#table-designer) table designer, selecting the table, and viewing the data.


