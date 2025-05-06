---
title: Overview of the Data workspace
description: Learn how to use the Data workspace.
author: pranita225
ms.topic: concept-concept-article
ms.custom: 
ms.date: 02/05/2025
ms.subservice:
ms.author: prpadalw
ms.reviewer: danamartens
contributors:
    - pranita225
---
# Overview of the Data workspace

With the **Data** workspace, you can easily visualize and manage business data for the site with tables, forms, and lists. All the data and changes are stored in Microsoft Dataverse. You can create and edit tables for the site, and create new (or edit existing) model-driven forms and views.

:::image type="content" source="media/data-workspace/left-data-pane.png" alt-text="Data workspace table designer.":::

Makers create basic forms, advanced forms, and lists by using forms and views created in the Data workspace.

## Solutions

The Data workspace left pane settings feature lets you select any unmanaged solution where changes made in Data workspace are added. Newly created tables, columns, forms, and views are added to the selected solution. Newly created tables and columns get the prefix of the selected solution's publisher. By default, all changes are saved in the Common Data Services Default Solution. To change this setting, choose the dropdown and select any unmanaged solution in the environment.

:::image type="content" source="media/data-workspace/set-solution.png" alt-text="The set a solution view lets makers choose a solution from a dropdown menu of options.":::

For more information, go to [Solution concepts](/power-platform/alm/solution-concepts-alm).

## Tables

On the Data workspace left pane, **Tables in this site** contextually shows all tables used in the site. **Other tables** shows Dataverse tables in the environment and the tables used in basic forms created in the site. You can also create a new table or open an existing one in the table designer to add new columns and rows on the **Table data** tab.

For more information, go to [Create and modify tables using Data Workspace](../configure/data-workspace-tables.md).

## Views

Views are a subset of table data. Create a view to select specific table columns and rows to display in a site. The **Views** tab shows views used in the site lists and all other views in the environment associated with the respective table. It only shows view types supported in portals. Selecting an existing view (or creating a new one) opens the Power Apps view designer, where you can define the view. Views are a foundation of the [list](add-list.md) component that can be added to pages.

For more information, go to [Create and modify views by using the Data workspace](../configure/data-workspace-views.md).

## Forms

The **Forms** tab shows the forms used in the site and all other forms in the environment associated with the respective table. It only shows the **main** form type that's supported in portals. Selecting an existing form (or creating a new one) opens the Power Apps form designer, where you can add form fields, components, and more. The form designer only provides features and properties that are supported in portals. To access all form features, go to the Power Apps form designer from the command bar.

Forms created here can be used to [add a form to a page](add-form.md) or to create [multistep forms](multistep-forms.md).

For more information, go to [Create and modify forms by using the Data workspace](../configure/data-workspace-forms.md).

## Next steps

[Create and modify tables by using the Data workspace](../configure/data-workspace-tables.md)
