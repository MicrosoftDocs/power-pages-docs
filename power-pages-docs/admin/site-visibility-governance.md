---
title: Configure non-production Power Pages site visibility
description: Control public access for non-production Power Pages sites with governance settings. Learn how to manage site visibility.
author: RitGan
ms.author: ritwikganni
ms.reviewer: smurkute
ms.date: 03/11/2026
ms.topic: how-to
---


# Control public access for non-production Power Pages sites

Tenant admins can control whether makers can make **non-production** Power Pages sites public, such as trial or developer sites. This governance control helps prevent accidental exposure of sites that are still in development.

This governance control doesn't change site visibility behavior for **production** sites.

## How the control affects makers

Depending on the policy you configure, makers might be able to switch a non-production site between **Private** and **Public**, or they might be blocked from making non-production sites public.

When makers are blocked, they see an **Access restricted** message in the **Site visibility** pane.

## Configure the governance control

1. Sign in [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Go to **Manage** > **Power Pages** > **Governance controls**.
1. From the dropdown list, select **Set site visibility to public access for non-production sites**.
1. Select the environment you want to manage.
1. Choose a policy value:
 - **None** – Makers can't make non-production sites public.
 - **All** – Makers can make any non-production site public or private.
 - **All sites except specific sites** – Makers can make non-production sites public except the sites you exclude.
 - **Specific sites** – Makers can make only the selected non-production sites public.
1. Save your changes.

> [!IMPORTANT]
> When this capability becomes available in your tenant, the default policy is **None** until you change it.

The changes take effect in the maker experience.