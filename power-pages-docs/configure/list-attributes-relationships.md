---
title: List attributes and relationships
description: Learn about attributions and relationships for a list of records on a website.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 02/11/2025
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft

---

# List attributes and relationships

The following are attributes when configuring a **list** component using the [Portal Management app](portal-management-app.md).

|              Name              |                                                                                                                                                                                        Description                                                                                                                                                                                         |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Name              |                                                                                                                                                                The descriptive name of the record. This field is required.                                                                                                                                                                 |
|          Table Name           |                                                                                                                                               The name of the table from which the Saved Query view will be loaded. This field is required.                                                                                                                                               |
|              View              |                                                                          The Saved Query view(s) of the target table that is to be rendered. This field is required. If more than one view has been specified, the webpage will contain a drop-down list to allow the user to switch between the various views.                                                                           |
|           Page Size            |                                                                                                                                            An integer value that specifies the number of records per page. This field is required. Default: 10                                                                                                                                             |
|   Web Page for Details View    |                                                                                                        An optional webpage that can be linked to for each record. The ID Query String Parameter Name and record ID will be appended to the query string of the URL to this webpage.                                                                                                        |
|      Details Button Label      |                     The text displayed for the details view button if **Web Page for Details View** has been specified. Default: View details <br>**Note**: For each language pack installed and enabled for the Microsoft Dataverse environment, a field will be available to enter the message in the associated language.                      |
|      Web Page for Create       |                                                                                                                                                             An optional webpage that will be the target of the create button.                                                                                                                                                              |
|      Create Button Label       |                              The text displayed for the create button if **Web Page for Create** has been specified. Default: Create <br>**Note**: For each language pack installed and enabled for the Dataverse environment, a field will be available to enter the message in the associated language._                              |
| ID Query String Parameter Name |                                                                                                                                           A parameter name provided in the query string of the URL to the Web Page for Details View. Default: id                                                                                                                                           |
|        Empty List Text         |  **Deprecated**.  The message displayed when there are no records.<br>**Note**: For each language pack installed and enabled for the Dataverse environment, a field will be available to enter the message in the associated language.                                                           |
|     Portal User Attribute      |                                                                                      An optional lookup attribute on the primary table that represents the website user record, either contact or system user, to which the current user's ID can be applied to filter the data rendered in the list.                                                                                      |
|       Account Attribute        |                                                                                       An optional lookup attribute on the primary table that represents an account record to which the current user contact's parent Customer account value can be applied to filter the data rendered in the list.                                                                                       |
|       Website Attribute        |                                                                                                          An optional lookup attribute on the primary table that represents the website to which the current website's ID can be applied to filter the data rendered in the list.                                                                                                          |
|         Search Enabled         | An optional Boolean value indicating whether search should be enabled. A text box will be rendered to allow users to do a quick search for records. Use the asterisk (\*) wildcard character to search on partial text. The search appends Or condition filters for each column of the primary table in the view to the view's existing predefined filter conditions to query and return the resulting records. <br> **Note**: This option doesn't search within related table columns. |
|    Search Placeholder Text     |                                                                                                                                                      An optional string used as the label displayed in the text box on initial load.                                                                                                                                                       |
|      Search Tooltip Text       |                                                                                                                                             An optional string used as the tooltip displayed when the user points to the **Search** text box.                                                                                                                                              |

> [!IMPORTANT]
> When search is enabled for a list that includes large text columns, it negatively impacts performance when searching for records. To optimize performance, exclude large text columns from the list.
> Learn more about best practices and query anti-patterns in [Query anti-patterns](/power-apps/developer/data-platform/query-antipatterns?tabs=fetchxml#PerformanceLargeColumnSearch).

### See also

- [Lists overview](lists.md)
- [Portal Management app](portal-management-app.md)  
- [Redirect to a new URL](add-redirect-url.md)
