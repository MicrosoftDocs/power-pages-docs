---
title: Create and Manage Server Logic in Power Pages
description: Learn how to create and manage server logic in Power Pages Studio, including setup steps, role assignments, and API integration examples.
#customer intent: As a developer, I want to create server logic in Power Pages Studio so that I can define custom server APIs for my application.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 09/30/2025
ms.topic: concept-article
---

# Author server logic

Server logic is created using the Set up workspace in Power Pages Studio. Each server logic record represents a distinct server API that can be invoked from the client with supported HTTP verbs.

## Steps to create server logic

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

2. Select site **+ Edit**.

3. Navigate to the **Set up** workspace, then select **Server logic (preview)**.

4. Click **+New server logic**.

5. Enter name for the server logic. This name is used in API as resource identifier while constructing the server logic API.

6. Click **+Add roles** to assign appropriate web role.

7. Select 3 dots (**…**) next to name and select **Edit code.**

8. Select **Open Visual Studio Code** to author the custom logic.

## Calling server logic from client script

> [!NOTE]
> Each request to server logic request should include Cross-Site Request Forgery (CSRF) token. In general, *shell.safeAjax* method wraps the CSRF token. You refer here for construction of [CSRF wrapper ajax function](/power-pages/configure/web-api-http-requests-handle-errors#example-wrapper-ajax-function-for-the-csrf-token).

### Example: calling HTTP GET

```javascript
shell.safeAjax({
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
shell.safeAjax({
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
shell.safeAjax({
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
shell.safeAjax({
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
shell.safeAjax({
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


