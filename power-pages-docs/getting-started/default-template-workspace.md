---
title: Data Workspace for default template
description: Learn how to utilize the Data workspace with default template.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 03/16/2022
ms.subservice: portals
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Data workspace for default template

The default design template comes with a rich set of sample tables and data you can edit from within the maker studio. Select the **Data** workspace on the toolbelt to look at the tables within the solution.

::: image="content" source="media/default-template/data.png" alt-text="The data workspace within maker studio." :::

This template uses the feedback table to store any feedback that has been received by a user that visits the site. The feedback form is located under the **Contact us** page. From here, you can add new records or edit existing records in the Feedback table or create new tables (or views or forms).

## Styling workspace for default template

To edit the styling of the default template, select the **Styling** icon on the toolbelt. Here you can select any of the preset themes in the **Themes** workspace and see how it styles the canvas on the right.

::: image type="content" source="media/default-template/styling.png" alt-text="The styling options for maker studio." :::

As you choose different themes you may notice the styling menu changes accordingly. You can make changes to the preset theme in the styling menu and save changes.

## Set up workspace for default template

Navigate to the **Set up** workspace on the toolbelt to configure settings that will ensure your site is protected and secure.

::: image type="content" source="media/default-template/set-up.png" alt-text="The set-up workspace on the maker studio toolbelt." :::

Here you can set up identity provider for sign-in/sign-up flow and set table permissions.

By default, local sign in and Azure Active directory identity providers are enabled. You can enable other identity providers like Facebook, LinkedIn by selecting the Configure option. Choose + New provider to add a new identity provider.

Based on the authentication supported, a user can sign in or register to gain access to the site.

The Set up workspace also includes table permissions. These allow a maker to define the access type, privileges, and assign roles. By default, this template has table permissions set to Global access, create privilege and roles set to Anonymous users, authenticated users, and administrators (i.e. all three roles can create a record in feedback table which occurs when the Contact us form is submitted).

::: image type="content" source="media/default-template/table-permissions.png" alt-text="The table permissions settings in maker studio." :::