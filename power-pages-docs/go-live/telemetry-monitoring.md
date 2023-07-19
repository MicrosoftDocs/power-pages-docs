---
title: Set up telemetry monitoring
description: Set up telemetry monitoring in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 07/19/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - gitanjalisingh33msft
---

# Set up telemetry monitoring

You can use a telemetry tracking code in your Power Pages site to monitor specific traffic analytics and trends.

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