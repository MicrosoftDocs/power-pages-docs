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

Form is a data-driven configuration that collects data in the portal without the need for a developer to surface the form in the portal. Forms are created in Microsoft Dataverse. You can use them on webpages in the portal or in conjunction with lists to build out complete web applications.

To add a form:

1. Open the [Power Apps portals Studio](https://docs.microsoft.com/en-us/powerapps/maker/portals/portal-designer-anatomy) to edit the content and components of the portal.

1. Ensure that the toggle for New Design Studio is on and then navigate to the Pages Workspace.

1. Select the page you would like to edit.

1. Select the Section which you would like to add Component into.

1. Hover to any editable canvas area and click ![components icon ](media/image3.png).

1. Select **Form.** You can select either to create a new form or use an existing form (if maker has created one previously)

1. If maker creates a new form, then the following box will appear  
    ![Graphical user interface  text  application  email Description automatically generated](media/image31.png)

**Form**

1. **Choose a table**: The name of the table in which data will be stored.

2. **Select a form**: select one of the Dataverse forms available for the selected table. To modify the fields or tabs within the Dataverse forms, maker need to access Data Workspace

3. **Name your copy of the selected form**: Name of the form.

**Data**
Maker could select if data entered by the user into the form should create a new record, update an existing one or if data is just read-only.

**On submit** Select one of the following options:

-   Show success message: Requires a message to be displayed to the user on successful submission of the form. You can also select Hide form on success to hide the form upon successful submission.

- Redirect to webpage: Redirects the user to the selected webpage in the portal. This field is required.

- Redirect to URL: Redirects the user to the specified URL. This field is required.

**Captcha** Maker can decide if they would like to show captcha to anonymous users or authenticated users or both.

Select the ellipse icon to duplicate the form, move it up/down within the section, or delete.