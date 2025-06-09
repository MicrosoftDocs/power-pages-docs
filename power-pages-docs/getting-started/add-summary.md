---
title: Add a summary component in Power Pages  
description: Learn how to add and configure the Summarization component in Power Pages to summarize data from Dataverse tables using the Summarization API.  
author: nageshbhat-msft  
contributors:  
ms.topic: how-to  
ms.date: 05/12/2025  
ms.author: nabha  
ms.reviewer: smurkute  
---

# Add a summary component

The summarization component gives a summary of content using the Power Pages Web API. It summarizes data from one or more Dataverse tables through the Web API.

> [!NOTE]
> The summary component is available only on websites that enable [Data summarization](/power-pages/configure/data-summarization-api#site-settings) through site settings.

## How to add a summary component

To add the summary component to a page:

1. Open [design studio](/power-pages/getting-started/use-design-studio) to edit your page's content and components.

1. Select the page you want to edit.

1. Select the section where you want to add the summary.

1. Hover over any editable canvas area, then select the **Summary** component from the component panel.

:::image type="content" source="media/add-summary/add-summary-component.png" alt-text="Screenshot of adding the Summary component to a page in design studio.":::

### Summary settings

Update the following settings to format and display the summary:

| Title                  | Title of the summary component. |
|------------------------|--------------------------------------------------------------|
| Summarization API      | The pages API that retrieves data from Dataverse tables. |
| Additional instruction | Guides the summary's behavior, tone, and focus. Explains how the summary appears, including preferences for tone, detail level, and any topics to focus on or avoid. |
| Keep summary expanded  | Sets whether the summary component is expanded or collapsed when the page loads. |

## Summarization API

[Summarization API](/power-pages/configure/data-summarization-api) is built on top of the Power Pages Web API, which lets you retrieve data from Dataverse tables.

### Examples of summarization queries

1. To summarize title and comments columns of all feedback records:

    ```txt
    feedback?$select=title,comments
    ```

2. To summarize selected idea name, description, and all related active comments with column name description:

    ```txt
    adx_ideas({{id}})?$select=name,description&$expand=adx_ideacomment($select=adx_comments,description;filter=statecode eq 0)
    ```

    In this example, replace the placeholder *`<id>`* with your own value.
