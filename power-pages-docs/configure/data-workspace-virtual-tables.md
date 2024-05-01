---
title: Create and modify virtual tables by using the Data workspace 
description: Learn how to use the Data workspace to create virtual tables in Microsoft Dataverse.
author: pranita225
ms.topic: conceptual
ms.custom: 
ms.date: 05/01/2024
ms.subservice:
ms.author: prpadalw
ms.reviewer: kkendrick
contributors:
    - pranita225
    - ProfessorKendrick
    - DanaMartens
---

# Create and modify virtual tables by using the Data workspace 

[Virtual tables](/power-apps/maker/data-platform/create-edit-virtual-entities) integrate data from external data sources by seamlessly representing that data as tables in Microsoft Dataverse, without data replication. Solutions, apps, flows, and more can use virtual tables as if they're native Dataverse tables. Virtual tables allow for full create, read, update, and delete privileges unless the data source they're connecting to specifically forbids it.

You can create virtual tables using the following virtual connector providers inside Data workspace:

- [SQL Server](/connectors/sql/)
- [Sharepoint](/connectors/sharepoint/)
- [Microsoft Fabric (preview)](/power-apps/maker/data-platform/azure-synapse-link-view-in-fabric)

:::image type="content" source="media/data-workspace-virtual-tables/create-virtual-table.png" alt-text="Create virtual table using Power Pages design studio from the Data workspace":::

## Create a new virtual table

1. Next to **Data**, select **+ Table**.

1. Select **New table from external data**.

1. Select any existing connection, if available. Otherwise, select **Add connection** to add a SharePoint or a SQL Server connection.

    If selected **Add connection**, select **Open connections** and [add a connection in Power Apps](/power-apps/maker/canvas-apps/add-data-connection). Once created, return to Power Pages design studio browser tab, and select **Refresh** to view and select the newly added connection.

1. Select **Next**, and enter the required connection details. For example, a SharePoint site, followed by selecting a list from the available options.

1. If necessary, update the following table properties: such as the **Display name**, **Plural name**, **Schema name**, and **Primary field**.

    | Property name | Description |
    | - | - |
    | Display name | The name used to identify your virtual table. |
    | Plural name | The logical name Dataverse uses for the virtual table, which includes the solution publisher prefix. |
    | Schema name (read-only) | This is the schema name of the column in the data source. This property is read only. |
    | Primary field | This is the text value to be used when looking up records on your virtual table. Only string fields may be selected. A primary key is a required field and chosen by Dataverse. |

1. If necessary, update the following column properties:

    | Property name | Description |
    | - | - |
    | Display name | The name that's used to identify your column. |
    | Schema name | The logical name for the column that includes your solution publisher prefix. You can also use **Quick Format Names** option from the top of the wizard to provide suggested name changes if you have a large number of fields that include prefixed values from your SQL server such as &lt;tablename&gt;.&lt;column name&gt;. For example, *Database12.Products* would change to **Products**. |

1. Select **Next**.

1. Review the configuration summary between the external data source, and the table is created in Dataverse. Select **Back** or **Edit configuration of table** to make any necessary changes.

1. Select **Finish**.

Once the table is created, you're taken directly to your new virtual table in the [table designer](data-workspace-tables.md#table-designer) where you can view your data and begin working with it.

## Manage existing connections

If you have already created custom or OData connectors, you can manage them from [Power Apps](https://make.powerapps.com). More information: [Manage connections](/power-apps/maker/canvas-apps/add-manage-connections)

### See also

- [Manually create virtual tables in Dataverse and integrate with Power Pages](virtual-tables.md)
- [Tables in Dataverse](/power-apps/maker/data-platform/entity-overview/)
