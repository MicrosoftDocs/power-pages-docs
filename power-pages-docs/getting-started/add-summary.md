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

The summarization component provides a summary of the content given using Power Pages Web API. Components can summarize the data from one or more Dataverse tables used on the Web API.

> [!NOTE]
> The summary component is only available on websites that have [Data summarization](/power-pages/configure/data-summarization-api#site-settings) enabled using site settings.

## How to add a summary component

To insert the summary component into a page:

1. Open [design studio](/power-pages/getting-started/use-design-studio) to edit the content and components of your page.

1. Select the page you want to edit.

1. Select the section you want to add the summary to.

1. Hover over any editable canvas area, then select the **Summary** component from the component panel.

:::image type="content" source="media/add-summary/add-summary-component.png" alt-text="Screenshot of adding the Summary component to a page in the design studio.":::

### Summary Settings

Update below settings to format and display the data summarization:

| Title                  | Title of the summary component  |
|------------------------|--------------------------------------------------------------|
| Summarization API      | The pages API to retrieve the data from the Dataverse tables   |
| Additional instruction | This setting guides the summary behavior, tone, and focus. It explains how the summary should appear, including preferences for tone, detail level, and any topics to focus on or avoid. |
| Keep summary expanded  | Flag to set summary component expanded or collapsed on page load  |

## Summarization API

[Summarization API](/power-pages/configure/data-summarization-api) is built on top of the Power Pages Web API which is used to retrieve the data from the Dataverse tables.

### Examples of summarization queries

1. To summarize title and comments columns of all feedback records:

`feedback?$select=title,comments`

2. To summarize selected idea name, description, and all related active comments with column name description:

`adx_ideas({{id}})?$select=name,description&$expand=adx_ideacomment($select=adx_comments,description;filter=statecode eq 0)`

whereas `{{id}}` is the query string parameter passed to the webpage.
