---
title: Power Pages Client APIs Overview (preview)
description: Learn how to use Power Pages client APIs to manipulate UI components, manage forms, lists, and user authentication effectively.
#customer intent: As a developer, I want to retrieve all forms on a Power Pages site so that I can programmatically interact with them.
author: shwetamurkute
ms.author: nenandw
ms.reviewer: smurkute
ms.date: 12/01/2025
ms.topic: reference
---
# Power Pages Client APIs (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

The client API provides objects and methods to manipulate UI components on a Power Pages site. After the client API is initialized, you can access it using a global variable with a name you decide.

> [!NOTE]
> This article uses the variable name `$pages` and we recommend you also follow this naming convention.

Use the `$pages` client API to interact with forms and lists, and perform operations such as record creation, retrieval, and user authentication.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## API initialization

The `$pages` client API isn't initialized immediately when the page loads. Use the `Microsoft.Dynamic365.Portal.onPagesClientApiReady` function to assign the `$pages` API object. There are two approaches to achieve this:


### Callback-based API readiness

Use a callback function that assigns the api object to a variable you define when it is ready. Two examples show how to do this.

With an anonymous function:

```javascript
Microsoft.Dynamic365.Portal.onPagesClientApiReady(($pages) => {
    const forms = $pages.currentPage.forms.getAll();
    console.log(`Found ${forms.length} forms on the page.`);
});
```

With a named function:

```javascript
function start($pages){
    const forms = $pages.currentPage.forms.getAll();
    console.log(`Found ${forms.length} forms on the page.`);
}

Microsoft.Dynamic365.Portal.onPagesClientApiReady(start)
```


### Promise/await-based API readiness

Uses [await](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/await) to handle the promise returned by the `Microsoft.Dynamic365.Portal.onPagesClientApiReady` function for a cleaner async flow.

```javascript
let $pages = await Microsoft.Dynamic365.Portal.onPagesClientApiReady();
const forms = $pages.currentPage.forms.getAll();
console.log(`Found ${forms.length} forms on the page.`);
```

### When to use each approach

The following table describes when you should use each approach.

| Approach | When to use |
|----------|-------------|
| **[Callback-based API readiness](#callback-based-api-readiness)** | Use when you need to support older browsers or legacy scripts that don't support `async/await`, or when you want to register multiple handlers that run when the API is ready. Ideal for event-driven patterns. |
| **[Promise/await-based API readiness](#promiseawait-based-api-readiness)** | Use in modern JavaScript environments that support `async/await` for cleaner, sequential code. Best when your logic depends on the API being ready before continuing execution. |

> [!TIP]
> If your codebase already uses `async/await`, prefer the Promise-based approach for consistency.

## $pages.currentPage.forms collection

The `$pages.currentPage.forms` collection includes methods to work with form elements on the page.

### forms getAll method

Returns a collection of all forms added to the current page.

**Syntax**: `$pages.currentPage.forms.getAll(): IForm[]`<br />
**Returns**: [IForm](#iform-interface)`[]`<br />
**Example**: `let forms = window.$pages.currentPage.forms.getAll();`

### forms getFormById method

Retrieves a form instance by its HTML element ID.

**Syntax**: `$pages.currentPage.forms.getFormById(id: string): IForm`<br />
**Parameter**: `id` (string): The ID of the form HTML element.<br />
**Returns**: A [form](#iform-interface) object.<br />
**Example**: `let form = window.$pages.currentPage.forms.getFormById('form_#1');`

### forms getFormByName method

Retrieves a form instance by its name.

**Syntax**: `$pages.currentPage.forms.getFormByName(name: string): IForm`<br />
**Parameter**: `name` (string): The name of the form.<br />
**Returns**: A [form](#iform-interface) object.<br />
**Example**: `let form = $pages.currentPage.forms.getFormByName('form_name');`

### IForm interface

The `IForm` interface represents a container for controls and tabs.

### IForm properties

The following properties describe the form and its contained controls and tabs.

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | The ID of the form. |
| `name` | string | The name of the form. |
| `controls` | [Control](#control)`[]` | All controls on the form.|
| `tabs` | [Tab](#tab)`[]` | All tabs on the form.|
| `isMultiStep` | boolean | True if the form is multistep; otherwise, false. |

### IForm methods

Use these methods to query a form's visibility and toggle whether it is shown.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the form is visible; otherwise, false. |
| `setVisible(isVisible: boolean)` | `void` | Sets the form's visibility. |


### IForm example

The following example retrieves a form by ID and logs its visibility, number of controls, and tabs.

```javascript
let form = $pages.currentPage.forms.getFormById('form_#1');

console.log(`Form id: ${form.id} has ${form.controls.length} controls.`); 

if (form.getVisible()) {  
console.log('Form is currently visible.');  
}  
let tabs = form.tabs;  
console.log(`Form has ${tabs.length} tabs.`);
```

### Multistep form

A multistep form is a container that holds multiple basic forms.

#### Multistep form properties


The following properties apply to the multistep form container and describe what is available in the currently active step.

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | The ID of the multistep form. |
| `controls` | [Control](#control)`[]` | All controls in the current step. |
| `tabs` | [Tab](#tab)`[]` | All tabs in the current step.|
| `isMultiStep` | boolean | True if the form is multistep; otherwise, false. |
| `nextButton` | [JQuery Element](https://api.jquery.com/Types/#Element) | Represents the next button (empty object if absent). |
| `previousButton` | [JQuery Element](https://api.jquery.com/Types/#Element) | Represents the previous button (empty object if absent). |


#### Multistep form methods

Use these methods to check visibility and move between steps in a multistep form.



| Name | Returns | Description |
|------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the form is visible; otherwise, false. |
| `setVisible(isVisible: boolean)` | `void` | Sets the form's visibility. |
| `isVisible` | `boolean` | Property indicating whether the form should be shown (true) or hidden (false). |
| `hasNextStep` | `boolean` | Returns true if a next step exists; otherwise, false. |
| `hasPreviousStep` | `boolean` | Returns true if a previous step exists; otherwise, false. |
| `goToNextStep` | `void` | Navigates to the next step; submits the form if no next step exists. |
| `goToPreviousStep` | `void` | Navigates to the previous step; throws an exception if none exists. |

#### Multistep form example

This example shows how to retrieve a multistep form, inspect it, and advance to the next step.

```javascript
let $pages = await window.Microsoft.Dynamic365.Portal.onPagesClientApiReady();
let form = $pages.currentPage.forms.getFormById('multiform_#1');
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

#### Tab `Sections` property

An array of [sections](#section) within the tab.

#### Tab methods

Use these methods to check a tab's visibility, retrieve its name, and toggle whether it is shown.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the tab is visible; otherwise, false. |
| `getName` | `string` | Returns the name of the tab. |
| `setVisible(isVisible: boolean)` | `void` | Sets the tab's visibility. |

#### Tab example

This example retrieves a form, enumerates its tabs, and logs the first tab's name.

```javascript
let form = $pages.currentPage.forms.getFormById('form_#1');  
let tabs = form.tabs;  
console.log(`Form has ${tabs.length} tabs.`);  
console.log(`First tab is named: ${tabs[0].getName()}`);  
```

### Section

Sections group controls within a tab.

### Section `Controls` property

An array of [controls](#control) within the section.

#### Section methods

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the section is visible; otherwise, false. |
| `getName` | `string` | Returns the section name. |
| `setVisible(isVisible: boolean)` | `void` | Sets the section's visibility. |

#### Section example

```javascript
let form = window.$pages.currentPage.forms.getFormById('form_#1');  
let sections = form.tabs[0].sections;  
console.log(`Tab has ${sections.length} section(s).`);  
console.log(`First section is named: ${sections[0].getName()}`);
```

### Control

Controls represent individual form elements.

#### Control methods

Use these methods to retrieve or update a control's value, visibility, and disabled state.

| Method | Returns | Description |
|--------|---------|-------------|
| `getDisabled` | `boolean` | Returns true if the control is disabled. |
| `getVisible` | `boolean` | Returns true if the control is visible. |
| `getName` | `string` | Returns the control's name. |
| `getValue` | `string` \| `undefined` | Retrieves the current value. |
| `setDisabled(isDisabled: boolean)` | `void` | Sets the disabled state. |
| `setVisible(isVisible: boolean)` | `void` | Sets the visibility. |
| `setValue(value: string)` | `void` | Sets a new value for the control. |

#### Control example

This example fetches a form, inspects the first control's visibility, and then hides it.

```javascript
let form = $pages.currentPage.forms.getFormById('form_#1');  
let controls = form.controls;  
if (controls.length > 0) {  
if (controls[0].getVisible()) {  
console.log(`Control ${controls[0].getName()} is visible.`);  
}  
controls[0].setVisible(false); // Hide the first control.  
}
```

#### Supported controls

[Learn about additional methods and implementation differences for different types of controls](client-api-controls.md)


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


## $pages.languageAPI object

The `$pages.languageAPI` object provides methods to retrieve the list of available languages for the website, get the currently active language, and set a new active language.

### getAll method

- **Description**: Retrieves the list of languages enabled for the website.
- **Parameters**: None
- **Returns**: string[]
- **Example**: `window.$pages.languages.getAll();`

### getActive method

- **Description**: Retrieves the currently active language.
- **Parameters**: None
- **Returns**: string[]
- **Example**: `window.$pages.languages.getActive();`

### getActive method

- **Description**: Retrieves the currently active language.
- **Parameters**: None
- **Returns**: `string[]`
- **Example**: `window.$pages.languages.getActive();`

### setActive method

- **Description**: Sets the given language as the active language.
- **Parameters**:

  - `language` (string): The new language to be set as active.
- **Returns**: void
- **Example**: `window.$pages.languages.setActive('hi-IN');`

> [!NOTE]
> setActive method will cause a page reload.