---
title: How to use Data Workspace
description: Learn how to use Data Worksapce.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 03/10/2022
ms.subservice: portals
ms.author: ndoelman
ms.reviewer:
contributors:
    - nickdoelman
    - ProfessorKendrick
---
# How to use data workspace

**Data workspace** lets you easily model, visualize and manage business data for the site with tables, forms, and lists. All the data and changes are stored in Dataverse. You can create and edit tables for the site and create new or edit existing model-driven forms and views. 

## Learn more about data workspace

In Data workspace left pane, you can see all Dataverse tables in the environment & those that are used in basic forms, lists created in the site. You can also create a new table or open an existing one in the table designer to add new columns and rows in Table data tab.

To find details regarding supported column types, please refer to appendix section.

## Views

Views are a subset of table data. Create a view to select specific table columns & rows that you would like to display in a site. The Views tab displays views referenced in the lists and all other views in the environment. It only shows view types that are supported in portals. Clicking on an existing view (or creating a new one) launches the **Power Apps view designer** where you can define the view. Views are a foundation of portals lists.

## Forms

Forms tab displays the forms referenced in the basic forms and all other forms in the environment. It only shows **main** form type that is supported in portals. Clicking on an existing form or creating a new one, launches the **Power Apps form designer** where you can add form fields, components and much more. The form designer only provides features and properties supported by portals. To access all form features, navigate to **Power Apps form designer** from the command bar.

## Appendix

### Column types

You can add the following column types to a table:

- text

- number

- email

- URL

- choice

- date

- lookup

- phone

- decimal

- formula

- yes/no

The following column types are not available to add to tables in Data workspace:

- multiline text

- date & time

- ticket symbol

- duration

- time-zone

- language

- currency

- customer

- file

- floating point number

- image

- table relationship

To access these functionalities, you can open a Table in Power Apps using **Edit in Power Apps** feature.