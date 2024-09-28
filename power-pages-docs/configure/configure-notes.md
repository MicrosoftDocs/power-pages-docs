---
title: Set up notes as attachments for basic and multistep forms
description: Learn how to add and configure notes as attachments on basic and multistep forms in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 3/10/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - GitanjaliSingh33msft
    - nageshbhat-msft
---

# Configure notes as attachments for basic and multistep forms

The following steps walk through the process of enabling the ability to add attachments to basic and multistep forms using the Portals Management app.

You can also enable adding attachments using the Power Pages design studio. See [Enable attachments on a form](../getting-started/add-form.md#enable-attachments-on-a-form) and [Enable attachments on a multistep form](../getting-started/multistep-forms.md#enable-attachments) for more details.

## Configure notes as attachments using Portals Management app

To add the ability to view notes and attachments on basic and multistep forms, you'll need to complete the following steps:

- [Enable attachments for the table in Microsoft Dataverse](/power-apps/maker/data-platform/data-platform-create-entity#create-a-table).

- Add the [timeline control](/power-apps/maker/model-driven-apps/set-up-timeline-control) to the Dataverse forms through the model-driven app [form designer](/power-apps/maker/model-driven-apps/create-design-forms) or [Data workspace](data-workspace-forms.md) if using the Power Pages design studio.

- Configure [table permissions](../security/table-permissions.md) for the notes (annotations) table.

> [!NOTE]
> - In order for a note to appear on the web page, the description of each note must be prefixed with **\*WEB\*** (*'WEB' keyword with an asterisk sign (\*) before and after*). Notes added through a form on a webpage will have the prefix automatically added.
> - You can specify a custom prefix by changing the **KnowledgeManagement/NotesFilter** [site setting](configure-site-settings.md) to a value of your choice. 
> - The ability to show both notes and [activities](/power-apps/maker/portals/configure/view-all-activities-in-portal-timeline) on the same form for a custom table is currently not supported with configuration.

## Notes configuration for basic forms

If you simply want to provide a file upload control, this can be accomplished using form [additional settings](basic-forms.md#additional-settings) or by enabling attachments using the [design studio](../getting-started/add-form.md#enable-attachments-on-a-form).

Adding a timeline control will allow users to view the attachments.

You can further configure the timeline control to allow site users to add, update, or delete notes and attachments by configuring the form metadata using the Portal Management app.

1. Open the [Portal Management app](portal-management-app.md)

1. Select **Basic Forms** under **Content** on the left pane.

1. From the list of forms, select to open a record of the form to which you want to add note configuration.

1. From the available tabs in form settings, select **Basic Form Metadata**.

    :::image type="content" source="media/configure-notes/form-metadata.png" alt-text="Basic form metadata.":::

1. Select **New Basic Form Metadata**.

    :::image type="content" source="media/configure-notes/new-form-metadata.png" alt-text="Add new basic form metadata.":::

1. Select **Type** as **Note**.

    :::image type="content" source="media/configure-notes/type-notes.png" alt-text="Type of note.":::

1. The notes configuration settings are displayed. Most of the settings are collapsed by default. You can expand a section to see more settings.

    :::image type="content" source="media/configure-notes/notes-options.png" alt-text="Note options.":::

    > [!NOTE]
    > If you want to enable storing note attachments in Azure, you will need to first [enable Azure storage](enable-azure-storage.md) for note attachments as well as update the **File Attachment Location** option to **Azure Blob Storage**.

1. Fill in the fields by entering appropriate values. These settings are explained in more detail below under [Attributes](#attributes), [Create dialog options](#create-dialog-options), [Edit dialog options](#edit-dialog-options), and [Delete dialog options](#delete-dialog-options).

1. Save the form.

After adding the configuration, the note control will be rendered by using the appropriate options enabled on the website.

### Attributes

| Name                  | Description                                                                                                                                                  |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Basic settings**    |                                                                                                                                                              |
| Create Enabled        | Enables the ability to add new notes to the table.                                                                                                          |
| Create Dialog Options | Contains settings for configuring the dialog box when **Create Enabled** is set to true. More information: [Create dialog options](#create-dialog-options).                                 |
| Edit Enabled          | Enables the ability to edit existing notes on the table.                                                                                                    |
| Edit Dialog Options   | Contains settings for configuring the dialog box when **EditEnabled** is set to true. More information: [Edit dialog options](#edit-dialog-options)                                         |
| Delete Enabled        | Enables the ability to delete notes from the table.                                                                                                         |
| Delete Dialog Options | Contains settings for configuring the dialog box when **DeleteEnabled** is set to true. More information: [Delete dialog options](#delete-dialog-options).           |
|File Attachment Location | Select the location of the file attachment:<ul><li>Note attachment</li><li>Azure Blob Storage</li></ul>|
|Accept MIME Type(s) | Allows you to specify a list of accepted MIME types. |
|Restrict MIME Types | Select whether to allow or restrict MIME types.|
|Maximum File Size (in KB) |Allows you to specify the maximum size of a file that can be attached. The maximum size of files that can be uploaded is determined by the *Maximum file size* setting in the [system settings email tab](/power-platform/admin/system-settings-dialog-box-email-tab) in the environment system settings dialog box. |
| **Advanced settings** |                                                                                                                                                              |
| List Title            | Overrides the title over the Notes area.                                                                                                                     |
| Add Note Button Label | Overrides the label on the Add Notes button.                                                                                                                 |
| Note Privacy Label    | Overrides the label denoting that a note is private.                                                                                                         |
| Loading Message       | Overrides the message shown while the list of notes is loading.                                                                                              |
| Error Message         | Overrides the message shown when an error occurs while trying to load the list of notes.                                                                     |
| Access Denied Message | Overrides the message shown when the user doesn't have sufficient permissions to view the list of notes.                                                    |
| Empty Message         | Overrides the message shown when the current table doesn't have any notes that can be viewed.                                                              |
| List Orders           | Allows you to set the order in which notes will be displayed. The List Orders setting allows you to set the following options: <ul><li>Attribute: The logical name of the column by which you wish to sort</li><li>Alias: The alias for the attribute in the query</li><li>Direction: Ascending (smallest to largest, or first to last), or Descending (largest to smallest, or last to first).</li></ul>:::image type="content" source="media/configure-notes/set-attributes-list-orders.png" alt-text="Set attributes for list orders.":::<br/>  To add a sorting rule, select "Column" (4) and fill in the details. List Orders will be processed in order from the top of the list having highest priority.|
||

#### Create dialog options

| Name                               | Description                                                                                                                                 |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Basic settings**                 |                                                                                                                                             |
| Display Privacy Options Field      | Enables a checkbox in the Add Note dialog box that allows the user to mark a note as private.                                                   |
| Privacy Option Field Default Value | Specifies the default value for the Display Privacy Options Field. The default value of this field is false.                     |
| Display Attach File                | Enables a file upload field in the Add Note dialog box, allowing a user to attach a file to a note.  <br /> **Note**: Only one file can be attached using this option.                                            |
| Attach File Accept                 | The MIME type accepted by the file upload input.                                                                                            |
| **Advanced settings**              |                                                                                                                                             |
| Note Field Label                   | Overrides the label for the Note field in the Add Note dialog box.                                                                              |
| Note Field Columns                 | Sets the columns value in the Note &lt;textarea&gt;.                                                                                            |
| Note Field Rows                    | Sets the rows value in the Note &lt;textarea&gt;.                                                                                            |
| Privacy Option Field Label         | Overrides the label for the Privacy Option Field (if enabled).                                                                              |
| Attach File Label                  | Overrides the label for the attached file (if enabled).                                                                                 |
| Left Column CSS Class              | Adds the CSS class or classes to the leftmost column containing labels in the Add Note dialog box.                                                  |
| Right Column CSS Class             | Adds the CSS class or classes to the rightmost column containing field inputs in the Add Note dialog box.                                           |
| Title                              | Overrides the HTML text in the header of the Add Note dialog box.                                                                               |
| Primary Button Text                | Overrides the HTML that appears in the Primary (Add Note) button in the dialog box.                                                           |
| Dismiss Button SR Text             | Overrides the screen reader text associated with the dialog box's dismiss button.                                                               |
| Close Button Text                  | Overrides the HTML that appears in the Close (Cancel) button in the dialog box.                                                               |
| Size                               | Specifies the size of the Add Note dialog box. The options are Default, Large, and Small.  |
| CSS Class                          | Specify a CSS class or classes that will be applied to the resulting dialog box.                                                                |
| Title CSS Class                    | Specifies a CSS class or classes that will be applied to the resulting dialog box's title bar.                                                    |
| Primary Button CSS Class           | Specifies a CSS class or classes that will be applied to the dialog box's Primary (Add Note) button.                                            |
| Close Button CSS Class             | Specifies a CSS class or classes that will be applied to the dialog box's Close (Cancel) button.                                                |
|||

#### Edit dialog options

| Name                               | Description                                                                                                                                   |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **Basic settings**                 |                                                                                                                                               |
| Display Privacy Options Field      | Enables a checkbox in the Edit Note dialog box that allows the user to mark a note as private.  |
| Privacy Option Field Default Value | Specifies the default value for the Display Privacy Options Field. The default value of this field is false.   |
| Display Attach File                | Enables a file upload field in the Edit Note dialog box, allowing a user to attach a file to a note. <br /> **Note**: Only one file can be attached using this option.                     |
| Attach File Accept                 | The MIME type accepted by the file upload input. |
| **Advanced settings**              |                                                                                              |
| Note Field Label                   | Overrides the label for the Note field in the Edit Note dialog box.|
| Note Field Columns                 | Sets the columns value in the Note &lt;textarea&gt;.                                                                                             |
| Note Field Rows                    | Sets the rows value in the Note &lt;textarea&gt;.                                                                                             |
| Privacy Option Field Label         | Overrides the label for the Privacy Option Field (if enabled).                                                                                
| Attach File Label                  | Overrides the label for the attached file (if enabled).                                                                                     |
| Left Column CSS Class              | Adds the CSS class or classes to the leftmost column containing labels in the Edit Note dialog box.                                                  |
| Right Column CSS Class             | Adds the CSS class or classes to the rightmost column containing field inputs in the Edit Note dialog box.                                           |
| Title                              | Overrides the HTML text in the header of the Edit Note dialog box.                                                                               |
| Primary Button Text                | Overrides the HTML that appears in the Primary (Update Note) button in the dialog box.                                                         |
| Dismiss Button SR Text             | Overrides the screen reader text associated with the dialog box's dismiss button.                                                                |
| Close Button Text                  | Overrides the HTML that appears in the Close (Cancel) button in the dialog box.                                                                |
| Size                               | Specifies the size of the Edit Note dialog box. The options are Default, Large, and Small. |
| CSS Class                          | Specifies a CSS class or classes that will be applied to the resulting dialog box.                                                                 |
| Title CSS Class                    | Specifies a CSS class or classes that will be applied to the resulting dialog's title bar.                                                     |
| Primary Button CSS Class           | Specifies a CSS class or classes that will be applied to the dialog box's Primary (Update Note) button.                                          |
| Close Button CSS Class             | Specifies a CSS class or classes that will be applied to the dialog box's Close (Cancel) button.                                                 |
|||

#### Delete dialog options

| Name                     | Description                                                                                                                                       |
|--------------------------|------------------------------|
| **Basic settings**       |                                                                                                                                                   |
| Confirmation             | Overrides the confirmation message to delete the note.                                                                                             |
| **Advanced settings**    |                                                                                                                                                   |
| Title                    | Overrides the HTML text in the header of the Delete Note dialog box.                                                                                  |
| Primary Button Text      | Overrides the HTML that appears in the Primary (Delete) button in the dialog box.                                                                   |
| Dismiss Button SR Text   | Overrides the screen reader text associated with the dialog box's dismiss button.                                                                     |
| Close Button Text        | Overrides the HTML that appears in the Close (Cancel) button in the dialog box.                                                                     |
| Size                     | Specifies the size of the Delete Note dialog box. The options are Default, Large, and Small.  |
| CSS Class                | Specifies a CSS class or classes that will be applied to the resulting dialog box.                                                                      |
| Title CSS Class          | Specifies a CSS class or classes that will be applied to the resulting dialog box's title bar.                                                          |
| Primary Button CSS Class | Specifies a CSS class or classes that will be applied to the dialog box's Primary (Delete) button.                                                    |
| Close Button CSS Class   | Specifies a CSS class or classes that will be applied to the dialog box's Close (Cancel) button.                                                      |
|||

### Assign table permissions

Notes, and the **Add**, **Edit**, and **Delete** buttons for the note control will be hidden on the basic or multistep form unless you create and assign the appropriate table permissions to the records as follows:

> [!IMPORTANT]
> A user must sign-in and be the creator of the note to edit or delete it using the portal. Users can't edit or delete a note created by others, even if you assign them table permissions.

1. Ensure the **Enable Table Permissions** checkbox is selected on the form for which you want notes to appear. Table permissions are enabled by default on all newly provisioned websites.

1. For the table that has the notes control enabled, create a table permission with the required privileges. The scope should be appropriately set depending on the level of access required to end users.

    For example, create a table permission for a table that shows notes on the basic form, with privileges including **Read**, **Write**, **Create**, **Append**, and **Append To**.

    :::image type="content" source="media/configure-notes/add-table-permissions.png" alt-text="Adding table permissions.":::

1. [Associate the table permission with a web role](../security/assign-table-permissions.md) for the user.

    For example, add the table permission created in the previous step to a web role.

1. Create a [child table permission](../security/table-permissions.md#configure-child-permissions) for the **Annotation** table from the table permission created in step 2 with the required privileges as explained in the table below. 

    | Note action | Required permissions |
    | - | - |
    | **Read** | Read |
    | **Add** | Create, Append (Append To required on Parent Table Permission) |
    | **Edit** | Write |
    | **Delete** | Delete |

    For example, create a child table permission for the Annotation table, with the  table permission created in the previous steps set as the parent table.

    :::image type="content" source="media/configure-notes/child-permissions.png" alt-text="Configure child permissions.":::

### Enable rich text editor

The rich text editor can be enabled when adding or editing notes on a form on a webpage.

A rich text editor can also be enabled for multiline text fields on a form. See [Tutorial: Configure the rich text editor control on Power Pages](component-rte-tutorial.md) for more information.

1. Open the [Portal Management app](portal-management-app.md).

1. Go to the **Website** section and select **Site Settings**.

1. Select **New** to create a new [site setting](/power-apps/maker/portals/configure/configure-site-settings).

1. Specify the following values for the site setting;
    1. **Name:** Timeline/RTEEnabled
    1. **Website:** *The associated website record*
    1. **Value:** True
    1. **Description:** (Optional)

1. Select **Save & Close**

1. Sync your website from the studio and preview the site.

1. You should be able to add and edit notes using the rich text editor.

### Notes created with rich text editor

You can view the notes created using the [Rich text editor control configurations](/power-apps/maker/model-driven-apps/rich-text-editor-control) on your portal webpage. 

However, if the [rich text editor](#enable-rich-text-editor) isn't enabled for notes on forms, when you try to edit, you'll see the text in HTML markup format.

For example, this note shows rich-text format in the model-driven app.

The portal webpage shows the note in rich-text format.

However, when editing the note from the portal webpage, you see the note in HTML markup format.

> [!IMPORTANT]
> If you try to save a note with HTML markup using the portal, you'll receive this error: *We're sorry, but something went wrong. Please try again, and if this persists, contact the website administrator.* To save the notes with HTML markup using the portal, you'll have to disable the request validation. However, disabling request validation applies to the entire website. For the steps to disable the request validation, and to understand its impact, go to [request validation](/power-apps/maker/portals/configure/entity-forms#request-validation).

## Notes configuration for multistep forms

Multistep form notes are configured in the same way as [basic form notes](#notes-configuration-for-basic-forms). Create a metadata record for the multistep form Step that has notes first, and then add the notes configuration metadata.

## Enable file attachment on form

Enable **Attach File** option for the **Basic Form** to show the attachment option available with the notes.

To enable attachment on a basic form:

1. Open the [Portal Management app](portal-management-app.md).

1. Select **Basic Forms** under **Content** on the left pane.

1. From the list of forms, select to open a record of the form to which you want to add note configuration.

1. Select **Additional Settings** for the form. Configure the additional settings as per the fields explained in the section below.

### Additional settings for file attachment

| Name | Description
| - | - 
| Attach File | Check the box to enable file attachments on the form.
| Attach File Save Option | Select **Notes** or **Portal Comments** to save file attachments. For notes attachments, select **Notes**.
| Allow Multiple Files | Check the box to allow multiple file attachments.
| Label | Specify a label for the attachment option.
| Attach File Storage Location | Select the location of the file attachment:<ul><li>Note attachment</li><li>Azure Blob Storage</li></ul>
| Accept MIME Types | Specify a list of accepted MIME types.
| Accept File Types | Specify a list of accepted file types. This option is only available when using the **Portal Comments** option for **Attach File Save Option**. 

### Attach a file option

After you configure the notes and enable notes attachments, you can see the **Attach File** option on the form.


