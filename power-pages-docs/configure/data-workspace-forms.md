---
title: Create and modify forms using Data Workspace
description: Learn how to use Data Workspace to create Dataverse forms.
author: pranita225
ms.topic: conceptual
ms.custom: 
ms.date: 04/22/2022
ms.subservice:
ms.author: prpadalw
ms.reviewer: ndoelman
contributors:
    - pranita225
    - nickdoelman
    - ProfessorKendrick
---

# How to create and modify Dataverse forms using data workspace

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Forms tab displays the forms referenced in the basic forms and all other forms in the environment. It only shows **main** form type that is supported in portals. 

The [Data workspace](..\getting-started\use-data-workspace.md) allows you to create and modify Dataverse table forms directly in the Power Pages design studio.

## Use Data workspace

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select a site and choose **Edit**.

1. On the left toolbelt, select **Data**.

## Table form designer

In the **Data** panel, under the **Tables in this site** section, you will see a list of tables that are used in basic forms created in the site. The **Other tables** section is a list of all Dataverse tables in the environment.

## Create or modify a form

1. Select the table that you want to either create or modify a form for from **Tables in this site** or **Other tables**.

1. Select the **Forms** tab from the table designer.

1. To create a new form, select **New form**.

    1. Enter a name and a description for your form.

    1. Select **Create**.

1. To modify an existing form, select the form from **Forms in this site** or **Forms available for this table**. 

    :::image type="content" source="media/data-workspace/form-designer.png" alt-text="Form designer.":::

1. The form will appear in the form designer which is the same designer used for [model-driven Power Apps](/power-apps/maker/model-driven-apps/form-designer-overview). 

1. The form can now be configured by adding fields, arranging fields, tabs, and sections.

## Form designer overview

The form designer provides a modern WYSIWYG authoring experience when you work modifying and creating forms. The forms can be used to add a form component to a page on your site.

Changes to the form are instantly reflected in the preview. An always available property pane makes the common task of updating properties quick and easy. Updates to properties are also instantly reflected in the form preview. The columns pane with searching and filtering capabilities helps makers quickly find and add columns to the form. 

The form designer interface has the following areas: 

### Command bar

| Item | Description |
| - | - |
| Back | Go back to table designer |
| Add field | Open the tables column pane which allows you to search and select a column to place on the form. You also have the option to create a new table column. |
| Add component | Open the components pane which allows you to search and select form components such as tab and section layouts, input components and related data views. |
| Undo/Redo | Allows for undo and redo of the last action/edit taken on the form |
| Cut | Cut a component from the form |
| Paste | Pastes a component on the form |
| Delete | Deletes a component from the form |
| Save | Saves the form |
| Publish form | Publishes the form and makes it available to add as a form to a page. |

### Other features

| Item | Description |
| - | - |
| Property pane | Displays properties of the selected element, and also allows you to make changes. |
| Preview size switcher | Changes the size of the form preview helping you to see how the form will appear on various screen sizes. |
| Show hidden | Displays hidden columns in the form preview area. By default, this option is turned off and hidden columns don't appear on the form preview and are visible only from the tree view pane. When enabled, columns that are hidden are indicated in the form preview area. |
| Zoom slider | Zooms in or out of the form preview helping you take a closer look. |
| Fit to width | Quick action to fit the form preview to the available width. |

## See also

[Add a form to a page](../getting-started/add-form.md)