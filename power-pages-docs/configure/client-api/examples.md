---
title: Power Pages Client API Examples (Preview)
description: Learn how to use the Power Pages client APIs to set lookup and choice values, control read-only fields, validate data, and show or hide list columns and rows.
#customer intent: As a developer, I want complete client API examples so that I can implement common form and list scenarios on my site.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: how-to
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Power Pages client API examples (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

The examples in this article show how to combine the [Power Pages client APIs](index.md) to implement common scenarios on forms and lists. Each example is complete, so you can copy it into a JavaScript web file or into the **Custom JavaScript** section of a page, and then change the form names, column names, and table names to match your site.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

All examples use the callback pattern described in [Client API initialization](initialization.md#microsoftpowerpagesonpagesclientapiready), which guarantees that the client API is ready before your code runs. The callback is declared with `async` so that it can use `await`. Omit the `async` keyword when your own code doesn't use `await`.

| Example | Description |
| --- | --- |
| [Set a modal lookup value from a Dataverse record](#set-a-modal-lookup-value-from-a-dataverse-record) | Retrieve a Dataverse record and use it to populate a modal lookup control. |
| [Set a lookup value when the lookup renders as a dropdown list](#set-a-lookup-value-when-the-lookup-renders-as-a-dropdown-list) | Set a lookup value based on whether the control renders as a dropdown list or a modal lookup. |
| [Read and set values in a multiselect choice column](#read-and-set-values-in-a-multiselect-choice-column) | Read the selected choices and add an option without removing existing selections. |
| [Work with controls that are read-only or hidden on the server](#work-with-controls-that-are-read-only-or-hidden-on-the-server) | Check control availability and read-only state before changing control behavior. |
| [Make a column required based on another column's value](#make-a-column-required-based-on-another-columns-value) | Apply conditional requirements and custom validation based on another control's value. |
| [Show or hide columns in a list](#show-or-hide-columns-in-a-list) | Hide a modern list column and customize another column's heading and tooltip. |
| [Show or hide records in a list](#show-or-hide-records-in-a-list) | Hide inactive rows and visually distinguish records that the current user can't edit. |

## Set a modal lookup value from a Dataverse record

This example retrieves an account record with the [Web API](dataverse.md#pageswebapi-object) and uses it to populate a [modal lookup](controls.md#modal-lookup) on a form. A modal lookup requires an object that contains the ID, the name, and the table name of the related record.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    // 1. Retrieve the first account record.
    //    $top=1 returns a single record, and $select limits the payload to the
    //    columns that the lookup control needs.
    const queryOptions = '$select=accountid,name&$top=1';
    const response = await $pages.webAPI.retrieveMultipleRecords('accounts', queryOptions);
    const records = response.value;

    if (!records || records.length === 0) {
        console.warn('No account records were returned from Dataverse.');
        return;
    }

    const firstAccount = records[0];
    console.log(`Retrieved account: ${firstAccount.name}`);

    // 2. Get the form. Use the name or the ID of your basic or multistep form.
    const form = $pages.currentPage.forms.getFormByName('Profile Web Form (Enhanced)');

    if (!form) {
        console.error('The target form was not found on the page.');
        return;
    }

    // 3. Get the lookup control by its logical name.
    const lookupControl = form.getControlByLogicalName('new_managingpartnerid');

    if (!lookupControl) {
        console.error('The lookup control was not found on the form.');
        return;
    }

    // 4. Set the lookup value. A modal lookup expects an object that contains
    //    the id, name, and entityType values.
    lookupControl.setValue({
        id: firstAccount.accountid,
        name: firstAccount.name,
        entityType: 'account'
    });

    console.log('The lookup control is populated.');
});
```

> [!TIP]
> To find a control when you don't know its logical name, enumerate `form.controls` and use the `getName` method, as in `form.controls.find(control => control.getName() === 'Managing Partner')`.

## Set a lookup value when the lookup renders as a dropdown list

A lookup column renders either as a modal dialog or as a dropdown list, depending on how the form is configured. The two controls accept different values in the `setValue` method, so check the `isDropdown` property before you set the value. A [dropdown lookup](controls.md#dropdown-lookup) expects the ID of the option to select, and a [modal lookup](controls.md#modal-lookup) expects an object.

> [!IMPORTANT]
> A dropdown lookup contains only the records that its configured view and filters return. Set the value to the ID of a record that's available in the dropdown list. In this example, filter your query so that it returns only records that the lookup offers.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const form = $pages.currentPage.forms.getFormByName('Profile Web Form (Enhanced)');
    const lookupControl = form && form.getControlByLogicalName('new_managingpartnerid');

    if (!lookupControl) {
        console.error('The lookup control was not found on the form.');
        return;
    }

    const response = await $pages.webAPI.retrieveMultipleRecords('accounts', '$select=accountid,name&$top=1');
    const records = response.value;

    if (!records || records.length === 0) {
        return;
    }

    const account = records[0];

    if (lookupControl.isDropdown) {
        // A dropdown lookup expects the ID of the option to select.
        lookupControl.setValue(account.accountid);

        // getValue returns an object that contains the id and name of the selected option.
        const selected = lookupControl.getValue();
        console.log(`Selected option: ${selected && selected.name}`);
    } else {
        // A modal lookup expects an object.
        lookupControl.setValue({
            id: account.accountid,
            name: account.name,
            entityType: 'account'
        });
    }
});
```

## Read and set values in a multiselect choice column

A [multiselect picklist control](controls.md#multiselect-picklist) stores an array of numbers. This example adds an option to the current selection without removing the options that someone already selected.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const form = $pages.currentPage.forms.getFormByName('Profile Web Form (Enhanced)');
    const control = form && form.getControlByLogicalName('new_areasofinterest');

    if (!control || control.getType() !== 'MultiSelectPicklist') {
        return;
    }

    // 1. Read the options that are currently selected.
    const selectedValues = control.getValue() || [];
    console.log(`Selected options: ${selectedValues.join(', ')}`);

    // 2. Add an option only when it isn't selected yet.
    //    setValue throws an error when a value isn't one of the available options.
    const newsletterOption = 740740002;

    if (!selectedValues.includes(newsletterOption)) {
        control.setValue([...selectedValues, newsletterOption]);
    }

    // 3. Clear the selection.
    // control.setValue([]);
});
```

## Work with controls that are read-only or hidden on the server

Power Pages applies form metadata and table permissions on the server, and the client API can't override those settings. Write defensive code that checks whether a control exists and whether it's read-only before you change it.

The following behaviors apply:

- A column that isn't on the form, or that someone doesn't have permission to read, isn't rendered. The `getControlByLogicalName` method returns `undefined` for that column, so check the result before you use it.
- When a control is locked on the server, such as a [multiselect picklist](controls.md#multiselect-picklist) on a read-only form or field, the `setDisabled(false)` method has no effect.
- The `setRequired(false)` method can't make a column optional when the column is required on the server.
- The `setVisible(false)` method hides a control in the browser only. Use table permissions and column security to protect data. Never rely on hiding a control to secure data.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const form = $pages.currentPage.forms.getFormByName('Profile Web Form (Enhanced)');

    if (!form) {
        return;
    }

    const creditLimit = form.getControlByLogicalName('creditlimit');

    // The column isn't on the form, or the user can't read it.
    if (!creditLimit) {
        console.log('The credit limit column is not available to this user.');
        return;
    }

    // A control that's locked on the server stays disabled, even after
    // you call setDisabled(false).
    creditLimit.setDisabled(false);

    if (creditLimit.getDisabled()) {
        console.log('The credit limit column is locked on the server.');
    }

    // Hide the control in the browser. This changes only what people see.
    // Use table permissions and column security to protect the data.
    const internalNotes = form.getControlByLogicalName('new_internalnotes');

    if (internalNotes) {
        internalNotes.setVisible(false);
    }
});
```

## Make a column required based on another column's value

This example makes a column required only when someone selects a specific option in another column, and it adds a custom validator that runs when the form is submitted. For more information, see [addValidator method parameters](control-methods.md#addvalidator-method-parameters).

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const form = $pages.currentPage.forms.getFormByName('Profile Web Form (Enhanced)');

    if (!form) {
        return;
    }

    const contactMethod = form.getControlByLogicalName('preferredcontactmethodcode');
    const mobilePhone = form.getControlByLogicalName('mobilephone');

    if (!contactMethod || !mobilePhone) {
        return;
    }

    const applyRules = () => {
        // Option 3 is Phone in this example.
        const requiresPhone = contactMethod.getValue() === '3';

        // Make the column required and provide a localized message.
        mobilePhone.setRequired(requiresPhone, 'Enter a mobile phone number.');

        if (requiresPhone) {
            // Add a format check that runs when the form is submitted.
            // Reusing the same ID replaces the earlier validator instead of adding another one.
            mobilePhone.addValidator(
                'mobilePhoneFormat',
                (value) => /^(?=.*\d)[0-9\s+()-]{7,20}$/.test((value || '').trim()),
                'Enter a valid mobile phone number.'
            );
        } else {
            mobilePhone.removeValidator('mobilePhoneFormat');
        }
    };

    // Apply the rules when the page loads and whenever a value on the form changes.
    applyRules();
    form.getHtmlElement().addEventListener('change', applyRules);
});
```

> [!NOTE]
> A column that's required on the server stays required, even when you call `setRequired(false)`.

## Show or hide columns in a list

This example hides a column in a modern list and renames another column. Read the list data in a `loaded` event handler, because the event occurs again each time the list refreshes, sorts, filters, or pages data. For more information, see [List events](lists.md#list-events).

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const list = $pages.currentPage.lists.getListById('list_#1');

    if (!list || !list.isModern) {
        return;
    }

    list.on('loaded', () => {
        // Hide a column that people don't need to see.
        const createdOn = list.getColumn('createdon');

        if (createdOn) {
            createdOn.setVisible(false);
        }

        // Rename a column and add a tooltip that screen readers use as the
        // accessible name of the header. Read the configured display name, and
        // then derive the header so that the code produces the same result
        // each time the event occurs.
        const name = list.getColumn('name');

        if (name) {
            name.setHeader(`${name.getDisplayName()} (primary)`);
            name.setTooltip('The primary name of the account.');
        }
    });
});
```

## Show or hide records in a list

This example hides inactive records and highlights the records that someone can't edit. Hiding a row changes only what people see in the list; it doesn't change the data or the number of records that the server returns.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const list = $pages.currentPage.lists.getListById('list_#1');

    if (!list || !list.isModern) {
        return;
    }

    list.on('loaded', () => {
        list.rows.forEach((row) => {
            const state = row.getState();

            // Hide inactive records, where statecode is 1.
            if (state && state.stateCode === 1) {
                row.setVisible(false);
                return;
            }

            // Highlight the records that this user can't edit.
            const privileges = row.getPrivileges();

            if (privileges && !privileges.canWrite) {
                row.addClassName('read-only-row');

                const nameCell = row.getCell('name');

                if (nameCell) {
                    nameCell.setStyle({ fontStyle: 'italic' });
                }
            }
        });
    });
});
```

> [!IMPORTANT]
> Use the values that the `getPrivileges` method returns to change how data appears. Don't use them to enforce security. Power Pages enforces table permissions on the server.

## Related information

- [Power Pages Client APIs](index.md)
- [Power Pages Client API supported controls](controls.md)
