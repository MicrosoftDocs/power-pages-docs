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

The following control types are currently supported. All these controls have all the common core [control properties and methods](client-api.md#control), however some method details may be implemented differently and some will have their own properties and methods.


## Address composite

Address input fields that contain multiple subcomponents (street, city, state, and so on) use the address composite control.

### Address composite properties and methods

- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects an object with the following fields.

   ```json
   {
   "line1": "address line one value",
   "line2": "address line two value",
   "line3": "address line three value",
   "city": "address city value",
   "state": "address state value",
   "postalCode": "address postalCode value",
   "country": "address country value",
   }
   ```

- `getValue` method returns the same object.

## Boolean

Radio button fields with **true/false** options use the boolean control.

### Boolean properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string value corresponding to localized **true or false**
- `getValue` method returns the selected option value as a string

## DateTime

Date and time input fields use the DateTime control

### DateTime properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `isDisabled` property - True if the field is disabled, otherwise false
- `dataType` property - The data type of the datetime field
- `setValue` method expects a datetime string in the appropriate format
- `getValue` method returns the datetime value as a string.

## Decimal

Decimal number input fields use the decimal control.

### Decimal properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid decimal number. `getValue()` returns the decimal value as a string.

## Double

The double control extends the control type for floating-point number input fields. 

### Double properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid floating-point number. `getValue()` returns the number value as a string.

## Dropdown

Dropdown control is an extension of control type. 

### Dropdown properties and methods

- `isDropdown` - is always **true**. Use this property to distinguish between a modal lookup and dropdown lookup.
- `IsReadonly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string parameter representing the ID of the option to select. `getValue()` returns the currently set option's ID as a string.

## Email

Email control is an extension of control type for email input fields. 

### Email properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid email address. `getValue()` returns the email value as a string.

## File

File control is an extension of control type. 

### File properties and methods

- `IsReadonly` - True if the field is a read-only field, otherwise false
- `maxFileSizeInByte` - The max size of the file in bytes that can be uploaded.

### Methods

`setValue()` expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and `getValue()` returns the same
- `removeFile()`: Removes the set file.

## Formatted integer

Formatted integer control is an extension of control type for integer fields with specific formatting requirements like duration, language, and timezone. 

### Formatted integer properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid formatted integer. `getValue()` returns the formatted integer value as a string.

## Full name

Full name control is an extension of control type for name input fields that might contain multiple components (first name, last name, and so on). 

`setValue()` expects an object of the following structure; `getValue()` returns the same: `{
  firstName: string;
  middleName: string;
  lastName: string;
}`

## Image

Image control extends the control type. 

### Image properties and methods

- `IsReadonly` - True if the field is a read-only field, otherwise false
- `maxFileSizeInByte` - The maximum size of the image in bytes that you can upload.

### Methods

`setValue()` expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and `getValue()` returns the same.
- `removeFile()`: Removes the set file.

## Integer

Integer control extends the control type for numeric input fields. 

###  Integer properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid integer. `getValue()` returns the integer value as a string.

## Memo

Memo control extends the control type for multiline text input fields. 

###  Memo properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false
- `maxLength` - The maximum length of text that you can enter

`setValue()` expects a string value. `getValue()` returns the memo text as a string.

## Modal lookup

Modal lookup control extends the control type. It represents a modal lookup field. 

### Modal lookup properties and methods

- `IsModal` - Always **true**, use this property to distinguish between a modal lookup and dropdown.
- `IsReadonly` - True if the field is a read-only field, otherwise false

### Methods

`setValue()` expects an object with the following interface and `getValue()` returns the same:
`{
  id: string;
  name: string;
  entityType: string;
}`
- `clearValue()`: Clears the set value from the field.

## Money

Money control extends the control type for currency input fields. 

### Money properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid monetary amount. `getValue()` returns the money value as a string.

## MultipleChoice

MultipleChoice control is an extension of control type for checkbox fields. 

`setValue()` expects a boolean value. `getValue()` returns the checkbox state as a boolean.

## MultiSelect picklist

MultiSelect picklist control is an extension of control type for multiselect option fields. 

`setValue()` and `getValue()` aren't yet supported for this control.

## Picklist

Picklist control is an extension of control type for option set fields (dropdown, radio buttons, etc.). 

### Picklist properties and methods

- `subType` - The subtype of the picklist control (VerticalRadioButton, HorizontalRadioButton, MultipleChoiceMatrix, or Dropdown)

`setValue()` expects a string representing the value of the option to select. `getValue()` returns the selected option value as a string.

## Status

Status control represents the current state of an entity record.

Setting the value for this field isn't supported by design; it's a readonly field.

## StatusReason

StatusReason control represents the current status reason of an entity record.

Setting the value for this field isn't supported by design; it's a readonly field.

## String

String control is an extension of control type for text input fields. 

### String properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false
- `maxLength` - The maximum length of text that you can enter

`setValue()` expects a string value. If the string exceeds the maximum length, an error is thrown.

## Ticker symbol

Ticker symbol control is an extension of control type for stock ticker symbol input fields. 

### Ticker symbol properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid ticker symbol. `getValue()` returns the ticker symbol as a string.

## URL

URL control is an extension of control type for URL input fields. The control includes the following other members:

### URL properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue()` expects a string representing a valid URL. `getValue()` returns the URL value as a string.