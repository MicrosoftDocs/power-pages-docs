---
title: Add a custom component (preview)
description: Learn how to add a custom component to a section in a Power Pages site.
author: pranita225
ms.topic: conceptual
ms.custom: 
ms.date: 08/07/2024
ms.subservice:
ms.author: prpadalw
ms.reviewer: dmartens
contributors:
    - DanaMartens
    - ProfessorKendrick
---

# Add a custom component (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

A custom component, also referred to as a web template, is a Power Pages site metadata record used to store template source content. Typically, a web template contains [Liquid](../configure/liquid-overview.md) for dynamic content rendering and serves as the central table for integrating Liquid templates with the rest of Power Pages.

Now, custom components can be added to a section of a page within the Pages workspace in the design studio, just like other components. Previously, adding a custom component to a web page required writing code in a code editor like VS Code. This section guides makers on how to add existing custom components with a manifest to a web page. Learn more about how to create a custom component or add manifests to them at [Web templates as components](../configure/web-templates-as-components.md).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

To add a custom component to a web page:

1. Open the design studio to edit the site's content and components.
1. Go to the **Pages** workspace.
1. Select the page you want to edit.
1. Select the section where you want to add the custom component. You can also [add a new section](add-sections.md) for the component.
1. Select the ellipses, and then select the custom component from the list.

    :::image type="content" source="media/custom-components/add-custom-component.png" alt-text="Screenshot of adding a custom component to a section.":::

    This list displays only the custom components in the site that have a manifest. If no such components exist, a "learn more" link is shown.

## Related information

[Web templates as components](../configure/web-templates-as-components.md)
