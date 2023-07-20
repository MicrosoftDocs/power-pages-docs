---
title: Set up telemetry monitoring
description: Set up telemetry monitoring in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 07/20/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - gitanjalisingh33msft
---

# Set up telemetry monitoring

You can use a telemetry tracking code in your Power Pages site to monitor specific traffic analytics and trends.

There are two different experiences depending if your website is using the standard or [enhanced](../admin/enhanced-data-model.md) data model.

## Set up telemetry monitoring using standard data model

Open the Portal Management app and navigate to the Enable Traffic Analysis section. Enter the snippet from your analytics provider.

:::image type="content" source="media/portal-analytics.png" alt-text="Enabling traffic analysis using Portal Management app.":::

## Set up telemetry monitoring using standard or enhanced data model

To enable telemetry monitoring on your website:

1. Open the [Power Pages Management app](../configure/portal-management-app.md).
1. Navigate to the **Content Snippets** section.
1. Create a new **Content Snippet** called **Tracking Code** of **type** = **Text**.
1. Leave the **Content Snippet Language** value blank.
1. Place the telemetry tracking HTML/JS snippet of code from the telemetry provider into the **Value** box.

:::image type="content" source="media/traffic-analysis.png" alt-text="Enabling traffic analysis.":::

Traffic on the website should now be monitored by the telemetry provider.

## See also

- [Enable Azure Monitor Application Insights Real User Monitoring](/azure/azure-monitor/app/javascript-sdk)