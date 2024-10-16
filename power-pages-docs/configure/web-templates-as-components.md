---
title: Web templates as components
description: Learn how to create and manage web templates as components in Power Pages.
author: ckwan-ms

ms.topic: conceptual
ms.custom: 
ms.date: 10/16/2024
ms.subservice:
ms.author: ckwan
ms.reviewer: dmartens
contributors:
    - clromano
---

# Web templates as components

Web templates can be created and used as components in web pages to allow makers to use these reusable components and provide parameters to meet requirements.

As a developer, you can create a web template to provide specific functionality that makers can configure while designing web pages.

For example, you can create the following components (and others) as web template components that can be configurable in the design studio:

- Location listing with maps
- Carousel display
- Gallery of images or videos

To add a component to a web page, you can edit the page using the [Visual Studio Code for the Web](visual-studio-code-editor.md) and adding a Liquid include object to the page copy:

`{% include '<<web template name>>' <<parameter 1>>: '<<value>>' <<paramter 2>>: '<<value>>' %}`

Example:

`{% include 'webTemplateName' name: 'Topics' count:'4' %}`

## Create a web template component

To create a web template component to which you can allow a maker to pass parameters, you need to add a `{% manifest %}` tag to the web template. The manifest section describes the parameters that you can configure to pass and be used by the web template code.

The manifest is a JSON object that defines the properties of the web template displayed in the design studio: type, display name, description, tables, and parameters.  These web template properties can be used to bridge the gap between pro-developers and low-code editing. The parameters relate to variables that developers use in their source code, and low-code makers can configure their values. 

### Manifest supported properties

| Manifest property | Description |
| - | - |
| Type | Needs to be set to **Functional**.<br/><br/>**Functional**: Add the web template component through the **Add component** process in design studio. |
| displayName | Friendly name for the web template component, to be surfaced in the design studio. |
| description | Description of the web template component. |
| tables | An array of Dataverse tables a maker can use to navigate directly to the [Data workspace](../getting-started/use-data-workspace.md) to edit the tables configuration or records. The tables need to be listed using their [logical name](/power-apps/developer/data-platform/entity-metadata#table-names). |
| params | Parameters with defined properties:<br/><br/>**id:** matches variable used in the web template code and the Liquid include tag.<br/><br/>**displayName:** Friendly name in design studio.<br/><br/>**description:** Short text surfaced through a tooltip to provide context to makers using the component. |

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

### Write web template code

If you want to extend an existing out-of-the-box web template, we recommend that you create a copy of the web template and extend the copy to preserve source code and prevent data loss.

All parameters are passed as strings. In your code, it's recommended to convert the parameter values to the desired types as required. Converting parameters can be achieved using [Liquid filters](liquid/liquid-filters.md).

Examples:

- `{% assign posts_count = count | integer %}`
- `{% assign column_count = columns | integer %}`

## Configure a web template component on a web page

When the web template component (with a manifest section) is created, you can add a corresponding Liquid reference to web page copy (using Visual Studio Code for the web, Visual Studio Code, Portal Management app or other methods) passing the various parameters, as shown in this example:

`{% include 'webTemplateName' name: 'Topics' count:'4' %}`

You're able to configure the parameters directly in the design studio. This way a pro-developer can build advanced components using web templates that low-code makers can configure using the design studio.

:::image type="content" source="media/web-template-components/configure-parameters.png" alt-text="Configure parameters in design studio.":::

## Limitations and known issues

Nesting web template components into other web template components isn't supported.

## Next step

[How to create a web template component](web-templates-as-components-how-to.md)

## See Also

- [Display product reviews as cards](web-templates-as-components-product-reviews.md)
- [Display locations as cards](web-templates-as-components-location-cards.md)
- [Display records as a carousel](web-templates-as-components-carousel.md)
