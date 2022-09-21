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

Multistep forms allows you to create a form with multiple steps.

> [!NOTE]
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

    - Continue with prepopulated name or give it a name of your choice
    
    :::image type="content" source="media/multistep-forms/multistep-form-setup.png" alt-text="Setup menu for multistep form.":::

1. Select **+ Add the first step** or **+ Add step**.

    :::image type="content" source="media/multistep-forms/add-step.png" alt-text="Add the first step to the form.":::

1. Provide a name for the step.

    :::image type="content" source="media/multistep-forms/select-form.png" alt-text="Add multistep form menu.":::

    - Select **Dataverse table**.

    - Select **Dataverse form**.

1.  Choose **Ok**.

1. Select **+ Add step** and repeat the process for additional steps.

    > [!NOTE]
    > By default, the first step is added in create mode and additional steps are added in edit mode.  You can change the mode for a step when adding it, or from the Step settings option in the toolbar once the step is created.  You can also enable note attachment for any step.

## Preview steps

You can preview all your steps in the maker studio.  To preview a step, select the step from the dropdown in the toolbar.  

> [!NOTE]
> Conditions and redirect steps are not supported in maker studio. To create or see conditions, or to redirect steps, use the Portal Management app. 

## Edit progress indicator

You can edit the progress indicator or form fields in-context.

## Enable table permissions

When you add a new form, you'll be prompted to set permission to allow users to interact with the form. 

> [!NOTE]
> Table permissions settings default to **create** and **append to**, but you'll need to assign web roles and save the settings.Child table permission for the **note (annotations)** table, which contains the attachments, will be created automatically.  

### See also

[Tutorial: Add a multistep form to your page](tutorial-add-multi-step-form.md)