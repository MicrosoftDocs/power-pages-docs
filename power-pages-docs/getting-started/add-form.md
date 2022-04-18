---
title: Add forms
description: Learn how to add forms to your Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/18/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Add Form

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

A form is a data-driven configuration that collects data in Power Pages sites. Forms on pages are created from Dataverse table forms. Dataverse table forms can be created using the [data workspace](use-data-workspace.md) or from [model-driven Power Apps](/power-apps/maker/model-driven-apps/form-designer-overview/). You can use them on pages or in conjunction with [lists](add-list.md) to build a complete web application.

To add a form:

1. Open the [design studio](use-design-studio.md) to edit the content and components of the site.

1. Navigate to the **Pages workspace**.

1. Select the page you would like to edit.

1. Select the section which you would like to add the form component.

1. Hover to any editable canvas area and choose the **Form** icon to add the form component.

1. You can select either to create a new form or use an existing form (if maker has created one previously).

1. If you choose new form, then you will need to enter the following criteria:
  
    :::image type="content" source="media/first-page/add-form.png" alt-text="Menu options for editing buttons.":::

    | Option | Description |
    | ----------- | ----------- |
    | Choose a table | Allows you to choose a table where data will be stored. |
    | Select a form | Selects one of the dataverse forms available for the selected table. |
    | Name your copy of the selected form| Allows you to name a copy of the form. |
    | Data | You can choose to have data entered by a user create a new record, update existing records, or make the data read-only. |
    | On submit | You can choose optionally choose to show a success message.  You must enter options to redirect to a webpage and redirect to a URL. |
    | Captcha | You can choose to show a captcha to anonymous users, authenticated users, or both.

1. You can select the ellipse icon to duplicate the form, move it up/down within the section, or delete.