---
title: Power Pages Client APIs Overview (preview)
description: Learn how to use Power Pages client APIs to manipulate UI components, manage forms, lists, and user authentication effectively.
#customer intent: As a developer, I want to retrieve all forms on a Power Pages site so that I can programmatically interact with them.
author: shwetamurkute
ms.author: nenandw
ms.reviewer: smurkute
ms.date: 10/28/2025
ms.topic: concept-article
---
# Power Pages Client APIs (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

The client API provides a set of methods to manipulate UI components on a Power Pages site. After the Pages libraries initialize, you can access the API through the global variable: `window.$pages.currentPage`.
Use this API to interact with forms and lists, and perform operations such as record creation, retrieval, and user authentication.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Library usage

The `onPagesClientApiReady` utility on the `window` object lets you easily use the client API. Pass a callback to `onPagesClientApiReady`. It receives the `$pages` SDK object for your business logic. The method also returns a promise that resolves to the `$pages` object, enabling asynchronous usage.

**Example1**:

```javascript
window.Microsoft.Dynamic365.Portal.onPagesClientApiReady(($pages) => {
    const forms = $pages.currentPage.forms.getAll();
    console.log(`Found ${forms.length} forms on the page.`);
});
```
**Example2**:

```javascript
let sdk = await window.Microsoft.Dynamic365.Portal.onPagesClientApiReady();
const forms = sdk.currentPage.forms.getAll();
console.log(`Found ${forms.length} forms on the page.`);
```

## $pages.currentPage.forms collection

The `$pages.currentPage.forms` collection includes methods to work with form elements on the page.

### forms getAll method

`$pages.currentPage.forms.getAll(): IForm[]`

- **Description**: Returns a collection of all forms added to the current page. See [IForm](#iform-interface).
- **Parameters**: None
- **Returns**: `IForm[]`
- **Example**: `let forms = window.$pages.currentPage.forms.getAll();`

### forms getFormById method

`$pages.currentPage.forms.getFormById(id: string): IForm`

- **Description**: Retrieves a form instance by its HTML element ID.
- **Parameters**: `id` (string): The ID of the form HTML element.
- **Returns**: A form object.
- **Example**: `let form = window.$pages.currentPage.forms.getFormById('form_#1');`

### forms getFormByName method

`$pages.currentPage.forms.getFormByName(name: string): IForm`

- **Description**: Retrieves a form instance by its name.
- **Parameters**: `name` (string): The name of the form.
- **Returns**: A form object.
- **Example**: 

  ```javascript
   let sdk = await window.Microsoft.Dynamic365.Portal.onPagesClientApiReady();
  let form = sdk.currentPage.forms.getFormByName('form_name');
   ```

### IForm interface

The `IForm` interface represents a container for controls and tabs.

- **Properties**:

  - `id`: The ID of the form.
  - `name`: The name of the form.
  - controls: `Control[]` - An array containing all controls on the form. See [Control](#control).
  - tabs: `Tab[]` - An array containing all tabs on the form. See [Tab](#tab).
  - `isMultiStep` - True if the form is multistep; otherwise, false.

- **Methods**:

  - `getVisible(): boolean` - Returns true if the form is visible; otherwise, false.
  - `setVisible(isVisible: boolean): void` - Sets the form's visibility.

- **Example**:

    ```javascript
    let form = window.$pages.currentPage.forms.getFormById('form_#1');  
    console.log(`Form id: ${form.id} has ${form.controls.length} controls.`);  
    if (form.getVisible()) {  
    console.log('Form is currently visible.');  
    }  
    let tabs = form.tabs;  
    console.log(`Form has ${tabs.length} tabs.`);
    ```

### Multistep form

A multistep form is a container that holds multiple basic forms.

- **Properties**:

  - `id`: The ID(GUID) of the multistep form.
  - `controls`: `Control[]` - An array that contains all controls in the current step. See [Control](#control).
  - `tabs`: `Tab[]` - An array that contains all tabs in the current step. See [Tab](#tab).
  - `isMultiStep` - True if the form is multistep; otherwise, false.
  - `nextButton (JQuery Element)` - jQuery object that represents the next button. It's an empty object if the button isn't present.
  - `previousButton (JQuery Element)` - jQuery object that represents the previous button. It's an empty object if the button isn't present.


- **Methods**:

  - `getVisible(): boolean` - Returns true if the form is visible; otherwise, false.
  - `setVisible(isVisible): void` - Sets the tab's visibility.
  - `isVisible (boolean)`: Specifies whether the form should be shown (true) or hidden (false) on the page.
  - `hasNextStep()`- Returns true if a next step exists; otherwise false.
  - `hasPreviousStep()`- Returns true if a previous step exists; otherwise false.
  - `goToNextStep()`- Redirects the page to the next step. If no next step is present, the form is submitted.
  - `goToPreviousStep()`- Redirects the page to the previous step. If no previous step is present, an exception is thrown.

- **Example**:
    
  ```javascript
    let sdk = await window.Microsoft.Dynamic365.Portal.onPagesClientApiReady();
    let form = sdk.currentPage.forms.getFormById('multiform_#1');
    console.log(`Form id: ${form.id} has ${form.controls.length} controls.`);
    
    if (form.getVisible()) {
      console.log('Form is currently visible.');
    }
    
    let tabs = form.tabs;
    console.log(`Form has ${tabs.length} tabs.`);
    
    form.goToNextStep();  
   ```

### Tab

A `Tab` contains one or more sections within a form.

- **Properties**:

  - *Sections*: `Section[]` - An array of sections within the tab. See [Section](#section).

- **Methods**:

  - `getVisible(): boolean` - Returns true if the tab is visible; otherwise, false.
  - `getName(): string` - Returns the name of the tab.
  - `setVisible(isVisible: boolean): void` - Sets the tab's visibility.

- **Example**:

    ```javascript
    let form = window.$pages.currentPage.forms.getFormById('form_#1');  
    let tabs = form.tabs;  
    console.log(`Form has ${tabs.length} tabs.`);  
    console.log(`First tab is named: ${tabs[0].getName()}`);  
    ```

### Section

Sections group controls within a tab.

- **Properties**:

  - *Controls*: `Control[]` - An array of controls within the section. See [Control](#control).

- **Methods**:

  - `getVisible(): boolean` - Returns true if the section is visible; otherwise, false.
  - `getName(): string` - Returns the section name.
  - `setVisible(isVisible: boolean): void` - Sets the section's visibility.

- **Example**:

    ```javascript
    let form = window.$pages.currentPage.forms.getFormById('form_#1');  
    let sections = form.tabs[0].sections;  
    console.log(`Tab has ${sections.length} section(s).`);  
    console.log(`First section is named: ${sections[0].getName()}`);
    ```

### Control

Controls represent individual form elements.

- **Methods**:

  - `getDisabled(): boolean` - Returns true if the control is disabled.
  - `getVisible(): boolean` - Returns true if the control is visible.
  - `getName(): string` - Returns the control's name.
  - `getValue(): string | undefined` - Retrieves the current value.
  - `setDisabled(isDisabled: boolean): void` - Sets the disabled state.
  - `setVisible(isVisible: boolean): void` - Sets the visibility.
  - `setValue(value: string): void` - Sets a new value for the control.

- **Example**:

    ```javascript
    let form = window.$pages.currentPage.forms.getFormById('form_#1');  
    let controls = form.controls;  
    if (controls.length > 0) {  
    if (controls[0].getVisible()) {  
    console.log(`Control ${controls[0].getName()} is visible.`);  
    }  
    controls[0].setVisible(false); // Hide the first control.  
    }
    ```

### Supported controls

The following control types are currently supported.

All these controls extend the control type. Therefore, these objects provide all the interfaces available on the control object, along with a few more.

#### Address composite control

The address composite control extends the control type for address input fields that contain multiple subcomponents (street, city, state, and so on). The following members are part of this control type:

##### Properties

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

#### Boolean control

The boolean control extends the control type for radio button fields with **true/false** options. The following members are part of this control type:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

setValue() expects a string value corresponding to localized **true or false**. getValue() returns the selected option value as a string.

#### DateTime control

The DateTime control extends the control type for date and time input fields. The following members are part of this control type:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**
- `isDisabled` - **true** if the field is disabled, else **false**
- `dataType` - The data type of the datetime field

`setValue()` expects a datetime string in the appropriate format. `getValue()` returns the datetime value as a string.

#### Decimal control

The decimal control extends the control type for decimal number input fields. The following members are part of this control type:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid decimal number. `getValue()` returns the decimal value as a string.

#### Double control

The double control extends the control type for floating-point number input fields. The following members are part of this control type:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid floating-point number. `getValue()` returns the number value as a string.

#### Dropdown control

Dropdown control is an extension of control type. The following members are part of this control:

##### Properties

- `isDropdown` - is always **true**. Use this property to distinguish between a modal lookup and dropdown lookup.
- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string parameter representing the ID of the option to select. `getValue()` returns the currently set option's ID as a string.

#### Email control

Email control is an extension of control type for email input fields. The following members are part of this control:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid email address. `getValue()` returns the email value as a string.

#### File control

File control is an extension of control type. The following members are part of this control:

##### Properties

- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**
- `maxFileSizeInByte` - The max size of the file in bytes that can be uploaded.

##### Methods

`setValue()` expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and `getValue()` returns the same
- `removeFile()`: Removes the set file.

#### Formatted integer control

Formatted integer control is an extension of control type for integer fields with specific formatting requirements like duration, language, and timezone. The following members are part of this control:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid formatted integer. `getValue()` returns the formatted integer value as a string.

#### Full name control

Full name control is an extension of control type for name input fields that might contain multiple components (first name, last name, and so on). The following members are part of this control:

`setValue()` expects an object of the following structure; `getValue()` returns the same: `{
  firstName: string;
  middleName: string;
  lastName: string;
}`

#### Image control

Image control extends the control type. It includes the following other members:

##### Properties

- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**
- `maxFileSizeInByte` - The maximum size of the image in bytes that you can upload.

##### Methods

`setValue()` expects an object of type [File](https://developer.mozilla.org/en-US/docs/Web/API/File) and `getValue()` returns the same.
- `removeFile()`: Removes the set file.

#### Integer control

Integer control extends the control type for numeric input fields. It includes the following other members:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid integer. `getValue()` returns the integer value as a string.

#### Memo control

Memo control extends the control type for multiline text input fields. It includes the following other members:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**
- `maxLength` - The maximum length of text that you can enter

`setValue()` expects a string value. `getValue()` returns the memo text as a string.

#### Modal lookup control

Modal lookup control extends the control type. It represents a modal lookup field. It includes the following other members:

##### Properties

- `IsModal` - Always **true**, use this property to distinguish between a modal lookup and dropdown.
- `IsReadonly` - **true** if the field is a read-only field, otherwise **false**

##### Methods

`setValue()` expects an object with the following interface and `getValue()` returns the same:
`{
  id: string;
  name: string;
  entityType: string;
}`
- `clearValue()`: Clears the set value from the field.

#### Money control

Money control extends the control type for currency input fields. It includes the following other members:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid monetary amount. `getValue()` returns the money value as a string.

#### MultipleChoice control

MultipleChoice control is an extension of control type for checkbox fields. The following members are part of this control:

`setValue()` expects a boolean value. `getValue()` returns the checkbox state as a boolean.

#### MultiSelect picklist control

MultiSelect picklist control is an extension of control type for multiselect option fields. The following members are part of this control:

`setValue()` and `getValue()` aren't yet supported for this control.

#### Picklist control

Picklist control is an extension of control type for option set fields (dropdown, radio buttons, etc.). The following members are part of this control:

##### Properties

- `subType` - The subtype of the picklist control (VerticalRadioButton, HorizontalRadioButton, MultipleChoiceMatrix, or Dropdown)

`setValue()` expects a string representing the value of the option to select. `getValue()` returns the selected option value as a string.

#### Status control

Status control represents the current state of an entity record.

Setting the value for this field isn't supported by design; it's a readonly field.

#### StatusReason control

StatusReason control represents the current status reason of an entity record.

Setting the value for this field isn't supported by design; it's a readonly field.

#### String control

String control is an extension of control type for text input fields. The following members are part of this control:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**
- `maxLength` - The maximum length of text that you can enter

`setValue()` expects a string value. If the string exceeds the maximum length, an error is thrown.

#### Ticker symbol control

Ticker symbol control is an extension of control type for stock ticker symbol input fields. The following members are part of this control:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid ticker symbol. `getValue()` returns the ticker symbol as a string.

#### URL control

URL control is an extension of control type for URL input fields. The control includes the following other members:

##### Properties

- `isReadOnly` - **true** if the field is a read-only field, otherwise **false**

`setValue()` expects a string representing a valid URL. `getValue()` returns the URL value as a string.

## $pages.currentPage.lists collection

The lists collection offers methods to handle traditional and modern list elements on the page.

### lists getAll method

`$pages.currentPage.lists.getAll(): IList[]`

- **Description**: Returns a collection of all lists on the current page. See [IList interface](#ilist-interface).
- **Parameters**: None
- **Returns**: `IList[]`
- **Example**: `let lists = window.$pages.currentPage.lists.getAll();`

### getListById method

`$pages.currentPage.lists.getListById(id: string): IList`

- **Description**: Retrieves an `IList` instance by its HTML element ID. See [IList interface](#ilist-interface).
- **Parameters**: `id (string)`: The ID of the list HTML element.
- **Returns**: A list object.
- **Example**: `let list = window.$pages.currentPage.lists.getListById('list_#1');`

### IList interface

A list represents a tabular or grid-like data component.

- **Properties**:

  - `id`: The list's unique identifier.
  - `isModern`: A Boolean value that's true for modern lists and false otherwise.

- **Methods**:

  - `getVisible(): boolean` - Returns true if the list is visible.
  - `setVisible(isVisible: boolean): void` - Sets the list's visibility.
  - `getHtmlElement(): HTMLElement` - Returns the underlying HTML element for the list.

- **Example**:

    ```javascript
    let list = window.$pages.currentPage.lists.getListById('list_#1');  
    console.log(`List id: ${list.id}`);  
    if (list.getVisible()) {  
    console.log('List is currently visible.');  
    }
    ```

## $pages.user object

The `$pages.user` object provides methods to sign the user in or out.

### signIn method

`$pages.user.signIn(): void`

- **Description**: Redirects the user to the sign-in page.
- **Parameters**: None
- **Returns**: void
- **Example**: `window.$pages.user.signIn();`

### signOut method

`$pages.user.signOut(): void`

- **Description**: Signs out the currently signed-in user.
- **Parameters**: None
- **Returns**: void
- **Example**: `window.$pages.user.signOut();`

## $pages.webAPI object

The `$pages.webAPI` object provides methods to create and retrieve records from a data source.

### createRecord method

`$pages.webAPI.createRecord(entitySetName: string, data: object): Promise<object>`

- **Description**: Creates a new record in the specified table.
- **Parameters**:

  - `entitySetName` (string): The name of the entity set.
  - `data` (object): The record data to create.

- **Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the created record or operation result.
- **Example**:

   ```javascript
   window.$pages.webAPI.createRecord('account', {  
   firstName: 'User',
   lastName: 'Test'  
   });
   ```

### retrieveRecord method

`$pages.webAPI.retrieveRecord(entitySetName: string, id: string, options?: string): Promise<object>`

- **Description**: Retrieves a record by its unique identifier.
- **Parameters**:

  - `entitySetName` (string): The name of the entity set.
  - `id` (string): The record's unique identifier.
  - `options` (string, optional): An optional OData query string to customize the returned data.

- **Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the record object.
- **Example**:

   `let record = await window.$pages.webAPI.retrieveRecord('accounts', '123',  '$select=name');`

### retrieveMultipleRecords

`$pages.webAPI.retrieveMultipleRecords(entitySetName: string, options?: string): Promise<object>`

- **Description**: Retrieves multiple records based on the provided query options.
- **Parameters**:

  - `entitySetName` (string): The name of the entity set.
  - `options` (string, optional): An OData query string to filter or select specific fields.

- **Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to an array of record objects.
- **Example**:

   `let records = await window.$pages.webAPI.retrieveMultipleRecords('accounts','$select=name&$top=3');`
