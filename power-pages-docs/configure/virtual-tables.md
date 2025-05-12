---
title: Integrate virtual tables with Power Pages
description: Learn how to integrate virtual tables with Power Pages.
author: nageshbhat-msft
ms.topic: how-to
ms.custom: 
ms.date: 05/21/2024
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - nageshbhat-msft
---

# Integrate virtual tables with Power Pages

A [virtual table](/power-apps/maker/data-platform/create-edit-virtual-entities) is a special type of table that doesn't have a physical representation in the Microsoft Dataverse but rather represents a query or view of the external data source. They enable the integration of external data source by seamlessly representing data as a table without data replication.

> [!NOTE]
> This article explains how to create virtual tables in Dataverse manually, and then, them in Power Pages. You can also create virtual tables directly from the Data workspace in the design studio. More information: [Create and modify virtual tables by using the Data workspace](data-workspace-virtual-tables.md)

## Steps to integrate virtual tables in Power Pages 

Using a virtual table in Power Pages follows a similar process to creating tables in Data workspace and using Dataverse views and forms to create web page list and form components.

1. Create a virtual table in Dataverse

1. Set up virtual table relationships

1. Configure a web page with components using a virtual table

## Create a virtual table in Dataverse

There are various ways to create a virtual table in Dataverse. Currently, Power Pages support virtual tables created using the providers listed below.

### Finance and operations virtual tables 

[Dynamics 365 Finance and Operations](/dynamics365/fin-ops-core/fin-ops/) is a business application that is designed to help organizations manage their financial, operations, and supply chain. Finance and operations apps are a virtual data source in Dataverse, and enable full create, read, update, and delete (CRUD) operations from Dataverse.  Learn how to [surface finance and operations virtual tables](/dynamics365/fin-ops-core/dev-itpro/power-platform/power-portal-reference) in Power Pages. 

### Virtual connector providers

Virtual connectors are built using Power Platform Connectors, which are pre-built connectors that provide a way to interact with external systems. Virtual connectors streamline creation experience by automating some of the creation and removing the need to use code to create the virtual tables.

To learn how to create virtual table in Dataverse, go to [create a virtual table using virtual connector](/power-apps/maker/data-platform/create-virtual-tables-using-connectors?tabs=sql#steps-to-create-a-virtual-table-in-power-apps-for-sql-or-sharepoint).

### Custom virtual table data providers

Using Microsoft Dataverse Data SDK, .NET Developers have the option of creating custom virtual table data providers to help integrate external data source types that are not supported by an existing data provider. Each data provider is composed of a reusable set of Dataverse plug-ins that implement the supported CRUD operations.

> [!NOTE]
> - Power Pages requires that all tables have an ID attribute, this ID is known as a unique identifier and the value must be a guid.
> - While retrieving the virtual table from external data source in plugin, explicitly set AllColumns attribute to true.

To learn how to create virtual table using custom data provider in Dataverse, go to [Custom virtual table data providers](/power-apps/developer/data-platform/virtual-entities//custom-ve-data-providers#steps-to-use-a-custom-data-provider).

### Business Central virtual tables

[Dynamics 365 Business Central](/dynamics365/business-central/) is a complete enterprise resource planning (ERP) software solution for mid-sized organizations. Business Central Virtual tables enables create, read, update, delete (CRUD) operations from Microsoft Dataverse. More information: [Business Central virtual tables with Power Pages](/dynamics365/business-central/dev-itpro/developer/power-pages-on-virtual-tables-overview)

## Set up virtual table relationship

Setting up a table relationship to a contact or account table is an optional step if you're configuring virtual table permission for **Global** type access. **Account** and **contact** access types provides limited access to table records for the website user. Learn more about securing the data using [table permissions](../security/table-permissions.md).

To configure the account and contact scope, you need to create a many-to-one relationship with virtual table to account and contact table respectively. To learn more about virtual table relationships, go to [Setting up a virtual table relationship](/power-apps/maker/data-platform/setup-virtual-table-relationships).

## Configure web page using virtual table

Once the virtual table is created in Dataverse, you can use to create a [list](../getting-started/add-list.md), [form](../getting-started/add-form.md), and [multistep form](../getting-started/multistep-forms.md) components using the same process as using a standard Dataverse table.

## Unsupported virtual tables and providers

The following virtual tables and providers are not supported for use with Power Pages;

- The [Microsoft Entra user virtual table](/power-apps/developer/data-platform/aaduser-entity).

## Limitations

Dataverse virtual tables have a set of limitations that also apply when using in Power Pages, For more details go to [Limitations and troubleshooting virtual tables](/power-apps/maker/data-platform/limits-tshoot-virtual-tables?tabs=sql).

### See also

[Create and modify virtual tables by using the Data workspace](data-workspace-virtual-tables.md)
