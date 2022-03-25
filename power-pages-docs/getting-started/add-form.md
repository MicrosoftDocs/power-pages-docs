---
title: Add forms
description: Learn how to add forms to your Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 03/15/2022
ms.subservice: portals
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Add Form

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Form is a data-driven configuration that collects data in the portal without the need for a developer to surface the form in the portal. Forms are created in Microsoft Dataverse. You can use them on webpages in the portal or in conjunction with lists to build out complete web applications.

To add a form:

1. Open the [Power Apps portals Studio](/powerapps/maker/portals/portal-designer-anatomy) to edit the content and components of the portal.

1. Ensure that the toggle for New Design Studio is on and then navigate to the Pages Workspace.

1. Select the page you would like to edit.

1. Select the Section which you would like to add Component into.

1. Hover to any editable canvas area and choose the {add words instead of icon photo}.

1. Select **Form.** You can select either to create a new form or use an existing form (if maker has created one previously)

1. If maker creates a new form, then the following box will appear  
    :::img type="content" source="media/first-page/add-form" alt-text="Menu options for editing buttons.":::

| Option | Description |
| ----------- | ----------- |
| Choose a table | Allows you to choose a table where data will be stored. |
| Select a form | Selects one of the dataverse forms available for the selected table. |
| Name your copy of the selected form| Allows you to name a copy of the form. |
| Data | You can choose to have data entered by a user create a new record, update existing records, or make the data read-only. |
| On submit | You can choose optionally choose to show a success message.  You must enter options to redirect to a webpage and redirect to a URL. |
| Captcha | You can choose to show a captcha to anonymous users, authenticated users, or both.

Select the ellipse icon to duplicate the form, move it up/down within the section, or delete.