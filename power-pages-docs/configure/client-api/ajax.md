---
title: Client API Server Endpoints and Cloud Flows (Preview)
description: Learn how to use the Power Pages Client API to call server endpoints, trigger cloud flows, handle errors, and cancel requests. Explore code examples.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API server endpoints and cloud flows (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## $pages.ajax

The `$pages.ajax` object provides a generic HTTP request method that you use to call server-side endpoints from your site. Use it to call server logic, cloud flows, and other custom `/_api/` endpoints from client scripts.
The `$pages.ajax` object provides a generic HTTP [request method](#request-method) that you use to call server-side endpoints from your site. Use it to call server logic, cloud flows, and other custom `/_api/` endpoints from client scripts.

Each request is handled automatically as follows:

- **Cross-site request forgery (CSRF) token**: The token is retrieved when it's first needed, cached in memory, and added to the header of every request. You don't need to retrieve or pass the token.
- **Credentials**: The session cookie is included with every request.
- **`x-requested-with` header**: This header is set to `XMLHttpRequest` on every request.

## request method

Makes an HTTP request to the specified URL.

**Syntax**: `$pages.ajax.request(options: object): Promise<AjaxResponse>`<br />
**Returns**: A [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to an [AjaxResponse](#ajaxresponse-object) object.

The promise rejects with an [AjaxError](#ajaxerror-object) object when the server returns a status code outside the 200–299 range or when the network fails. Cancellation errors from an `AbortSignal` object aren't wrapped in an [`AjaxError`](#ajaxerror-object) object. See [Cancel a request](#cancel-a-request).

### request method parameters

The `options` parameter accepts the following properties.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `url` | string | Yes | A relative path, such as `/_api/serverlogics/mylogic`, or an absolute URL. |
| `method` | string | No | The HTTP method: `GET`, `POST`, `PUT`, `PATCH`, or `DELETE`. This value isn't case-sensitive. The default value is `GET` when you don't provide a body, and `POST` when you provide a body. |
| `body` | object | No | The request payload, which is serialized to JSON automatically. The body is sent for all methods, including `GET`. A `GET` request with a body is nonstandard and some HTTP intermediaries remove it, so use a body with `GET` only when the API you call supports it. |
| `params` | object | No | Key/value pairs that are appended to the URL as a query string. Values are converted to strings. When the URL already contains a query string, the values are appended to it. |
| `headers` | object | No | More headers to merge with the default headers. You can't override the CSRF header or the `x-requested-with` header. |
| `signal` | [AbortSignal](https://developer.mozilla.org/docs/Web/API/AbortSignal) | No | A signal that cancels a request that's in progress. See [Cancel a request](#cancel-a-request). |

## AjaxResponse object

The [`request`](#request-method) method resolves to an object that has the following properties.

| Property | Type | Description |
|----------|------|-------------|
| `data` | unknown | The parsed response body. |
| `status` | number | The HTTP status code. |
| `ok` | boolean | True when the status code is in the 200–299 range. Because the [`request`](#request-method) method rejects for other status codes, this value is true for every response that the method resolves to. |
| `headers` | object | The response headers as key/value pairs. |

## AjaxError object

The [`request`](#request-method) method rejects with an object that has the following properties.

| Property | Type | Description |
|----------|------|-------------|
| `name` | string | The value `AjaxError`. Check this property to tell a failed request apart from other errors. |
| `message` | string | A description of the error. |
| `status` | number | The HTTP status code. The value is `0` when the network fails and no response is received. |
| `body` | unknown | The parsed response body when the server returns one; otherwise, null. |
| `requestId` | string \| undefined | The server-side request trace ID from the `x-ms-request-id` response header. Include this value when you report an issue. |

## Request method examples

Use the following examples to learn how to use the [request method](#request-method).

| Example | Description |
|---------|-------------|
| [Call server logic by using a GET request](#call-server-logic-by-using-a-get-request) | Passes query string parameters to server logic by using a GET request. |
| [Call server logic by using a POST request](#call-server-logic-by-using-a-post-request) | Sends a request body to server logic by using a POST request. |
| [Trigger a cloud flow](#trigger-a-cloud-flow) | Triggers a cloud flow registered with the site and handles the flow response. |
| [Update a resource by using a PUT request](#update-a-resource-by-using-a-put-request) | Updates a server resource by sending a request body with a PUT request. |
| [Delete a resource by using a DELETE request](#delete-a-resource-by-using-a-delete-request) | Deletes a server resource by using a DELETE request with query string parameters. |
| [Handle errors](#handle-errors) | Catches an `AjaxError` and logs its status, response body, and request ID. |
| [Cancel a request](#cancel-a-request) | Explains how an `AbortSignal` cancels a request and how cancellation errors are returned. |
| [Cancel a request after a fixed duration](#cancel-a-request-after-a-fixed-duration) | Uses `AbortSignal.timeout` to cancel a request after a maximum wait time. |
| [Cancel a request when a component is removed](#cancel-a-request-when-a-component-is-removed) | Uses an `AbortController` to cancel a request when its associated component is removed. |
| [Cancel a previous request](#cancel-a-previous-request) | Cancels an unfinished request before starting a replacement so that stale responses don't arrive out of order. |

### Call server logic by using a GET request

This example passes query string parameters to server logic.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const response = await $pages.ajax.request({
      method: 'GET',
      url: '/_api/serverlogics/getweather',
      params: { city: 'Seattle' }
    });
    console.log(response.data);
});
```

### Call server logic by using a POST request

This example sends a request body to server logic.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const response = await $pages.ajax.request({
      method: 'POST',
      url: '/_api/serverlogics/createorder',
      body: { productId: 'abc123', quantity: 2 }
    });
    console.log(response.data);
});
```

### Trigger a cloud flow

Power Pages design studio generates the cloud flow URL when you register the flow with the site.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const response = await $pages.ajax.request({
      method: 'POST',
      url: '/_api/cloudflow/v1.0/trigger/aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb',
      body: { Location: 'Seattle' }
    });

    // The data property is null when the flow has no Response action and returns 202 Accepted.
    // The data property contains the flow output when the flow has a Response action and returns 200 OK.
    if (response.data) {
      console.log(response.data);
    }
});
```

### Update a resource by using a PUT request

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.ajax.request({
      method: 'PUT',
      url: '/_api/serverlogics/updateprofile',
      body: { displayName: 'New Name' }
    });
});
```

### Delete a resource by using a DELETE request

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    await $pages.ajax.request({
      method: 'DELETE',
      url: '/_api/serverlogics/deleteitem',
      params: { id: '99' }
    });
});
```

### Handle errors

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    try {
      const response = await $pages.ajax.request({
        method: 'POST',
        url: '/_api/serverlogics/createorder',
        body: { productId: 'abc123', quantity: 2 }
      });
      console.log('Order created:', response.data);
    } catch (err) {
      if (err.name === 'AjaxError') {
        console.error(`Request failed with status ${err.status}`);
        console.error('Response body:', err.body);
        // Provide err.requestId to support for server-side tracing.
        if (err.requestId) {
          console.error('Request ID:', err.requestId);
        }
      } else {
        throw err;
      }
    }
});
```

### Cancel a request

The `signal` property accepts an [AbortSignal](https://developer.mozilla.org/docs/Web/API/AbortSignal) object. When the signal is aborted, the request in progress is canceled and the promise rejects with a cancellation error. This error isn't wrapped in an [AjaxError](#ajaxerror-object) object, and its `name` property is `CanceledError`. Don't treat this error as a failed request.

### Cancel a request after a fixed duration

Use the `AbortSignal.timeout` method to set a maximum wait time without managing a controller.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    try {
      const response = await $pages.ajax.request({
        method: 'GET',
        url: '/_api/serverlogics/slowlogic',
        signal: AbortSignal.timeout(5000) // Cancel after 5 seconds.
      });
      console.log(response.data);
    } catch (err) {
      // A timeout is reported as a CanceledError. The underlying DOMException, which has
      // the name TimeoutError, is available on err.cause when you need to tell a timeout
      // apart from a manual cancellation.
      if (err.name === 'CanceledError') {
        if (err.cause?.name === 'TimeoutError') {
          console.warn('Request timed out.');
        } else {
          console.warn('Request was canceled.');
        }
      } else {
        // Handle server and network failures.
        console.error(err);
      }
    }
});
```

### Cancel a request when a component is removed

When a request is tied to the lifecycle of a component, cancel the request when the component is removed so that your code doesn't update a component that no longer exists.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const controller = new AbortController();

    $pages.ajax.request({
      method: 'GET',
      url: '/_api/serverlogics/getdata',
      signal: controller.signal
    })
    .then(response => {
      // Update the UI with response.data.
    })
    .catch(err => {
      if (err.name !== 'CanceledError') {
        // Handle actual errors and ignore intentional cancellations.
        console.error(err);
      }
    });

    // Call this function from your cleanup logic, such as when the component
    // is removed from the page.
    const dispose = () => {
        controller.abort();
    };
});
```

### Cancel a previous request

When someone triggers a new request before the previous request finishes, such as when they type in a search box, cancel the previous request so that stale responses don't arrive out of order.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    let controller = null;

    async function search(query) {
      if (controller) {
        controller.abort(); // Cancel the previous request.
      }
      controller = new AbortController();

      try {
        const response = await $pages.ajax.request({
          method: 'GET',
          url: '/_api/serverlogics/search',
          params: { q: query },
          signal: controller.signal
        });
        console.log('Results:', response.data);
      } catch (err) {
        if (err.name !== 'CanceledError') {
          console.error(err);
        }
      }
    }

    // Run a search each time someone types in the search box.
    const searchBox = document.querySelector('#searchBox');

    if (searchBox) {
        searchBox.addEventListener('input', (e) => search(e.target.value));
    }
});
```

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
