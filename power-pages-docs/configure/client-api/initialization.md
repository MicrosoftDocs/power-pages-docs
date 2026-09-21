---
title: Client API Initialization (Preview)
description: Learn how Power Pages Client API initialization works with callback and Promise/await patterns, then choose the best approach for your scripts.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API initialization (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Microsoft.PowerPages.onPagesClientApiReady

Power Pages Client API initialization doesn't occur immediately when the page loads. Use the `Microsoft.PowerPages.onPagesClientApiReady` function to assign the API object to `$pages` when it's ready, so your scripts can access page APIs only after initialization completes. You can initialize it in two ways.

> [!IMPORTANT]
> The `Microsoft.Dynamic365.Portal.onPagesClientApiReady` alias is deprecated. It still works so that existing scripts keep running, but it writes a one-time warning to the browser console and is removed in a future release. Use `Microsoft.PowerPages.onPagesClientApiReady` instead.

## Callback-based API readiness

Use a callback function that assigns the API object to a variable you define when it's ready. Two examples show how:

By using an anonymous function:

```javascript
Microsoft.PowerPages.onPagesClientApiReady(($pages) => {
    const forms = $pages.currentPage.forms.getAll();
    console.log(`Found ${forms.length} forms on the page.`);
});
```

By using a named function:

```javascript
function start($pages){
    const forms = $pages.currentPage.forms.getAll();
    console.log(`Found ${forms.length} forms on the page.`);
}

Microsoft.PowerPages.onPagesClientApiReady(start)
```


## Promise/await-based API readiness

Uses [await](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/await) to handle the promise returned by the `Microsoft.PowerPages.onPagesClientApiReady` function for a cleaner async flow.

```javascript
let $pages = await Microsoft.PowerPages.onPagesClientApiReady();
const forms = $pages.currentPage.forms.getAll();
console.log(`Found ${forms.length} forms on the page.`);
```

## When to use each approach

The following table describes when to use each approach.

| Approach | When to use |
|----------|-------------|
| **[Callback-based API readiness](#callback-based-api-readiness)** | Use when you need to support older browsers or legacy scripts that don't support `async/await`, or when you want to register multiple handlers that run when the API is ready. Ideal for event-driven patterns. |
| **[Promise/await-based API readiness](#promiseawait-based-api-readiness)** | Use in modern JavaScript environments that support `async/await` for cleaner, sequential code. Best when your logic depends on the API being ready before continuing execution. |

> [!TIP]
> If your codebase already uses `async/await`, prefer the Promise-based approach for consistency.

The examples in this article and in [Client API control types](controls.md) use the callback-based pattern with an `async` callback, so that each example can use `await` when it calls an asynchronous method. Omit the `async` keyword when your own code doesn't use `await`. Each example demonstrates one or more API calls, and the [agent examples](agents.md#sendactivity-method) build on the values that the preceding example defines. For examples that combine several APIs to implement a complete scenario, see [Power Pages Client API examples](examples.md).

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
