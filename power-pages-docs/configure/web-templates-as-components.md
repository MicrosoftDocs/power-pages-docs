---
title: Web templates as components
description: Learn how to create and manage web templates as components in Power Pages.
author: clromano

ms.topic: conceptual
ms.custom: 
ms.date: 04/28/2023
ms.subservice:
ms.author: clromano
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - clromano
    - ProfessorKendrick
---

# Web templates as components

Web templates can be created and used as components in web pages to allow makers to use these reusable components and provide parameters to meet requirements.

As a developer, you can create a web template to provide specific functionality that can be configured by makers designing web pages.

To add a component to a web page, you can edit the page using the [Visual Studio Code for the Web](visual-studio-code-editor.md) and adding a Liquid include object to the page copy:

`{% include '<<web template name>>' <<parameter 1>>: '<<value>>' <<paramter 2>>: '<<value>>' %}`

Example:

`{% include 'webTemplateName' name: 'Topics' count:'4' %}`

## Create a web template component

To create a web template component to which you can allow a maker to pass parameters, you will need to add a `{% manifest %}` tag to the web template. The manifest section will describe the parameters that can be configured by a maker to pass and be used by the web template code.

The manifest is a JSON object that defines the properties of the web template that will be shown in the design studio: type, display name, description, tables, and parameters.  These properties can be used to bridge the gap between pro-developers and low-code editing as the parameters relate to variables that developers use in their source code while low-code makers can configure their values. 

### Manifest supported properties

| Manifest property | Description |
| - | - |
| Type | Needs to be either **Functional** or **Layout**.<br/><br/>**Layout**: Add the web template component through the **Add section** process in design studio.<br/><br/>**Functional**: Add the web template component through the **Add component** process in design studio. |
| displayName | Friendly name for the web template component, to be surfaced in the design studio. |
| description | Description of the web template component. |
| tables | An array of Dataverse tables where a maker will be able to navigate directly to the [Data workspace](../getting-started/use-data-workspace.md) to edit the tables configuration or records. The tables will need to be identified by their [logical name](/power-apps/developer/data-platform/entity-metadata#table-names). |
| params | Parameters with defined properties:<br/><br/>**id:** matches variable used in the web template code as well as the Liquid include tag.<br/><br/>**displayName:** Friendly name in design studio.<br/><br/>**description:** Short text surfaced through a tooltip to provide context to makers using the component. |

Example:

```html
{% manifest %} 
    { 
    "type": "Functional", 
    "displayName": "Data Cards", 
    "description": "This component displays data using a cards layout", 
    "tables": ["cards"], 
    "params": [ 
        { 
        "id": "title", 
        "displayName": "Title", 
        "description": "Heading for this component" 
        }, 
        { 
        "id": "count", 
        "displayName": "Count", 
        "description": "No. of items to be displayed" 
        }] 
    } 
{% endmanifest %} 

<!--additional web template code to use parameters to specialized functionality-->

```

When the web template component (with a manifest section) is created, you can add a corresponding Liquid reference to web page copy (using Visual Studio code for the web, Visual Studio code, Portal Management app or other methods) passing the various parameters, like the example below:

`{% include 'webTemplateName' name: 'Topics' count:'4' %}`

You will be able to configure the parameters directly in the design studio. This way a pro-developer can build advanced components using web templates that can be configured by low-code makers using the design studio.

