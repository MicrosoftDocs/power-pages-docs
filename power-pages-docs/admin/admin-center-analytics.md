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

Use the Power Platform admin center to monitor the traffic to the websites in your tenant. You can also see key information such as how many sites have Web Application Firewall disabled, how many sites have external authentication enabled, etc.

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

To access the security dashboard, you should have one of the following roles:

- Global Administrator
- Dynamics 365 administrator
- Power Platform administrator
- System administrator

>[!NOTE]
> System administrators can see only the environments for which they are a System Administrator.

## View traffic analytics for all websites in a tenant

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left pane, select **Resources**, then select **Power Pages sites**.
1. Go to **Analytics**.

Here you will find the traffic that your websites are receiving: DAU (Daily Active Users), WAU (Weekly Active Users) and MAU (Monthly Active Users)

All charts show the DAU, WAU and MAU across all the sites in the selected environment. You can select the environment of your interest using the drop down.

Within the selected environment, you can also select a specific site for which you want to see the traffic. Select the Site ID from the drop down (You can select multiple sites by using ctrl + click) to see traffic for that site.

>[!NOTE]
> Currently only Site ID is supported for filtering. The Site ID can be found under the 'Your Sites' tab.

### Authenticated and Anonymous User Analytics

The charts show DAU, WAU and MAU numbers for the following categories of users:

- Authenticated Users shows the unique authenticated users who accessed the websites.
- Anonymous Users shows the unique anonymous users who accessed the websites.
- All Users shows the unique users who accessed the websites (either by authentication or anonymously)

>[!IMPORTANT]
> 
> - All the traffic numbers (DAU, WAU and MAU) shown are with the intent of understanding the visits to the websites. 
> - The authenticated user counts may vary slightly from license consumption reports. For instance, in cases where the authenticated user already has a Power Apps license, the visit will not be counted in license consumption, but will be counted in the total authenticated users visiting the website.
> - The usage numbers can be under reported for the first few days after enabling the feature. For instance, the monthly active users will be accurate after 30 days of this feature being live, and weekly active users will be accurate after 7 days of this feature being live.


