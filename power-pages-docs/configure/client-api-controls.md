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

The following control types are currently supported. All these controls have all the common core [control methods](client-api.md#control-methods), however some method details may be implemented differently and some will have their own properties and methods.


## Address composite

Address input fields that contain multiple subcomponents (street, city, state, and so on) use the address composite control.

### Address composite properties and methods

- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects an object with the following properties:

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
- `setValue` method expects a string value corresponding to localized **true or false** values
- `getValue` method returns the selected option value as a string

## DateTime

Date and time input fields use the dateTime control.

### DateTime properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `isDisabled` property - True if the field is disabled, otherwise false
- `dataType` property - The data type of the datetime field
- `setValue` method expects a datetime string in the appropriate format
- `getValue` method returns the datetime value as a string.

## Decimal

Decimal number input fields use the decimal control.

### Decimal properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid decimal number
- `getValue` returns the decimal value as a string

## Double

Floating-point number input fields use the double control.

### Double properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid floating-point number.
- `getValue` method returns the number value as a string.

## Dropdown lookup

<!-- TODO: Need a clear description about what a dropdown lookup control is. Seems it isn't a picklist, and is actually some kind of lookup? -->

### Dropdown properties and methods

- `isDropdown` property - Is always **true**. Use this property to distinguish between a [modal lookup](#modal-lookup) and dropdown lookup
- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string parameter representing the ID of the option to select
- `getValue` method returns the currently set option's ID as a string

## Email

Email input fields use the email control.

### Email properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` expects a string representing a valid email address
- `getValue` returns the email value as a string

## File

<!-- TODO: Need a clear description about what a file control is. I expect it provides capabilities to upload and download a file -->

### File properties and methods

- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `maxFileSizeInByte` property - The max size of the file in bytes that can be uploaded
- `setValue` method expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `getValue` method returns an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `removeFile` method removes the set file

## Formatted integer

Integer fields with specific formatting requirements like duration, language, and timezone use the formatted integer control.

### Formatted integer properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid formatted integer
- `getValue` method returns the formatted integer value as a string

## Full name

Name input fields that might contain multiple components (first name, last name, and so on) use the full name control

### Full name methods

- `setValue` method expects an object with the following properties:

   ```json
   {
   "firstName": "first name value",
   "middleName": "middle name value",
   "lastName": "last name value"
   }
   ```

- `getValue` method returns the same object

## Image

<!-- TODO: Need a clear description about what a Image control is. I expect it provides capabilities to view, upload, and download a Image -->

### Image properties and methods

- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `maxFileSizeInByte` property - The maximum size of the image in bytes that you can upload
- `setValue` method expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `getValue` method returns an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `removeFile` method removes the set image

## Integer

Numeric input fields use the integer control

###  Integer properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid integer
- `getValue` method returns the integer value as a string.

## Memo

Multiline text input fields use the memo control

### Memo properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `maxLength` property - The maximum length of text that you can enter
- `setValue` method expects a string value
- `getValue` method returns the memo text as a string

## Modal lookup

Modal lookup fields use the modal lookup control

### Modal lookup properties and methods

- `IsModal` property - Always true. Use this property to distinguish between a modal lookup and dropdown lookup.
- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects an object with the following properties:

   ```json
   {
   "id": "The unique identifier of the record.",
   "name": "The primary name field value of the record",
   "entityType": "The entity type name value of the table."
   }
   ```

- `getValue` method returns the same object
- `clearValue` method clears the set value from the field.

## Money

Currency input fields use the money control

### Money properties and methods

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid monetary amount
- `getValue` method returns the money value as a string

## MultipleChoice

MultipleChoice control is an extension of control type for checkbox fields. 

`setValue` expects a boolean value. `getValue` returns the checkbox state as a boolean.

## MultiSelect picklist

MultiSelect picklist control is an extension of control type for multiselect option fields. 

`setValue` and `getValue` aren't yet supported for this control.

## Picklist

Picklist control is an extension of control type for option set fields (dropdown, radio buttons, etc.). 

### Picklist properties and methods

- `subType` - The subtype of the picklist control (VerticalRadioButton, HorizontalRadioButton, MultipleChoiceMatrix, or Dropdown)

`setValue` expects a string representing the value of the option to select. `getValue` returns the selected option value as a string.

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

`setValue` expects a string value. If the string exceeds the maximum length, an error is thrown.

## Ticker symbol

Ticker symbol control is an extension of control type for stock ticker symbol input fields. 

### Ticker symbol properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue` expects a string representing a valid ticker symbol. `getValue` returns the ticker symbol as a string.

## URL

URL control is an extension of control type for URL input fields. The control includes the following other members:

### URL properties and methods

- `isReadOnly` - True if the field is a read-only field, otherwise false

`setValue` expects a string representing a valid URL. `getValue` returns the URL value as a string.