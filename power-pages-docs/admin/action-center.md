---
title: Use Power Pages Action Center
description: Learn how to use the Power Pages action center to streamlines oversight and enhances responsiveness across your Power Pages experience.
ms.topic: conceptual
ms.custom: 
ms.date: 05/07/2025
ms.subservice:
author: PramithaU
ms.author: pudupa
ms.reviewer: smurkute
contributors:
    - PramithaU
    - shwetamurkute

---

# Use Power Pages Action Center

The Action Center in Power Pages home provides a centralized and environment-level view to help admins and makers manage critical insights, security recommendations, and key administrative actions. It improves oversight and responsiveness by surfacing actionable insights directly within Power Pages home.

## Access Power Pages Action Center

- Select your environment from [Power Pages home](https://make.powerpages.microsoft.com/).
- Select **Action Center** from the menu options to view Action Center dashboard.


## Review recommendations

The Action Center provides a centralized list of insights and recommended actions, enabling admins to manage their Power Pages environments efficiently. Key recommendations include: 

### Power Pages - Review & assign capacity to avoid degraded performance

This recommendation identifies environments where capacity consumption is nearing or exceeding the assigned limits. To prevent performance degradation, review the affected environments and allocate more capacity as needed. Select an environment to [manage and adjust capacity assignments](/power-pages/admin/capacity-management) accordingly.

### Websites are expiring in the next seven days

This recommendation lists trial websites that are expiring in the next seven days. Review and [convert the websites to production](/power-pages/admin/convert-site) as needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites didn't receive any traffic in the last 30 days

This recommendation lists websites that received no traffic in the last 30 days. This means some websites
in your tenant had no visitors in the past month. These websites might be outdated, irrelevant, or redundant.

To review these websites, select the recommendation to see a list of the websites, their URLs, environment names, and environment types. You can also visit the Power Pages admin center to get more insights into the traffic.

1. Select **Resources** > **Power Pages sites** > **Analytics**.

If a website isn't currently needed, you can shut it down. When a website is shut down, it's unavailable to users. You can always restart the websites later if you need them.

#### Supported actions for websites without traffic in the last 30 days

##### Shut down

To shut down a site:

1. Select one or more sites from the list and select **Shut down**.
1. After you confirm the shutdown operation, the selected sites are shut down.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites don't have Content Delivery Network (CDN) enabled

This recommendation lists production websites that don't have Content Delivery Network (CDN) enabled. Review the websites and [enable Content Delivery Network](/power-pages/configure/configure-cdn) where needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites don't have Web Application Firewall (WAF) enabled

This recommendation lists production websites that have Web Application Firewall (WAF) disabled. Review the websites and [enable Web Application Firewall](/power-pages/security/configure-web-application-firewall) where needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

#### Supported actions for websites without Web Application Firewall (WAF)

##### Enable

To enable WAF:

1. Select one or more sites from the list and select **Enable WAF**.
1. Confirm the operation to enable WAF for the selected sites.

### Websites have SSL certificates that have expired or are about to expire within 90 days

This recommendation lists production websites with SSL certificates that are expired or will expire within 90 days. Review the websites and [renew the SSL certificates](/power-pages/admin/add-custom-domain) as needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites are still on Bootstrap version 3

This recommendation lists production websites that aren't migrated to Bootstrap version 5. Review the websites and [migrate them to Bootstrap version 5 using the Power Pages bootstrap migration tool](/power-pages/configure/migrate-bootstrap) as needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites are still on standard data model

This recommendation lists production websites that aren't migrated to the enhanced data model. Review the websites and [migrate them to the enhanced data model using the Power Pages site migration tool](/power-pages/admin/migrate-enhanced-data-model?branch=main&branchFallbackFrom=pr-en-us-648) where possible.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

## Take actions 

Where applicable, makers act on these recommendations directly via the Power Platform Admin Center or Studio. If elevated privileges are required, they can contact tenant admins to take the necessary actions. 

## Share recommendations

All recommendations in Action center can be shared in Microsoft Teams with other users for team collaboration.

An admin can share the entire recommendation or share specific rows within the recommendation with another user by entering their name in the **Share to** textbox located in the **Share this recommendation** pane.

When an entire recommendation or multiple rows in the recommendation are shared, the sharing card provides a link to that recommendation for the admin.

> [!NOTE]
>
> - Shared recommendations are sent as an adaptive card in a personal Teams chat.
> - When recommendations are shared, the sharing card provides a link to that recommendation for the admin.
> - When an app or resource is shared, the sharing card provides a link to both the recommendation and the app in the maker portal.

## Inline actions 

You can take action for each recommendation in the recommendation pane. An admin can take action on a specific resource or perform a bulk action by selecting up to 10 resources from the recommendation list. 
 

The Action Center is available to users with environment-level permissions in Power Pages. These users typically include: 

- Makers with access to manage and build sites in a specific environment. 

- System Admins or Environment Admins who manage security, compliance, and operations across environments.

Access to certain actions and insights can vary based on role and privileges. While makers can view and act on many recommendations, some actions might require coordination with tenant-level admins. 

