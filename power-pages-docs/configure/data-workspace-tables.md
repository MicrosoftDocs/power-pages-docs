---
title: Create and modify tables by using the Data workspace
description: Learn how to use the Data workspace to create Dataverse tables.
author: pranita225
ms.topic: conceptual
ms.custom: 
ms.date: 03/06/2025
ms.subservice:
ms.author: prpadalw
ms.reviewer: dmartens
contributors:
    - pranita225
    - DanaMartens
    - nageshbhat-msft
---

# How to create and modify Dataverse tables by using the Data workspace

You use the [data workspace](..\getting-started\use-data-workspace.md) to create and modify Microsoft Dataverse tables directly in the Power Pages design studio. 

## Use the Data workspace

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select a site, and then select **Edit**.

1. On the left tool belt, select **Data**.

## Table designer

On the left pane of the **Data** workspace, the **Tables in this site** section lists tables that are used in basic forms created in the site. The **Other tables** section lists all Dataverse tables in the environment.

:::image type="content" source="media/data-workspace/table-designer.png" alt-text="Data workspace table designer.":::

## Create a new table

1. Next to **Data**, select **+ Table**.

1. Select **New table**.

1. In the window that appears, enter a name for your table. By expanding **Advanced settings**, you can modify the plural name of your table.

    > [!NOTE]
    > The table will be created as part of the *default* solution.
    > Power Pages does not currently support [Dataverse Elastic Tables](/power-apps/maker/data-platform/create-edit-elastic-tables).

1. Select **Create**.

The table will be created in Dataverse. You can now begin to configure your table.

## Configure a table

1. From the **Tables in this site** or **Other tables** section, select the table you want to edit.

1. In the table designer, modify any existing data rows. In addition, the following options are available.

| Action | Description |
| - | - |
| New row | Create a blank row and enter in a new data row. |
| New column | Create a new data column for the table. You'll need to specify the name, data type, and format along with other column configuration options. For a complete list of Dataverse column types, go to [Types of columns](/power-apps/maker/data-platform/types-of-fields). |
| Show/hide columns | Select which columns you want to be visible or invisible in the table designer. |
| Refresh | Reload the table data. |
| Edit table properties | Change the name and other advanced properties of the table. |

## Next steps

[Create and modify Dataverse views by using the Data workspace](data-workspace-views.md)<br>
[Create and modify forms by using the Data workspace](data-workspace-forms.md) <br>
[Create and modify virtual tables by using the Data workspace](data-workspace-virtual-tables.md)

### See also

- [Tables in Dataverse](/power-apps/maker/data-platform/entity-overview/)

