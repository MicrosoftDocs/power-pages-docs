---
title: Add forms
description: Add forms to your page in Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/24/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Add a form

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

A form is a data-driven configuration that collects data in Power Pages sites. Forms on pages are created from Dataverse table forms. Dataverse table forms can be created by using the [Data workspace](use-data-workspace.md) or from [model-driven apps created in Power Apps](/power-apps/maker/model-driven-apps/form-designer-overview/). You can use them on pages or with [lists](add-list.md) to build a complete web application.

To add a form:

1. Open the [design studio](use-design-studio.md) to edit the content and components of the site.

1. Go to the **Pages** workspace.

1. Select the page you want to edit.

1. Select the section you want to add the form component to.

1. Hover over any editable canvas area, and then select the **Form** icon.

    :::image type="content" source="media/first-page/add-component-to-section.png" alt-text="The add component menu.":::

1. You can choose either to create a new form or use an existing form (if a maker has created one previously).

   If you choose to create a new form, you'll need to enter the following criteria.
  
    :::image type="content" source="media/first-page/add-form.png" alt-text="Add a form to a page.":::

    | Option | Description |
    | ----------- | ----------- |
    | Choose a table | Choose the table where data will be stored. |
    | Select a form | Select one of the Dataverse forms available for the selected table. |
    | Name your copy of the selected form| Give your copy of the form a name. |
    | Data | You can choose to have the data that's entered by a user create a new record, update existing records, or make the data read-only. |
    | On submit | You can choose optionally to show a success message. You must enter the options to redirect to a webpage and redirect to a URL. |
    | Captcha | You can choose to show a captcha to anonymous users, authenticated users, or both.

    > [!NOTE]
    > You'll need to enable [table permissions](../security/table-permissions.md) to ensure that users will be able to interact with the data on the forms.

1. You can select the ellipsis (**...**) to duplicate the form, move it up or down within the section, or delete it.

### See also

[Create and modify forms](../configure/data-workspace-forms.md)<br />
[Tutorial: Add a form to a page](tutorial-add-form-to-page.md)