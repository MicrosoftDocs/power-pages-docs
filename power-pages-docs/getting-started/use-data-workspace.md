---
title: Overview of Data Workspace
description: Learn how to use Data Worksapce.
author: pranita225
ms.topic: conceptual
ms.custom: 
ms.date: 05/16/2022
ms.subservice:
ms.author: prpadalw
ms.reviewer: ndoelman
contributors:
    - pranita225
    - nickdoelman
    - ProfessorKendrick
---
# Overview of data workspace

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

**Data workspace** lets you easily visualize, and manage business data for the site with tables, forms, and lists. All the data and changes are stored in Dataverse. You can create and edit tables for the site and create new or edit existing model-driven forms and views.

:::image type="content" source="media/data-workspace/table-designer.png" alt-text="Data workspace table designer.":::

Makers can create Portals basic form, advanced form and lists using forms and views created in data workspace.

## Tables

In the data workspace left pane, you can see **Tables in this site** which contextually displays all tables being used in the site. **Other tables** displays all Dataverse tables in the environment and those that are used in basic forms created in the site. You can also create a new table or open an existing one in the table designer to add new columns and rows in **Table** data tab.

For more info: [Create and modify tables using Data Workspace](../configure/data-workspace-tables.md)

## Views

Views are a subset of table data. Create a view to select specific table columns & rows that you would like to display in a site. The Views tab displays views being used in the site lists and all other views in the environment associated with the respective table. It only shows view types that are supported in portals. Clicking on an existing view (or creating a new one) launches the **Power Apps view designer** where you can define the view. Views are a foundation of the [list](add-list.md) component that can be added to pages.

For more info: [Create and modify views using Data Workspace](../configure/data-workspace-views.md)

## Forms

Forms tab displays the forms being used in the basic forms used in the site and all other forms in the environment associated with the respective table. It only shows **main** form type that is supported in portals. Clicking on an existing form or creating a new one, launches the **Power Apps form designer** where you can add form fields, components and much more. The form designer only provides features and properties supported by portals. To access all form features, navigate to **Power Apps form designer** from the command bar.

Forms created here can be used to add a [form](add-form.md) to a page or used in creating [advanced forms](advanced-forms.md).

For more info: [Create and modify forms using Data Workspace](../configure/data-workspace-forms.md)

## Next Steps
[Create and modify tables using Data Workspace](../configure/data-workspace-tables.md)
