---
title: Configure basic form metadata for Power Pages
description: Learn how to add and configure basic form metadata for a portal.
author: nageshbhat-msft

ms.topic: how-to
ms.custom: 
ms.date: 01/09/2025
ms.subservice: 
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - nageshbhat-msft
---

# Configure basic form metadata for portals

The basic form Metadata contains extra behavior modification logic to augment or override the functionality of form fields that is otherwise not possible with native basic form editing capabilities.

Some form configuration is possible using the Power Pages design studio. See [Add form](../getting-started/add-form.md) for more information.

> [!TIP]
> If two or more basic form metadata records are created for the same attribute that have conflicting actions, the basic form metadata record that was created **first** is applied and the subsequent records won't.

## Add a new record

1. Open the [Portal Management app](portal-management-app.md).

1. Select the form you want to enhance from **Basic Forms** under the **Content** section.

1. On the basic form that has fields that you would like to modify, go to **Related** > **Basic Form Metadata** 

2. Select **New Basic Form Metadata**.

## Basic form metadata properties

The following attributes provide extra styling and capabilities for elements on a form.

| Name          | Description                                                                                                                                                                                                                                                                                                                                          |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Basic form | The basic form associated with the basic form Metadata record.                                                                                                                                                                                                                                                                                      |
| Type          | Available options are:<ul><li>Attribute </li><li>Notes</li><li>Section</li><li>Subgrid</li><li>Tab</li><li>Timeline</li></ul> Each type represents appropriate options for the selection. |

## Basic form metadata type = Attribute

The following properties are displayed when the Type selected is 'Attribute'.


|          Name          |                                                                                                                                                    Description                                                                                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Attribute Logical Name |                                                                                                                              The logical name of the attribute field to be modified.<br> **Note:** Columns of type *choices* don't appear on the drop-down list of columns. You can enter the logical name of the choices column directly in the **Attribute Logical Name** text box.                                                                                                                              |
|         Label          | Replaces the default label assigned to the attribute on the table with the text specified in this input. For each language pack installed and enabled for the Microsoft Dataverse environment a field is available to enter the message in the associated language. |

### Control style

The following options modify the style and functionality of an attribute's field.


|                      Name                       |                                                                                                                                                                                                                                                                                                                                       Description                                                                                                                                                                                                                                                                                                                                       |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      Style                      | Options:<ul><li>Option Set as Vertical Radio Button List</li><li>Option Set as Horizontal Radio Button List</li><li>Single Line of Text as Geolocation Lookup Validator (requires Bing Maps settings)</li><li>Group Whole Number as Constant Sum (requires Group Name)</li><li>Group Whole Number as Rank Order Scale No Ties (requires Group Name)</li><li>Group Whole Number as Rank Order Scale Allow Ties (requires Group Name)</li><li>Multiple Choice Matrix (requires Group Name)</li><li>Multiple Choice (requires Group Name)</li><li>Group Whole Number as Stack Rank (requires Group Name)</li><li>Code component</li><li>Render Lookup as Dropdown</li></u> |
|                   Group Name                    |                                                                                                                                                                                                                                                                                                             A name used to group controls together as a composite control.                                                                                                                                                                                                                                                                                                              |
| Multiple Choice Minimum Required Selected Count |                                                                                                                                                                                                                                                                      The required minimum values selected in the multiple choice question. Only necessary if 'Multiple Choice' Control Style is selected.                                                                                                                                                                                                                                                                       |
|       Multiple Choice Max Selected Count        |                                                                                                                                                                                                                                                          This count is the maximum number of values allowed to be selected in the multiple choice question. Only necessary if 'Multiple Choice' Control Style is selected.                                                                                                                                                                                                                                                          |
|           Constant Sum Minimum Total            |                                                                                                                                                                                                                                                             This number is the required minimum value applied to a constant sum response field. Only necessary if 'Group Whole Number as Constant Sum' Control Style is selected.                                                                                                                                                                                                                                                              |
|           Constant Sum Maximum Total            |                                                                                                                                                                                                                                                 This number is the maximum permitted value to be applied to a constant sum response field. Only necessary if 'Group Whole Number as Constant Sum' Control Style is selected.                                                                                                                                                                                                                                                 |
|           Randomize Option Set Values           |                                                                                                                                                                                                                                                                     Specifying Yes results in randomly ordered options listed for an Option Set control. Only applicable to attributes that are of type Option Set.                                                                                                                                                                                                                                                                     |
|                    CSS Class                    |                                                                                                                                                                                                                                                                                                                      Adds a custom CSS class name to the control.                                                                                                                                                                                                                                                                                                                       |

### Prepopulate field

The following options provide a default value for fields on the form.


|         Name         |                                                                                                                                                                                                                                                                Description                                                                                                                                                                                                                                                                 |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ignore Default Value |                                                                              Ignores the default value of the specified attribute field. Useful for attributes that are Two Option fields that are rendered as Yes and No radio buttons. Because a value of yes or no is automatically assigned by default, this option makes it possible to display Yes/No questions without a predefined response.                                                                               |
|         Type         | One of the following types:<ul><li>Value</li><li>Today's Date</li><li>Current User's Contact</li></ul>Selecting Value requires a value to be specified in the **Value** field that is assigned to the field when the form is loaded. Selecting Today's Date assigns the current date and time to the attribute field. Selecting Current User's Contact requires a **From Attribute** that is an attribute on the contact table that is retrieved from the current user's contact record and set on the attribute field specified. |
|        Value         |                                                                                                                                                                                                                                        A value to be assigned to the field when the form is loaded.                                                                                                                                                                                                                                        |
|    From Attribute    |                                                                                                                                                                                             An attribute on the contact table that is retrieved from the current portal user's record and assigned to the field when the form is loaded.                                                                                                                                                                                             |

### Set Value On Save

The following options specify a value to be set when the form is saved.

| Name              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Set Value On Save | Yes indicates that a value should be assigned to the attribute using the input provided in the **Value** field. <br>**Note**: All attribute types are supported except the following types: Unique Identifier.       |
| Type              | Options:<ul><li>Value</li><li>  Today's Date</li><li>Current User's Contact</li></ul>Selecting Value requires a value to be specified in the **Value** field that is assigned to the field when the form is loaded. Selecting Today's Date assigns the current date and time to the attribute field. Selecting Current User's Contact requires a **From Attribute** that is an attribute on the contact table that is retrieved from the current user's contact record and set on the attribute field specified.  |
| Value             | Value assigned to the attribute when the form is being saved.<br>For Two Option (Boolean) fields use true or false.<br>For Option Set field use the integer value for the option.<br>For Lookup (TableReference) fields, use the GUID.<br>**Note**: If the attribute is also on the form, the user's value is overwritten with this value.|
| From Attribute    | An attribute on the contact table that is retrieved from the current portal user's record and assigned to the field during save. |

### Lookup Settings

The lookup setting **Basic form for Create** is used to populate the basic form for creating a new record from the lookup when the metadata created for an attribute is of lookup type.

### Validation

The following section contains properties that modify various validation parameters and error messages.

For each language pack installed and enabled for the Dataverse environment, a field is available to enter the message in the associated language.

| Name                                        | Description                                                                                                                                                                                                                                                      |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Validation Error Message                    | Overrides the default validation error message for the field.                                                                                                                                                                                                    |
| Regular Expression                          | A regular expression to be added to validate the field.                                                                                                                                                                                                          |
| Regular Expression Validation Error Message | The validation error message to display if the regular expression validated fails.                                                                                                                                                                               |
| Field is Required                           | Check to make the attribute field required to contain a value.                                                                                                                                                                                                   |
| Required Field Validation Error Message     | Overrides the default required field error message if the field doesn't contain a value.                                                                                                                                                                        |
| Range Validation Error Message              | Overrides the default range validation error message displayed if the field's value is outside of the appropriate minimum and maximum values specified on the table attribute that are of type Whole Number, Decimal Number, Floating Point Number, or Currency. |
| Geolocation Validator Error Message         | This message overrides the default error message if the attribute is a Single Line of Text, the Control Style is Single Line of Text, and the Geolocation Lookup Validator is specified. |
| Constant Sum Validation Error Message       | If the attribute is a whole number type and the control style is Group Whole Number as Constant Sum, this message overrides the default error message displayed if input validation fails.                  |
| Multiple Choice Validation Error Message    | If the attribute is a Two Option type and the Control Style is Multiple Choice, this message overrides the default error message displayed if input validation fails.                                      |
| Rank Order No Ties Validation Error Message | This message overrides the default error message if the attribute is a Whole Number type, the Control Style is Group Whole Number as Rank Order No Ties, and input validation fails.              |

### Description and instructions

The following properties specify the location and content of custom description or instructions.


|                 Name                 |                                                                                                                                                           Description                                                                                                                                                           |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Add Description            |                                                                                                                        Yes results in custom text being displayed on the form in the position specified.                                                                                                                        |
|               Position               |                                                                                                             Options:<ul><li>Above the field</li><li>Below the field</li><li>Above the label</li></ul>                                                                                                              |
| Use Attribute's Description Property |                                                                                       Select 'Yes' to use the description assigned to the attribute metadata on the table. Select 'No' to provide a custom description. Default is 'No'.                                                                                       |
|             Description              | Custom text to be displayed on the form. Used in conjunction when Use Attribute's Description Property is set to 'No'. For each language pack installed and enabled for the Dataverse environment, a field is available to enter the message in the associated language. |

## Basic form metadata type = Notes

See [Configure notes as attachments for basic and multistep forms](configure-notes.md). These settings are used to configure the *timeline* control on a form. You can also enable a file upload control through [form additional settings](basic-forms.md#additional-settings).

## Basic form metadata type = Section

The following properties are displayed when the selected Type equals 'Section'.


|     Name     |                                                                                                                                                   Description                                                                                                                                                    |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Section Name |                                                                                           The name of the section on the table's form to be modified.                                                                                            |
|    Label     | Replaces the default label assigned to the section on the table with the text specified in this input. For each language pack installed and enabled for the Dataverse environment, a field is available to enter the message in the associated language. |

## Basic form metadata type = Subgrid

See [Configure basic form subgrid](configure-basic-form-subgrid.md)

## Basic form metadata type = Tab

The following properties are displayed when the selected Type equals 'Tab'


|   Name   |                                                                                                                                                 Description                                                                                                                                                  |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tab Name |                                                                                           The name of the tab on the table's form to be modified.                                                                                            |
|  Label   | Replaces the default label assigned to the tab on the table with the text specified in this input. For each language pack installed and enabled for the Dataverse environment, a field is available to enter the message in the associated language. |

## Basic form metadata type = Timeline

The following properties are displayed when the selected Type equals 'Timeline'.

| Name                  | Description                                                                                                                                                  |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Basic settings**    |                                                                                                                                                              |
| Create Enabled        | Enables the ability to add new notes to the table.                                                                                                          |
| Create Dialog Options | Whether to display the attached file.                                 |
|File Attachment Location | Select the location of the file attachment:<ul><li>Note attachment</li><li>Azure Blob Storage</li></ul>|
|Accept MIME Type(s) | Allows you to specify a list of accepted MIME types. |
|Accept Extension Type(s) | Allows you to specify a list of extension types. |
|Restrict MIME Types | Select whether to allow or restrict MIME types.|
|Maximum File Size (in KB) |Allows you to specify the maximum size of a file that can be attached. |

### See also

[Portals Management app](./portal-management-app.md)  
[Define basic forms](basic-forms.md)  

