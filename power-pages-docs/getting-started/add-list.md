---
title: Add lists
description: Create and add a list from views to your page in Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 10/08/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Add a list

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

A list is a data-driven configuration used to render a list of records without the need for a developer to surface the grid in the portal. Lists use Dataverse views to display records on the portal.

A list displays data in a grid view on Power Pages sites. Lists on pages are created from Dataverse table views. Dataverse table views can be created by using the [Data workspace](use-data-workspace.md) or from [model-driven apps created in Power Apps](/power-apps/maker/model-driven-apps/accessing-view-definitions/). You can use them on pages or with [forms](add-form.md) to build a complete web application.

> [!TIP]
> We've created a series of tutorials and videos for you to learn to use Power Pages and how create a view and add a list to a page. For more information, go to [Tutorial: Add a list to a page](tutorial-add-list-to-page.md).

To add a list:

1. Open the [design studio](use-design-studio.md) to edit the content and components of the page.

1. Select the page you want to edit.

1. Select the section you want to add the list component to.

1. Hover over any editable canvas area, and then select the **List** icon.

    :::image type="content" source="media/common/component-options.png" alt-text="The add component menu options.":::

1. You can choose either to create a new list or use an existing list.

   If you choose to create a new list, you'll need to enter the following criteria.
 
    :::image type="content" source="media/first-page/add-list.png" alt-text="Add a list to a page.":::

    | List | Description |
    | ----------- | ----------- |
    | Choose a table | The name of the table the views are loaded from. |
    | Select Dataverse views | The view of the target table that will be rendered. To modify the columns within the view, you'll need to access the Data workspace. |
    | Name your copy of the selected list | The name of the list. |

    | Data | Description |
    | ----------- | ----------- |
    | Create a new record | Allows the user to create a new record. You'll need to select the target webpage, form, or URL that contains the new record. |
    | View details | Allows the user to view details.  You'll need to select the webpage, form, or URL that contains the details. | 
    | Delete record | Allows the user to delete the record. | 

    | Settings | Description |
    | - | - |
    | Number of records per page | Determines how many records will be displayed per page. If the table contains more records, navigation controls will appear for the user to view the next or previous set of records. |
    | Enable search in list | Turns on the search feature for the list. |

    > [!NOTE]
    > You'll need to enable [table permissions](../security/table-permissions.md) to ensure that users will be able to view the data on the lists.

1. You can select the ellipsis (**...**) to duplicate the list, move it up or down within the section, or delete it.

### See also

- [Create and modify views](../configure/data-workspace-views.md)
- [Tutorial: Add a list to a page](tutorial-add-list-to-page.md)

