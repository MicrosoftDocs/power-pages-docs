---
title: Access user and website details with server objects
description: Learn how to use built-in server objects like Logger, HttpClient, and Dataverse to simplify development and integrate with external services effectively.
#customer intent: As a developer, I want to send HTTP requests using the **HttpClient** object so that I can integrate with external services.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 09/15/2026
ms.topic: reference
---

# Server objects 

Server logic provides built-in objects under the server namespace. These objects simplify development by letting you log messages, call external services, work with Dataverse, or access request details.

## HttpClient

Use the HTTP client to integrate with external services by sending HTTP requests.

> [!NOTE]
> Currently, server logic supports only `application/json`, `text/html`, and `application/x-www-form-urlencoded` content types in the request body.

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

Use this connector to read site setting values for the current website.

> [!NOTE]
> Don't store secrets, such as API keys or credentials, directly in server logic. Instead, store them securely in Azure Key Vault, source them through environment variables, and reference them by using site settings.

**Example**

```javascript
Server.SiteSetting.Get("Search/Enabled");
```

## EnvironmentVariable

Use this connector to read the value of an environment variable.

**Example**

```javascript
Server.EnvironmentVariable.get("SITEPATH");
```


## Website

Use this connector to get details of the current website record in Dataverse.

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

Use the `Server.Connector.Dataverse` object to perform CRUD operations on Dataverse tables and invoke custom APIs.

> [!NOTE]
>- When you refer to Dataverse tables in your code, use the [EntitySetName](/power-apps/developer/data-platform/entity-metadata#table-names). For example, to access the `account` table, use the EntitySetName `accounts`.



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
Server.Connector.Dataverse.RetrieveRecord(string entitySetName, string id)
Server.Connector.Dataverse.RetrieveRecord(string entitySetName, string id, string options)
Server.Connector.Dataverse.RetrieveRecord(string entitySetName, string id, string options, bool skipCache)
```

**Example**

```javascript
Server.Connector.Dataverse.RetrieveRecord("accounts", "00000000-0000-0000-0000-000000000001", "$select=name,telephone1");
```

### RetrieveMultipleRecords

Retrieves a collection of records. 

```javascript
Server.Connector.Dataverse.RetrieveMultipleRecords(string entitySetName)
Server.Connector.Dataverse.RetrieveMultipleRecords(string entitySetName, string options)
Server.Connector.Dataverse.RetrieveMultipleRecords(string entitySetName, string options, bool skipCache) 
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

Invoke an unbound action:

```javascript
Server.Connector.Dataverse.InvokeCustomApi("post", "new_Action", "{ \"parameter1\": \"value1\" }");
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

## CloudFlow

Use the `Server.Connector.CloudFlow` object to trigger a Power Automate cloud flow from server logic. The flow must already be [added to your site](/en-us/power-pages/configure/cloud-flow-integration#add-a-flow-to-your-site). It's the server-side equivalent of invoking a flow by using the [cloud flow API](/en-us/power-pages/configure/cloud-flow-integration#invoke-a-flow-from-web-page) from a webpage. It uses the same underlying pipeline as the `/_api/cloudflow/v1.0/trigger/<guid>` endpoint. Setup, authorization, and payload behavior are the same. Only the calling context differs.

> [!NOTE]
> - `Server.Connector.CloudFlow.TriggerAsync` is asynchronous. Use `await` and mark the calling function `async`.
> -  Before you can trigger a flow from server logic, [create the flow](/en-us/power-pages/configure/cloud-flow-integration#create-a-flow) and [add it to your site with an authorized web role](/en-us/power-pages/configure/cloud-flow-integration#add-a-flow-to-your-site). The signed-in user must hold one of those roles.
> -  If you move a site to another environment, [register the cloud flow in the target environment](/en-us/power-pages/configure/cloud-flow-integration#application-lifecycle-management-alm-for-cloud-flows) before you invoke it.

### TriggerAsync

Triggers a cloud flow and returns the response envelope.

```javascript
Server.Connector.CloudFlow.TriggerAsync(string flowId, string payload = null)
```

- `flowId`: The flow identifier. The same GUID that appears in the [cloud flow API URI](/en-us/power-pages/configure/cloud-flow-integration#invoke-a-flow-from-web-page) (`/_api/cloudflow/v1.0/trigger/<guid>`). You can find this value on the site's **Cloud flows** page under **Set up** > **Integrations**.
- `payload`: Optional JSON string that contains [trigger input parameters](/en-us/power-pages/configure/cloud-flow-integration#passing-parameter-to-cloud-flow), keyed by the parameter names defined on the flow's trigger. Pass `null` or an empty string if the flow takes no inputs. The `siteId`, `siteUrl`, and `userId` are added to the payload automatically.


#### Example

```javascript
async function post() {
    let flowId = "00000000-0000-0000-0000-000000000001";
    let payload = JSON.stringify({ Location: "Seattle" });

    let response = await Server.Connector.CloudFlow.TriggerAsync(flowId, payload);
    let result = JSON.parse(response);

    if (!result.IsSuccessStatusCode) {
        Server.Logger.Error("Cloud flow trigger failed: " + result.ReasonPhrase);
        return JSON.stringify({ success: false, error: result.ReasonPhrase });
    }

    return JSON.stringify({ success: true, flowResponse: result.Body });
}
```

### Example: Response

```javascript
{
    "StatusCode": 200,
    "Body": "JsonString",
    "IsSuccessStatusCode": true,
    "ReasonPhrase": "OK",
    "ServerError": false,
    "ServerErrorMessage": null
}
```

If the cloud flow doesn't include a response action, it returns `202 Accepted` and an empty `Body`. In server logic, this response is reported as `IsSuccessStatusCode: true`.

## Logger

Use the logger to write diagnostic messages that you can view in the [DevTools extension](../configure/devtools-addon.md).

Example:

```javascript
Server.Logger.Log("Information message");
Server.Logger.Warn("Warning message");
Server.Logger.Error("Error message");
```

## Context

The `Server.Context` object provides information about the current server logic invocation. The available properties depend on whether the server logic was invoked through an HTTP request or from a Liquid template.

### Properties

| Name | Available for | Description |
| --- | --- | --- |
| `ActivityId` | HTTP and Liquid | Unique identifier for the server logic invocation. Use this value to correlate logs and troubleshoot an operation. |
| `Body` | HTTP | Raw HTTP request body. |
| `FunctionName` | HTTP and Liquid | Name of the JavaScript function being invoked. For a Liquid invocation, this value corresponds to the `operation` parameter of the `serverlogic` tag. |
| `Headers` | HTTP | HTTP request headers. |
| `HttpMethod` | HTTP | HTTP request method, such as `GET`, `POST`, `PUT`, `PATCH`, or `DELETE`. |
| `Input` | Liquid | Input string supplied through the `input` parameter of the `serverlogic` Liquid tag. When the input contains structured data, parse it as JSON before using it. |
| `QueryParameters` | HTTP | Query-string parameters from the HTTP request. |
| `ServerLogicName` | HTTP and Liquid | Name of the server logic record being invoked. |
| `Url` | HTTP | Full URL of the HTTP request. |

### Access HTTP request context

The following example reads the `id` query parameter when server logic is invoked through an HTTP request:

```javascript
var id = Server.Context.QueryParameters["id"];
```

You can also access request metadata:

```javascript
function getRequestInformation() {
    return JSON.stringify({
        activityId: Server.Context.ActivityId,
        functionName: Server.Context.FunctionName,
        httpMethod: Server.Context.HttpMethod,
        serverLogicName: Server.Context.ServerLogicName,
        url: Server.Context.Url
    });
}
```

### Access Liquid invocation context

When server logic is invoked from Liquid, use `Server.Context.Input` to read the value supplied through the tag's `input` parameter.

For example, the following Liquid passes JSON input:

```liquid
{% assign inputData = '{"category":"active","maximumResults":5}' %}

{% serverlogic output: result, name: 'customer-summary', operation: 'getSummary', input: inputData %}
```

The server logic operation can parse the input and access information about the Liquid invocation:

```javascript
function getSummary() {
    var input = JSON.parse(Server.Context.Input || "{}");

    return JSON.stringify({
        category: input.category,
        maximumResults: input.maximumResults,
        activityId: Server.Context.ActivityId,
        functionName: Server.Context.FunctionName,
        serverLogicName: Server.Context.ServerLogicName
    });
}
```


## Next step

[How to interact with Dataverse tables using server logic](server-logic-operations.md)

### Related information

[Server logic overview](server-logic-overview.md)  
[Author server logic](author-server-logic.md)  

