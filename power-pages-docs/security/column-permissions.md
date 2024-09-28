---
title: Set column permissions
description: Learn how to use permissions to restrict access to specific table columns when you use the Microsoft Power Pages portals Web API.
ms.date: 07/20/2023
ms.topic: how-to
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - nickdoelman
    - neerajnandwana-msft
ms.custom: bap-template
---

# Set column permissions

In Power Pages, [table permissions](table-permissions.md) apply security to individual Dataverse table records. You can apply column-level permissions to restrict access even further when you use the Power Pages Web API to work with your site's data. Column permissions apply only to the [portals Web API](../configure/web-api-overview.md).

 Column permissions are an optional configuration that you associate with [web roles](create-web-roles.md). Web roles can have any number of table permissions and column permissions. If a web role has multiple column permissions, they are all applied to the selected web role.

Table permissions are evaluated before column permissions. If a user has access to a table, then the table's column permissions are applied. If the user doesn't have access to the table, any column permissions the user has are ignored. When no column permissions are defined, the table permissions apply to all columns.

> [!Important]
> The column permissions feature requires portal host version 9.4.1.*x* or later and starter portal package version 9.3.2201.*x* or later.

Use the [Portal Management app](../configure/portal-management-app.md) to manage column permissions.

## Add column permissions to a web role

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, scroll down to the **Security** section and select **Web Roles**.

1. Select a web role.

1. Under **Related**, select **Column Permission Profiles**.

1. Select **Add Existing Column Permission Profile** and then:

    - To add an existing column permission to the web role, search for or browse to the record you want, and then select **Add**.

    - To add a new column permission profile record, select **+ New Record** > **Column Permission Profiles**. Enter or select the required information. Select **Save & Close**, and then select **Add**.

1. Select **Save**.

## Attributes and relationships

The following table describes the table permission attributes.

| Name | Description |
|------|-------------|
| Profile Name | The descriptive name of the table record; required |
| Table Name | The logical name of the table that contains the column; required |
| Website | The website associated with the table; required |
| All Column Permissions | Available permissions are **Create**, **Read**, and **Update**, in any combination |
| Column Permissions | The permissions to apply to the column; columns that aren't defined here follow the **All Column Permissions** setting |
| Web Roles | The web roles associated with the column permission profile |

The **All Column Permissions** setting allows you to limit the access users have to the column. You can select more than one value to "tune" access to particular columns. For example, the table permissions might grant Create and Read permissions on all columns. Use the **All Column Permissions** setting to further limit users to only Read permission on all columns.

In another example, you might want a specific web role to be able to read all contact columns and update the FirstName and LastName columns. In this case, you select Read for the **All Column Permissions** setting, and create column permission profiles for the FirstName and LastName columns with Read and Update permissions.

## Examples of table and column permissions

Let's look at some examples to understand how table and column permissions work together. In these examples, we have a contact table with the columns JobTitle and Salary.

| Scenario | Table permission | Site setting<br>**Webapi/Contact/Enabled** | Site setting<br>**Webapi/Contact/Fields** | Column permission |
|-|-|-|-|-|
| The user has no permissions to the columns. | Contact (Create, Read, Update) | TRUE |  |  |
| The user has no permissions to the columns. | Contact (Create, Read, Update) | FALSE |  |  |
| The user has no permissions to the columns. | Contact (none) | TRUE | * | **All Column Permissions:** Create, Read, Update<br/>**Column Permissions:** (none) |
| The user has all permissions to all columns. | Contact (Create, Read, Update) | TRUE | * |  |
| The user has no permissions to the columns. | Contact (Create, Read, Update) | TRUE |  | **All Column Permissions:** Create, Read, Update<br/>**Column Permissions:** (none) |
| The user can read JobTitle and create, read, and update all other columns. | Contact (Create, Read, Update) | TRUE | * | **All Column Permissions:** (none)<br/>**Column Permissions:**<br/>JobTitle: Read |
| The user can create, read, and update JobTitle and read all other columns.| Contact (Create, Read, Update) | TRUE | * | **All Column Permissions:** Read<br/>**Column Permissions:**<br/>JobTitle: Create, Read, Update |
| The user can create, read, and update JobTitle and Salary. | Contact (Create, Read, Update) | TRUE | JobTitle, Salary |  |
| The user can create, read, and update JobTitle and Salary and has no permission to other columns. | Contact (Create, Read, Update) | TRUE | JobTitle, Salary | **All Column Permissions:** Create, Read, Update<br/>**Column Permissions:** (none) |
| The user can create, read, and update JobTitle and Salary. | Contact (Create, Read, Update) | TRUE | JobTitle, Salary | **All Column Permissions:** (none)<br/>**Column Permissions:**<br/>JobTitle: Create, Read, Update<br/>Salary: Create, Read, Update |
| The user can create, read, and update JobTitle and has no permission to Salary.| Contact (Create, Read, Update) | TRUE | JobTitle | **All Column Permissions:** (none)<br/>**Column Permissions:**<br/>JobTitle: Create, Read, Update<br/>Salary: Create, Read, Update |
| The user can create, read, and update JobTitle and read Salary. | Contact (Create, Read, Update) | TRUE | JobTitle, Salary | **All Column Permissions:** (none)<br/>**Column Permissions:**<br/>JobTitle: Create, Read, Update<br/>Salary: Read |

### See also

[Assign table permissions](assign-table-permissions.md)  
[Create web roles for Power Pages](create-web-roles.md)  
[Portals Web API overview](../configure/web-api-overview.md)
