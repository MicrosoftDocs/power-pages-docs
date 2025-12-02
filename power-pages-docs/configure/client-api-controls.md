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

The following control types are currently supported. All these controls have all the common core [control methods](client-api.md#control-methods), however some method details might be implemented differently, and some have their own properties and methods.


## Address composite

Address input fields that contain multiple subcomponents (street, city, state, and so on) use the address composite control.

### Address composite properties and methods

Use these members to configure and read address composite values.

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
   "country": "address country value"
   }
   ```

- `getValue` method returns the same object.

## Boolean

Radio button fields with **true/false** options use the boolean control.

### Boolean properties and methods

Use these members to set and retrieve boolean field values.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string value corresponding to localized **true or false** values
- `getValue` method returns the selected option value as a string

## DateTime

Date and time input fields use the dateTime control.

### DateTime properties and methods

Use these members to manage and access date and time values.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `isDisabled` property - True if the field is disabled, otherwise false
- `dataType` property - The data type of the datetime field
- `setValue` method expects a datetime string in the appropriate format
- `getValue` method returns the datetime value as a string.

## Decimal

Decimal number input fields use the decimal control.

### Decimal properties and methods

Use these members to work with decimal number inputs.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid decimal number
- `getValue` returns the decimal value as a string

## Double

Floating-point number input fields use the double control.

### Double properties and methods

Use these members to handle floating-point number values.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid floating-point number.
- `getValue` method returns the number value as a string.

## Dropdown lookup

Lookup controls that aren't modal use the dropdown lookup control.

### Dropdown properties and methods

Use these members to interact with dropdown lookup selections.

- `isDropdown` property - Is always **true**. Use this property to distinguish between a [modal lookup](#modal-lookup) and dropdown lookup
- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string parameter representing the ID of the option to select
- `getValue` method returns the currently set option's ID as a string

## Email

Email input fields use the email control.

### Email properties and methods

Use these members to validate and retrieve email address values.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` expects a string representing a valid email address
- `getValue` returns the email value as a string

## File

The file control provides capabilities to upload and download a file.

### File properties and methods

Use these members to upload, access, and remove files.

- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `maxFileSizeInByte` property - The max size of the file in bytes that can be uploaded
- `setValue` method expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `getValue` method returns an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `removeFile` method removes the set file

## Formatted integer

Integer fields with specific formatting requirements like duration, language, and timezone use the formatted integer control.

### Formatted integer properties and methods

Use these members to manage integers with specialized formatting.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid formatted integer
- `getValue` method returns the formatted integer value as a string

## Full name

Name input fields that might contain multiple components (first name, last name, and so on) use the full name control

### Full name methods

Use these methods to set and get full name components.

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

The image control provides capabilities to view, upload, and download an image.

### Image properties and methods

Use these members to upload, access, and remove images.

- `IsReadonly` property - True if the field is a read-only field, otherwise false
- `maxFileSizeInByte` property - The maximum size of the image in bytes that you can upload
- `setValue` method expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `getValue` method returns an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
- `removeFile` method removes the set image

## Integer

Numeric input fields use the integer control

### Integer properties and methods

Use these members to set and retrieve integer field values.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid integer
- `getValue` method returns the integer value as a string.

## Memo

Multiline text input fields use the memo control

### Memo properties and methods

Use these members to manage multiline text input content.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `maxLength` property - The maximum length of text that you can enter
- `setValue` method expects a string value
- `getValue` method returns the memo text as a string

## Modal lookup

Modal lookup fields use the modal lookup control

### Modal lookup properties and methods

Use these members to set, get, and clear modal lookup values.

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

Currency input fields use the money control.

### Money properties and methods

Use these members to set and retrieve currency amounts.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid monetary amount
- `getValue` method returns the money value as a string

## Multiple choice

Checkbox fields use the multiple choice control

### Multiple choice methods

Use these methods to set and read checkbox states.

- `setValue` method expects a boolean value
- `getValue` method returns the checkbox state as a boolean

## MultiSelect picklist

Multiselect option fields use the multiSelect picklist control.

> [!NOTE]
> `setValue` and `getValue` methods aren't yet supported for this control.


## Picklist

Option set fields (dropdown, radio buttons, and so on) use the picklist control.

### Picklist properties and methods

Use these members to configure and read option set selections.

- `subType` property - The subtype of the picklist control. Possible values are:

  - `VerticalRadioButton`
  - `HorizontalRadioButton`
  - `MultipleChoiceMatrix`
  - `Dropdown`

- `setValue` method expects a string representing the value of the option to select.
- `getValue` method returns the selected option value as a string.

## Status

The current state of an entity record uses the status control.

> [!NOTE]
> This control doesn't allow setting the value. The value is read-only.

## Status reason

The current status reason of an entity record uses the status reason control.

> [!NOTE]
> This control doesn't allow setting the value. The value is read-only.

## String

Text input fields use the string control.

### String properties and methods

Use these members to manage single-line text input values.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `maxLength` property - The maximum length of text that you can enter
- `setValue` An error occurs if the string length exceeds the `maxLength` value

## Ticker symbol

Stock ticker symbol input fields use the ticker symbol control

### Ticker symbol properties and methods

Use these members to set and retrieve stock ticker symbols.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid ticker symbol
- `getValue` method returns the ticker symbol as a string

## URL

URL input fields use the url control.

### URL properties and methods

Use these members to validate and retrieve URL values.

- `isReadOnly` property - True if the field is a read-only field, otherwise false
- `setValue` method expects a string representing a valid URL
- `getValue` method returns the URL value as a string
