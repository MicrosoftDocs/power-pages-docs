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

In the steps below, you'll set Global access with Read permissions for an Authenticated user.

1. View a page that includes a view that you do not have permissions to view the data.
1. From a list, choose on the **Permission** button.
1. Select to create a new table permission.
1. Give the table permission a name and choose **Table**.
1. Select Access type **Global access**.
1. Set permissions to **Read**.
1. Assign the Table permission to the **Authenticated user** web role.
1. Select **Save**.
1. View the page on the portal. When a user logs in they should see all the data in the table.

> [!NOTE]
> There are several different access types and privileges in Power Pages.  
> For more information, see: <br> 
> - [Assign table permissions](../security/assign-table-permissions.md) <br>
> - [Provide access to external audiences](../security/external-access.md)

## Add web roles

When creating table permissions or page access permissions,these need to associate with a web role in order for portal visitors to be able to access the data or view a protected page.

1. From an existing list or form, select the **Permission** button and view a table permission.
1. Open the Portals Management app and view **Web Roles**.
1. Create a new web role and give it a descriptive name.  Do not set the Authenticated Users role or the Anonymous Users role.
1. Save the web role record.  
1. Select **Related** and choose a few contacts.
1. Within the studio on a list or a form, choose the permissions button and select a table permission, then assign the custom web role.

> [!NOTE]
> You'll need to clear the cache by hitting ctrl + F5 to view the new role.

## Next steps

Advance to the next article to learn how to 