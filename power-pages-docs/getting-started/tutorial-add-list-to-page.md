---
title: "Tutorial: Add a list to your page"
description: Learn how to add lists to your Power Pages.
author: pranita225
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 02/05/2025
ms.subservice:
ms.author: prpadalw 
ms.reviewer:
contributors:
    - pranita225
---

# Tutorial: Add a list to your page

In this tutorial, you'll learn how to display a list business information to your users from Microsoft Dataverse on a page in your site.  

First, you'll need to create a table (or choose an existing table) in Dataverse to store your business information. You'll also need to configure a view from the table that will define the columns and structure for your list. You'll add the list component to a page. For security reasons, your users won't yet be able to view the information until we define table permissions in the following tutorial.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create a table
> * Create a view
> * Add a list to the page

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- Complete the [Add and design a page](tutorial-add-webpage.md) tutorial.

## Create a table

This video provides an overview of the steps to create a table.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=7a4a2df7-fa5e-46ff-ba52-f16a4bfe8745]

Use the steps below to create a table. 

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select the **Data** icon on the left navigation.

    - Select the **New table** button.
    
    :::image type="content" source="media/tutorial/new-table.png" alt-text="Create a new table button.":::

1. Give the table a name and select **Create**.

    :::image type="content" source="media/tutorial/create-new-table.png" alt-text="Create a new table window.":::

1. Select **New column**. 

    :::image type="content" source="media/tutorial/new-column.png" alt-text="Add a new column button.":::

1. Enter a name and a data type, then choose **Save**.

    :::image type="content" source="media/tutorial/new-column-settings.png" alt-text="New column settings.":::

1. Select the space under the name field and enter your data.  

    :::image type="content" source="media/tutorial/enter-text-name.png" alt-text="Enter text for column.":::

>[!NOTE]
> You can use the tab key to move to the next column and enter additional data.  You can also use the tab key to navigate to the next row and add additional records.

 For more information, see [How to create and modify Dataverse tables using data workspace](../configure/data-workspace-tables.md).

## Create a view

This video provides an overview of the steps to create a view.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=db19432b-f0dc-4d86-8a71-8b11db44c030]

Use the steps below to create a custom view for the table you created. 

1. Select the table you created in the steps above.

    - Select **Views** and choose **New view**.
    
    :::image type="content" source="media/tutorial/new-view.png" alt-text="The new view.":::

    - Enter a name for the view.

    :::image type="content" source="media/tutorial/name-view.png" alt-text="Enter a name for the view.":::

1. Add the application data and status reason columns to the view.

1. Select **Save** and choose **Publish**.

1. Select **Views** to show the available views for the table.

For more information, see [Create and modify Dataverse views using data workspace](../configure/data-workspace-views.md).

## Add a list to the page

This video provides an overview of the steps to add a list to a page.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=43ed8812-e09c-433e-be10-a3c667823cb4]

Use the steps below to add a list to a web page so you can view information stored in Dataverse.

1. Inside the design studio, choose the option to **Create a new page**.

1. Add a name for the page.

1. Choose the **Start from blank** layout.

    - Select **Add**.
    - Select **List**.

1. Fill in the details.

    - Choose the table and view you'd like from the dropdown menus.
    
        :::image type="content" source="media/first-page/add-list.png" alt-text="Add list options.":::

1. Select **Preview**.

    :::image type="content" source="media/tutorial/preview-icon.png" alt-text="The preview icon.":::

    > [!NOTE]
    > When you first view the page, you will see a message displayed that you do not have permissions to view the data.  Security is very important when building sites.  

    :::image type="content" source="media/tutorial/list-no-access.png" alt-text="A list view without access to data.":::

For more information, see [Add a list](../getting-started/add-list.md).

## Next steps

In order for the site users to see data, we need to create table permissions to allow users to view data securely.

> [!div class="nextstepaction"]
> [Display data securely on pages](tutorial-display-data-securely.md)
