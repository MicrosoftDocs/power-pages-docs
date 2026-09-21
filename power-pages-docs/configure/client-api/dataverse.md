---
title: Dataverse Records, Files, and Images Client API (Preview)
description: Learn how to use the Power Pages Client API to create, retrieve, update, and delete Dataverse records and work with files and images.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API Dataverse records, files, and images (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## $pages.webAPI object

Use the Power Pages Client API `$pages.webAPI` object to create, retrieve, update, and delete Dataverse records and to work with content stored in file and image columns.

| Method | Description |
|--------|-------------|
| [`createRecord`](#createrecord-method) | Creates a new record in the specified table. |
| [`retrieveRecord`](#retrieverecord-method) | Retrieves a record by its unique identifier. |
| [`retrieveMultipleRecords`](#retrievemultiplerecords-method) | Retrieves multiple records based on the provided query options. |
| [`updateRecord`](#updaterecord-method) | Updates an existing record in the specified table. |
| [`deleteRecord`](#deleterecord-method) | Deletes a record from the specified table. |
| [`updateSingleProperty`](#updatesingleproperty-method) | Updates a single column value of an existing record. |
| [`deleteSingleProperty`](#deletesingleproperty-method) | Clears the value of a single column in an existing record by setting it to null. |
| [`associateRecord`](#associaterecord-method) | Creates an association between two records by using a collection-valued navigation property. |
| [`disassociateRecord`](#disassociaterecord-method) | Removes an association between two records. |
| [`getRecordCount`](#getrecordcount-method) | Returns the total number of records in the specified table. |
| [`uploadFileToColumn`](#uploadfiletocolumn-method) | Uploads a file or an image to a file column or an image column of an existing record. |
| [`downloadFileFromColumn`](#downloadfilefromcolumn-method) | Downloads the binary content of a file column or an image column of an existing record. |

## createRecord method

Creates a new record in the specified table.

**Syntax**: `$pages.webAPI.createRecord(entitySetName: string, data: object): Promise<string>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the ID of the created record.

### createRecord method parameters

Provide the target table and the data object representing the record to create.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. [Learn about entity set name in Dataverse Web API](/power-apps/developer/data-platform/webapi/web-api-service-documents#entity-set-name) |
| `data` | object | The record data to create. |


### createRecord method example

This example demonstrates calling `createRecord` with an entity set name and a minimal data object.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    $pages.webAPI.createRecord('contacts', {
        firstName: 'User',
        lastName: 'Test'
    });
});
```

## retrieveRecord method

Retrieves a record by its unique identifier.

**Syntax**: `$pages.webAPI.retrieveRecord(entitySetName: string, id: string, options?: string): Promise<object>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the record object.


### retrieveRecord method parameters

Specify the table, record ID, and optional OData `$select` query options to shape the response.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. [Learn about entity set name in Dataverse Web API](/power-apps/developer/data-platform/webapi/web-api-service-documents#entity-set-name).|
| `id` | string | The record's unique identifier. |
| `options` | string (optional) | An optional OData `$select` query string to limit the data returned. |

> [!NOTE]
> While the `options` parameter is optional, for best performance always limit the number of column values returned by using the [`$select` option](/power-apps/developer/data-platform/webapi/query/select-columns).


### retrieveRecord method example

This example retrieves a single record by ID and limits the returned columns by using an OData `$select` query option.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let record = await $pages.webAPI.retrieveRecord('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb',  '$select=name');
});
```

## retrieveMultipleRecords method

Retrieves multiple records based on the provided query options.

**Syntax**: `$pages.webAPI.retrieveMultipleRecords(entitySetName: string, options?: string): Promise<object>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the OData response object. The `value` property of the response contains the array of records.


### retrieveMultipleRecords method parameters

Specify the table and optional OData query to filter results and limit returned columns.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `options` | string (optional) | An OData query options string to control the data returned. [Learn more about OData query options supported by Dataverse Web API](/power-apps/developer/data-platform/webapi/query/overview#odata-query-options) |

> [!NOTE]
> While the `options` parameter is optional, for best performance always limit the number of column values returned by using the [`$select` option](/power-apps/developer/data-platform/webapi/query/select-columns).


### retrieveMultipleRecords method example

This example retrieves multiple records and uses OData `$select` and `$top` to limit returned columns and row count.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let response = await $pages.webAPI.retrieveMultipleRecords('accounts', '$select=name&$top=3');
    let records = response.value;
    console.log(`Retrieved ${records.length} records.`);
});
```

## updateRecord method

Updates an existing record in the specified table.

**Syntax**: `$pages.webAPI.updateRecord(entitySetName: string, id: string, data: object): Promise<void>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves when the record is updated.

### updateRecord method parameters

Specify the table, the record to update, and the column values to set.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `id` | string | The unique identifier of the record to update. |
| `data` | object | The columns and values to update. |

### updateRecord method example

This example updates the name of an account record.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.webAPI.updateRecord('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb', { name: 'Updated Name' });
});
```

## deleteRecord method

Deletes a record from the specified table.

**Syntax**: `$pages.webAPI.deleteRecord(entitySetName: string, id: string): Promise<void>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves when the record is deleted.

### deleteRecord method parameters

Specify the table and the record to delete.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `id` | string | The unique identifier of the record to delete. |

### deleteRecord method example

This example deletes an account record.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.webAPI.deleteRecord('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb');
});
```

## updateSingleProperty method

Updates a single column value of an existing record.

**Syntax**: `$pages.webAPI.updateSingleProperty(entitySetName: string, id: string, property: string, value: unknown): Promise<void>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves when the column is updated.

### updateSingleProperty method parameters

Specify the table, the record, the column to update, and the new value.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `id` | string | The unique identifier of the record. |
| `property` | string | The name of the column to update. |
| `value` | unknown | The new value for the column. |

### updateSingleProperty method example

This example updates the name column of an account record.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.webAPI.updateSingleProperty('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb', 'name', 'New Name');
});
```

## deleteSingleProperty method

Clears the value of a single column in an existing record by setting it to null.

**Syntax**: `$pages.webAPI.deleteSingleProperty(entitySetName: string, id: string, property: string): Promise<void>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves when the column value is cleared.

### deleteSingleProperty method parameters

Specify the table, the record, and the column to clear.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `id` | string | The unique identifier of the record. |
| `property` | string | The name of the column to clear. |

### deleteSingleProperty method example

This example clears the description column of an account record.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.webAPI.deleteSingleProperty('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb', 'description');
});
```

## associateRecord method

Creates an association between two records by using a collection-valued navigation property. This method uses the OData `$ref` operation to create the link.

**Syntax**: `$pages.webAPI.associateRecord(entitySetName: string, id: string, navigationProperty: string, relatedEntitySetName: string, relatedId: string): Promise<void>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves when the records are associated.

### associateRecord method parameters

Specify the parent record first, and then the navigation property and the related record.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The entity set name of the parent record on the one side of the relationship. |
| `id` | string | The unique identifier of the parent record. |
| `navigationProperty` | string | The name of the collection-valued navigation property that defines the relationship. |
| `relatedEntitySetName` | string | The entity set name of the related record on the many side of the relationship. |
| `relatedId` | string | The unique identifier of the related record to associate. |

> [!IMPORTANT]
> Always specify the parent record on the one side of the relationship first, by using the `entitySetName` and `id` parameters.

### associateRecord method example

This example associates a contact record with an account record by using the `contact_association` navigation property.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.webAPI.associateRecord(
        'accounts',
        'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb',
        'contact_association',
        'contacts',
        'cccccccc-0000-1111-2222-dddddddddddd'
    );
});
```

## disassociateRecord method

Removes an association between two records.

**Syntax**: `$pages.webAPI.disassociateRecord(entitySetName: string, id: string, navigationProperty: string, relatedEntitySetName: string, relatedId: string): Promise<void>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves when the association is removed.

### disassociateRecord method parameters

Specify the parent record first, and then the navigation property and the related record.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The entity set name of the parent record on the one side of the relationship. |
| `id` | string | The unique identifier of the parent record. |
| `navigationProperty` | string | The name of the collection-valued navigation property that defines the relationship. |
| `relatedEntitySetName` | string | The entity set name of the related record. |
| `relatedId` | string | The unique identifier of the related record to disassociate. |

> [!IMPORTANT]
> Always specify the parent record on the one side of the relationship first, by using the `entitySetName` and `id` parameters.

### disassociateRecord method example

This example removes the association between an account record and a contact record.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.webAPI.disassociateRecord(
        'accounts',
        'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb',
        'contact_association',
        'contacts',
        'cccccccc-0000-1111-2222-dddddddddddd'
    );
});
```

## getRecordCount method

Returns the total number of records in the specified table. This method calls the OData `/$count` endpoint, which returns an integer instead of a collection of records.

**Syntax**: `$pages.webAPI.getRecordCount(entitySetName: string): Promise<number>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the number of records.

### getRecordCount method parameters

Specify the table to count records in.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |

> [!NOTE]
> The server returns a maximum count of 5,000. When a table contains more than 5,000 records, the result is 5,000. To retrieve records together with their total count, use the [retrieveMultipleRecords method](#retrievemultiplerecords-method) with the [`$count=true` query option](/power-apps/developer/data-platform/webapi/query/count-rows) instead. That method returns the collection in the `value` property of the response, and the total count in the `@odata.count` property.

### getRecordCount method example

This example returns the total number of account records.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const total = await $pages.webAPI.getRecordCount('accounts');
    console.log(`Total accounts: ${total}`);
});
```

## uploadFileToColumn method

Uploads a file or an image to a file column or an image column of an existing record. Dataverse stores the binary content and automatically updates the `{columnName}_Name` column with the file name.

**Syntax**: `$pages.webAPI.uploadFileToColumn(entitySetName: string, id: string, columnName: string, file: File): Promise<void>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves when the file is uploaded.

### uploadFileToColumn method parameters

Specify the table, the record, the column, and the file to upload.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `id` | string | The unique identifier of the record. |
| `columnName` | string | The logical name of the file or image column. |
| `file` | [File](https://developer.mozilla.org/docs/Web/API/File) | The file to upload. |

> [!NOTE]
> You can use this method with image columns. Dataverse removes EXIF metadata on the server and generates a thumbnail automatically. Use the [downloadFileFromColumn method](#downloadfilefromcolumn-method) to download either the full image or the thumbnail.

### uploadFileToColumn method example

This example uploads a file that someone selects by using a file input element.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const fileInput = document.querySelector('input[type="file"]');

    if (!fileInput || fileInput.files.length === 0) {
        return;
    }

    const file = fileInput.files[0];
    await $pages.webAPI.uploadFileToColumn('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb', 'new_attachment', file);
});
```

## downloadFileFromColumn method

Downloads the binary content of a file column or an image column of an existing record. Large files are downloaded in 4-MB chunks and combined into a single Blob automatically.

**Syntax**: `$pages.webAPI.downloadFileFromColumn(entitySetName: string, id: string, columnName: string, options?: object): Promise<Blob>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to a [Blob](https://developer.mozilla.org/docs/Web/API/Blob) that contains the binary data. The `type` property of the Blob contains the MIME type that the server returns.

### downloadFileFromColumn method parameters

Specify the table, the record, and the column to download from.

| Parameter | Type | Description |
|-----------|------|-------------|
| `entitySetName` | string | The name of the entity set. |
| `id` | string | The unique identifier of the record. |
| `columnName` | string | The logical name of the file or image column. |
| `options` | object (optional) | Options for the download. The `size` property applies to image columns and accepts `full` to download the original image or `thumbnail` to download the thumbnail that Dataverse generates. The default value is `full`. |

> [!NOTE]
> The response doesn't include the file name. To get the file name, use the [retrieveRecord method](#retrieverecord-method) to query the `{columnName}_Name` column of the record.

### downloadFileFromColumn method examples

This example downloads a file from a file column and prompts the browser to save it.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const blob = await $pages.webAPI.downloadFileFromColumn('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb', 'new_attachment');

    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = 'downloaded_file';
    a.click();
    URL.revokeObjectURL(url);
});
```

This example downloads the full image and the thumbnail from an image column.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    // Full-resolution image, which is the default.
    const fullBlob = await $pages.webAPI.downloadFileFromColumn('accounts', 'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb', 'entityimage');

    // Thumbnail that Dataverse generates.
    const thumbnailBlob = await $pages.webAPI.downloadFileFromColumn(
        'accounts',
        'aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb',
        'entityimage',
        { size: 'thumbnail' }
    );
});
```

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
