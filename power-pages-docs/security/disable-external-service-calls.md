---
title: Use governance controls to disable external service calls
description: Learn how to disable external service calls from Power Pages server logic to enhance security, prevent data exfiltration, and enforce network-boundary policies.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 03/19/2026
ms.topic: feature-guide
---

# Use governance controls to disable external service calls from server logic in Power Pages

As an admin, you can prevent Power Pages server logic from making outbound HTTP calls to external services. Blocking these calls helps protect your organization from data exfiltration and enforces network-boundary policies at the tenant level. When you enable this setting, any server logic script that attempts an outbound HTTP request returns an HTTP 403 – Forbidden response instead of executing the call.

## Admin experience

Control outbound HTTP calls from server logic on a site-by-site basis by using the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. In the left-side menu, select Resources > Power Pages Sites.

1. Select **Governance Controls** from the top ribbon menu.

1. Select **Disable external service calls from Server Logic** from the list.

1. In the slide-out panel, choose the **Environment** > **Set up**.

1. Select **On** and choose the following options:

   | Option | Description |
   |---|---|
   | All sites in this environment | Disable server logic to make outbound HTTP calls in all websites in the selected environment. |
   | All sites except specific site | Disable outbound calls everywhere except the sites you choose. Those selected sites have all outbound HTTP calls blocked. |
   | Specific sites | Blocks outbound calls only in the sites you select. All other sites continue normally. |

1. Save.

> [!IMPORTANT]
> - The default behavior allows server logic to make outbound HTTP calls. No action is required unless your organization wants to restrict this capability.
> - This governance control takes effect immediately after you save. Existing server logic scripts that make outbound HTTP calls begin returning HTTP 403 – Forbidden without any redeployment of the affected websites.
