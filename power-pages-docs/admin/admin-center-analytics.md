---
title: Monitor website traffic from the Power Platform admin center (preview)
description: Learn how to use the Power Platform admin center to monitor traffic to the websites in your tenant.
author: vamseedillimsft
ms.topic: conceptual
ms.custom: 
ms.date: 10/03/2023
ms.subservice: 
ms.author: vamseedilli
ms.reviewer: kkendrick
contributors:
    - vamseedillimsft
    - professorkendrick
---

# Monitor traffic to your websites (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Use the Power Platform admin center to monitor the traffic to the websites in your tenant.

> [!IMPORTANT]
>
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This feature is gradually being rolled out across regions and might not be available yet in your region.

### Access the analytics dashboard

To access the analytics dashboard, you should have one of the following roles:

- Global Administrator
- Dynamics 365 administrator
- Power Platform administrator
- System administrator (You can only see environments for which you're a system administrator.)

### View traffic analytics for all websites in a tenant

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left pane, select **Resources**, then select **Power Pages sites**.
1. Go to **Analytics**.
    :::image type="content" source="Media/admin-center-analytics/usage-data.png" alt-text="Screenshot of the Power Platform admin center. The Power Page site displaying Usage data.":::

From here you can view the traffic that your websites are receiving: Daily Active Users (DAU), Weekly Active Users (WAU), and Monthly Active Users (MAU).

Each chart displays the DAU, WAU, and MAU for all sites in the selected environment. Select your environment in the upper-right corner of the page.

:::image type="content" source="Media/admin-center-analytics/analytics-environment-dropdown.png" alt-text="Screenshot of the Power Platform admin center. The Environment dropdown on the Analytics Usage Data page.":::

To view the traffic for a specific site, select it in the **Site ID** list. To view the traffic for multiple sites, select **Ctrl** while you select the sites in the list.

:::image type="content" source="Media/admin-center-analytics/analytics-site-id.png" alt-text="Screenshot of the Power Platform admin center. The Site ID dropdown on the Analytics Usage Data page.":::

>[!NOTE]
> Currently, only Site ID is supported for filtering. The Site ID can be found under the **Your Sites** tab.
> Traffic reports are available only for public sites. Private sites are not included in these reports. More information: [Difference between a private site and a public site](../security/site-visibility.md#difference-between-a-private-site-and-a-public-site)

### Considerations

- The charts show DAU, WAU, and MAU numbers for the following categories of users:
  - **Authenticated Users** shows the unique authenticated users who accessed the websites.
  - **Anonymous Users** shows the unique anonymous users who accessed the websites.
  - **All Users** shows the unique users who accessed the websites (either by authentication or anonymously).
- The number of authenticated users may vary slightly from the license consumption reports. For instance, in cases where the authenticated user already has a Power Apps license, the visit isn't counted in license consumption but is counted in the total authenticated users visiting the website.
- The usage numbers may not be accurate for the first few days after enabling the feature. For instance, the MAU will be accurate after the feature has been live for 30 days and the WAU will be accurate after the feature has been live for 7 days.

### See also

- [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation)
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)  
- [Upgrade a website](upgrade-site.md)
