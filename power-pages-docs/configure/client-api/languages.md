---
title: "Client API Languages: Get and Set Website Languages (Preview)"
description: Explore Power Pages Client API languages to retrieve available website languages, identify the active language, and switch languages with a practical example.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API languages (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Use the Power Pages Client API languages object, [`$pages.languages`](#pageslanguages-object), to retrieve the site's available languages, identify the active language, and switch languages when needed.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## $pages.languages object

| Method | Returns | Description |
|--------|---------|-------------|
| `getAll()` | `string[]` | Returns the languages enabled for the website. |
| `getActive()` | `string` | Returns the currently active language. |
| `setActive(language: string)` | `void` | Sets the active language and reloads the page. |

## Client API language example

This example retrieves all languages enabled for the website, gets the active language, and then sets Hindi (India) as the active language, which reloads the page.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const allLanguages = $pages.languages.getAll();
    const activeLanguage = $pages.languages.getActive();
    $pages.languages.setActive('hi-IN');
});
```

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
