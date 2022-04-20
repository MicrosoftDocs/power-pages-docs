---
title: Add lists
description: Learn how to add lists to your Power Pages.
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

# Add list

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

List is a data-driven configuration to render a list of records without the need for a developer to surface the grid in the portal. Lists use Dataverse views to display records on the portal.

A list is a data-driven configuration that display data in a grid view on Power Pages sites. Lists on pages are created from Dataverse table views. Dataverse table views can be created using the [data workspace](use-data-workspace.md) or from [model-driven Power Apps](/power-apps/maker/model-driven-apps/accessing-view-definitions/). You can use them on pages or in conjunction with [forms](add-form.md) to build a complete web application.

To add a list:

1. Open the [design studio](use-design-studio.md) to edit the content and components of the page.

1. Select the page you would like to edit.

1. Select the section which you would like to add the list component.

1. Hover to any editable canvas area and select the **List** icon.

    :::image type="content" source="media/first-page/add-component-to-section.png" alt-text="The add component menu.":::

1. You can select either to create a new list or use an existing list.

1. If you choose new list, then you will need to enter the following criteria:
 
    :::image type="content" source="media/first-page/add-list.png" alt-text="The add a list to a page.":::

    | List | Description |
    | ----------- | ----------- |
    | Choose a table | The name of the table the views are loaded from. |
    | Select Dataverse views | The view of the target table that will be rendered. To modify the columns within the view, you'll need to access Data Workspace |
    | Name your copy of the selected list | The name of the list. |

    | Data | Description |
    | ----------- | ----------- |
    | Create a new record | Allows the user to create a new record. You'll need to select the target webpage/form/URL containing the new record. |
    | View details | Allows the user to view details.  You'll need to select the webpage/form/URL containing the details. | 
    | Delete record | Allows the user to delete the record. | 

    | Settings | Description |
    | - | - |
    | Number of records per page | Determines how many records will be displayed per page. Note that if the table contains more records, navigation controls will appear for the end user to view the next or previous set of records. |
    | Enable search in list | turns on the search feature for the list |

    > [!NOTE]
    > You will need to enable [table permissions](../security/table-permissions.md) to ensure that users will be able to view the data on the lists.

1. You can select the ellipse icon to duplicate the list, move it up/down within the section, or delete.

## See also



