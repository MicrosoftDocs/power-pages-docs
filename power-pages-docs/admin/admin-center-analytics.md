---
title: Monitor website traffic from the Power Platform admin center
description: Learn how to use the Power Platform admin center to monitor the traffic to the websites in your tenant.
ms.topic: how-to
ms.custom: 
ms.date: 09/12/2025
ms.subservice:
author: PramithaU
ms.author: pudupa
ms.reviewer: danamartens
contributors:
    - vamseedillimsft
    - shwetamurkute
---

# Monitor traffic to your websites

Learn how to use the Power Platform admin center to monitor the traffic to the websites in your tenant. 

### Access the analytics dashboard

To access the analytics dashboard, you should have one of the following roles:

- Dynamics 365 administrator
- Power Platform administrator
- System administrator (You can only see environments for which you're a system administrator.)

## View traffic analytics for all websites in a tenant

The steps to access traffic analytics differ slightly depending on whether you're using the [new admin center](new-admin-overview.md) or the [classic admin center](admin-overview.md):

# [Classic admin center](#tab/classic)

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left pane, select **Resources**, > **Power Pages sites** > **Analytics**.

:::image type="content" source="Media/admin-center-analytics/usage-data.png" alt-text="A screenshot of Power Pages sites inside Power Platform admin center displaying usage data.":::

# [New admin center](#tab/new)

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the left navigation, select **Manage**.
1. Under **Products**, select **Power Pages** and then select **Analytics (preview)**.

:::image type="content" source="Media/admin-center-analytics/analytics-tab.png" alt-text="A screenshot of Power Pages sites inside the new Power Platform admin center displaying usage data.":::

---

From here you can view the traffic that your websites are receiving: DAU (Daily Active Users), WAU (Weekly Active Users), and MAU (Monthly Active Users).

Each chart displays the DAU, WAU, and MAU for all the sites in the selected environment. Select your environment in the upper-right corner of the page.

:::image type="content" source="media/admin-center-analytics/analytics-environment-dropdown.png" alt-text="A screenshot of the Power Platform admin center showing the Analytics Usage Data's Environment dropdown.":::

To view the traffic for a specific site, select it in the **Site ID** list. To view the traffic for multiple sites, select **Ctrl** while you select the sites in the list.

:::image type="content" source="Media/admin-center-analytics/analytics-site-id.png" alt-text="A screenshot of the Power Platform admin center showing the Analytics Usage Data's Site ID dropdown.":::

>[!NOTE]
> Currently, only Site ID is supported for filtering. The Site ID can be found under the **Your Sites** tab.
> Traffic reports are available only for public sites. Private sites aren't included in these reports. More information: [Difference between a private site and a public site](../security/site-visibility.md#difference-between-a-private-site-and-a-public-site)

### Considerations

- The charts show DAU, WAU, and MAU numbers for the following categories of users:
    - **Authenticated Users** shows the unique authenticated users who accessed the websites.
    - **Anonymous Users** shows the unique anonymous users who accessed the websites.
    - **All Users** shows the unique users who accessed the websites (either by authentication or anonymously).
- All the traffic numbers (DAU, WAU, and MAU) shown are with the intent of understanding the visits to the websites. 
- The authenticated user counts may vary slightly from license consumption reports. For instance, in cases where the authenticated user already has a Power Apps license, the visit isn't counted in license consumption. However, it's counted in the total authenticated users visiting the website.
- The usage numbers can be under-reported for the first few days after enabling the feature. For example, the monthly active users are accurate after the feature has been live for 30 days and the WAU is accurate after the feature has been live for 7 days.
- The dashboards for daily, weekly, and monthly active users (DAU, WAU, MAU) only show data for the last 30 days.

| Metric    | Definition              | How it’s Calculated / Displayed          | 
|-----------|-------------------------|------------------------------------------|
| **MAU (Monthly Active Users)**  | The number of distinct users active in the past 30 days (rolling window). | For each date on the x-axis, MAU shows the number of unique users who access the site in the preceding 30 days.   | 
| **WAU (Weekly Active Users)**   | The number of distinct users active in the past seven days (rolling window).  | For each date, WAU counts unique users who accessed the site in the preceding seven days.            | 
| **DAU (Daily Active Users)**    | The number of distinct users active on that date.   | For each date, DAU counts unique users on that single day.  | 
| **MoM (Month-over-Month Authenticated Users)** | The number of distinct authenticated users in a given calendar month. | This is an aggregated calendar month view (for example, July 1–31), not a rolling window.          |

### See also

- [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation)
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)  
- [Upgrade a website](upgrade-site.md)
