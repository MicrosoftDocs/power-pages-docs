---
title: Monitor website traffic from the Power Platform admin center (preview)
description: Learn how to use the Power Platform admin center to monitor the traffic to the websites in your tenant.
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

Learn how to use the Power Platform admin center to monitor the traffic to the websites in your tenant. 

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This feature is gradually being rolled out across regions and might not be available yet in your region.

### Access the analytics dashboard

To access the analytics dashboard, you should have one of the following roles:

- Dynamics 365 administrator
- Power Platform administrator
- System administrator (You can only see environments for which you're a system administrator.)

## View traffic analytics for all websites in a tenant

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left pane, select **Resources**, > **Power Pages sites** > **Analytics**.
    :::image type="content" source="Media/admin-center-analytics/usage-data.png" alt-text="A screenshot of Power Pages sites inside Power Platform admin center displaying Usage data.":::

From here you can view the traffic that your websites are receiving: DAU (Daily Active Users), WAU (Weekly Active Users), and MAU (Monthly Active Users).

Each chart displays the DAU, WAU, and MAU for all the sites in the selected environment. Select your environment in the upper-right corner of the page.

:::image type="content" source="media/admin-center-analytics/analytics-environment-dropdown.png" alt-text="A screenshot of the Power Platform admin center showing the Analytics Usage Data's Environment dropdown.":::

To view the traffic for a specific site, select it in the **Site ID** list. To view the traffic for multiple sites, select **Ctrl** while you select the sites in the list.

:::image type="content" source="Media/admin-center-analytics/analytics-site-id.png" alt-text="A screenshot of the Power Platform admin center showing the Analytics Usage Data's Site ID dropdown.":::

>[!NOTE]
> Currently, only Site ID is supported for filtering. The Site ID can be found under the **Your Sites** tab.
> Traffic reports are available only for public sites. Private sites are not included in these reports. More information: [Difference between a private site and a public site](../security/site-visibility.md#difference-between-a-private-site-and-a-public-site)

### Considerations

- The charts show DAU, WAU, and MAU numbers for the following categories of users:
    - **Authenticated Users** shows the unique authenticated users who accessed the websites.
    - **Anonymous Users** shows the unique anonymous users who accessed the websites.
    - **All Users** shows the unique users who accessed the websites (either by authentication or anonymously).
- All the traffic numbers (DAU, WAU, and MAU) shown are with the intent of understanding the visits to the websites. 
- The authenticated user counts may vary slightly from license consumption reports. For instance, in cases where the authenticated user already has a Power Apps license, the visit isn't counted in license consumption. However, it is counted in the total authenticated users visiting the website.
- The usage numbers can be under-reported for the first few days after enabling the feature. For instance, the monthly active users will be accurate after the feature has been live for 30 days and the WAU will be accurate after the feature has been live for 7 days. 

### See also

- [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation)
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)  
- [Upgrade a website](upgrade-site.md)

