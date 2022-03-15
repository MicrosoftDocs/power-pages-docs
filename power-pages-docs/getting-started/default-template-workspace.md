---
title: Data Workspace for Default template
description: Learn how to utilize the Data workspace with Default template.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 03/14/2022
ms.subservice: portals
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Data workspace for Default Template

The default design template comes with a rich set of sample tables and data you can edit from within the maker studio. Select the **Data** workspace on the Toolbelt to look at the tables within the solution.

This template uses the Feedback table to store any feedback that has been received by a user that visits the site. The feedback form is located under the **Contact us** page. From here, you can add new records or edit existing records in the Feedback table or create new tables (or views or forms).

## Styling workspace for Default Template

To edit the styling of the default template, select the **Styling** icon on the Toolbelt. Here you can select any of the preset themes in the Themes workspace and see how it styles the canvas on the right. As you choose different themes you may notice the styling menu changes accordingly. You can make changes to the preset theme in the styling menu and save changes.

## Set up workspace for Default Template

Navigate to the **Set up** workspace on the Toolbelt to configure settings that will ensure your site is protected and secure. Here you can set up identity provider for sign-in/sign-up flow and set table permissions.

By default, local sign in and Azure Active directory identity providers are enabled. You can enable other identity providers like Facebook, LinkedIn by selecting the Configure option. Click the + New provider to add a new identity provide if you like to configure a new one.

Based on the authentication supported, a user can sign in or register to gain access to the site.

The Set up workspace also includes table permissions. These allow a maker to define the access type, privileges, and assign roles. By default, this template has table permissions set to Global access, create privilege and roles set to Anonymous users, authenticated users, and administrators (i.e. all three roles can create a record in Feedback table which is performed upon Contact us form submission)

