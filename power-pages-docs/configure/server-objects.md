---
title: Access user and website details with server objects
description: Learn how to use built-in server objects like Logger, HttpClient, and Dataverse to simplify development and integrate with external services effectively.
#customer intent: As a developer, I want to send HTTP requests using the **HttpClient** object so that I can integrate with external services.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 10/27/2025
ms.topic: reference
---

# Server objects 

Server logic provides built-in objects under the server namespace. These objects simplify development by letting you log messages, call external services, work with Dataverse, or access request details.

## HttpClient

Use the HTTP client to integrate with external services by sending HTTP requests.

> [!NOTE]
> Currently server logic supports only `application/json`, `text/html` and `application/x-www-form-urlencoded` content types in request body.

### Examples

#### HTTP GET

```javascript
let url = "https://contoso.com/objects";
let header = { client_id: "00001111-aaaa-2222-bbbb-3333cccc4444" };

let response = await Server.Connector.HttpClient.GetAsync(url, header);
```

#### HTTP POST

```javascript
let url = "https://contoso.com/objects";
let body = JSON.stringify({ name: "Sample Account" });
let header = { client_id: "00001111-aaaa-2222-bbbb-3333cccc4444" };
let contentType = "application/json";

// Make the POST request
let response = await Server.Connector.HttpClient.PostAsync(url, body, header, contentType);
```

#### HTTP PUT

```javascript
let url = "https://contoso.com/objects/6";
let body = JSON.stringify({ name: "Updated Sample Account" });
let header = { client_id: "00001111-aaaa-2222-bbbb-3333cccc4444" };
let contentType = "application/json";

// Make the PUT request
let response = await Server.Connector.HttpClient.PutAsync(url, body, header, contentType);
```

#### HTTP PATCH

```javascript
let url = "https://contoso.com/objects/6";
let body = JSON.stringify({ name: "{\"capacity\": \"2 TB\"}" });
let header = { client_id: "00001111-aaaa-2222-bbbb-3333cccc4444" };
let contentType = "application/json";

// Make the PATCH request
let response = await Server.Connector.HttpClient.PatchAsync(url, body, header, contentType);
```

#### HTTP DELETE

```javascript
let url = "https://contoso.com/objects/6";
let header = { contentType: "application/json" };

let response = await Server.Connector.HttpClient.DeleteAsync(url, header);
```

### Example: Response

```javascript
{
    "StatusCode": 200,
    "Body": "JsonString",
    "IsSuccessStatusCode": true,
    "ReasonPhrase": "OK",
    "ServerError": false,
    "ServerErrorMessage": null,
    "Headers": {
        "Transfer-Encoding": "chunked",
        "Connection": "keep-alive",
        "Server": "",
        "Content-Type": "application/json"
    }
}

```

## SiteSetting

Allows you to read site setting values for the current website.

**Example**

```javascript
Server.SiteSetting.Get("Search/Enabled");
```

## Website

Provides details of the current website record in Dataverse.

**Example**

```javascript
Server.Website.adx_primarydomain;
```

## User

Provides details of the signed-in user. Returns null if anonymous.

**Example**

```javascript
Server.User.fullname;
```

## Dataverse

The `Server.Connector.Dataverse` object lets you perform CRUD operations on Dataverse tables, and invoke custom APIs.

> [!NOTE]
>- Only Dataverse-bound actions and functions are supported.
>- When referring to Dataverse tables in your code, you need to use the [EntitySetName](/power-apps/developer/data-platform/entity-metadata#table-names), for example, to access the `account` table, the code syntax uses the EntitySetName of `accounts`.



### CreateRecord

Create new record.

```javascript
Server.Connector.Dataverse.CreateRecord(string entitySetName, string payload)   
```

#### Example

```javascript
Server.Connector.Dataverse.CreateRecord("accounts", "{\"name\": \"Contoso Ltd.\", \"telephone1\": \"555-555-0100\", \"websiteurl\": \"https://contoso.com\"}");
```

### RetrieveRecord

Retrieves a single record by ID. 

```javascript
Server.Connector.Dataverse.RetrieveRecord(string entitySetName, string id, string options = null)
```

**Example**

```javascript
Server.Connector.Dataverse.RetrieveRecord("accounts", "00000000-0000-0000-0000-000000000001", "$select=name,telephone1");
```

### RetrieveMultipleRecords

Retrieves a collection of records. 

```javascript
Server.Connector.Dataverse.RetrieveMultipleRecords(string entitySetName, string options = null)   
```

**Example**

```javascript
Server.Connector.Dataverse.RetrieveMultipleRecords("accounts", "$select=name,emailaddress1&$top=3");
```

### UpdateRecord

Updates an existing record by ID.

```javascript
Server.Connector.Dataverse.UpdateRecord(string entitySetName, string id, string payload)   
```

**Example**

```javascript
Server.Connector.Dataverse.UpdateRecord("accounts", "00000000-0000-0000-0000-000000000001", "{ \"telephone1\": \"555-555-0100\" }");
```

#### DeleteRecord

Deletes a record by ID. 

```javascript
Server.Connector.Dataverse.DeleteRecord(string entitySetName, string id) 
```

**Example**

```javascript
Server.Connector.Dataverse.DeleteRecord("accounts", "00000000-0000-0000-0000-000000000001");
```

#### InvokeCustomApi

```javascript
Server.Connector.Dataverse.InvokeCustomApi(string httpMethod, string url, string payload = null) 
```

Invoke a bound function:

```javascript
Server.Connector.Dataverse.InvokeCustomApi("get", "accounts(00000000-0000-0000-0000-000000000001)/Microsoft.Dynamics.CRM.new_CustomBoundFunction");
```

Invoke a bound action:

```javascript
Server.Connector.Dataverse.InvokeCustomApi("post", "accounts(00000000-0000-0000-0000-000000000001)/Microsoft.Dynamics.CRM.new_CustomBoundAction", "{ \"parameter1\": \"value1\" }");
```


### Example: Response

```javascript
{
    "StatusCode": 204,
    "Body": "",
    "IsSuccessStatusCode": true,
    "ReasonPhrase": "No Content",
    "ServerError": false,
    "ServerErrorMessage": null,
    "Headers": {
        "x-ms-cds-service-request-id": "00001111-aaaa-2222-bbbb-3333cccc4444"
    }
}
```

## Logger

Use the logger to write diagnostic messages that can be viewed in the [DevTools extension](../configure/devtools-addon.md).

Example:

```javascript
Server.Logger.Log("Information message");
Server.Logger.Warn("Warning message");
Server.Logger.Error("Error message");
```

## Context

Provides metadata about the current request, including query parameters, headers, and body.

### Properties

| Name              | Description               |
|-------------------|---------------------------|
| ActivityId        | Unique request ID         |
| Body              | Raw request body          |
| FunctionName      | Invoked function name     |
| Headers           | Request headers           |
| HttpMethod        | HTTP method               |
| QueryParameters   | Query string parameters   |
| ServerLogicName   | Name of the server logic  |
| Url               | Full request URL          |

**Example**

Read query parameter `id` from the URL:

```javascript
Server.QueryParameters['id'];
```

## Next step

[How to interact with Dataverse tables using server logic](server-logic-operations.md)

### Related information

[Server logic overview](server-logic-overview.md)  
[Author server logic](author-server-logic.md)  

