---
title: Client API Forms, Tabs, and Sections (Preview)
description: Learn how to use Power Pages Client API forms, tabs, sections, and controls to manage page elements, visibility, values, and navigation.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API forms, tabs, and sections (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Use Power Pages Client API forms, tabs, sections, and controls to inspect and manage page elements. This reference explains the available collections, properties, and methods for controlling visibility, values, and multistep navigation.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## $pages.currentPage.forms

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
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let forms = $pages.currentPage.forms.getAll();
    let form1 = $pages.currentPage.forms.getFormById('form_#1');
    let form2 = $pages.currentPage.forms.getFormByName('form_name')
});
```

## IForm interface

The `IForm` interface represents a container for controls and tabs.

### IForm properties

The following properties describe the form and its contained controls and tabs.

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | The ID of the form. |
| `name` | string | The name of the form. |
| `controls` | [Control](#control)`[]` | All controls on the form.|
| `tabs` | [Tab](#tab)`[]` | All tabs on the form.|
| `isMultiStep` | boolean | True if the form is multistep; otherwise, false. See [Multistep form](#multistep-form). |

### IForm methods

Use these methods to query a form's visibility and toggle whether it's visible.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the form is visible; otherwise, false. |
| `setVisible(isVisible: boolean)` | `void` | Sets the form's visibility. |
| `getHtmlElement` | [`HTMLElement`](https://developer.mozilla.org/docs/Web/API/HTMLElement) | Returns the underlying HTML element for the form. |
| `getControlByLogicalName(logicalName: string)` | [Control](#control) \| `undefined` | Returns the control on the form that has the specified logical name, such as the column schema name. Returns undefined when no control matches. |


### IForm example

The following example retrieves a form by ID and logs its visibility, number of controls, and tabs.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let form = $pages.currentPage.forms.getFormById('form_#1');

    console.log(`Form id: ${form.id} has ${form.controls.length} controls.`);

    if (form.getVisible()) {
        console.log('Form is currently visible.');
    }
    let tabs = form.tabs;
    console.log(`Form has ${tabs.length} tabs.`);

    // Look up a control by its logical name.
    let nameControl = form.getControlByLogicalName('fullname');
    if (nameControl) {
        nameControl.setValue('Jane Doe');
    }
});
```

## Multistep form

A multistep form is a container that holds multiple basic forms.

### Multistep form properties

The following properties apply to the multistep form container and describe what is available in the currently active step.

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | The ID of the multistep form. |
| `controls` | [Control](#control)`[]` | All controls in the current step. |
| `tabs` | [Tab](#tab)`[]` | All tabs in the current step.|
| `isMultiStep` | boolean | True if the form is multistep; otherwise, false. |
| `nextButton` | [JQuery Element](https://api.jquery.com/Types/#Element) | Represents the next button (empty object if absent). |
| `previousButton` | [JQuery Element](https://api.jquery.com/Types/#Element) | Represents the previous button (empty object if absent). |


### Multistep form methods

Use these methods to check visibility and move between steps in a multistep form.

| Name | Returns | Description |
|------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the form is visible; otherwise, false. |
| `setVisible(isVisible: boolean)` | `void` | Sets the form's visibility. |
| `hasNextStep` | `boolean` | Returns true if a next step exists; otherwise, false. |
| `hasPreviousStep` | `boolean` | Returns true if a previous step exists; otherwise, false. |
| `goToNextStep` | `void` | Navigates to the next step; submits the form if no next step exists. |
| `goToPreviousStep` | `void` | Navigates to the previous step; throws an exception if none exists. |
| `getControlByLogicalName(logicalName: string)` | [Control](#control) \| `undefined` | Returns the control in the current step that has the specified logical name, such as the column schema name. Returns undefined when no control matches. |

### Multistep form example

This example shows how to retrieve a multistep form, inspect it, and advance to the next step.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let form = $pages.currentPage.forms.getFormById('multiform_#1');
    console.log(`Form id: ${form.id} has ${form.controls.length} controls.`);

    if (form.getVisible()) {
        console.log('Form is currently visible.');
    }

    let tabs = form.tabs;
    console.log(`Form has ${tabs.length} tabs.`);

    form.goToNextStep();
});
```

## Tab

A `Tab` contains one or more sections within a form.

### Tab `Sections` property

An array of [sections](#section) within the tab.

### Tab methods

Use these methods to check a tab's visibility, retrieve its name, and toggle whether it's visible.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the tab is visible; otherwise, false. |
| `getName` | `string` | Returns the name of the tab. |
| `setVisible(isVisible: boolean)` | `void` | Sets the tab's visibility. |

### Tab example

This example retrieves a form, enumerates its tabs, and logs the first tab's name.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let form = $pages.currentPage.forms.getFormById('form_#1');
    let tabs = form.tabs;
    console.log(`Form has ${tabs.length} tabs.`);
    console.log(`First tab is named: ${tabs[0].getName()}`);
});
```

## Section

Sections group controls within a tab.

### Section `Controls` property

An array of [controls](#control) within the section.

### Section methods

Use these methods to read a section's name and control its visibility.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the section is visible; otherwise, false. |
| `getName` | `string` | Returns the section name. |
| `setVisible(isVisible: boolean)` | `void` | Sets the section's visibility. |

### Section example

This example retrieves sections from the first tab of a form and logs basic details.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let form = $pages.currentPage.forms.getFormById('form_#1');
    let sections = form.tabs[0].sections;
    console.log(`Tab has ${sections.length} section(s).`);
    console.log(`First section is named: ${sections[0].getName()}`);
});
```

## Control

A `Control` represents an individual form element. Use the [common control methods](control-methods.md) to retrieve or update its value, visibility, required state, and disabled state, and to add client-side validation. The value types and additional members depend on the [control type](controls.md).


## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
