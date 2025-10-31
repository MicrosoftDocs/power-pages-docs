---
title: Create and manage server logic in Power Pages
description: Learn how to create and manage server logic in Power Pages, including setup steps, role assignments, and API integration examples.
#customer intent: As a developer, I want to create server logic in Power Pages so that I can define custom server APIs for my application.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 09/30/2025
ms.topic: concept-article
---

# Author server logic

Create server logic in the [Set up workspace](setup-workspace.md) in design studio. Each server logic record represents a distinct server API that you can invoke from the client with supported HTTP verbs.

## Steps to create server logic

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).
1. Select site **+ Edit**.
1. Navigate to the **Set up** workspace, then select **Server logic (preview)**.
    :::image type="content" source="media/server-logic-overview/server-logic-preview-screen.png" alt-text="Server logic preview screen showing different operations":::
1. Select **+New server logic**.
1. Enter name for the server logic. This name is used in API as resource identifier while constructing the server logic API.
1. Select **+Add roles** to assign appropriate web role.
1. Select 3 dots (**…**) next to name and select **Edit code.**
1. Select **Open Visual Studio Code** to author the custom logic.

## Call server logic from client script

> [!NOTE]
> Each request to server logic request should include Cross-Site Request Forgery (CSRF) token. In general, *webapi.safeAjax* method wraps the CSRF token. Learn more about how to construct requests in [CSRF wrapper AJAX function](/power-pages/configure/web-api-http-requests-handle-errors#example-wrapper-ajax-function-for-the-csrf-token).

### Example: calling HTTP GET

```javascript
webapi.safeAjax({
  type: "GET",
  url: "/_api/serverlogics/serverlogicname?id=1",
  contentType: "application/json",
  success: function (res) {
    console.log(res);
  }
});
```

### Example: calling HTTP POST

```javascript
webapi.safeAjax({
  type: "POST",
  url: "/_api/serverlogics/serverlogicname",
  contentType: "application/json",
  data: JSON.stringify({
    "name": "Sample name"
  }),
  success: function (res) {
    console.log("res");
  }
});
```

### Example: calling HTTP PUT

```javascript
webapi.safeAjax({
  type: "PUT",
  url: "/_api/serverlogics/serverlogicname",
  contentType: "application/json",
  data: JSON.stringify({
    "name": "Sample name"
  }),
  success: function (res) {
    console.log("res");
  }
});
```

### Example: calling HTTP PATCH

```javascript
webapi.safeAjax({
  type: "PATCH",
  url: "/_api/serverlogics/serverlogicname",
  contentType: "application/json",
  data: JSON.stringify({
    "name": "Sample name"
  }),
  success: function (res) {
    console.log("res");
  }
});
```

### Example: calling HTTP DELETE

```javascript
webapi.safeAjax({
  type: "DELETE",
  url: "/_api/serverlogics/serverlogicname?id=1",
  contentType: "application/json"
  success: function (res) {
    console.log("res");
  }
});
```

### Example: Response

```javascript
{
  "RequestId": "811b363e-36d2-4213-9f44-a73bf7550ce8",
  "Success": true,
  "Data": "Sample data",
  "ExecutionTime": 9256.331,
  "ServerLogicName": "serverlogicname",
  "Error": null
}
```

## Next step

[Server objects](server-objects.md)

### Related information

[Server logic overview](server-logic-overview.md)  
[How to interact with Dataverse tables using server logic](server-logic-operations.md)  
 

