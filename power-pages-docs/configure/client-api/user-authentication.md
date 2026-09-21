---
title: Client API User Authentication Methods (Preview)
description: Learn how Client API user authentication uses the $pages.user object to sign users in and out of Power Pages sites. Explore the available methods.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API user authentication (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## $pages.user object

Client API user authentication uses the `$pages.user` object to sign users in and out of a Power Pages site. Use these methods to manage user access in client-side code.

### $pages.user methods

These methods don't return any value.

| Method | Description |
|--------|-------------|
| `signIn` | Redirects the user to the sign-in page. |
| `signOut` | Signs out the currently signed-in user. |

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
