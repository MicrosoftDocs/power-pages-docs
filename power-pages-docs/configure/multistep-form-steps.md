---
title: Define multistep form steps for Power Pages
description: Learn how to create a multistep form steps for a multistep form on a website.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 04/06/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
    
---

# Define multistep form steps for Power Pages

The multistep form step provides the flow logic of the form's user experience such as steps and conditional branching. It also provided details about the rendering of a form and additional behavior.

Multistep form steps can also be defined using the design studio. For more information, see [Add a multistep form](../getting-started/multistep-forms.md). The details below are viewed and configured using the [Portal Management app](portal-management-app.md).

> [!NOTE]
> Multistep forms persists the history of the steps a user has visited in an object on an multistep form session table. If an multistep form's steps have been modified, previously created history data could now be stale. Anytime steps are changed, it is recommended that you delete all multistep form session records to eliminate miss match between sequence of steps logged in history and the current sequence.

Each multistep form will be presented on a website has one or more steps. These steps share some common properties, outlined below. Each Step contains a pointer (a lookup) to the next step, except for terminal steps. Terminal steps don't have a next time, and are thus the last step of the multistep form (because of conditional branching, there can be multiple terminal steps).

| Name     | Description                                    |
|----------|------------------------------------------------|
| Name     | A title used for reference.                    |
| Multistep Form | The Multistep Form associated with the current step. |
|Type|Available types:<br>[Load Form/Load Tab step type](load-form-step.md): displays properties of forms. <ul><li>[Load Form/Load Tab step type](load-form-step.md): displays properties of tabs.</li><li>[Conditional step type](add-conditional-step.md): displays properties for specifying expressions to be evaluated for conditional branching. </li><li>[Redirect step type](add-redirect-step.md): displays the settings appropriate for configuring a website redirection.</li></ul><br>For more information on the settings for these multistep  form step types, see their corresponding sections later.<br>**Note**: The first step can't be of type "Condition".|
| Next Step                 | The step that will follow the current step. This option will be blank for single-step single form.                                                                                                            |
| Target Table Logical Name | The logical name of the table associated with the form.                                                                                                                                               |
| Move Previous Permitted    | Indicates whether the user is given an option to navigate to the previous step in a multiple step multistep  form. Default is true. Uncheck to prevent the user from being able to move to the previous step. |
||

> [!NOTE]
> The step type of **Load User Control** is retired and no longer supported.

## Considerations for multistep  form steps

Multistep form steps can't be reused. If you try to use multistep form step again, you'll see the following message:

"The step \<multistep  form step name\> has already been used earlier in this form. Update the multistep form to use each step only once, and try again."

When that happens, ensure you use don't reuse multistep  form steps in a multistep form.

The following conditions are exempt from the limitation of multistep  form step reuse:

- When using "Next step if Condition fails" option in step type "Condition".
- When using different&mdash;Yes/No&mdash;branches.

### See also

- [Add a multistep form](../getting-started/multistep-forms.md)
- [Portal Management app](portal-management-app.md)  
- [Basic forms](basic-forms.md)  
- [Load Form/Load Tab step type](load-form-step.md)  
- [Redirect step type](add-redirect-step.md)  
- [Conditional step type](add-conditional-step.md)  
- [Add custom JavaScript](add-custom-javascript.md)  

