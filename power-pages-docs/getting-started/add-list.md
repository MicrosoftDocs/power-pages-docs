---
title: Add lists
description: Learn how to add lists to your Power Pages.
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

# Add list

List is a data-driven configuration to render a list of records without the need for a developer to surface the grid in the portal. Lists use Dataverse views to display records on the portal.

To add a list:

1. Open the [Power Apps portals Studio](https://docs.microsoft.com/en-us/powerapps/maker/portals/portal-designer-anatomy) to edit the content and components of the portal.

1. Ensure that the toggle for New Design Studio is on and then navigate to the Pages Workspace.

1. Select the page you would like to edit.

1. Select the Section which you would like to add Component into.

1. Hover to any editable canvas area and click ![components icon ](media/image3.png).

1. Select **List.** You can select either to create a new list or use an existing list (if maker has created one previously)

1. If maker creates a new list, then the following box will appear  
    ![Graphical user interface  text  application  email Description automatically generated](media/image30.png)

    | List | Description |
    | ----------- | ----------- |
    | Choose a table | The name of the table the views are loaded from. |
    | Select Dataverse views | The view of the target table that will be rendered. To modify the columns within the view, you'll need to accss Data Workspace |
    | Name your copy of the selected list | The name of the list. |

    | Data | Description |
    | ----------- | ----------- |
    | Create a new record | Allows the user to create a new record. You'll need to select the target webpage/form/URL containing the new record. |
    | View details | Allows the user to view details.  You'll need to select the webpage/form/URL containing the details. | 
    | Delete record | Allows the user to delete the record. | 

## Settings

Maker can define the number of records to be displayed on each page and if user is allowed to perform a search.

Select the ellipse icon to duplicate the List, move it up/down within the section, or delete the list.