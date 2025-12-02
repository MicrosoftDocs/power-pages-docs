---
title: Use Power Pages action center
description: Learn how to use the Power Pages action center to streamlines oversight and enhances responsiveness across your Power Pages experience.
ms.topic: concept-article
ms.custom: 
ms.date: 05/27/2025
ms.subservice:
author: PramithaU
ms.author: pudupa
ms.reviewer: smurkute
contributors:
    - PramithaU
    - shwetamurkute

---

# Use Power Pages action center

The action center in Power Pages home provides a centralized and environment-level view to help admins and makers manage critical insights, security recommendations, and key administrative actions. It improves oversight and responsiveness by surfacing actionable insights directly within Power Pages home.

 :::image type="content" source="media/action-center/action_center_home.png" alt-text="Screenshot that shows action center home page" lightbox="media/action-center/action_center_home.png":::

## Access Power Pages action center

To view the action center, follow these steps:

1. Select your environment from [Power Pages home](https://make.powerpages.microsoft.com/).
1. Select **Action Center** from the menu options to the view action center dashboard.


## Review recommendations

The action center shows a centralized list of insights and recommended actions, so admins can manage Power Pages environments efficiently. Key recommendations include:

### Websites are expiring in the next seven days

This recommendation lists trial websites that expire in the next seven days. Review and [convert the websites to production](/power-pages/admin/convert-site) as needed.

> [!NOTE]
> After you take an action, it can take up to one day for the sites to be removed from the list.

### Websites didn't receive any traffic in the last 30 days

This recommendation lists websites that didn't get any traffic in the last 30 days. This means some websites in your environment didn't have visitors in the past month. These websites might be outdated, irrelevant, or redundant.

To review these websites:

1. Select the recommendation to see a list of the websites, their URLs, environment names, and environment types. You can also go to the Power Pages admin center for more traffic insights.
1. Select **Resources** > **Power Pages sites** > **Analytics**.

If a website isn't currently needed, you can shut it down. When a website is shut down, it's unavailable to users. You can always restart the websites later if you need them.

### Websites don't have Content Delivery Network (CDN) enabled

This recommendation lists production websites that don't have Content Delivery Network (CDN) enabled. Review the websites and [enable Content Delivery Network](/power-pages/configure/configure-cdn) where needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites don't have Web Application Firewall (WAF) enabled

This recommendation lists production websites that have Web Application Firewall (WAF) disabled. Review the websites and [enable Web Application Firewall](/power-pages/security/configure-web-application-firewall) where needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites have SSL certificates that have expired or are about to expire within 90 days

This recommendation lists production websites with SSL certificates that are expired or expire within 90 days. Review the websites and [renew the SSL certificates](/power-pages/admin/add-custom-domain) as needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites are still on Bootstrap version 3

This recommendation lists production websites that aren't using Bootstrap version 5. Review the websites and [migrate them to Bootstrap version 5 using the Power Pages bootstrap migration tool](/power-pages/configure/migrate-bootstrap) as needed.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

### Websites are still on standard data model

This recommendation lists production websites that aren't using the enhanced data model. Review the websites and [migrate them to the enhanced data model using the Power Pages site migration tool](/power-pages/admin/migrate-enhanced-data-model?branch=main&branchFallbackFrom=pr-en-us-648) where possible.

> [!NOTE]
> Once an action is taken, it takes up to one day for the sites to be removed from the list.

## Take actions 

When possible, makers act on these recommendations directly in the Power Platform admin center or studio. If they need elevated privileges, they contact tenant admins to take the necessary actions.

## Share recommendations

You can share all recommendations in action center in Microsoft Teams with other users for team collaboration.

A maker can share the entire recommendation or specific rows within the recommendation with another user by entering their name in the **Share to** textbox in the **Share this recommendation** pane.

When you share an entire recommendation or multiple rows, the sharing card provides a link to that recommendation for the maker.

> [!NOTE]
>
> - Shared recommendations are sent as an adaptive card in a personal Teams chat.
> - When you share recommendations, the sharing card provides a link to that recommendation for the admin.
> - When you share an app or resource, the sharing card provides a link to both the recommendation and the app in the maker portal.

## Access 

The action center is available to users with environment-level permissions in Power Pages. These users typically include:

- Makers who manage and build sites in a specific environment.

- System admins or environment admins who manage security, compliance, and operations across environments.

Access to certain actions and insights varies based on role and privileges. While makers can view and act on many recommendations, some actions can require coordination with tenant-level admins. 

