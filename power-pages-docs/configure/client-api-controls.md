---
title: Power Pages Client API supported controls (preview)
description: Learn about the different types of supported controls used with the Power Pages Client API
#customer intent: As a developer, I want to programmatically interact with controls in a form.
author: shwetamurkute
ms.author: nenandw
ms.reviewer: smurkute
ms.date: 12/01/2025
ms.topic: reference
---
# Power Pages Client API supported controls (preview)

The following control types are currently supported.

All these controls extend the base control type. Therefore, these objects provide all the interfaces available on the control object, along with a few more.

## Address composite control

The address composite control extends the control type for address input fields that contain multiple subcomponents (street, city, state, and so on). The following members are part of this control type:

### Properties

- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects an object with the following fields. `getValue()` returns the same object: `{
  line1: string;
  line2: string;
  line3: string;
  city: string;
  state: string;
  postalCode: string;
  country: string;
}`

## Boolean control

The boolean control extends the control type for radio button fields with **true/false** options. The following members are part of this control type:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

setValue() expects a string value corresponding to localized **true or false**. getValue() returns the selected option value as a string.

## DateTime control

The DateTime control extends the control type for date and time input fields. The following members are part of this control type:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**
- `isDisabled` - **true** if the field is disabled, else **false**
- `dataType` - The data type of the datetime field

`setValue()` expects a datetime string in the appropriate format. `getValue()` returns the datetime value as a string.

## Decimal control

The decimal control extends the control type for decimal number input fields. The following members are part of this control type:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid decimal number. `getValue()` returns the decimal value as a string.

## Double control

The double control extends the control type for floating-point number input fields. The following members are part of this control type:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid floating-point number. `getValue()` returns the number value as a string.

## Dropdown control

Dropdown control is an extension of control type. The following members are part of this control:

### Properties

- `isDropdown` - is always **true**. Use this property to distinguish between a modal lookup and dropdown lookup.
- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string parameter representing the ID of the option to select. `getValue()` returns the currently set option's ID as a string.

## Email control

Email control is an extension of control type for email input fields. The following members are part of this control:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid email address. `getValue()` returns the email value as a string.

## File control

File control is an extension of control type. The following members are part of this control:

### Properties

- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**
- `maxFileSizeInByte` - The max size of the file in bytes that can be uploaded.

### Methods

`setValue()` expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and `getValue()` returns the same
- `removeFile()`: Removes the set file.

## Formatted integer control

Formatted integer control is an extension of control type for integer fields with specific formatting requirements like duration, language, and timezone. The following members are part of this control:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid formatted integer. `getValue()` returns the formatted integer value as a string.

## Full name control

Full name control is an extension of control type for name input fields that might contain multiple components (first name, last name, and so on). The following members are part of this control:

`setValue()` expects an object of the following structure; `getValue()` returns the same: `{
  firstName: string;
  middleName: string;
  lastName: string;
}`

## Image control

Image control extends the control type. It includes the following other members:

### Properties

- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**
- `maxFileSizeInByte` - The maximum size of the image in bytes that you can upload.

### Methods

`setValue()` expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and `getValue()` returns the same.
- `removeFile()`: Removes the set file.

## Integer control

Integer control extends the control type for numeric input fields. It includes the following other members:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid integer. `getValue()` returns the integer value as a string.

## Memo control

Memo control extends the control type for multiline text input fields. It includes the following other members:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**
- `maxLength` - The maximum length of text that you can enter

`setValue()` expects a string value. `getValue()` returns the memo text as a string.

## Modal lookup control

Modal lookup control extends the control type. It represents a modal lookup field. It includes the following other members:

### Properties

- `IsModal` - Always **true**, use this property to distinguish between a modal lookup and dropdown.
- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**

### Methods

`setValue()` expects an object with the following interface and `getValue()` returns the same:
`{
  id: string;
  name: string;
  entityType: string;
}`
- `clearValue()`: Clears the set value from the field.

## Money control

Money control extends the control type for currency input fields. It includes the following other members:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid monetary amount. `getValue()` returns the money value as a string.

## MultipleChoice control

MultipleChoice control is an extension of control type for checkbox fields. The following members are part of this control:

`setValue()` expects a boolean value. `getValue()` returns the checkbox state as a boolean.

## MultiSelect picklist control

MultiSelect picklist control is an extension of control type for multiselect option fields. The following members are part of this control:

`setValue()` and `getValue()` aren't yet supported for this control.

## Picklist control

Picklist control is an extension of control type for option set fields (dropdown, radio buttons, etc.). The following members are part of this control:

### Properties

- `subType` - The subtype of the picklist control (VerticalRadioButton, HorizontalRadioButton, MultipleChoiceMatrix, or Dropdown)

`setValue()` expects a string representing the value of the option to select. `getValue()` returns the selected option value as a string.

## Status control

Status control represents the current state of an entity record.

Setting the value for this field isn't supported by design; it's a readonly field.

## StatusReason control

StatusReason control represents the current status reason of an entity record.

Setting the value for this field isn't supported by design; it's a readonly field.

## String control

String control is an extension of control type for text input fields. The following members are part of this control:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**
- `maxLength` - The maximum length of text that you can enter

`setValue()` expects a string value. If the string exceeds the maximum length, an error is thrown.

## Ticker symbol control

Ticker symbol control is an extension of control type for stock ticker symbol input fields. The following members are part of this control:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid ticker symbol. `getValue()` returns the ticker symbol as a string.

## URL control

URL control is an extension of control type for URL input fields. The control includes the following other members:

### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid URL. `getValue()` returns the URL value as a string.