---
title: Add a search component  
description: Learn how to add and configure the Search component, including AI-powered search features, search bar settings, and creating a custom search results page.  
author: nageshbhat-msft  
contributors:  
ms.topic: how-to  
ms.date: 04/23/2025  
ms.author: nabha  
ms.reviewer: dmartens  
---

# Add a search component

The search component lets users input queries and find information on a website. It's especially useful for content-heavy sites where users need to quickly locate relevant information.

> [!NOTE]  
> The AI-powered search component is available only on websites that have [Generative AI Search](/power-pages/configure/search/generative-ai#enable-site-search-with-generative-ai) enabled.  

## How to add a search component

To insert the search component into a page:

1. Open [design studio](/power-pages/getting-started/use-design-studio) to edit the content and components of your page.
1. Select the page you want to edit.
1. Select the section you want to add the search to.
1. Hover over an editable canvas area and select **Search** from the component panel.

:::image type="content" source="media/add-search/add-search-component.png" alt-text="Screenshot of adding the Search component to a page in the design studio.":::

### Search bar

The search bar enables users to enter their queries.

| Show search result inline | Determines whether the results summary is displayed on the same page or redirects to a dedicated search results page. |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------|
| Placeholder text          | Text shown inside the search bar before the user enters a prompt (for example, "What would you like to search?").             |

### Search summary

The search summary section displays an AI-generated summary of relevant content retrieved from the website.

| Heading text | The header displayed above the AI-generated search summary. |
|--------------|-------------------------------------------------------------|  

## Add a search result page

A default search results page is automatically provisioned when a site is created, but this page isn't visible in the Pages workspace. Therefore, it can't be customized directly. If you need to create a custom search results page, follow these steps:

1. Open [design studio](/power-pages/getting-started/use-design-studio).  
1. Select **+ Page** to open the page creation dialog.
1. Select **Other ways to add page**, available at the bottom of the page.
1. Enter the page name.
1. Select the **Search** standard page layout.
1. Select **Add**.

> [!NOTE]  
> A website can only have one search results page at a time. Adding a new search layout page replaces the existing one.

To restore or reassign the previous search result page:

1. Open the [management app](/power-pages/configure/portal-management-app).
1. Go to **Site Markers**.  
1. Open the **Search** site marker for the selected website.
1. Update the **Page** to be used as the search result page.  

### Search result

This section is only available when the Search component is used on the designated Search Results Page.

| Heading text | The heading displayed above the full list of matched search results. |
|--------------|---------------------------------------------------------------------|
