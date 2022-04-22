---
title: Create and modify tables using Data Workspace
description: Learn how to use Data Workspace to create Dataverse tables.
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

# How to create and modify Dataverse tables using data workspace

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The [Data workspace](..\getting-started\use-data-workspace.md) allows you to create and modify Dataverse tables directly in the Power Pages design studio. Tables to be used to create powerful web applications in Power Pages.

## Use Data workspace

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select a site and choose **Edit**.

1. On the left toolbelt, select **Data**.

## Table designer

In the **Data** panel, under the **Tables in this site** section, you will see a list of tables that are used in basic forms created in the site. The **Other tables** section is a list of all Dataverse tables in the environment.

:::image type="content" source="media/data-workspace/table-designer.png" alt-text="Data workspace table designer.":::

## Create a new table

1. Select **+** beside the **Tables in this site** label.

1. A window will appear, enter in a name for your table. Expanding the **Advanced settings** will allow you to modify the plural name of your table.

    > [!NOTE]
    > The table will be created as part of the *default* solution.

1. Select **Create**.

The table will be created in Dataverse. You can now begin to configure your table.

## Configure a table

1. Select the table you want to edit from either **Tables in this site** or **Other tables**.

1. The table will appear in the designer and allow you to modify any existing data rows. In addition, the following options are available;

| Action | Description |
| - | - |
| New row | Creates a blank row and allows you to enter in a new data row. |
| New column | Creates a new data column for the table. You will need to specify the name, data type and format along with other column configuration options. See [Types of columns](/power-apps/maker/data-platform/types-of-fields) for a complete list of Dataverse column types. |
| Show/hide columns | Allows you to select which columns are visible or not in the table designer. |
| Refresh | Reloads the table data. |
| Edit table properties | Allows you to change the name and other advanced properties of the table. |

## Next steps

[Create and modify Dataverse views using data workspace](data-workspace-views.md)<br>
[Create and modify forms using Data Workspace](data-workspace-forms.md)

## See also

[Tables in Dataverse](/power-apps/maker/data-platform/entity-overview/)

