---
title: Portal Management app overview
description: Learn how to use the Portal Management app.
author: gitanjalisingh33msft
ms.topic: conceptual
ms.custom: 
ms.date: 06/31/2024
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - ProfessorKendrick
    - gitanjalisingh33msft
    - DanaMartens
---

# Portal Management app overview

You can use the Portal Management app, a model-driven Power App, for advanced configuration of your Power Pages sites.

> [!IMPORTANT]
> - If your website is using the [enhanced data model](../admin/enhanced-data-model.md), the app will appear as **Power Pages Management**.
> - Starting in August 2023, the Power Pages Management app is installed by default on new instances of Microsoft Dataverse in supported regions, including environments where there are no Power Pages sites.

## Prerequisites

To use the Portal Management app, you need to be assigned the [system administrator](/power-platform/admin/assign-security-roles) role in the same Microsoft Dataverse environment as your site. Users in the [system customizer](/power-platform/admin/assign-security-roles) role also have access to use the Portal Management app however they may have limited privileges on certain tables (for example,  Notes / Attachments related to [Web Files](/power-apps/maker/portals/configure/web-files)) that do not allow them to view or update records created by other users.

## Open the Portal Management app from the Power Pages home page

On the Power Pages home page, select the ellipsis (**...**) from the site section, and select **Portal management**.

:::image type="content" source="media/portals-management-app/home-page.png" alt-text="Launch Portal Management app from home page.":::

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

This error occurs for forms such as [Web pages](web-page.md), [Basic Forms](basic-forms.md), [Lists](lists.md), or [Multistep Form Steps](multistep-form-steps.md). To resolve this error, disable extensions such as ad-blockers in your browser. You may also use a different browser instead that doesn't have such extensions enabled.
