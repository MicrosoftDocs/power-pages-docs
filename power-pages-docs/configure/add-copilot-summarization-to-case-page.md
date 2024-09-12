---
title: How to - add Copilot summarization to case page (preview)
description: Learn how to add Copilot summarization to the case page in Power Pages.
author: nageshbhat-msft
ms.topic: conceptual
ms.date: 09/13/2024
ms.author: nabha
ms.reviewer: dmartens
ms.collection:
 - bap-ai-copilot
contributors:
    - dmartens
    - tapanm
---

# Add Copilot summarization to case page

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

In this guide, you can set up the Copilot summarization section for the support case page, enabling users to quickly review the case and its timeline summary.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Prerequisites

Make sure you use the site created using the [Community](/power-pages/templates/dynamics-365-apps/overview?WT.mc_id=powerportals_inproduct_portalstudio2#community) or the [Customer self-service](/power-pages/templates/dynamics-365-apps/overview?WT.mc_id=powerportals_inproduct_portalstudio2#customer-self-service) portal template. These portals contain the support case page.

## Step 1 - Create site settings

Before you can use the summarization API, you have to enable the required site settings with the Portal Management app.

1. Start the [Portal Management app](/power-pages/configure/portal-management-app).

1. On the selected website record, select **Site Settings**.

1. Enter the following site settings and values:

    | Setting Description                              | Name                              | Value                                      |
    |--------------------------------------------------|-----------------------------------|--------------------------------------------|
    | Enable the summarization API                     | Summarization/Data/Enable         | true                                       |
    | Set the summarization prompt                     | Summarization/prompt/case_summary | "Summarize key details and critical information" |
    | Enable the web API for the case table            | Webapi/incident/enabled           | true                                       |
    | Enable description and title field of the case table | Webapi/incident/fields            | description,title                      |
    | Enable the portal comments table for the web API | Webapi/adx_portalcomment/enabled  | true                                       |
    | Enable the description field of the portal comments table | Webapi/adx_portalcomment/fields   | description                                |

## Step 2 - Add Copilot summary section

In this step, you add a summary section on top of the case page.

1. Open [Power Pages studio](https://make.powerpages.microsoft.com).
1. Select **Edit** for the site you want to edit.
1. Select **Customer Service - Edit Case**

   On this page, you add a summary section.
1. Select **Edit code** to open **Visual Studio Code**.
1. Copy the following code and add it to the beginning of the code block.

    `<PLACEHOLDER FOR CODE>`

1. Save the file.
1. Select **Preview** to open the site.

## Step 3 - Test the summarization

1. Select the **My support** tab.
1. Create a new case and add a case description.
1. Add a couple of comments.
1. To view the case summary, select the down arrow in the Copilot summary section.
1. Try these steps for other case records.

## Related information

- [Data summarization API (preview)](data-summarization-api.md)
- [FAQ for data summarization API](..\faqs-data-summarization.md)
