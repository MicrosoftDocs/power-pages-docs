---
title: Add a conditional step type
description: Learn how to add and configure a conditional step type for multistep form in Power Pages.
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

# Add a conditional step type

A multistep form step can be a **Condition** type that indicates the step should evaluate an expression. If the expression evaluates to true then the next step is displayed. If the expression evaluates to false and if the **Next Step If Condition Fails** has been specified, that step will be displayed. The current table is the target used to evaluate the expression against. **Record Source** defaults to the **Record Source** of the previous step.

## Attributes

| Name                         | Description                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Condition                    | The Conditional expression to be evaluated                                                                                                                                                                                           |
| Next Step if Condition Fails | The Conditional Step Type, unlike all others, has two Next Step lookups. The default Next Step lookup will be respected if the condition evaluates to true. This property sets the next step should the condition evaluate to false. |

The available operands are as follows:

| Operand(s)    | Type                   |
|---------------|------------------------|
| =, ==         | Equals                 |
| !=            | Not Equals             |
| &gt;          | Greater Than           |
| &lt;          | Less Than              |
| &gt;=         | Greater Than or Equals |
| &lt;=         | Less Than or Equals    |
| &             | And                    |
| \|             | Or                     |
| !             | Not                    |
| =\*, ==\*, ~= | Like                   |
| !=\*          | Not Like               |

## Format

The format of the expression is as follows:

`[entity attribute logical name] [operand] [value]`

Example:

`new_categorycode = 750101`

A condition can have multiple expressions. You can use parentheses to group nested expressions, for example:

- `new_categorycode = 750101 & gendercode = 2`

- `new_categorycode = 750101 & (gendercode = 2 | gendercode = 3)`

- `new_name = Jane Doe`

- `new_twooptionfield = true`

- `new_twooptionfield = false`

### See also

- [Portal Management app](portal-management-app.md)  
- [Define basic forms](basic-forms.md)  
- [Multistep form steps](multistep-form-steps.md)  
- [Load Form/Load Tab step type](load-form-step.md)  
- [Redirect step type](add-redirect-step.md)  
- [Add custom JavaScript](add-custom-javascript.md)  
