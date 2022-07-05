---
title: "Tutorial: Create, update, and read Dataverse information on pages"
description: Learn how to create a set of pages to create, read, and update Dataverse data in Power Pages.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 07/04/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Create, update, and read Dataverse information on pages

The ability to dynamically interact with Dataverse information is one of the key features of Power Pages. Users visiting a site can perform actions such as viewing a list of programs, registering their children, scheduling a meeting or applying for a building permit. All of the information can be tracked in Dataverse, and can then be accessed by other Power Platform services such as Power Apps, Power Automate, or Power BI.

In this tutorial, you'll build a simple web application in Power Pages that will allow authenticated users the ability to create, read, update and delete records in Dataverse. You can use this as a foundation to build your own Dataverse powered sites.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create a Dataverse table
> * Create a Dataverse view
> * Create a Dataverse form
> * Configure table permissions to allow you to read, create and update records
> * Add a list to the page
> * Add a page with a form to create records
> * Add a page with a form to view/edit records
> * Update the list to allow your to navigate to pages to create records and view/edit records

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).

## Create a Dataverse table

In this section you will use the Data workspace to create a Dataverse table. A table is used to store information about specific objects. A scholarship, an application, or company are some examples of tables. A table is make up of a series of columns. A column is a specific piece of information about the object, like name, description, application date, or color. 

Use the steps below to create a table and columns.

1. Go to [Power Pages](https://make.powerpages.microsoft.com).

1. Select the Data icon on the left navigation.

1. Select the new table **(+)** button, to the right of the **Tables in this site** heading.

1. Give your new table an appropriate name.

1. Select **Create** to create the table in Dataverse.

    :::image type="content" source="media/tutorial-dataverse/create-table.png" alt-text="Create a new table.":::

1. To add a column to the table, choose **+ New column**. Enter a **Display name** and select the **Data type** as select the other options. Select **Save**.

    :::image type="content" source="media/tutorial-dataverse/add-columns.png" alt-text="Add new columns to a new table.":::

1. Repeat the previous step until you have created all the columns required for your table.

## Create a Dataverse view

A Dataverse view is essentially a query to display specific rows and columns of data from a Dataverse table. When you create a view, you specify certain criteria such as which columns to show, how the records are sorted, and how the rows are filtered (for example, you can show only records that have certain criteria like a date happening in the future).

In this section you will use the Data workspace to create a Dataverse view.

1. Select the table from the list of tables in **Data** workspace to which you want to create a new view.

1. Select the **Views** tab.

1. Select **New view**.

1. Enter in the name of your view and optionally, a description.

1. Select **Create**.

    :::image type="content" source="media/tutorial-dataverse/create-view.png" alt-text="Add a new view to a new table.":::

1. The view designer will appear. You can add columns to the view and adjust the width.

1. You can select to sort by specific table columns in the **Sort by...** section on the right side flyout panel.

1. You can also choose to configure specific row filtering options by selecting **Edit filters...** on the **Filter by** section on the right side flyout panel.

1. When you are finished configuring the view, select **Save** and then **Publish view**.

    :::image type="content" source="media/tutorial-dataverse/configure-view.png" alt-text="Configure the new view to a new table.":::

## Create a Dataverse form

In this section you will use the Data workspace to create a Dataverse table.

## Configure table permissions
## Add a list to the page
## Add a page with a form to create records
## Add a page with a form to view/edit records
## Update the list to allow your to navigate to pages to create records and view/edit records


## Next steps

