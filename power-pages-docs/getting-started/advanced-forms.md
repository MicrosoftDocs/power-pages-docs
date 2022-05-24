---
title: Advanced forms
description: Learn how to add advanced forms to your Power Pages site.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/24/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Add an advanced form

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE[powerapps-info](../includes/cc-powerapps-info.md)]

You can create Advanced forms by using the [Portal Management app](../configure/portal-management-app.md). For details on how to create advanced forms, go to [Define advanced form properties for portals](/power-apps/maker/portals/configure/web-form-properties) in the Power Apps portals documentation.

After you've created your advanced form configuration, you can add it to your page in the design studio with the code editor.

1. In the design studio, create or edit a page.

1. Select the [code editor](code-editor.md) icon, and in between the `<div></div>` tags, enter the following Liquid code snippet:

    ```html
    {% webform name: '<name of advanced form>' %}
    ```

    For example, if your advanced form name is *Scholarship Application*, the code will be:

    ```html
    {% webform name: 'Scholarship Application' %}
    ```

    :::image type="content" source="media/first-page/add-advanced-form.png" alt-text="Adding an advanced form.":::

1. Select **Save** in the code editor window.

### See also

[Tutorial: Add a multi-step form to your page](tutorial-add-multi-step-form.md)<br>