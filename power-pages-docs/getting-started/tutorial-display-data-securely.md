---
title: "Tutorial: Display data securely on your site"
description: Learn how to set up table permissions and link to web roles.
author: gitanjalisingh33msft
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 02/10/2025
ms.subservice:
ms.author: gisingh 
ms.reviewer: danamartens
contributors:
    - gitanjalisingh33msft
---

# Tutorial: Display data securely on your site

In the previous tutorial, you added a list to a page; however, users wouldn't be able to view any data. Power Pages has security enabled by default to protect your business data. This tutorial explains how to create table permissions and associate them with web roles so visitors to your site can only interact with the information you allow.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create table permissions
> * Set access type and privileges
> * Add web roles

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- Complete the [Add and design a page](tutorial-add-webpage.md) tutorial.
- Complete the [Add a list to a page](tutorial-add-list-to-page.md) tutorial.

## Create table permissions

This video provides an overview of the steps to create table permissions.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=43e87d4c-b01e-4b60-adfc-958ed1fdebc6]

To learn how to configure table permissions to view data:

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In the pages workspace, on the page with a list component, select the component and choose the **Permissions** button.

1. Select **New table permissions**.

1. Give table permission a name.  

1. Select a Dataverse table.

1. Set the access type to **Global**.

1. Set the permissions to **Read**.

1. Choose **Anonymous** and **Authorized user** for the web roles.

    :::image type="content" source="media/tutorial/create-table-permissions.png" alt-text="Create a table permission.":::

1. Now that table permissions are set, view the page by selecting **Preview**.

1. You should now see a list of Dataverse records on the page.

> [!NOTE]
> You can give the table permission any name, but ideally it should be descriptive.  

## Set access type and privileges

When you configure a list or a form in Power Pages, by default, users don't have access to the information in Dataverse. Sometimes, you might want to limit what data a particular set of users can access. You can do control access with a combination of table permissions and security roles.

If your table in Dataverse has a relationship with a Contact or Account table, you can filter the records based on that relationship.

In the following example, we created a table that has a lookup to the contact table.

This video provides an overview of the steps to set access types and privileges.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=e8f6fda9-5102-4f0b-b9af-1b324529de93]

1. Create a page with a list showing records that have a relationship to the contact table.

    > [!NOTE]
    > Go to [Tutorial: Add list to a page](tutorial-add-list-to-page.md) for details on how to a list to page. Create a table with a lookup to the contact table.

1. From the list on the page, choose on the **Permission** button.

1. Select to create a new table permission.

1. Give the table permission a name and choose **Table**.

1. Select Access type **Global access**.

1. Set permissions to **Read**.

1. Assign the Table permission to the **Authenticated user** web role.

1. Select **Save**.

    :::image type="content" source="media/tutorial/create-table-permissions-application.png" alt-text="Screenshot showing creation of a table permission for a table with contact lookup.":::

1. Preview the site and sign-in. For purposes of this tutorial, you can sign in using **Microsoft Entra ID**.

1. View the page on the site. When any user signs in, they should see **all** the data in the table.

    :::image type="content" source="media/tutorial/list-view.png" alt-text="Logged in user viewing all data on a page.":::

1. In our example, we would only want to show records that related to the currently signed-in user. Return to the design studio, select the list on the page and select permissions.

1. Modify the existing table permission and change the **Access Type** to **Contact Access**.

1. You need to specify the relationship between your table and the contact table.

    > [!NOTE]
    > If you don't see a relationship, you need to define a lookup to the contact table using the [Data workspace](use-data-workspace.md). Create or update some records that are related to the contact record you're using to sign-in to the site.

    :::image type="content" source="media/tutorial/filtered-list.png" alt-text="Screenshot of a table filtered by the currently signed in user.":::

1. Preview the site and sign-in. You now should only see records that are related to the contact that signed in to the site.

    :::image type="content" source="media/tutorial/filtered-list-contact.png" alt-text="Screenshot of a list view only showing related records.":::


### More information

There are several different access types and privileges in Power Pages.  
For more information, see: 
 - [Assign table permissions](../security/assign-table-permissions.md) 
 - [Provide access to external audiences](../security/external-access.md)

## Add web roles

In our examples so far, we assigned the table permissions to the default **Authenticated Users** and **Anonymous Users** web roles.

This video provides an overview of using web roles.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=192007af-dcc6-40fa-b683-0eb36e27a584]

We can also create our own custom web roles to further limit access to data and pages to certain site visitors.

1. In the design studio, select the ellipses **...** from the side menu and select **Portal Management** to open the Portal Management app.

1. In the Portals Management app, under the **Security** section, select **Web Roles**.

1. Select **New** to create a new web role and give it a descriptive name. Leave the **Authenticated Users** and the **Anonymous Users** roles set to **No**.

    :::image type="content" source="media/tutorial/create-webrole.png" alt-text="Create web role.":::

1. Save the web role record.  

1. Select **Related** and choose **Contacts**. Select **Add existing contacts** choose a few contacts.

    :::image type="content" source="media/tutorial/add-contacts-webrole.png" alt-text="Add contacts to web role.":::

    > [!NOTE]
    > Site users are stored as Contacts records.

1. Within the design studio on a list or a form, choose the permissions button and select a table permission, then assign the custom web role.

    :::image type="content" source="media/tutorial/assign-student-webrole.png" alt-text="Screenshot that shows assigning the student web role.":::

    > [!NOTE]
    > You need to restart the design studio or clear the browser cache (ctrl + F5) to see the new web role.

1. Preview the site and note that only users logged in are able to view the data on a form or list.

## Next steps

Showing data in a list view to the correct audience is an important feature of Power Pages. The next tutorial will cover adding a form to a page to allow users to create and edit business data.

> [!div class="nextstepaction"]
> [Add a form to a page](tutorial-add-form-to-page.md)
