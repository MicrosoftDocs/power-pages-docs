---
title: Add AI summary to list (preview)
description: Learn more about how the AI summary list feature works to simplify and summarize data in Microsoft Power Pages.
author: neerajnandwana-msft
ms.topic: how-to
ms.date: 03/13/2025
ms.author: nenandw
ms.reviewer: dmartens
ms.collection:
 - bap-ai-copilot
contributors:
    - dmartens
    - tapanm
---

# Add AI summary to list (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

The AI summary feature for list simplifies the consumption of data by transforming complex data tables into insightful, visual summaries and chart representations. The feature enhances user efficiency and makes it easier for users to analyze data. Data presented in traditional table formats can often be difficult to interpret, leading to challenges in extracting meaningful insights. The AI summary list provides easy-to-understand chart formats and concise data summaries.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

This guide walks you through enabling and configuring the AI-powered insights for data lists in Power Pages.

## Benefits

AI summary for list provides the following benefits:

- **Chart Visualizations:** The feature converts complex data lists into graphical charts, making trends and key data points more accessible and easier to understand.

- **Data Summarization:** Automatically generated summaries offer high-level insights into your data, reducing the time spent on manual analysis.

You can add AI summary on either a new or existing list.

## Enable AI summary on a new list

When creating a new data list, you can enable the **AI summary** feature to automatically generate insightful summaries and visual charts for the list.

To enable AI summary on a new list:

1. [Add a list](/power-pages/getting-started/add-list) to the page.

1. Select **AI summary for list** to enable or disable AI summary for the selected list. Default for this toggle is enabled.

   :::image type="content" source="media/add-ai-summary-list/list-settings.png" alt-text="Screenshot that shows the list settings from the **Set up** tab.":::

   1. Complete the configuration and select **Done**.

   Once AI summary list is turned on, the data lists automatically provide AI-driven summaries and visual representations of the data, allowing for a more intuitive and insightful user experience.

## Enable AI summary for an existing list

You can also enable the **AI summary** feature on an existing data list.

To enable AI summary on an existing list:

1. Select the existing list on the page.

1. Select **Edit List**.

1. In the settings panel, locate the **AI Summary for List** option.

1. Toggle the option to **On**.

1. Save your changes.

The data list now includes automatically generated summaries and chart visualizations.

## Customizing AI summaries

To customize an AI-generated summary:

1. Select the AI card within the list.
   
1. Navigate to **Insights** to access customization options.
   :::image type="content" source="media/add-ai-summary-list/list-ai-insights-settings.png" alt-text="Screenshot that shows the AI insights settings from the **Insights** tab.":::
   
1. Toggle the **Keep insights expanded** option ON or OFF to control whether the AI card remains expanded or collapsed by default when the page loads.
   
1. Modify the AI card **Title** to replace the default title with a custom one.
   
1. Provide **Additional Instructions** to refine the AI's insights or influence data visualization.
   
1. Define **Chart Type** preferences, to allow AI to select the most suitable visualization for displaying the data.

### Guidelines for additional instructions

When adding extra instructions, avoid the following:

- Grouping data within the instructions. Example, *show top 5 products by order quantity.*
- Applying filters, as this may lead to inaccurate summaries. Example, *show insights specific to the "Electronic" product category.*

## Limitations

- Virtual tables aren't supported.
- A table should have at least five rows to generate any meaningful summary.
- Limitations of the Tabular Data Stream (TDS) endpoint also apply to this feature. Learn more about unsupported column types at [Supported operations and data types](/power-apps/developer/data-platform/dataverse-sql-query#supported-operations-and-data-types).

### Related information

- [Responsible AI FAQ for AI summary list](../faqs-ai-summary-list.md)
- [Disable Generative AI features for users (preview)](../admin/copilot-governance.md)
