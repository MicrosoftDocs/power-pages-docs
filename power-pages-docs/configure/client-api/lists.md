---
title: Client API Lists for Rows, Columns, Cells, and Events (Preview)
description: Explore Power Pages Client API lists to manage lists, rows, columns, cells, visibility, and events. Use the reference and examples to build list experiences.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API lists (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Use Power Pages Client API lists to access and customize traditional and modern lists. This reference explains how to work with rows, columns, cells, visibility, and list events.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## $pages.currentPage.lists

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
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let lists = $pages.currentPage.lists.getAll();
    let list = $pages.currentPage.lists.getListById('list_#1');
});
```

## IList interface

A list represents a tabular or grid-like data component.

### IList properties

These properties identify the list and indicate whether it uses the modern rendering model.

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | The list's unique identifier. |
| `isModern` | boolean | A Boolean value that's true for modern lists and false otherwise. |
| `rows` | [IRow](#irow-interface)`[]` | The rows that the list currently publishes. Each time you read this property, it returns the latest data, so read it in a `loaded` event handler to make sure the data is available. |
| `columns` | [IColumn](#icolumn-interface)`[]` | The columns in the list's current view. |

> [!NOTE]
> The `rows` and `columns` properties, the `getColumn`, `on`, and `off` methods, and everything they return are supported only on modern lists, where `isModern` is true. On a traditional list, they're safe to call but do nothing: `rows` and `columns` return empty arrays, `getColumn` returns undefined, and `on` and `off` do nothing. Check `isModern` before you access list data, or use the `loaded` event, which never occurs for a traditional list.

### IList methods

Use these methods to check list visibility, toggle whether it's visible, access the underlying HTML element, and work with columns and events.

| Method | Returns | Description |
|--------|---------|-------------|
| `getVisible` | `boolean` | Returns true if the list is visible. |
| `setVisible(isVisible: boolean)` | `void` | Sets the list's visibility. |
| `getHtmlElement` | [`HTMLElement`](https://developer.mozilla.org/docs/Web/API/HTMLElement) | Returns the underlying HTML element for the list. |
| `getColumn(logicalName: string)` | [IColumn](#icolumn-interface) \| `undefined` | Returns the column that has the specified logical (schema) name. Returns undefined when no column matches. |
| `on(event: string, handler: function)` | `void` | Subscribes a handler to a list event. See [List events](#list-events). Subscribing the same handler to the same event more than once has no effect. |
| `off(event: string, handler: function)` | `void` | Unsubscribes a handler that was registered with `on`. Pass the same function reference that you passed to `on`. A different reference doesn't unsubscribe the handler. |

### IList example

The following example retrieves a list by ID, logs its visibility status, and reads its data when the grid loads.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let list = $pages.currentPage.lists.getListById('list_#1');
    console.log(`List id: ${list.id}`);
    if (list.getVisible()) {
        console.log('List is currently visible.');
    }

    // Modern list data is available only after the grid loads, so read it in a `loaded` handler.
    if (list.isModern) {
        list.on('loaded', () => {
            console.log(`List has ${list.rows.length} rows and ${list.columns.length} columns.`);
        });
    }
});
```

## IRow interface

The `IRow` interface represents a single row in a modern list. Get a row from the `list.rows` property or from a [list event](#list-events) payload.

The methods that begin with `get` return the data that the grid published. The other methods set how the row appears, such as its style, class names, and visibility. The grid applies these settings when it renders the row. Hiding a row changes only how the row appears; the underlying data isn't changed.

### IRow methods

Use these methods to read a row's data and change how the row appears.

| Method | Returns | Description |
|--------|---------|-------------|
| `getId` | `string` | Returns the row's Dataverse record ID as a GUID string. |
| `getValue(logicalName: string)` | `string` \| `number` \| `boolean` \| `Date` \| `null` | Returns a raw string, number, Boolean, valid date, or numeric option value for the column that has the specified logical (schema) name. Returns null when the column isn't in the row or its raw value is an unsupported complex value, including a lookup-shaped object. Use `getDisplayValue` when the raw complex value isn't available. |
| `getDisplayValue(logicalName: string)` | `string` | Returns the value of the column formatted for the current locale. Returns an empty string when the column isn't in the row. |
| `getPrivileges` | `object` \| `undefined` | Returns the privileges that the server evaluated for the record: `canRead`, `canWrite`, `canDelete`, `canAppend`, and `canAppendTo`. Returns undefined when the server doesn't provide them. Use these values to change how data appears, not to enforce security. |
| `getState` | `object` \| `undefined` | Returns the `stateCode` and `statusCode` values of the record. Returns undefined when the server doesn't provide them. |
| `setStyle(style: object)` | `void` | Merges inline CSS styles onto the row. Each call adds to the styles that are already set. |
| `setClassName(className: string)` | `void` | Replaces the row's CSS class names with the space-separated class names that you specify. |
| `addClassName(className: string)` | `void` | Adds one or more space-separated CSS class names to the row. |
| `removeClassName(className: string)` | `void` | Removes one or more space-separated CSS class names from the row. |
| `setVisible(visible: boolean)` | `void` | Shows or hides the row. This method changes only how the row appears. |
| `getCell(logicalName: string)` | [ICell](#icell-interface) | Returns a handle that you use to change how one of the row's cells appears. |

### IRow example

This example highlights canceled records and hides inactive records.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const list = $pages.currentPage.lists.getListById('list_#1');

    list.on('loaded', () => {
        list.rows.forEach((row) => {
            // Highlight canceled records where statuscode is 6.
            if (row.getValue('statuscode') === 6) {
                row.setStyle({ backgroundColor: '#fde7e9', color: '#a80000' });
            }
            // Hide inactive records where statecode is 1.
            if (row.getValue('statecode') === 1) {
                row.setVisible(false);
            }
        });
    });
});
```

## IColumn interface

The `IColumn` interface represents a single column in a modern list. Get a column from the `list.columns` property or from the `list.getColumn` method. You can set the header, visibility, and tooltip independently of each other.

The `get` methods return the source data, not the values that you set. For example, `getDisplayName` returns the configured display name even after you call `setHeader`, just as `row.getDisplayValue` returns the value that the server formatted even after you call `cell.setDisplayText`. This behavior makes your code safe to run more than once, because your `loaded` handler runs again each time the list fetches, sorts, filters, or pages data. For example, `column.setHeader(column.getDisplayName() + ' *')` produces the same result every time instead of adding another asterisk. Read the source value, and then derive the value that you set.

### IColumn methods

Use these methods to read a column's names and change how the column appears.

| Method | Returns | Description |
|--------|---------|-------------|
| `getLogicalName` | `string` | Returns the column's logical (schema) name. |
| `getDisplayName` | `string` | Returns the column's configured display name. `setHeader` doesn't change this value. |
| `setHeader(header: string)` | `void` | Overrides the text in the column header. |
| `setVisible(visible: boolean)` | `void` | Shows or hides the entire column. |
| `setTooltip(tooltip: string)` | `void` | Sets the tooltip for the column header. The tooltip appears when someone hovers over the header, and screen readers use it as the accessible name of the header. |

### IColumn example

This example sets the header text and tooltip for a column.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const list = $pages.currentPage.lists.getListById('list_#1');

    list.on('loaded', () => {
        const column = list.getColumn('name');
        if (column) {
            column.setHeader('Account name');
            column.setTooltip('The primary name of the account');
        }
    });
});
```

## ICell interface

The `ICell` interface represents a single cell, which is the intersection of a row and a column. Get a cell from the `row.getCell` method. A cell is write-only by design. To read the value of a cell, use the `getValue` or `getDisplayValue` method of the [row](#irow-interface) that contains it.

### ICell methods

Use these methods to change the text and style of a cell.

| Method | Returns | Description |
|--------|---------|-------------|
| `setDisplayText(text: string)` | `void` | Replaces the text that appears in the cell. Use this method to show friendly text instead of a code, mask a value, or show a badge. |
| `setStyle(style: object)` | `void` | Merges inline CSS styles onto the cell. Each call adds to the styles that are already set. |

### ICell example

This example changes the text and style of a cell in each row.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const list = $pages.currentPage.lists.getListById('list_#1');

    list.on('loaded', () => {
        list.rows.forEach((row) => {
            const cell = row.getCell('statuscode');
            cell.setDisplayText('Active');
            cell.setStyle({ fontWeight: 'bold', backgroundColor: '#fff4ce' });
        });
    });
});
```

## List events

Modern lists raise events that you subscribe to by using the `list.on` method and unsubscribe from by using the `list.off` method. Because these events provide [row](#irow-interface) objects, they're also the recommended place to read or style row data. The data is available after the `loaded` event occurs.

| Event | When it occurs | Payload |
|-------|----------------|---------|
| `loaded` | After the list fetches and publishes its row data. This event occurs again each time the list refreshes or pages data. | `{ rows: IRow[] }` |
| `rowclick` | Someone selects a row. | `{ row: IRow, event: MouseEvent }` |
| `cellclick` | Someone selects a cell. When a `cellclick` handler is registered, the `rowclick` event doesn't occur for that selection. | `{ row: IRow, columnName: string, event: MouseEvent }` |

> [!IMPORTANT]
> If both `rowclick` and `cellclick` handlers are registered, selecting a cell invokes only the `cellclick` handler. The `rowclick` handler isn't invoked for the same selection.

### List events example

This example subscribes to the `rowclick` and `cellclick` events.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const list = $pages.currentPage.lists.getListById('list_#1');

    const onRowClick = (e) => {
        console.log('Selected row:', e.row.getId());
        e.row.setStyle({ outline: '2px solid #0078d4' });
    };

    list.on('rowclick', onRowClick);

    list.on('cellclick', (e) => {
        console.log('Selected cell:', e.row.getId(), 'column:', e.columnName);
        e.row.getCell(e.columnName).setStyle({ backgroundColor: '#e5f1fb' });
    });

    // Define a cleanup function, and call it when your code no longer needs
    // the events. Pass the same handler reference that you passed to the on method.
    const stopListening = () => {
        list.off('rowclick', onRowClick);
    };
});
```

To unsubscribe, pass the same function reference to the `off` method that you passed to the `on` method. A different reference doesn't unsubscribe the handler.

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
