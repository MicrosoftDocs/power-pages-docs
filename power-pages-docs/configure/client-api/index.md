---
title: Power Pages Client APIs Overview (Preview)
description: Learn how to use Power Pages client APIs to manipulate UI components, manage forms, lists, and user authentication effectively.
customer intent: As a developer, I want to retrieve all forms on a Power Pages site so that I can programmatically interact with them.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/09/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
- mkaur
---
# Power Pages client APIs (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Power Pages client APIs help developers manipulate UI components, manage forms and lists, handle user authentication, and interact with Dataverse records programmatically. The client API becomes available when your page loads and can be accessed through a global variable with a name you choose.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

This documentation uses the variable name `$pages` throughout examples and recommends you follow this naming convention for consistency.

By using the `$pages` client API, you can:

- Retrieve and modify forms and form controls
- Validate data that people enter in form controls
- Show or hide UI elements
- Read and style rows, columns, and cells in modern lists
- Create, retrieve, update, and delete records by using the Web API
- Upload and download files and images stored in file and image columns
- Manage user authentication
- Work with multilingual content
- Call server logic, cloud flows, and other custom endpoints by using the Ajax API
- Communicate with Microsoft Copilot Studio agents

## Client API reference

| Area | Reference |
|------|-----------|
| Initialization | [Client API initialization](initialization.md) |
| Forms, tabs, and sections | [Client API forms, tabs, and sections](forms-tabs-sections.md) |
| Controls | [Client API controls](control-methods.md) |
| Control types | [Client API control types](controls.md) |
| Lists | [Client API lists](lists.md) |
| User authentication | [Client API user authentication](user-authentication.md) |
| Dataverse records, files, and images | [Client API Dataverse records, files, and images](dataverse.md) |
| Languages | [Client API languages](languages.md) |
| Server endpoints and cloud flows | [Client API server endpoints and cloud flows](ajax.md) |
| Copilot Studio agents | [Client API Copilot Studio agents](agents.md) |

## Related information

- [Client API examples](examples.md)
