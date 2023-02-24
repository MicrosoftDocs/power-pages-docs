---
title: Portal Management app overview
description: Learn how to use the Portal Management app.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 02/24/2023
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Portal Management app overview

The Portal Management app lets you do advanced configuration actions on your site and allows you to configure the site metadata directly using a model-driven Power App.

> [!NOTE]
> To use the Portal Management app, you will need to be assigned the [system administrator role](/power-platform/admin/assign-security-roles) in the same Microsoft Dataverse environment as your site.  

## Open the Portal Management app from the Power Pages home page



## Open the Portal Management app from the Power Pages design studio

In the design studio, select the ellipsis (**...**) from the tool belt, and then select **Portal Management**.

:::image type="content" source="media/portals-management-app/launch-portals-management-app.png" alt-text="Open the Portal Management app.":::

## Open the Portal Management app from Power Apps

To open Portal Management app:

1. Go to [Power Apps](https://make.powerapps.com).

1. Select **Apps** from the left pane.

1. Select **Portal Management** app to open.

1. **Portal Management** app opens in a new browser tab.

To get started with configuring your site, select the relevant option from the left pane.

## Browser considerations

If your web browser has any extensions such as ad-blockers, you may see a script error when using the Portal Management app: `One of the scripts for this record has caused an error. For more details, download the log file.` In addition, the downloaded log file may reference this error: `ReferenceError: Web resource method does not exist.` 

:::image type="content" source="media/portals-management-app/script-error.png" alt-text="Script error":::

This error occurs for forms such as [Web pages](web-page.md), [Basic Forms](entity-forms.md), [Lists](entity-lists.md), or [Multistep Form Steps](web-form-steps.md). To resolve this error, disable extensions such as ad-blockers in your browser. You may also use a different browser instead that doesn't have such extensions enabled.