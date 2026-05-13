---
title: Create and manage server logic in Power Pages
description: Learn how to create and manage server logic in Power Pages, including setup steps, role assignments, and API integration examples.
#customer intent: As a developer, I want to create server logic in Power Pages so that I can define custom server APIs for my application.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 05/13/2026
ms.topic: concept-article
---

# Author server logic

Create server logic in the [Set up workspace](setup-workspace.md) in design studio. Each server logic record represents a distinct server API that you can invoke from the client by using supported HTTP verbs.

## Steps to create server logic

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select site **+ Edit**.
1. Navigate to the **Set up** workspace, then select **Server logic**.
1. Select **+New server logic**.
1. Enter a name for the server logic. The API uses this name as the resource identifier when constructing the server logic API.
1. Select **+Add roles** to assign the appropriate web role.
1. Select the three dots (**…**) next to the name and select **Edit code**.
1. Select **Open Visual Studio Code** to author the custom logic.

## Call server logic from client script

> [!NOTE]
> Each request to server logic should include a Cross-Site Request Forgery (CSRF) token. In general, the *shell.safeAjax* method wraps the CSRF token. For more information about how to construct requests, see [CSRF wrapper AJAX function](/power-pages/configure/web-api-http-requests-handle-errors#example-wrapper-ajax-function-for-the-csrf-token).

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
## Limitations

The following limitations apply when authoring server logic:

- **Browser-specific APIs aren't supported**  
  Server logic runs in a server environment and doesn't support browser-based APIs or libraries.  
  Examples include `fetch`, `XMLHttpRequest`, and other DOM-related features.

- **Restricted keywords and patterns**  
  To maintain a secure execution environment, the system validates server logic scripts and rejects those that contain certain unsafe or restricted keywords. These keywords include those that enable dynamic code execution, process control, or prototype manipulation.

  The following patterns aren't allowed:
  
  ```
  __dirname
  __filename
  import(, import from
  eval(, Function(
  setTimeout(, setInterval(, setImmediate(
  process.exit, process.kill, child_process
  fs., require(
  constructor.constructor, this.constructor, arguments.callee
  with(, delete
  Object.getPrototypeOf, Object.setPrototypeOf
  Proxy(, Reflect.
  Symbol.for
  __proto__, prototype
  debugger
  ```

  
## Next step

[Server objects](server-objects.md)

### Related information

[Server logic overview](server-logic-overview.md)  
[How to interact with Dataverse tables using server logic](server-logic-operations.md)  
 

