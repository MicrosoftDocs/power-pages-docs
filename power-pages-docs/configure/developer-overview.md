---
title: Overview of developer capabilities
description: Learn how to customize and extend Power Pages using pro-developer tools and methods.
author: neerajnandwana-msft
ms.topic: overview
ms.custom: 
ms.date: 08/29/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: dmartens
contributors:
    - neerajnandwana-msft
    - nickdoelman
ms.collection: 
    - bap-ai-copilot
---

# Overview of developer capabilities

Power Pages provides tools for low-code makers and web designers to build and configure powerful websites.

In many projects, there's a need to further extend the capabilities of the web application that require pro-development techniques.

The Power Pages platform provides tools and technologies that empower a developer to address advanced and complex requirements.

## Tools

Tools are available to Power Pages developers to create assets, and to edit HTML, JavaScript, Liquid, and CSS code.

| Tool | Description | 
| - | - | 
| [Visual Studio Code for the Web](visual-studio-code-editor.md) | View and edit the HTML, JavaScript, Liquid, and CSS code. Edit code on multistep forms, basic forms, content snippets, lists, web files, web pages, and web templates. |
| [Visual Studio Code desktop](vs-code-extension.md) | View and edit the HTML, JavaScript, Liquid, and CSS code. Create web pages, web templates, page templates, content snippets, and web files. Edit code and website metadata with intellisense and generate code using Copilot. | 
| [Power Pages management app](portal-management-app.md) | Create Power Pages metadata records. View and edit the HTML, JavaScript, Liquid, and CSS code within the context of a model-driven app. |
| [Power Platform CLI](power-platform-cli.md) | Download and upload Power Pages metadata to your local workstation to edit in Visual Studio Code (or other editors). |
| [Community tools](/power-apps/developer/data-platform/community-tools) | There are many community tools that can assist developers in extending Power Pages. Tools created by the community aren't supported by Microsoft. If you have questions or issues with community tools, contact the publisher of the tool. |

## JavaScript

Websites created using Power Pages can utilize client side JavaScript to address many requirements.

- Add logic to form and list components to hide and show fields, set requirement levels, prepopulate values and other enhancements.
- Call APIs such as Power Automate and the Power Pages WebAPI.
- Build interactive functionality
- JavaScript be added to webpages, basic forms, multistep form steps, lists, and web templates.

More information: 
- [Add custom JavaScript](add-custom-javascript.md)
- [About basic forms](basic-forms.md#additional-settings)
- [Add custom JavaScript to a list](add-custom-javascript-list.md)


## Liquid

Liquid is an open-source template language integrated into Power Pages. It can securely retrieve data from Microsoft Dataverse and dynamically display content on webpages.

- Add dynamic content to webpages.
- Create custom web templates and web template components.
- Build configurable headers and navigation interfaces.

More information:
- [Liquid overview](liquid/liquid-overview.md)
- [Web templates overview](web-templates.md)
- [Web templates as components](./web-templates-as-components.md)

## Power Pages Web API

The Web API enables a richer user experience inside Power Pages sites. You can use the Web API to perform create, read, update, and delete operations across all Microsoft Dataverse tables from your webpages.

- Create and update records without using a form component.
- Retrieve information interactively from Microsoft Dataverse.

More information:
- [Web API overview](web-api-overview.md)

## Custom Components

Power Pages supports controls built for Power Apps created using the [Power Apps component framework](/power-apps/developer/component-framework/overview).

- Build custom user interface controls on fields on forms.
- Create a custom visual experience bound to datasets.

More information:
- [Code components overview](component-framework.md)

## AI-generated code 

Add AI-generated code using Copilot in Visual Studio Code helps you create code using natural language chat interaction.

More information:
- [Add AI-generated code using Copilot](add-code-copilot.md)


