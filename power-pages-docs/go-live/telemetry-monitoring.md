---
title: Set up telemetry monitoring
description: Set up telemetry monitoring in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 07/20/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - gitanjalisingh33msft
---

# Set up telemetry monitoring

You can use a telemetry tracking code in your Power Pages site to monitor specific traffic analytics and trends.

There are two different experiences depending on whether your website uses the [standard or enhanced](../admin/enhanced-data-model.md#determine-whether-your-site-is-using-the-standard-or-enhanced-data-model) data model.

## Set up telemetry monitoring using standard data model

Open the Portal Management app and navigate to the **Enable Traffic Analysis** section. Enter the snippet from your analytics provider.

:::image type="content" source="media/portal-analytics.png" alt-text="Enabling traffic analysis using Portal Management app.":::

This process will automatically create a content snippet called **Tracking Code** containing the HTML/JS snippet.

## Set up telemetry monitoring using enhanced data model

The **Enable Traffic Analysis** section does not exist in the Power Pages management app.

To enable telemetry monitoring on your website using the enhanced data model:

1. Open the [Power Pages management app](../configure/portal-management-app.md).
1. Navigate to the **Content Snippets** section.
1. Create a new content snippet called **Tracking Code** of **Type** = **Text**.
1. Leave the **Content Snippet Language** value blank.
1. Place the telemetry tracking HTML/JS snippet of code from the telemetry provider into the **Value** box.

:::image type="content" source="media/traffic-analysis.png" alt-text="Enabling traffic analysis.":::

Traffic on the website should now be monitored by the telemetry provider.

## See also

- [Enable Azure Monitor Application Insights Real User Monitoring](/azure/azure-monitor/app/javascript-sdk)
- [Set up telemetry monitoring using enhanced data model](https://youtu.be/WtZS68RPo5E?feature=shared)
