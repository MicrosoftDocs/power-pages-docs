---
title: Add an agent available in Microsoft Copilot Studio
description: Learn how to add an agent available in Microsoft Copilot Studio.
ms.topic: how-to
ms.date: 08/04/2025
ms.update-cycle: 180-days
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
contributors:
  - nageshbhat-msft
  - DanaMartens
ms.custom: bap-template
ms.collection: 
    - bap-ai-copilot
---

# Add an agent available in Microsoft Copilot Studio

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

This article offers a comprehensive, step-by-step guide for updating default Power Pages agent with another agent available in Microsoft Copilot Studio.

## Prerequisites

- You need an agent created in [Microsoft Copilot Studio](/microsoft-copilot-studio/nlu-gpt-quickstart#create-a-boosted-bot).

- [Agent](enable-agent.md#add-an-agent) needs to be created and published in the site where you're updating another agent available in Microsoft Copilot Studio.

## Copy the agent schema name

1. Sign in to [Microsoft Copilot Studio](https://web.powerva.microsoft.com/).

1. Select the agent you want to use in Power Pages.

1. Go to **Agent details** under **Settings**.

1. Select the **Advanced** tab.

1. Copy the **Schema name** field.

## Verify data model version

Agent can be enabled for both standard and enhanced site data models. The steps to replace it vary based on the data model. Make sure you follow the correct steps for your data model.

1. Go to [Set up workspace](../configure/setup-workspace.md).

1. Select **Site details**.

1. Verify the **Data Model** version. Choose either **Standard** or **Enhanced**.

## Update the agent based on your data model version

To see the appropriate steps, select the tab that corresponds to your data model.

# [Standard data model](#tab/standard)

1. Go to the [Data workspace](use-data-workspace.md).
1. Search for and select the **Bot consumer** table.
1. Locate the row with the selected website name.
1. Replace the value in the Schema Name column with the new schema name you copied earlier.

# [Enhanced data model](#tab/enhanced)

1. Go to the [Data workspace](use-data-workspace.md).
1. Search for and select the **Site Component** table.
1. Find the **Component Type** column and select the filter icon next to it.
1. Filter the records by selecting the **Bot Consumer** option.
1. Locate the row with the selected website name in the **Power Pages Site id** column.
1. Choose **Edit row using form**.
1. In **Content**, update the **botschemaname** JSON value with the new schema name you copied earlier.

    :::image type="content" source="media/pva-bot-how-to/bot-enhanced-data-model.png" alt-text="Screenshot of the general options for Bot Consumer with the **botschemaname** JSON value emphasized.":::

1. Choose **Save & Close**.

---
