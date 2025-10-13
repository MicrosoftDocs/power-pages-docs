---
title: Access user and website details with server objects
description: Learn how to use built-in server objects like Logger, HttpClient, and Dataverse to simplify development and integrate with external services effectively.
#customer intent: As a developer, I want to send HTTP requests using the **HttpClient** object so that I can integrate with external services.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 09/30/2025
ms.topic: concept-article
---

# Server objects 

Server logic provides built-in objects under the Server namespace. These objects simplify development by letting you log messages, call external services, work with Dataverse, or access request details.


## Logger

Use the logger to write diagnostic messages that can be viewed in the [DevTools extension](../configure/devtools-addon.md).

Example:

```javascript
Server.Logger.Log("Information message");
Server.Logger.Warn("Warning message");
Server.Logger.Error("Error message");
```

## HttpClient

Use the HTTP client to integrate with external services by sending HTTP requests.

> [!NOTE]
> Currently server logic supports only `application/json` and `application/x-www-form-urlencoded` content types in request body.

### Examples

#### HTTP GET

```javascript
Server.Connector.HttpClient.GetAsync("https://contoso.com/objects", {"client_id": "00000000-0000-0000-0000-000000000000"});
```

#### HTTP POST

```javascript
Server.Connector.HttpClient.PostAsync("https://contoso.com/objects", "{\"name\": \"Apple MacBook Pro 16\"}", {"client_id": "30d49153-11da-4994-a58f-7be8e91c6"}, "application/json");
```

#### HTTP PUT

```javascript
Server.Connector.HttpClient.PutAsync("https://contoso.com/objects/6", "{\"name\": \"Updated MacBook\"}", {"client_id": "00000000-0000-0000-0000-000000000000"}, "application/json");
```

#### HTTP PATCH

```javascript
Server.Connector.HttpClient.PatchAsync("https://contoso.com/objects/6", "{\"capacity\": \"2 TB\"}", {"client_id": "00000000-0000-0000-0000-000000000000"}, "application/json");
```

#### HTTP DELETE

```javascript
Server.Connector.HttpClient.DeleteAsync("https://contoso.com/objects/6", {"content-type": "application/json"});
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

## Dataverse

The `Server.Connector.Dataverse` object lets you perform CRUD operations on Dataverse tables, as well as invoke custom APIs.

> [!NOTE]
>- Only Dataverse-bound actions and functions are supported.
>- When referring to Dataverse tables using the portals Web API in your code, you need to use the [EntitySetName](../power-apps/developer/data-platform/entity-metadata.md#table-names), for example, to access the `account` table, the code syntax uses the EntitySetName of `accounts`.



### CreateRecord

Create new record.

```javascript
Server.Connector.Dataverse.CreateRecord(string entitySetName, string payload)   
```

#### Example

```javascript
Server.Connector.Dataverse.CreateRecord("accounts", "{\"name\": \"Contoso Ltd.\", \"telephone1\": \"123-456-7890\", \"websiteurl\": \"https://contoso.com\"}");
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
Server.Connector.Dataverse. Server.Connector.Dataverse.UpdateRecord(string entitySetName, string id, string payload)   
```

**Example**

```javascript
Server.Connector.Dataverse.UpdateRecord("accounts", "00000000-0000-0000-0000-000000000001", "{ \"telephone1\": \"987-654-3210\" }");
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
        "x-ms-cds-service-request-id": "00000000-0000-0000-0000-000000000000"
    }
}
```


## User

Provides details of the signed-in user. Returns null if anonymous.

**Example**

```javascript
Server.User.fullname;
```

## Website

Provides details of the current website record in Dataverse.

**Example**

```javascript
Server.Website.adx_primarydomain;
```

## SiteSetting

Allows you to read site setting values for the current website.

**Example**

```javascript
Server.SiteSetting.Get("Authentication/Registration/Enabled");
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
