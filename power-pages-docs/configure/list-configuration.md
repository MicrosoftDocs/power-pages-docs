---
title: List configuration
description: Learn how to configure lists on a website.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 09/22/2026
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: smurkute
contributors:
    - sandhangitmsft

---

# List configuration

You can easily enable and configure actions (create, edit, delete, and so on) for records in a list. You can also override default labels, sizes, and other attributes so that the list displays exactly the way you want.

Modern list is the default list experience for newly created Power Pages sites. You can configure many of these features directly in the [Power Pages design studio](../getting-started/add-list.md). This article provides information on how to configure lists metadata by using the [Portal Management app](portal-management-app.md).

> [!IMPORTANT]
> Modern and classic lists use the same underlying list configuration, but some presentation settings in the Portal Management app apply only to classic lists. For modern lists, use the design studio to configure colors, fonts, spacing, and other visual styles.

Find these settings on the **Options** tab in the **Grid Configuration** section of the list configuration. By default, only **Basic Settings** are shown. Select **Advanced Settings** to see more settings.

:::image type="content" source="media/lists/configure-list.png" alt-text="Configure a list."::: 

**Attributes**

|Name                   |Description|
|---------------------------|-----------|
|**Basic Settings**         |   |
| View Actions              |Use to add action buttons for actions that are applicable for the table set and appear above the grid. The available actions are: <ul><li>Create</li> <li>Download</li></ul> Selecting one of these options displays a configuration area for that action.|
| Items Actions             |Use to add action buttons for actions that are applicable for an individual record and appear for each row in the grid, provided the appropriate privilege is granted by Table Permissions. The actions generally available are:<ul><li>Details</li><li>Edit</li><li>Delete</li><li>Workflow</li><li>Activate</li><li>Deactivate</li></ul> Selecting one of these options displays a configuration area for that action. See the following section for details about each action. Furthermore, certain tables have special actions that are available to them on a per-table basis:<ul><li>Calculate Value of Opportunity (opportunity)</li><li>Cancel Case action (incident)</li><li>Close (resolve) Case action (incident)</li><li>Convert Quote to Order (quote)</li><li>Convert Order to Invoice (sales order)</li><li>Generate Quote from Opportunity (opportunity)</li><li>Lose Opportunity action (opportunity)</li><li>Win Opportunity action (opportunity)</li><li>Reopen Case action (incident)</li><li>Set Opportunity on Hold (opportunity)</li></ul>|
| Override Column Attributes|Use to override display settings for individual columns in the grid.<ul><li>Attribute: Logical name of the column you want to override</li><li>Display Name: New column title to override the default</li><li>Width: Width (in either percent or pixels) of the column to override the default. See also Grid Column Width Style</li></ul> To override settings on a column, select **+ Column** and fill in the details.|
|**Advanced Settings**      |  |
| Loading Message           |Overrides the default HTML message that appears while the grid is loading.|
| Error Message             |Overrides the default HTML message that appears when an error occurs while loading the grid.|
| Access Denied Message     |Overrides the default HTML message that appears when a user doesn't have sufficient Table Permissions to view the list.|
| Empty Message             |Overrides the HTML message that appears when the grid contains no data.|
| Details Form Dialog       |Controls the settings for the dialog box that appears when a user activates the Details action.|
| Edit Form Dialog          |Controls the settings for the dialog box that appears when a user activates the Edit action.|
| Create Form Dialog        |Controls the settings for the dialog box that appears when a user activates the Create action.|
| Delete Dialog             |Controls the settings for the dialog box that appears when a user activates the Delete action.|
| Error Dialog              |Controls the settings for the dialog box that appears when an error occurs during any action.|
| CSS Class                 |Specify a CSS class or classes that apply to the HTML element that contains the entire grid area, including the grid and action buttons.|
| Grid CSS Class            |Specify a CSS class or classes that apply to the list's HTML \<table\> element.|
| Grid Column Width Style   |Configures whether the **Width** values in the Override Column Attributes are specified in **Pixels** or **Percent**.|

**General action settings**

In general, table actions have settings that you can configure. In all cases, these settings give you more options for customization, and the fields aren't required. If you add the action, the action is available on the website, provided the appropriate privilege is granted by table permissions.

Generally, you can configure the corresponding dialog box for each action, which appears only if you select **Confirmation Required**.


| Name                   | Description                                                                                                                                                                                                                   |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Basic Settings**         |                                                                                                                                                                                                                               |
| Confirmation Required? | Determines whether a confirmation prompts the user to confirm when the action is selected.                                                                                                                                   |
| **Advanced Settings**      |                                                                                                                                                                                                                               |
| Confirmation           | Overrides the confirmation HTML message displayed when the user activates the action.                                                                                                                                         |
| Button Label           | Overrides the HTML label for this action displayed in the list row.                                                                                                                                                    |
| Button Tooltip         | Overrides the tooltip text that appears when the user points to the button for this action displayed in the list row.                                                                                           |
| Button CSS Class       | Adds a CSS class to the button.                                                                                                                                                      |
| Redirect to Webpage    | Some actions (not all) allow a redirect upon completion of the action. It's highly recommended for the Delete action. For most other actions, it's optional. You can choose a webpage to redirect to when the action is completed. |
| Redirect URL           | An alternative to the **Redirect to Webpage** option&mdash;allows redirecting to a specific URL.                                                                                                                                   |

**General dialog box advanced settings**

|**Name**                 |**Description**                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Title                    | Overrides the HTML that appears in the title bar of the dialog box.|                                                                         
| Primary Button Text      | Overrides the HTML that appears in the Primary (Delete) button on the dialog box.                                                         |
| Close Button Text        | Overrides the HTML that appears in the Close (Cancel) button on the dialog box.                                                           |
| Dismiss Button Sr Text   | Overrides the screen reader text associated with the dialog box's Dismiss button.                                                           |
| Size                     | Specifies the size of the Delete dialog box. The options are Default, Large, and Small. The default size is Default. |
| CSS Class                | Specify a CSS class or classes that apply to the resulting dialog box.                                                            |
| Tile CSS Class           | Specify a CSS class or classes that apply to the resulting dialog box's title bar.                                                |
| Primary Button CSS Class | Specify a CSS class or classes that apply to the dialog box's Primary (Delete) button.                                          |
| Close Button CSS Class   | Specify a CSS class or classes that apply to the dialog box's Close (Cancel) button.                                            |

**Create action settings**

When you enable a **Create Action**, you add a button above the list. When a user selects the button, it opens a dialog box with a basic form that the user can use to create a new record, if the user has the Create privilege through Table Permissions.

| Name               | Description                          |
|--------------------|--------------------------------------|
| **Basic Settings**     |                                                                                                                                                                       |
| Basic Form     | Specifies the basic form that the app uses to create the new record. The drop-down list includes all basic forms that are configured for the table type of the list. <br>**Note**: If the table type of the list has no basic forms, the drop-down list is empty. If you don't supply a basic form for the Create action, the app ignores the action and doesn't render the button on the list. |
| **Advanced Settings**          |                                                                                                                                                                       |
| Button Label                                                                                                                                                                                                                 | Overrides the HTML label displayed in the Create action button above the list.                                                                                        |
| Button Tooltip                                                                                                                                                                                                               | Overrides the tooltip text that appears when the user points to the Create action button.                                                                         |

**Create Form dialog box advanced settings**

|**Name**               |**Description**                                                                                                                                 |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Loading Message        | Overrides the message that appears while the dialog box is loading.                                                                                  |
| Title                  | Overrides the HTML that appears in the title bar of the dialog box.                                                                                  |
| Dismiss Button Sr Text | Overrides the screen reader text associated with the dialog box's Dismiss button.                                                                   |
| Size                   | Specifies the size of the Create Form dialog box. The options are Default, Large, and Small. The default size is Large. |
| CSS Class              | Specify a CSS class or classes that apply to the resulting dialog box.                                                                    |
| Title CSS Class        | Specify a CSS class or classes that apply to the resulting dialog box's title bar.                                                        |

**Download action settings**

When you enable a **Download Action**, you add a button above the list. When a user selects the button, it downloads the data from the list to an Excel (.xlsx) file. This button uses [Microsoft Dataverse FetchXML](/power-apps/developer/data-platform/fetchxml/overview) to query the records, and FetchXML limitations apply.

| Name              | Description                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| **Basic Settings**    |                                                                                                    |
| None              |                                                                                                    |
| **Advanced Settings** |                                                                                                    |
| Button Label      | Overrides the HTML label displayed in the Download action button above the list.            |
| Button Tooltip    | Overrides the tooltip text that appears when the user points to the Download action button. |

**Details action settings**

When you enable a **Details Action**, a user can view a read-only basic form of a selected row in the list.


|                 Name                  |                                                                                                                                                                                                                      Description                                                                                                                                                                                                                      |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Basic Settings**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              Basic Form              | Specifies the basic form that the app uses to view the details of the selected table. The drop-down list includes all basic forms that are configured for the table type of the list. <br><br> **Note**: If the table type of the list has no basic forms, the drop-down list is empty. If you don't supply a basic form for the Details action, the app ignores the action and doesn't render the button in the list.<br><br>The behavior of the target form (read-only or edit) is determined by the configuration of the [form mode](basic-forms.md#basic-form-attributes-and-relationships) and the [table permissions](../security/table-permissions.md) assigned to the web roles associated with the user. |
|         **Advanced Settings**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Record ID Parameter Name |                                                                    Specifies the name of the Query String parameter that the app uses to select the table to view in the selected basic form. This value matches the value in that basic form's Record ID Parameter Name. The default value for this field, both here and in basic form configuration, is **id**.                                                                     |
|             Button Label              |                                                                                                                                                                                      Overrides the HTML label for this action displayed in the list row.                                                                                                                                                                                       |
|            Button tooltip             |                                                                                                                                                             Overrides the tooltip text that appears when the user points to the button for this action displayed in the list row.                                                                                                                                                              |

**Details dialog box advanced settings**

|**Name**               |**Description**                                                                                                                         |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Loading Message        | Overrides the HTML that appears when the dialog box is loading.                                                                             |
| Title                  | Overrides the HTML that appears in the title bar of the dialog box.                                                                         |
| Dismiss Button Sr Text | Overrides the screen reader text associated with the dialog box's Dismiss button.                                                           |
| Size                   | Specifies the size of the Details dialog box. The options are Default, Large, and Small. The default size is Large. |
| CSS Class              | Specify a CSS class or classes that apply to the resulting dialog box.                                                            |
| Title CSS Class        | Specify a CSS class or classes that apply to the resulting dialog box's title bar.                                                |

**Edit action settings**

Enabling an **Edit Action** allows a user to view an editable basic form that is data-bound to the record of the selected row from the list, provided the Write privilege has been granted by Table Permissions.


|                 Name                  |                                                                                                                                                                                                             Description                                                                                                                                                                                                             |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Basic Settings**           |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|              Basic Form              | Specifies the basic form that will be used to edit the selected table. The drop-down list will include all basic forms that are configured for the table type of the list. <br><br> **Note**: If the table type of the list has no basic forms, the drop-down list will appear empty. If no basic form is supplied for the Edit action, it will be ignored and the button won't be rendered in the list.<br><br>The behavior of the target form (read-only or edit) will be determined by the configuration of the [form mode](basic-forms.md#basic-form-attributes-and-relationships) and the [table permissions](../security/table-permissions.md) assigned to the web roles associated with the user. |
|         **Advanced Settings**         |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Record ID Parameter Name |                                                           Specifies the name of the Query String parameter that will be used to select the table to edit in the selected basic form. This should match the value in that basic form's Record ID Parameter Name. The default value for this field, both here and in basic form configuration, is **id**.                                                            |
|             Button Label              |                                                                                                                                                                             Overrides the HTML label for this action displayed in the list row.                                                                                                                                                                              |
|            Button Tooltip             |                                                                                                                                                    Overrides the tooltip text that appears when the user points to the button for this action displayed in the list row.                                                                                                                                                     |

**Edit form dialog box advanced settings**

|**Name**               |**Description**                                                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Loading Message        | Overrides the HTML that appears when the dialog box is loading.                                                                       |
| Title                  | Overrides the HTML that appears in the title bar of the dialog box.                                                                   |
| Dismiss Button Sr Text | Overrides the screen reader text associated with the dialog box's Dismiss button.                                                     |
| Size                   | Specifies the size of the Edit dialog box. The options are Default, Large, and Small. The default size is Large. |
| CSS Class              | Specify a CSS class or classes that apply to the resulting dialog box.                                                      |
| Title CSS Class        | Specify a CSS class or classes that apply to the resulting dialog box's title bar.                                          |

**Delete action settings**

When you enable a **Delete Action**, users can permanently delete the record of the selected row from the list. The Table Permissions grant the Delete privilege.

| Name              | Description                                                                                                                         |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| **Basic Settings**    |                                                                                                                                     |
| none              |                                                                                                                                     |
| **Advanced Settings** |                                                                                                                                     |
| Confirmation      | Overrides the confirmation HTML message displayed when the user activates the Delete action.                                        |
| Button Label      | Overrides the HTML label for this action displayed in the list row.                                                          |
| Button Tooltip    | Overrides the tooltip text that appears when the user points to the button for this action displayed in the list row. |

**Delete dialog box (advanced) settings**

|**Name**                 |**Description**                                                                                                                         |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Title                    | Overrides the HTML that appears in the title bar of the dialog box.                                                                         |
| Primary Button Text      | Overrides the HTML that appears in the Primary (Delete) button on the dialog box.                                                         |
| Close Button Text        | Overrides the HTML that appears in the Close (Cancel) button on the dialog box.                                                           |
| Dismiss Button Sr Text   | Overrides the screen reader text associated with the dialog box's Dismiss button.                                                           |
| Size                     | Specifies the size of the Delete dialog box. The options are Default, Large, and Small. The default size is Default. |
| CSS Class                | Specify a CSS class or classes that apply to the resulting dialog box.                                                            |
| Title CSS Class          | Specify a CSS class or classes that apply to the resulting dialog box's title bar.                                                |
| Primary Button CSS Class | Specify a CSS class or classes that apply to the dialog box's Primary (Delete) button.                                          |
| Close Button CSS Class   | Specify a CSS class or classes that apply to the dialog box's Close (Cancel) button.                                            |

**Workflow action settings**

When you enable a **Workflow action**, you can run an on-demand workflow against the record of the selected row from the list. You can add any number of Workflow actions to the list.


|         Name          |                                                                                                                                                           Description                                                                                                                                                           |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Basic Settings**   |                                                                                                                                                                                                                                                                                                                                 |
|       Workflow        | Specifies the on-demand workflow that runs when the user activates this action. <br> **Note**: If the table type of the list has no workflows, the drop-down list appears empty. If you don't supply a workflow for the Workflow action, the system ignores it and doesn't render the button in the list. |
|     Button Label      |                                                                                                                 Sets the HTML label for this action displayed in the list row. This setting is required.                                                                                                                 |
| **Advanced Settings** |                                                                                                                                                                                                                                                                                                                                 |
|    Button Tooltip     |                                                                                                  Overrides the tooltip text that appears when the user points to the button for this action displayed in the list row.                                                                                                   |

### See also

- [Lists overview](lists.md)
- [Portal Management app](portal-management-app.md)  
- [Redirect to a new URL](add-redirect-url.md)
