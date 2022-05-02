---
title: "Tutorial: Display data securely on your site"
description: Learn how to set up table permissions and link to web roles.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 05/02/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Display data securely on your site 

[Add your introductory paragraph]

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create table permissions
> * Set access type and privileges
> * Add web roles

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).

## Create table permissions

When you create a list on a web page you, you won't be able to see the data. Power Pages has data security enabled by default.  Use the steps below to learn how to configure table permissions to view data.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. In the pages workspace on the page where you have a list component, select the component and choose the **Permissions** button.
1. Select **New table permissions**.
1. Give table permission a name.  
1. Select a Dataverse table.
1. Set the access type to **Global**.
1. Set the permissions to **Read**.
1. Choose **Anonymous** and **Authorized user** for the web roles.
1. Now that table permissions are set, view the page by selecting **Preview**.

> [!NOTE]
> You can give the table permission any name, but ideally it should be descriptive.  

## Set access type and privileges

When you configure a list or a form in Power pages, by default your users won't have access to the information in Dataverse.  To grant your users access, you'll need to configure Table permissions.

There are multiple access types within Power Pages.

|Access type  |Description  |
|---------|---------|
|Global access |Users will be able to view all records from the Dataverse table. Limit the use of this access type wherever possible as it provides the greatest access to data.|
|Contact access |         |
|Account access |         |
|Self access | Unique to the Contact table.  This access level allows users who are logged in to access their related contact record in Dataverse.  This permission is typically used to update a contact's profile record. |


1. <!-- Step 1 -->
1. <!-- Step 2 -->
1. <!-- Step n -->

## Add web roles
<!-- Introduction paragraph -->
1. <!-- Step 1 -->
1. <!-- Step 2 -->
1. <!-- Step n -->

## Next steps

Advance to the next article to learn how to 