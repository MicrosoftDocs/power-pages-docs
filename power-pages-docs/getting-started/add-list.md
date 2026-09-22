---
title: Add lists
description: Create and add a list from views to your page in Power Pages.
author: shwetamurkute
ms.topic: how-to
ms.custom: 
ms.date: 09/22/2026
ms.subservice:
ms.author: bipuldeora 
ms.reviewer: smurkute
contributors:
    - pranita225
---

# Add list

A list is a data-driven configuration that renders a list of records without requiring a developer to surface the grid in the portal. Lists use Dataverse views to display records on the portal.

A list displays data in a grid view on Power Pages sites. You create lists on pages from Dataverse table views. Use the [Data workspace](use-data-workspace.md) or [model-driven apps created in Power Apps](/power-apps/maker/model-driven-apps/accessing-view-definitions/) to create Dataverse table views. Use them on pages or with [forms](add-form.md) to build a complete web application.

> [!TIP]
> To learn how to use Power Pages, create a view, and add a list to a page, see [Tutorial: Add a list to a page](tutorial-add-list-to-page.md).

To add a list:

1. Open the [design studio](use-design-studio.md) to edit the content and components of the page.

1. Select the page you want to edit.

1. Select the section where you want to add the list component.

1. Hover over any editable canvas area, and then select the **List** icon from the component panel.

    :::image type="content" source="media/common/component-options.png" alt-text="The add component menu options.":::

    The **Add a list** window opens.

1. Choose to create a new list or choose an existing list, and then select **Ok**.

    > [!NOTE]
    > Modern list is the default list experience for newly created sites. To use the classic list experience, turn off the **Modern list** toggle.

    - If you choose to create a new list, the **Add a list** window opens to the **Set up** tab.
    - If you use an existing list, you're redirected to the list displayed in the Pages workspace.  Choose the list and select the **Edit list** button just above the component to access configuration options in the **Add a list** window. You can also choose to change your list to a modern list when you edit your list.

## Modern list

Modern list is the default list experience for newly created Power Pages sites. It provides a refreshed appearance, improved loading and navigation, and enhanced styling capabilities.

When you add a list to a newly created site, the list uses the modern experience by default. To use the classic list experience, turn off the **Modern list** toggle when you add or edit the list.

- **Shimmer loading** - Loading animation displays while data is retrieved from your data source.
- **Infinite scroll**  - Content automatically loads at the bottom of the page when users scroll.
- **Inline filters** - Filters apply automatically to all columns in the list view.
- **Styling options** - Customize elements such as background and font color, add alternating row colors, and adjust margins and padding.

> [!TIP]
> You can copy the style from one modern list to other modern lists in your site for a consistent design experience across pages.

## Set up your list

Specify values for each field in the **Set up** section. Select the **Set up** menu tab in the **Add a list** window to complete this step.


| List | Description |
| ----------- | ----------- |
| Choose a table | The name of the table the views load from. |
| Select Dataverse views | The view of the target table to render. To modify the columns within the view, access the Data workspace. |
| Name your list | The name of the list. |

 ## Choose list actions

Specify the actions you want to take for your list by configuring list actions. The actions are listed under the **Actions** menu tab in the **Add a list** window. For each of these options, you can also change the default button label by editing the **Display label** field. 

| Data | Description |
| ----------- | ----------- |
| Create a new record | Allows the user to create a new record. Select the target webpage, form, or URL that contains the new record. |
| Download list contents | Allows the user to download list contents into an *.xlsx file.  |
| View details | Allows the user to view details.  Select the webpage, form, or URL that contains the details.| 
| Edit record | Allows the user to edit the record. Select the webpage, form, or URL that contains the record details to edit.  |
| Delete record | Allows the user to delete the record.  | 

## Specify more options

You might want to customize your list options even further.  Visit the **More options** menu tab from the **Add a list** window to configure more options for your list.

| Settings | Description |
| - | - |
| Number of records per page | Applies only to classic lists. Determines how many records are displayed per page. If the table contains more records, navigation controls appear so users can view the next or previous set of records. Modern lists use infinite scrolling, so this option isn't available when **Modern list** is turned on. |
| Enable search in list | Turns on the search feature for the list. Add a placeholder text for the search bar. |

> [!NOTE]
> Enable [table permissions](../security/table-permissions.md) to ensure that users can view the data on the lists.

You can also specify more options by using the [Portal Management app](../configure/portal-management-app.md).

## Duplicate a list

From the **Pages** workspace inside design studio, you can select the ellipsis (**...**) on the list component to duplicate a list, move it up or down within the section, or delete it.

## List filters

Makers can add list filters to their Power Pages site from the design studio.  

### Filter types

You can configure all types of metadata filters that the [Portal Management app](../configure/portal-management-app.md) supports within Power Pages studio. Each filter type has a simplified name that matches its visualization. Makers can also edit or delete the filters when working with the list component inside the design studio.

| Filter Visualization | Description  |
|---------|---------|
|Text    | Filters the list by using a text box to search for matching text in a selected attribute of the given table.        |
|Checkbox, Dropdown, and Radio Button    | Makers can choose between checkboxes, dropdowns, and radio buttons as visualizations for their filter type. More options to configure the filter appear once makers pick the column. These options vary based on the column's data type.       |
|Custom   | Filters the list by using a FetchXML filter condition. When a maker selects custom, a text box appears.  Makers enter their XML statement in this field.        |

### Add a list filter

To add a list filter, select the list component you previously added and configured.  

1. Choose the **Add filter** menu item from the toolbar.

    :::image type="content" source="media/add-list/add-filter.png" alt-text="The list toolbar inside the Pages workspace with the Add filter menu item emphasized.":::

    A pop-up window displays in the Pages workspace with list filter options.  

    :::image type="content" source="media/add-list/add-filter-pop-up.png" alt-text="The Add filter pop-up window inside Pages workspace.":::

1. Select the type of filter you want to use from the drop-down selector under the **Type label**.

1. Choose the column you want to filter from the drop-down selector under the **Column label**.

    >[!NOTE]
    > The studio displays the different options for makers to filter their data based on the filter type and column they choose.

1. Select the **OK button** to save your selections.  

1. Once the filter is applied, you can edit the filter configuration by selecting the **Edit filter** button in the design studio.
    
    :::image type="content" source="media/add-list/edit-filter.png" alt-text="The edit filter menu options inside design studio."::: 

### Filter settings

You can edit filter settings by selecting the filter settings option on the component in design studio.

:::image type="content" source="media/add-list/filter-settings.png" alt-text="The filter settings menu options inside Design Studio with the vertical filter orientation button selected.":::

### See also

- [Create and modify views](../configure/data-workspace-views.md)
- [Tutorial: Add a list to a page](tutorial-add-list-to-page.md)
