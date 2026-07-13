---
title: Connect to Power Pages MCP server
description: Connect securely to Power Pages Model Context Protocol (MCP) Server. Learn how to expose APIs, manage permissions, and more.
#customer intent: As a Power Pages maker, I want to enable the MCP Server so that AI agents can securely interact with my portal data and APIs
author: shwetamurkute
ms.author: vipingulati
ms.reviewer: smurkute
ms.date: 07/13/2026
ms.topic: concept-article
ms.collection: bap-ai-copilot
---

# Model Context Protocol (MCP) Server for Power Pages overview

The Model Context Protocol (MCP) Server for Power Pages lets AI agents and copilots securely interact with Power Pages data through a standardized interface. This capability lets organizations extend their Power Pages sites into AI-native experiences while maintaining full control over security and permissions.

## What is MCP Server for Power Pages?

MCP Server for Power Pages is a feature that exposes Power Pages data, APIs, and business logic through an MCP-compliant interface. It lets AI agents like Microsoft 365 Copilot perform secure CRUD (Create, Read, Update, Delete) operations on Dataverse data while respecting web roles, table permissions, and authentication boundaries.

As organizations increasingly use AI agents to interact with business data, the need for secure, standardized interfaces between AI systems and enterprise applications grows. The Model Context Protocol provides this standardization, letting AI assistants query and manipulate Power Pages data conversationally through any MCP-compatible AI client.

## Key capabilities

With MCP Server for Power Pages, makers can:

- **Leverage Power Pages resources**: Make data, APIs, and business logic available through an MCP-compliant interface.
- **Enable secure CRUD operations**: Allow AI agents to interact with Power Pages Web APIs to create, read, update, and delete Dataverse records.
- **Maintain security controls**: Keep full control through web roles, table permissions, and authentication boundaries.
- **Extend to AI experiences**: Enable Power Pages sites to be consumed from Microsoft 365 Copilot.
- **Support internal workflows**: Empower internal teams to perform portal operations without navigating the portal UI.

## Related articles

- [Enable Power Pages MCP server](mcp-configure-entra.md)   
- [Connect to MCP server via Microsoft 365 Copilot](mcp-connect-clients.md)





















