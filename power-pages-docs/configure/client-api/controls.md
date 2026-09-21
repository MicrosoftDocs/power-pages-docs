---
title: Client API control types (preview)
description: Learn about the control types supported by the Power Pages Client API.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API control types (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article lists the supported control types. All controls have the [common control methods](control-methods.md), but some methods use different value types and some controls have additional members.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

| Control Type | Description |
| --- | --- |
| [Address composite](#address-composite) | Provides address input fields with multiple subcomponents, such as street, city, and state. |
| [Boolean](#boolean) | Provides radio button fields with true or false options. |
| [DateTime](#datetime) | Provides date and time input fields. |
| [Decimal](#decimal) | Provides decimal number input fields. |
| [Double](#double) | Provides floating-point number input fields. |
| [Dropdown lookup](#dropdown-lookup) | Provides a nonmodal dropdown for selecting a related record. |
| [Email](#email) | Provides email address input fields. |
| [File](#file) | Lets someone select a file for an editable form. |
| [Formatted integer](#formatted-integer) | Provides integer fields formatted as values such as durations, languages, and time zones. |
| [Full name](#full-name) | Provides name input fields with multiple components, such as first and last name. |
| [Image](#image) | Lets someone select an image for an editable form. |
| [Integer](#integer) | Provides numeric integer input fields. |
| [Memo](#memo) | Provides multiline text input fields. |
| [Modal lookup](#modal-lookup) | Provides a modal dialog for selecting a related record. |
| [Money](#money) | Provides currency input fields. |
| [Multiple choice](#multiple-choice) | Provides checkbox fields. |
| [MultiSelect picklist](#multiselect-picklist) | Provides fields for selecting multiple options. |
| [Picklist](#picklist) | Provides option set fields, such as dropdowns and radio buttons. |
| [Status](#status) | Provides the current state of a table record as a read-only value. |
| [Status reason](#status-reason) | Provides the current status reason of a table record as a read-only value. |
| [String](#string) | Provides single-line text input fields. |
| [Ticker symbol](#ticker-symbol) | Provides stock ticker symbol input fields. |
| [URL](#url) | Provides URL input fields. |

## Address composite

Address input fields that contain multiple subcomponents, such as street, city, and state, use the address composite control.

### Address composite properties and methods

Use these members to configure and read address composite values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | See [setValue method parameter](#setvalue-method-parameter). |
| `getValue` | Method | Returns the same object. |

#### setValue method parameter

Expects an object with the following properties.

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

## Boolean

Radio button fields with **true/false** options use the Boolean control.

### Boolean properties and methods

Use these members to set and retrieve Boolean field values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string value corresponding to localized **true or false** values |
| `getValue` | Method | Returns the selected option value as a string |

## DateTime

Date and time input fields use the DateTime control.

### DateTime properties and methods

Use these members to manage and access date and time values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `isDisabled` | Property | Returns `true` if the field is disabled, otherwise `false`. |
| `dataType` | Property | The data type of the datetime field |
| `setValue` | Method | Expects a datetime string in the appropriate format |
| `getValue` | Method | Returns the datetime value as a string. |

## Decimal

Decimal number input fields use the Decimal control.

### Decimal properties and methods

Use these members to work with decimal number inputs.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid decimal number. |
| `getValue` | Method | Returns the decimal value as a string. |

## Double

Floating-point number input fields use the Double control.

### Double properties and methods

Use these members to handle floating-point number values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid floating-point number. |
| `getValue` | Method | Returns the number value as a string. |

## Dropdown lookup

Lookup controls that aren't modal use the dropdown lookup control.

### Dropdown properties and methods

Use these members to interact with dropdown lookup selections.

| Member | Kind | Description |
|--------|------|-------------|
| `isDropdown` | Property | Is always **true**. Use this property to distinguish between a [modal lookup](#modal-lookup) and dropdown lookup. |
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string parameter representing the ID of the option to select. |
| `getValue` | Method | Returns an object of the form `{ id: string, name: string }` for the selected option, or **undefined** when no option is selected. |

## Email

Email input fields use the Email control.

### Email properties and methods

Use these members to validate and retrieve email address values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid email address. |
| `getValue` | Method | Returns the email value as a string. |

## File

The File control lets someone select a file for an editable form.

### File properties and methods

Use these members to select, access, and remove files.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `maxFileSizeInByte` | Property | The maximum size of the file in bytes that you can upload. |
| `setValue` | Method | Expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and sets it as if someone selected it with the file picker. The method throws an error when the file is empty or exceeds `maxFileSizeInByte`. |
| `getValue` | Method | Returns the [File](https://developer.mozilla.org/en-US/docs/Web/API/File) object that you selected or set during the current form session. It doesn't download a file that's already stored in Dataverse. |
| `removeFile` | Method | Removes the set file. |

To download a file that's stored in a Dataverse file column, use the [`downloadFileFromColumn` method](dataverse.md#downloadfilefromcolumn-method).

## Formatted integer

Integer fields with specific formatting requirements like duration, language, and timezone use the formatted integer control.

### Formatted integer properties and methods

Use these members to manage integers with specialized formatting.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid formatted integer. |
| `getValue` | Method | Returns the formatted integer value as a string. |

## Full name

Name input fields that might contain multiple components (first name, last name, and so on) use the full name control.

### Full name methods

Use these members to configure and read full name components.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects an object with the following properties: `{ "firstName": "first name value", "middleName": "middle name value", "lastName": "last name value" }`. |
| `getValue` | Method | Returns the same object. |

## Image

The Image control lets someone select an image for an editable form.

### Image properties and methods

Use these members to select, access, and remove images.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `maxFileSizeInByte` | Property | The maximum size of the image in bytes that you can upload. |
| `setValue` | Method | Expects an image of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and sets it as if someone selected it with the file picker. The method throws an error when the file is empty, exceeds `maxFileSizeInByte`, or doesn't have an image MIME type. |
| `getValue` | Method | Returns the [File](https://developer.mozilla.org/en-US/docs/Web/API/File) object that you selected or set during the current form session. It doesn't download an image that's already stored in Dataverse. |
| `removeFile` | Method | Removes the set image. |

To download an image that's stored in a Dataverse image column, use the [`downloadFileFromColumn` method](dataverse.md#downloadfilefromcolumn-method).

## Integer

Numeric input fields use the Integer control.

### Integer properties and methods

Use these members to set and retrieve integer field values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid integer. |
| `getValue` | Method | Returns the integer value as a string. |

## Memo

Multiline text input fields use the Memo control.

### Memo properties and methods

Use these members to manage multiline text input content.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string value. The method throws an error when the value exceeds the field's configured maximum length. |
| `getValue` | Method | Returns the memo text as a string. |

## Modal lookup

Modal lookup fields use the modal lookup control.

### Modal lookup properties and methods

Use these members to set, get, and clear modal lookup values.

| Member | Kind | Description |
|--------|------|-------------|
| `isModal` | Property | Always true. Use this property to distinguish between a modal lookup and dropdown lookup. |
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects an object with the following properties: { "id": "The unique identifier of the record.", "name": "The primary name field value of the record", "entityType": "The entity type name value of the table." } |
| `getValue` | Method | Returns the same object. |
| `clearValue` | Method | Clears the set value from the field. |

## Money

Currency input fields use the Money control.

### Money properties and methods

Use these members to set and retrieve currency amounts.

| Member | Kind | Description |
|--------|------|-------------|
| `readOnly` | Property | `true` if the field is a read-only field, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid monetary amount. |
| `getValue` | Method | returns the money value as a string. |

## Multiple choice

Checkbox fields use the multiple choice control.

### Multiple choice methods

Use these methods to set and read checkbox states.

| Member | Kind | Description |
|--------|------|-------------|
| `setValue` | Method | Expects a boolean value. |
| `getValue` | Method | returns the checkbox state as a boolean. |

## MultiSelect picklist

Multiselect option fields use the MultiSelect picklist control.

### MultiSelect picklist methods

Use these methods to set and read the selected options.

| Member | Kind | Description |
|--------|------|-------------|
| `setValue` | Method | Expects an array of numbers that represent the option values to select. Returns an error if a value isn't one of the available options. |
| `getValue` | Method | Returns the selected option values as an array of numbers. |
| `setDisabled` | Method | Has no effect when the form or the field is read-only, because the control is locked on the server. |

The following example reads and sets the selected options.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let form = $pages.currentPage.forms.getFormById('form_#1');
    let control = form && form.controls.find(c => c.getType() === 'MultiSelectPicklist');

    if (!control) {
        return;
    }

    // Get the selected values.
    let selectedValues = control.getValue(); // For example, [740740000, 740740001]

    // Set the selected values.
    control.setValue([740740000, 740740001]);
});
```

## Picklist

Option set fields (dropdown, radio buttons, and so on) use the Picklist control.

### Picklist properties and methods

Use these members to configure and read option set selections.

| Member | Kind | Description |
|--------|------|-------------|
| `subType` | Property | The subtype of the picklist control. Possible values are: `VerticalRadioButton`, `HorizontalRadioButton`, `MultipleChoiceMatrix`, `Dropdown` |
| `setValue` | Method | Expects a string representing the value of the option to select. |
| `getValue` | Method | Returns the selected option value as a string. |

## Status

The current state of an entity record uses the Status control.

> [!NOTE]
> This control doesn't allow setting the value. The value is read-only.

## Status reason

The current status reason of an entity record uses the status reason control.

> [!NOTE]
> This control doesn't allow setting the value. The value is read-only.

## String

Text input fields use the String control.

### String properties and methods

Use these members to manage single-line text input values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string value. The method throws an error when the value exceeds the field's configured maximum length. |
| `getValue` | Method | Returns the string value. |

## Ticker symbol

Stock ticker symbol input fields use the ticker symbol control.

### Ticker symbol properties and methods

Use these members to set and retrieve stock ticker symbols.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid ticker symbol. |
| `getValue` | Method | Returns the ticker symbol as a string. |

## URL

URL input fields use the URL control.

### URL properties and methods

Use these members to validate and retrieve URL values.

| Member | Kind | Description |
|--------|------|-------------|
| `isReadOnly` | Property | Returns `true` if the field is read-only, otherwise `false`. |
| `setValue` | Method | Expects a string representing a valid URL. |
| `getValue` | Method | Returns the URL value as a string. |

## Related information

- [Client API overview](index.md)
- [Power Pages Client API examples](examples.md)
