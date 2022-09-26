---
title: Multistep forms
description: Learn how to add multistep forms to your Power Pages site.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 09/20/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Add a multistep form

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE[powerapps-info](../includes/cc-powerapps-info.md)]

Multistep forms allow you to create a form with multiple steps.

> [!NOTE]
>
> - Multistep forms were formerly called advanced forms.
> - Some features of multistep forms still need to be configured using the Portal Management App. More information: [Define advanced form steps for portals](/power-apps/maker/portals/configure/web-form-steps).

## Create new multistep form

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select **Edit** on the site you want to add a page to.

1. Add a section on any page.

1. Choose **Multistep form** from component library.

    :::image type="content" source="media/multistep-forms/multistep-form-component.png" alt-text="Menu to select a component from available options.":::

1. Select on **+ New multistep form**.

    :::image type="content" source="media/multistep-forms/add-multistep-form.png" alt-text="Add a multistep form.":::

    - Continue with pre-populated name or give it a name of your choice
    
    :::image type="content" source="media/multistep-forms/multistep-form-setup.png" alt-text="Setup menu for multistep form.":::

    

1. Select **+ Add the first step** or **+ Add step**.

    :::image type="content" source="media/multistep-forms/add-step.png" alt-text="Add the first step to the form.":::

1. Provide a name for the step.

    :::image type="content" source="media/multistep-forms/select-form.png" alt-text="Add multistep form menu.":::

    - Select **Dataverse table**.

    - Select **Dataverse form**.

1.  Choose **Ok**.

1. Add more steps by selecting **+ Add step** from the toolbar. 

    :::image type="content" source="media/multistep-forms/add-more-steps.png" alt-text="Add more steps to the multistep-form..":::

    > [!NOTE]
    > Conditions and redirect steps are not supported in maker studio. Go to the [Portal Management app](/power-apps/maker/portals/configure/configure-portal) to create or view conditions and redirect steps.


## Preview steps

You can preview all steps inside the maker studio by selecting the step from the step dropdown in the toolbar.

:::image type="content" source="media/multistep-forms/preview-steps.png" alt-text="The step dropdown option in the maker studio with the Course Details step selected.":::

## Step mode

You can change the mode for a step when adding it, or from the Step settings option in the toolbar once the step is created.

> [!NOTE] 
> By default, the first step is added in create mode and additional steps are added in edit mode.

## Enable notes attachment

You can enable notes attachment for any step. To enable notes attachment, go to **Step settings** > **Attachments** > select **Enable attachments**.

:::image type="content" source="media/multistep-forms/enable-attachments.png" alt-text="The Add step menu options with Enable attachments selected from the Attachments options.":::

## Progress indicator

A progress indicator shows you the step that you're currently on within a multistep form. You can change the progress indicator type and position.



Select Edit indicator to modify the progress indicator.

:::image type="content" source="media/multistep-forms/progress-indicator.png" alt-text="The Edit progress indicator window inside the maker studio.":::

## Enable table permissions

When you add a new form, you'll be prompted to set permission to allow users to interact with the form. 

:::image type="content" source="media/multistep-forms/table-permissions.png" alt-text="The new table permissions options inside the maker studio.":::

Table permissions settings default to **create** and **append to**, but you'll need to assign web roles and save the settings. Child table permission for the **note (annotations)** table, which contains the attachments, will be created automatically.  

### See also

[Tutorial: Add a multistep form to your page](tutorial-add-multi-step-form.md)