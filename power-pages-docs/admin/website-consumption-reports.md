---
title: Website capacity consumption reports
description: Learn how to view, download, and review the Power Pages capacity consumption reports from the Power Platform admin center.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 3/22/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---
 
# Website capacity consumption reports

Power Pages is licensed by using **authenticated user monthly capacity** and **anonymous user monthly capacity** add-ons for external users. This capacity must be allocated to a Microsoft Power Platform environment by an administrator. More information: [Licensing FAQ](/power-platform/admin/powerapps-flow-licensing-faq?branch=main#power-pages)

Administrators can download **Power Pages authenticated** and **Power Pages anonymous** view reports (as well as legacy **Portal logins** and **Portal page views** reports) from the [Power Platform admin center](https://admin.powerplatform.com). These reports show the number of authenticated sign-ins and anonymous user site accesses for Power Pages websites across all environments for a tenant. 

> [!NOTE]
> Administrators should use the Power Pages capacity management experience in the Power Platform admin center to monitor capacity consumption for authenticated and anonymous users. More information: [Manage and monitor capacity (preview)](capacity-management.md)

## Download the reports

The individual reports contain data for a duration of 30 days preceding the date you select while downloading the reports.

**To download the reports**

1. Go to [Power Platform admin center](https://admin.powerplatform.com).

1. On the left pane, expand **Resources**.

1. Select **Capacity**.

1. In the **Add-ons** section, select **Download reports**.

    :::image type="content" source="media/website-consumption-reports/summary-add-ons.png" alt-text="Add-ons.":::

1. Select **New**.

1. Select the **Power Pages authenticated** or **Power Pages anonymous** report. You can also select **Portals logins** or **Portal page views** if still using legacy licensing.

    :::image type="content" source="media/website-consumption-reports/new-report.png" alt-text="Request a report from the admin center.":::

1. Select **Submit**.

1. After the generated report becomes available, select the **Download** tab.

    :::image type="content" source="media/website-consumption-reports/download-report.png" alt-text="Download report.":::

1. Select **Save**, and then select **Open**.

## Analyze reports

You can view reports based on the licensing type applied to the website.

# [Authenticated and anonymous users capacity](#tab/PPS)

The report contains capacity consumption of all available websites across all environments for the tenant, organized by date. You can filter on different columns in the report&mdash;such as website ID, environment ID, or date range&mdash;for more analysis.

The following table describes the columns in the downloaded report.

> [!NOTE]
> The format is the same for both the **Power Pages authenticated** and **Power Pages anonymous** reports.

| Column name | Description |
| - | - |
| Environment ID | The ID of the Microsoft Power Platform environment. To check the ID of an environment: <ul><li> Go to the [Power Platform admin center](https://aka.ms/ppac). </li><li>In the **Environments** tab, select the environment.</li><li>In the **Details** section, you can see the **Environment ID**</li></ul> |
| Environment Name | The name of the Power Platform environment. |
| Resource Type | The resource type, will be *Power Pages Website*. |
| Resource ID | The ID of the Power Pages website. |
| Meter Category | The meter category, will be *Power Pages*. |
| Meter Subcategory | Will indicate the type of meter being measure, will be *authenticated mau* or *anonymous mau*. MAU is an acronym for *Monthly Active Users*. |
| Usage Datetime | The date where unique users are measured. |
| Billed Quantity | The total number of authenticated or anonymous site accesses during the **Usage Datetime** value that access the site for the *first time* in the given month. </br></br>For example, when a user accesses the website for the first time during the month, they will not be counted again during that month. </br></br>To view the total monthly capacity consumed, sum all the **Billed Quantity** values for the given month. You can compare the consumption number in the report for each environment by date with the configured maximum allowed capacity by using [Power Platform admin center - Manage add-ons](https://admin.powerplatform.microsoft.com/resources/capacity#add-ons). More information: [Microsoft Power Platform add-on capacity management](/power-platform/admin/capacity-add-on). |
| Unit of Measure | What the **Billed Quantity** value represents, will be *Unique users per website*. |
| Website License Type | The type of the license, will be *capacity* or *add-on*. |

# [Portal logins and page views](#tab/PLV)

The report contains capacity consumption of all available websites across all environments for the tenant, organized by date. You can filter on different columns in the report&mdash;such as website ID, environment ID, or date range&mdash;for more analysis.

The following table describes the columns in the downloaded report.

> [!NOTE]
> The format is the same for both the **Portal Logins** and **Portal Views** reports.

| Column name | Description |
| - | - |
| **Date** | The date for the report data available in the row. |
| **PortalId** | The ID of the portal. To check the ID, [open the _services/about page](/power-apps/maker/portals/admin/clear-server-side-cache) for that portal. |
| **EnvironmentId** | The ID of the Microsoft Power Platform environment. To check the ID of an environment: <ul><li> Go to [Power Apps](https://make.powerapps.com). </li><li> Select the environment from the environments list in the upper-right corner. </li> <li> Copy the environment ID from the browser's address bar. <br> For example, `https://make.powerapps.com/environments/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home` is the ID of the environment. </li> </ul> |
| **Consumption** | The total number of sign-ins or views, depending on the report you downloaded. You can compare the consumption number in the report for each environment by date with the configured maximum allowed numbers for sign-ins or views by using [Power Platform admin center - Manage add-ons](https://admin.powerplatform.microsoft.com/resources/capacity#add-ons). More information: [Microsoft Power Platform add-on capacity management](/power-platform/admin/capacity-add-on) |
| **LicenseType** | The type of the license: <ul> <li> **Capacity** - specifies that the portal uses the [capacity-based licensing model](/power-platform/admin/powerapps-flow-licensing-faq#portals). </li> <li> **AddOn** - specifies that the portal uses, and was [provisioned using the older portal add-on plan](/power-apps/maker/portals/provision-portal-add-on). </li> </ul> More information: [Licensing FAQ for Power Apps](/power-platform/admin/powerapps-flow-licensing-faq#portals) and [Download the Power Platform Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130)

---

### See also

[Microsoft Power Platform add-on capacity management](/power-platform/admin/capacity-add-on)  
[Licensing FAQ for Power Pages](/power-platform/admin/powerapps-flow-licensing-faq#power-pages)  
[Download the Power Platform Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130)


