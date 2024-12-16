---
title: Power Pages search with generative AI (preview)
description: Learn how to enhance search results with generative AI.
author: nageshbhat-msft
ms.topic: conceptual
ms.custom: 
ms.date: 12/16/2024
ms.subservice: 
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - nageshbhat-msft
    - DanaMartens
---

# Power Pages search with generative AI (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Using Generative AI for Power Pages Search is about incorporating generative artificial intelligence (AI) models into web search features. Generative AI can comprehend context, meaning, and user goals to summarize search results. This method uses natural language processing (NLP) and machine learning techniques to improve user experience by offering more precise and varied search results.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../../includes/cc-preview-features-definition.md)]
> - Generative AI search is available for sites created with English language.
> - This feature is not available in Government Community Cloud (GCC), Government Community Cloud - High (GCC High), or Department of Defense (DoD) regions.
> - Power Pages site version must be 9.6.3.41 or higher.
> - Faceted search isn't available when you enable generative AI search.

:::image type="content" source="../media/generative-ai/generative-ai.png" alt-text="Screenshot of an AI generated summary of search results in Power Pages search.":::

## Enable site search with generative AI

To include generative AI in Power Pages search:

1. Go to [Set up workspace](../setup-workspace.md).
1. Under **Copilot** select **Site search (preview)**.
1. Turn on **Enable Site search with generative AI (preview)**.

## Refine search source

When the search feature is activated on the website, it designates the entire website as a searchable domain. The Dataverse service orchestrates the indexing of the website's content and the configured tables. Then Azure OpenAI aggregates the indexed content for search summarization.

> [!NOTE]
> The same content is used by both generative AI search and keyword search.

To customize the source of search content:

1. Go to [Set up workspace](../setup-workspace.md), select **Site search**.
1. Under **Refine your data**, select **Make changes**.
1. Select **Choose tables** to select or deselect tables.
    - You can select multiple tables in this section.
    - Ensure that any table you select is used on the site.
    - On subsequent pages, you must specify the page where the table is used to create the citation URL.
1. Select **Next**.
1. Select **Choose table** and select the table that contains the columns and page link you want to select.
    - A table doesn't appear unless it has at least one multi-line column.
    - You can select one table at a time.
1. Under **Choose page to associate with the table**, select the page where the table is used.

    > [!NOTE]
    > - Make sure you select the correct page where the table is used. Choosing the wrong table will result in the bot providing an incorrect citation URL for the answers.
    > - The page must use 'id' as the query string parameter; the citation URL will not function correctly if any other parameter name is used.

1. Under **Choose columns**, select the list of columns that are used in the page.
    - Only columns with multiline text are available to select.
1. Select **Next** and review the selection.

    > [!IMPORTANT]
    > If you selected more than one table, you need to configure the page and column options for each table before you can select **Next**.

1. Select **Save** to submit the changes.

## Table row filter

When table is included for search scope, a new view is added to the table as defined in site setting `Search/IndexQueryName`.
The default value for `Search/IndexQueryName` is "Portal Search".

If you want to further refine the content of the search scope, use this filter to customize it.

## Apply style to search result page

The Power Pages search result page, which is powered by generative AI search follows the themes defined in the [Style workspace](../../getting-started/style-site.md). To make any appearances changes, use the style workspace.

The static content on the search result component is designed using [content snippets](../customize-content-snippets.md). If you want to update the Generative AI Summary title or Keyword result title, use the following content snippets:

- Generative AI Summary - `Search/Summary/Title`
- Keyword search - `Search/Results/Title`

## Search Summary API

If you aren't using the search control and are developing a custom page that provides the search summary, use the following API to get the details.

| Method | URI                                                    |
|--------|--------------------------------------------------------|
| POST   | \[Site URI\]\_api/search/v1.0/summary |

## Example: Request

```html
POST https://contoso.powerappsportals.com/_api/search/v1.0/summary
{
        data: { userQuery: "Fix problems with slow coffee dispense" }
}
```

### Example: Response

```html
HTTP/1.1 200 OK
Content-Type: application/json
Body
{
    "Summary":"To fix problems with slow coffee dispense, consider the following steps:\n\n1. **Check for Mineral Deposits**: One of the most common reasons for slow brewing is the buildup of mineral deposits inside the coffee maker. If you are using tap water, minerals like calcium can accumulate, leading to slow brew times and poor-tasting coffee.",
    "Citations’":{
                  "[1]": " https://contoso.powerappsportals.com /knowledgebase/article/KA-01055",
    }
}
```

### Sample JavaScript

This sample shows how to call a search summary API using asynchronous JavaScript and XML (AJAX).

```javascript
    shell.ajaxSafePost({
        type: "POST",
        url: "https://contoso.powerappsportals.com/_api/search/v1.0/summary",
        contentType: "application/x-www-form-urlencoded",
        data: { userQuery: "Fix problems with slow coffee dispense" }
    })
    .done(function (response) {
        // Handle success
    })
    .fail(function() {
        // Handle failure
    });
```

## See also

- [FAQ for site search with generative AI](../../faqs-generative-ai-search.md)
- [Enable site search with generative AI (video)](https://youtu.be/2SEGiPhyYiQ?feature=shared)
