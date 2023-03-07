---
title: Website capacity consumption reports
description: Learn how to view, download, and review the Power Apps portals capacity consumption reports from the Power Platform admin center.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 03/07/2023
ms.subservice: portals
ms.author: sandhan
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
---
 
# Website capacity consumption reports

Power Pages is licensed by using **authenticated user capacity** and **anonymous user monthly capacity** capacity add-ons for external users. This capacity must be allocated to a Microsoft Power Platform environment by an administrator. More information: [Licensing FAQ](/power-platform/admin/powerapps-flow-licensing-faq?branch=main#power-pages)

Administrators can download **Power Pages authenticated** and **Power Pages anonymous** view reports (as well as legacy **Portal logins** and **Portal page views** reports) from the [Power Platform admin center](https://admin.powerplatform.com). These reports show the number of authenticated sign-ins ("logins") and anonymous user site accesses for Power Pages websites across all environments for a tenant.

## Download the reports

The individual reports contain data for a duration of 30 days preceding the date you select while downloading the reports.

**To download the reports**

1. Go to [Power Platform admin center](https://admin.powerplatform.com).

1. On the left pane, expand **Resources**.

1. Select **Capacity**.

1. In the **Add-ons** section, select **Download reports**.

    :::image type="content" source="media/website-consumption-reports/summary-add-ons.png" alt-text="Add-ons.":::

1. Select **New**.

1. Select the **Power Pages authenticated** or **Power Pages anonymous** report.

    :::image type="content" source="media/website-consumption-reports/new-report.png" alt-text="Request a report from the admin center.":::

1. Select **Submit**.

1. After the generated report becomes available, select the **Download** tab.

    :::image type="content" source="media/website-consumption-reports/download-report.png" alt-text="Download report.":::

1. Select **Save**, and then select **Open**.

## Analyze reports

The report contains capacity consumption of all available websites across all environments for the tenant, organized by date. You can filter on different columns in the report&mdash;such as website ID, environment ID, or date range&mdash;for more analysis.

The following table describes the columns in the downloaded report.

> [!NOTE]
> The format is the same for both the **Power Pages authenticated** and **Power Pages anonymous** reports.

| Column name | Description |
| - | - |
| Environment ID | The ID of the Microsoft Power Platform environment. To check the ID of an environment: <ul><li> Go to the [Power Platform admin center](https://aka.ms/ppac). </li><li>In the **Environments** tab, select the environment.</li><li>In the **Details** section, you can see the **Environment ID**</li></ul> |
| Environment Name | The name of the Power Platform environment |
| Resource Type | |
| Resource ID | |
| Meter Category | |
| Meter Subcategory | |
| Usage Datetime | The date range for the report data available in the row. |
| Billed Quantity | The total number of authenticate sign-ins or anonymous site accesses, depending on the report you downloaded. You can compare the consumption number in the report for each environment by date with the configured maximum allowed capacity numbers using [Power Platform admin center - Manage add-ons](https://admin.powerplatform.microsoft.com/resources/capacity#add-ons). More information: [Microsoft Power Platform add-on capacity management](/power-platform/admin/capacity-add-on) |
| Unit of Measure | |
| Website License Type | The type of the license: |

### See also

[Microsoft Power Platform add-on capacity management](/power-platform/admin/capacity-add-on)  
[Licensing FAQ for Power Pages](/power-platform/admin/powerapps-flow-licensing-faq#power-pages)  
[Download the Power Platform Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130)


