---
title: "Tutorial: Add a multi-step form to your page"
description: Learn how to add multi-step forms to your Power Pages.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 04/21/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Add a multi-step form to your page

Advanced forms are a powerful way to collect and update information in Dataverse from a page.  

Advanced forms extend basic forms by:

- Allows data collection or update process to be broken up over multiple steps.
- Provides interactive conditions to direct a user down different paths of data updates.
- Session tracking allows a user to pick up where they left off when following a data update process.

An advanced form is composed of an advanced form record and a series of steps.

:::image type="content" source="media/tutorial/advanced-form-diagram.png" alt-text="A diagram of an advanced form.":::

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create an advanced form
> * Create Advanced form options
> * Add an advanced form to a page

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).

> [!NOTE]
> When creating an advanced from, it is important to plan the steps first.  This will make the configuration process easier.  Establish the individual steps and any conditional branches to the multi-step process.


## Create an advanced form 

In the steps below, we'll create an advanced form.  This advanced form will allow users to authenticate before creating an application.  Users will also be able to pick up where they left off and apply multiple times.  

> [!NOTE]
> You'll need to adjust these steps to reflect your own business requirements.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. In the design studio, create/edit an existing form.
1. Go to the **Portal Management app**.
1. In **Advanced forms**, create a new Advanced forms record.
    :::image type="content" source="media/tutorial/new-advanced-forms-record.png" alt-text="Active Advanced Forms inside the Portal Management App.":::
1. Specify the configurations.
    - Set **Authentication required** to **Yes**.
    - Set **Start new session on load** to **No**.
    - Set **Multiple records per user permitted** to **Yes**.
    :::image type="content" source="media/tutorial/advanced-form-config.png" alt-text="New Advanced Form configurations.":::

### Add advanced form steps

1. In the **Advanced form steps tab**, create a **new Advanced from step record**.
        :::image type="content" source="media/tutorial/new-advanced-form-steps.png" alt-text="New advanced form steps menu option in Portal Management app.":::
1. Specify the configurations.
    - Set **Type** to **Load Form**.
    - Select the **Target Table name** from the drop-down menu.
    :::image type="content" source="media/tutorial/advanced-form-step-config.png" alt-text="Configurations for the new advanced form step in Portal Management app.":::
1. In the **Form Definition** tab, set the **Mode** to **Insert**.
:::image type="content" source="media/tutorial/new-advanced-form-step-mode.png" alt-text="Form Definition mode configuration set to insert.":::
1. Scroll down the page and select the **Form Name** from the drop-down menu.
:::image type="content" source="media/tutorial/advanced-form-definition-form-name.png" alt-text="Specifying the form name in the Form Definition field for the New Advanced Form Step.":::  
1. Scroll down the page and select the **Portal User Lookup Column** from the drop-down menu.
:::image type="content" source="media/tutorial/advanced-form-portal-user-lookup-column.png" alt-text="Specifying the Portal user lookup column.":::

#### Adding conditions to your advanced form

If you need to add conditional logic to your advanced form, you'll need to identify the condition by adding the Dataverse schema name and the evaluation you want to perform.

In the steps below, we'll check to see if an applicant is pursuing a Masters degree. If a user is pursuing an advanced degree, they'll be directed to extra steps.  Other applicants will skip that step.

1. In the **Advanced form steps tab**, create a **new Advanced from step record**.
        :::image type="content" source="media/tutorial/new-advanced-form-steps.png" alt-text="New advanced form steps menu option in Portal Management app.":::
1. Specify the configurations.
    - Set **Type** to **Condition**.
    - Select the **Target Table name** from the drop-down menu.
    :::image type="content" source="media/tutorial/advanced-form-type-condition.png" alt-text="Set configurations for an advanced form step of type condition.":::
1. Select the Condition tab and enter the condition.
:::image type="content" source="media/tutorial/advanced-form-specify-condition.png" alt-text="Text entry field for a condition on an advanced form step.":::

Repeat the instructions outlined until you've created the number of steps needed for your business process.

## Create advanced form options
<!-- Introduction paragraph -->
1. <!-- Step 1 -->
1. <!-- Step 2 -->
1. <!-- Step n -->

## Add an advanced form to a page

## Next steps

Advance to the next article to learn how to configure site authentication to allow users to sign in using Azure AD B2C.
> [!div class="nextstepaction"]
> [Next steps](tutorial-setup-site-authentication.md)
