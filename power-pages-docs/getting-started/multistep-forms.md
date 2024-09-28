---
title: Multistep forms
description: Learn how to add multistep forms to your Power Pages site.
author: pranita225
ms.topic: conceptual
ms.custom: 
ms.date: 05/15/2024
ms.subservice:
ms.author: prpadalw
ms.reviewer: danamartens
contributors:
    - pranita225
---

# Add a multistep form

While you can use a [form](add-form.md) to collect data in Power Pages sites, a **multistep form** allows you to create a form with multiple steps. Use a multistep form when you want to collect user input through multiple forms that use different components.

> [!NOTE]
>
> - Multistep forms were called advanced forms earlier.
> - Some features of multistep forms still need to be configured using the Portal Management app. Learn more: [Define multistep form properties](../configure/multistep-form-properties.md).

## Create new multistep form

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select **Edit** on the site you want to add a page to.

1. Add a section on any page.

    You can use [Copilot to add multistep forms to your Power Pages site (preview)](multistep-forms-copilot.md). For more information, go to [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md).

1. Choose **Multistep form** from component library.

    :::image type="content" source="media/add-multistep-form/multistep-form-component.png" alt-text="Screenshot of menu to select a component from available options.":::

1. Select **+ New multistep form**. Alternatively, you can also choose an existing multistep form (if a maker created one previously).

    :::image type="content" source="media/add-multistep-form/add-multistep-form.png" alt-text="Screenshot of Add a multistep form.":::

1. If necessary, edit the form name, and configure the form options with the following criteria.

    :::image type="content" source="media/add-multistep-form/multistep-form-setup.png" alt-text="Screenshot of Setup menu for multistep form.":::

    | Option                            | Description                                                                                                                         |
    |-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | Show progress indicator           | Enable or disable   progress indicator when submitting a multistep form. More information: [Progress indicator](#progress-indicator)                       |
    | Add multiple entries per person | When enabled, allows the form to be submitted multiple times by same authenticated user. If you allow anonymous users to access the form, they can submit the form multiple times. |
    | On submit                         | You   can choose optionally to show a success message. You must enter the options   to redirect to a webpage and redirect to a URL. |
    | Captcha                           | You   can choose to show a captcha to anonymous users, authenticated users, or   both.                                              |
    | More options                      | From here, you can launch the form in Portal Management app for more   settings.                                          |

1. Select **+ Add the first step** or **+ Add step**.

    :::image type="content" source="media/add-multistep-form/add-step.png" alt-text="Screenshot of add the first step to the form.":::

1. Enter a name for the step, and then select a table and the form.

    :::image type="content" source="media/add-multistep-form/select-form.png" alt-text="Screenshot of add multistep form menu.":::

    |     Option            |     Description                                                                                              |
    |-----------------------|--------------------------------------------------------------------------------------------------------------|
    |     Step name         |     Name of the step.    |
    |     Choose a table    |     Select the table where the data is stored.                                                          |
    |     Select a form     |     Select one of the Dataverse forms available for   the selected table.                                    |
    |     Attachments       |     Configure attachments for the step. More   information: [Enable attachments](#enable-attachments)                             |
    |     More options      |     Allows you to [change step mode](#change-step-mode), enable or disable back button, and launch the Portal Management app from here for more settings. More information: [Configure more options](#configure-more-options). If you want to create a new table or a new form, use [Data workspace](use-data-workspace.md).                      |

1. Select **Ok**.

1. Add more steps by selecting **+ Add step** from the toolbar.

    :::image type="content" source="media/add-multistep-form/add-more-steps.png" alt-text="Screenshot of Add more steps to the multistep-form.":::

   Conditions and redirect steps aren't supported in maker studio. Go to the [Portal Management app](/power-apps/maker/portals/configure/configure-portal) to create or view conditions and redirect steps.

## Preview steps

You can preview all steps inside the design studio by selecting the step from the step dropdown in the toolbar.

:::image type="content" source="media/add-multistep-form/preview-steps.png" alt-text="Screenshot of the step dropdown option in the maker studio with the Course Details step selected.":::

## Enable attachments

You can enable notes attachment for any step. To enable notes attachment, go to **Step settings** > **Attachments** > select **Enable attachments**.

:::image type="content" source="media/add-multistep-form/enable-attachments.png" alt-text="Screenshot of the Add step menu options with Enable attachments selected from the Attachments options.":::

|     Option                           |     Description                                                                                                      |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------|
|     Enable attachments               |     Enables or disables attachments on the multiform   step.                                                         |
|     Attachment is required           |     Makes attachments mandatory or optional.                                                                         |
|     Allow multiple files             |     Allow more than one file to the multistep form.                                                                   |
|     Attachments display label        |     Label that appears on the form for attachment   upload.                                                           |
|     Max file size allowed (in KB)    |     File size in KB allowed for the upload. Maximum limit depends on the value set in the Dataverse.    |
|     File types allowed               |     Select one or more file types from the available   options that you want to allow for upload.                     |

## Configure more options

You can configure form mode, back button and open the step in Portal Management app for more configuration.

:::image type="content" source="media/add-multistep-form/more-options.png" alt-text="Screenshot of configure more options.":::

### Change step mode

Form can be added to a step in **create**, **update**, or **read-only** mode. Step mode defines if the user can give inputs to submit a form, or edit an existing form, or open a form in read-only mode.

You can change the mode for a step when adding it, or from the **Step settings** > **More options** in the toolbar once the step is created.

:::image type="content" source="media/add-multistep-form/step-mode.png" alt-text="Screenshot of step mode that defines whether the step is to create, update, or read-only.":::

> [!NOTE]
>
> - By default, the first step is added in create mode and additional steps are added in edit mode.
> - Different steps within a single multistep form can have different step modes.

### Display back button

Enables or disables the back button when moving through different multistep form steps.

### Open Portal Management app

Opens Portal Management app for more configuration.

## Progress indicator

A progress indicator shows you the step that you're currently on within a multistep form. You can change the progress indicator type and position.

Select Edit indicator to modify the progress indicator.

:::image type="content" source="media/add-multistep-form/progress-indicator.png" alt-text="Screenshot of the Edit progress indicator window inside the maker studio.":::

## Enable table permissions

When you add a new form, you're prompted to set permission to allow users to interact with the form.

:::image type="content" source="media/add-multistep-form/table-permissions.png" alt-text="Screenshot of the new table permissions options inside the maker studio.":::

Table permissions settings default to **create** and **append to**, but you need to assign web roles and save the settings. Child table permission for the **note (annotations)** table, which contains the attachments, are created automatically.  

## See also

[Tutorial: Add a multistep form to your page](tutorial-add-multi-step-form.md)
