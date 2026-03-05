---
title: Power Pages Client APIs Overview (preview)
description: Learn how to use Power Pages client APIs to manipulate UI components, manage forms, lists, and user authentication effectively.
#customer intent: As a developer, I want to retrieve all forms on a Power Pages site so that I can programmatically interact with them.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 03/05/2026
ms.topic: reference
contributors:
- JimDaly
- mkaur
---
# Power Pages Client APIs (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Power Pages client APIs help developers manipulate UI components, manage forms and lists, handle user authentication, and interact with Dataverse records programmatically. The client API becomes available when your page loads and can be accessed through a global variable with a name you choose.

This article uses the variable name `$pages` throughout examples and recommends you follow this naming convention for consistency.

With the client APIs, you can: 

With the `$pages` client API, you can:  

- Retrieve and modify forms and form controls
- Show or hide UI elements  
- Create and retrieve records using the Web API
- Manage user authentication
- Work with multilingual content

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Client API initialization

The `$pages` client API doesn't initialize immediately when the page loads. Use the `Microsoft.Dynamic365.Portal.onPagesClientApiReady` function to assign the API object to the `$pages` variable. There is two ways exist to initialize the client API:


### Callback-based API readiness

Use a callback function that assigns the API object to a variable you define when it's ready. Two examples show how:

By using an anonymous function:

```javascript
Microsoft.Dynamic365.Portal.onPagesClientApiReady(($pages) => {
    const forms = $pages.currentPage.forms.getAll();
    console.log(`Found ${forms.length} forms on the page.`);
});
```

By using a named function:

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

The following table describes when to use each approach.

| Approach | When to use |
|----------|-------------|
| **[Callback-based API readiness](#callback-based-api-readiness)** | Use when you need to support older browsers or legacy scripts that don't support `async/await`, or when you want to register multiple handlers that run when the API is ready. Ideal for event-driven patterns. |
| **[Promise/await-based API readiness](#promiseawait-based-api-readiness)** | Use in modern JavaScript environments that support `async/await` for cleaner, sequential code. Best when your logic depends on the API being ready before continuing execution. |

> [!TIP]
> If your codebase already uses `async/await`, prefer the Promise-based approach for consistency.

## $pages.currentPage.forms collection

The `$pages.currentPage.forms` collection includes methods to work with form elements on the page.

### $pages.currentPage.forms methods

Use these methods to list forms and get specific form instances.

| Method | Returns | Description |
|--------|---------|-------------|
| `getAll` | [`IForm`](#iform-interface)`[]` | Returns all forms added to the current page. |
| `getFormById(id: string)` | [`IForm`](#iform-interface) | Retrieves a form by its HTML element ID. |
| `getFormByName(name: string)` | [`IForm`](#iform-interface) | Retrieves a form by its name. |

### $pages.currentPage.forms method examples

These examples show how to get all forms and retrieve specific forms by ID or name.

```javascript
let forms = $pages.currentPage.forms.getAll();
let form1 = $pages.currentPage.forms.getFormById('form_#1');
let form2 = $pages.currentPage.forms.getFormByName('form_name')
```

### IForm interface

The `IForm` interface represents a container for controls and tabs.

#### IForm properties

The following properties describe the form and its contained controls and tabs.

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | The ID of the form. |
| `name` | string | The name of the form. |
| `controls` | [Control](#control)`[]` | All controls on the form.|
| `tabs` | [Tab](#tab)`[]` | All tabs on the form.|
| `isMultiStep` | boolean | True if the form is multistep; otherwise, false. See [Multistep form](#multistep-form). |

#### IForm methods

Use these methods to query a form's visibility and toggle whether it's visible.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the form is visible; otherwise, false. |
| `setVisible(isVisible: boolean)` | `void` | Sets the form's visibility. |


#### IForm example

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
let $pages = await Microsoft.Dynamic365.Portal.onPagesClientApiReady();
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

Use these methods to check a tab's visibility, retrieve its name, and toggle whether it's visible.

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

#### Section `Controls` property

An array of [controls](#control) within the section.

#### Section methods

Use these methods to read a section's name and control its visibility.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the section is visible; otherwise, false. |
| `getName` | `string` | Returns the section name. |
| `setVisible(isVisible: boolean)` | `void` | Sets the section's visibility. |

#### Section example

This example retrieves sections from the first tab of a form and logs basic details.

```javascript
let form = $pages.currentPage.forms.getFormById('form_#1');  
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

This example fetches a form, checks the first control's visibility, and then hides it.

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

All controls implement the standard [control methods](#control-methods). Some controls provide more methods and have different implementation details from the standard control methods. [Learn about other methods and implementation differences for different types of controls](client-api-controls.md).


## $pages.currentPage.lists collection

The lists collection provides methods to work with traditional and modern list elements on the page.

### $pages.currentPage.lists methods

Use these methods to enumerate all lists on the page and get a specific list by its HTML element ID.

| Method | Returns | Description |
|--------|---------|-------------|
| `getAll` | [IList](#ilist-interface)`[]` | Returns all lists on the current page. |
| `getListById(id: string)` | [IList](#ilist-interface) | Gets a list by its HTML element ID. |

### $pages.currentPage.lists examples

These examples show how to enumerate all lists on the page and get a specific list by its HTML element ID.

```javascript
let lists = $pages.currentPage.lists.getAll();
let list = $pages.currentPage.lists.getListById('list_#1');
```

### IList interface

A list represents a tabular or grid-like data component.

#### IList properties

These properties identify the list and indicate whether it uses the modern rendering model.

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | The list's unique identifier. |
| `isModern` | boolean | A Boolean value that's true for modern lists and false otherwise. |

#### IList methods

Use these methods to check list visibility, toggle whether it's visible, and access the underlying HTML element.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the list is visible. |
| `setVisible(isVisible: boolean)` | `void` | Sets the list's visibility. |
| `getHtmlElement` | [`HTMLElement`](https://developer.mozilla.org/docs/Web/API/HTMLElement) | Returns the underlying HTML element for the list. |

#### IList example

The following example retrieves a list by ID and logs its visibility status.

```javascript
let list = $pages.currentPage.lists.getListById('list_#1');  
console.log(`List id: ${list.id}`);  
if (list.getVisible()) {  
console.log('List is currently visible.');  
}
```

## $pages.user object

The `$pages.user` object provides methods to sign the user in or out.

### $pages.user methods

These methods don't return any value.

| Method | Description |
|--------|-------------|
| `signIn` | Redirects the user to the sign-in page. |
| `signOut` | Signs out the currently signed-in user. |


## $pages.webAPI object

The `$pages.webAPI` object provides methods to create and retrieve records from a data source.

### createRecord method

Creates a new record in the specified table.

**Syntax**: `$pages.webAPI.createRecord(entitySetName: string, data: object): Promise<object>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the created record or operation result.

#### createRecord method parameters

Provide the target table and the data object representing the record to create.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. [Learn about entity set name in Dataverse Web API](/power-apps/developer/data-platform/webapi/web-api-service-documents#entity-set-name) |
| `data` | object | The record data to create. |


#### createRecord method example

This example demonstrates calling `createRecord` with an entity set name and a minimal data object.

```javascript
$pages.webAPI.createRecord('contacts', {  
firstName: 'User',
lastName: 'Test'  
});
```

### retrieveRecord method

Retrieves a record by its unique identifier.

**Syntax**: `$pages.webAPI.retrieveRecord(entitySetName: string, id: string, options?: string): Promise<object>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the record object.


#### retrieveRecord method parameters

Specify the table, record ID, and optional OData `$select` query options to shape the response.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. [Learn about entity set name in Dataverse Web API](/power-apps/developer/data-platform/webapi/web-api-service-documents#entity-set-name).|
| `id` | string | The record's unique identifier. |
| `options` | string (optional) | An optional OData `$select` query string to limit the data returned. |

> [!NOTE]
> While the `options` parameter is optional, for best performance always limit the number of column values returned by using the [`$select` option](/power-apps/developer/data-platform/webapi/query/select-columns).


#### retrieveRecord method example

This example retrieves a single record by ID and limits the returned columns by using an OData `$select` query option.

```javascript
let record = await $pages.webAPI.retrieveRecord('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb',  '$select=name');
```

### retrieveMultipleRecords method

Retrieves multiple records based on the provided query options.

**Syntax**: `$pages.webAPI.retrieveMultipleRecords(entitySetName: string, options?: string): Promise<object>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to an array of record objects.


#### retrieveMultipleRecords method parameters

Specify the table and optional OData query to filter results and limit returned columns.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `options` | string (optional) | An OData query options string to control the data returned. [Learn more about OData query options supported by Dataverse Web API](/power-apps/developer/data-platform/webapi/query/overview#odata-query-options) |

> [!NOTE]
> While the `options` parameter is optional, for best performance always limit the number of column values returned by using the [`$select` option](/power-apps/developer/data-platform/webapi/query/select-columns).


#### retrieveMultipleRecords method example

This example retrieves multiple records and uses OData `$select` and `$top` to limit returned columns and row count.

```javascript
let records = await $pages.webAPI.retrieveMultipleRecords('accounts','$select=name&$top=3');
```

## $pages.languages

The `$pages.languages` object provides methods to retrieve the list of available languages for the website, get the currently active language, and set a new active language.

### $pages.languages methods

Use these methods to read the available languages, check the current language, and change it for the site.

| Method | Description | Returns |
|--------|-------------|---------|
| `getAll` | Retrieves the list of languages enabled for the website. | `string[]` |
| `getActive` | Retrieves the currently active language. | `string` |
| `setActive(language: string)` | Sets the given language as the active language. | `void` |

> [!NOTE]
> `setActive` method causes a page reload.

### $pages.languages method examples

These examples show how to list all languages, read the active language, and set a new active language.

```javascript
let allLanguages = $pages.languages.getAll();
let activeLanguage = $pages.languages.getActive();
$pages.languages.setActive('hi-IN');
```

## $pages.agent

The `$pages.agent` object provides methods to establish communication between the site and the Microsoft Copilot Studio agent available to the current user. 

```javascript
$pages.agent.SendActivity(
    agentSchemaName: string,
    inputActivity: object,
    responseSubscriber: function,
    errorSubscriber: function
);
```

| Parameter Name | Type | Description |
|----------------|----- |-------------|
| `agentSchemaName` | String | Schema name of the bot to which the activity is sent. |
| `inputActivity`   | Object | Object containing the text or event to send to the bot. |
| `responseSubscriber` | function | Callback function that runs when the agent sends a response. |
| `errorSubscriber` | function | Callback function that handles errors. |

Return type: void - The function doesn't return anything.

Response object from agent received in the following format:

| Name | Type | Description |
|------|----- |-------------|
| `type` | String | Type of the activity such as message. |
| `text` | String | Optional, message from agent. |
| `textFormat` | String | Optional, format of the message's text such as markdown, plain, or XML. |
| `Id` | String | ID that uniquely identifies the activity. |
| `From` | Object | Specifies the sender of the activity (includes id, name (optional), and role information).|
| `Conversation` | Object | Contains the ID of the conversation to which the activity belongs. |
| `InputHint` | String | Optional, indicates whether the bot is accepting, expecting, or ignoring user input. |
| `replyToId` | String | ID of the reply message.|


### Example

#### Callback method
Define the `responseSubscriber` and `errorSubscriber` callback functions to handle agent responses and errors.

```javascript
const responseSubscriber = (response) => {  
// Replace with your response handling.
console.log('Agent response:', response);
};

const errorSubscriber = (error) => {
// Replace with your error handling.
console.error('Error:', error);
};  

// Replace with your agent schema name.
const agentSchemaName = 'agent SchemaName';  
```

#### Send message to agent

```javascript
const inputActivity = {
    text: 'Hello!', // Message to the agent.
    };

$pages.agent.SendActivity(agentSchemaName, inputActivity, responseSubscriber, 
  ErrorSubscriber);

```

#### Invoke client event

```javascript
const inputActivity = {
    name: 'AgentEvent', // The name of the event to be invoked
    value: {key1:'value1', key2:'value2'} // Open-ended value used to carry additional data or payloads necessary for specific agent operations or responses
    };

$pages.agent.SendActivity(agentSchemaName, inputActivity, responseSubscriber, 
  ErrorSubscriber);

```
### Error messages

Here are possible error messages that users can encounter and their potential causes.

| **Error type** | **Cause** | **Error message for user** |
|----|----|----|
| Agent schema validation | Invalid bot schema name provided or user doesn't have access permissions to the agent | `Invalid bot schema name or access denied. Please check the bot schema name and try again.` |
| Fetch token error | An error occurred while fetching the direct line token | `Something went wrong while fetching the token. Please try again.` |
| Posting activity error (retry) | An error occurred while posting the activity and a retry is needed. | `Something went wrong while posting the activity: retry.` |
| Posting activity error (timeout) | Timed out while waiting for outgoing message or postActivity | `Timed out while posting activity: Please retry.` |
| Posting activity error (invalid activity) | The input activity doesn't have text or a name to invoke the event. | `Invalid activity: At least one of text, name, or attachments must be provided.` |
| Posting activity error (user ID not found or token not found) | Token isn't found in session storage or user ID isn't found in token | `Error retrieving user ID: {error message}` |
| Posting activity error (general) | An unspecified error occurred while posting the activity | `Something went wrong while posting the activity: Please try again.` |
| Direct line connection error | An error occurred while creating direct line connection with the bot. | `Something went wrong while creating direct line connection: Please try again.`|
| General error | An unexpected error that doesn't fall into the above categories | `An unexpected error occurred while sending activity: Please try again.` |
