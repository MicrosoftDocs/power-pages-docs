---
title: Power Pages Client APIs Overview (Preview)
description: Learn how to use Power Pages client APIs to manipulate UI components, manage forms, lists, and user authentication effectively.
#customer intent: As a developer, I want to retrieve all forms on a Power Pages site so that I can programmatically interact with them.
author: shwetamurkute
ms.author: nenandw
ms.reviewer: smurkute
ms.date: 10/28/2025
ms.topic: concept-article
---


# Power Pages Client APIs (Preview) 

The client API provides a set of methods to manipulate UI components on a Power Pages site. After the Pages libraries initialize, the API becomes accessible via the global variable: `window.$pages.currentPage`. 
Use this API to interact with forms and lists, and perform operations such as record creation, retrieval, and user authentication.

## Form API

The form API includes methods and types to work with form elements on the page.

### Methods

`getAll(): IForm[]`

   - **Description**: Returns a collection of all forms added to the current page.
   - **Parameters**: None
   - **Returns**: `IForm[]`
   - **Example**: `let forms = window.$pages.currentPage.forms.getAll();`

`getFormById(id: string): Form`

   - **Description**: Retrieves a form instance by its HTML element ID.
   - **Parameters**: `id` (string): The ID of the form HTML element.
   - **Returns**: A form object.
   - **Example**: `let form = window.$pages.currentPage.forms.getFormById('form_#1');`

### Types

#### Form

A form represents a container for controls and tabs.

- **Properties**:
   - `id`: The ID of the form.
   - controls: `Control[]` - An array containing all controls on the form.
   - tabs: `Tab[]` - An array containing all tabs on the form.
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

#### Tab

A tab contains one or more sections within a form.

- **Properties**:
   - *Sections*: `Section[]` - An array of sections within the tab.
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

#### Section

Sections group controls within a tab.

- **Properties**:
   - *Controls*: `Control[]` - An array of controls within the section.  
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

#### Control

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

## List API

The list API offers methods to handle traditional and modern list elements on the page.

### Methods

`getAll(): IList[]`

   - **Description**: Returns a collection of all lists on the current page.
   - **Parameters**: None
   - **Returns**: `IList[]`
   - **Example**: `let lists = window.$pages.currentPage.lists.getAll();`

`getListById(id: string): List`

   - **Description**: Retrieves a list instance by its HTML element ID.
   - **Parameters**: `id (string)`: The ID of the list HTML element.
   - **Returns**: A list object.
   - **Example**: `let list = window.$pages.currentPage.lists.getListById('list_#1');`

### Type

#### List

A list represents a tabular or grid-like data component.

- **Properties**:
   - `id`: The list's unique identifier.
   - `isModern`: A Boolean value that is true for modern lists and false otherwise.
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

## User API

The User API facilitates user authentication actions such as signing in and signing out.

### Methods

`signIn(): void`

   - **Description**: Redirects the user to the sign-in page.
   - **Parameters**: None
   - **Returns**: void
   - **Example**: `window.$pages.user.signIn();`

`signOut(): void`

   - **Description**: Logs out the currently signed-in user.
   - **Parameters**: None
   - **Returns**: void
   - **Example**: `window.$pages.user.signOut();`

## Web API

The WebAPI methods allow you to create and retrieve records from a data source.

### Methods

`createRecord(entitySetName: string, data: object): Promise<object>`

   - **Description**: Creates a new record in the specified table.
   - **Parameters**:
       - `entitySetName` (string): The name of the entity set.
       - `data` (object): The record data to be created.
   - **Returns**: A Promise that resolves to the created record or operation result.
   - **Example**:

        ```javascript
        window.\$pages.webAPI.createRecord('account', {  
        firstName: 'User',
        lastName: 'Test'  
        });
        ```

`retrieveRecord(entitySetName: string, id: string, options?: string): Promise<object>`

- **Description**: Retrieves a record by its unique identifier.
- **Parameters**:
   - `entitySetName` (string): The name of the entity set.
   - `id` (string): The record's unique identifier.
   - `options` (string, optional): An optional OData query string to customize the returned data.
- **Returns**: A Promise that resolves to the record object.
- **Example**:
    `let record = await window.$pages.webAPI.retrieveRecord('accounts', '123',  '$select=name');`

`retrieveMultipleRecords(entitySetName: string, options?: string): Promise<object>`

- **Description**: Retrieves multiple records based on the provided query options.
- **Parameters**:
   - `entitySetName` (string): The name of the entity set.
   - `options` (string, optional): An OData query string to filter or select specific fields.
- **Returns**: A Promise that resolves to an array of record objects.
- **Example**:  
    `let records = await window.$pages.webAPI.retrieveMultipleRecords('accounts','$select=name&$top=3');`
