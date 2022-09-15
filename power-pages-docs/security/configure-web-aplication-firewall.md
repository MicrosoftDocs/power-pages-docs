---
title: Configure Web Application Firewall for Power Pages
description: Learn how to configure Web Application Firewall on Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 09/14/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Configure Web Application Firewall for Power Pages

Web Application Firewall (WAF) is available for production websites.

>[!IMPORTANT]
> - You must be an administrator to configure Web Application Firewall.
> - WAF requires Content Delivery Network (CDN) on websites. You must [configure CDN](/power-apps/maker/portals/configure/configure-cdn) before you enable WAF.

## Enable Web Application Firewall

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments).

1. Go to **Environments**.  

1. Select the environment where the portal was created.

1. On the **Resources** card, select **Portals**.

1. Choose the portal from the available list, and then select **Manage**.

1. Under **Performance & protection** card, turn on **Enable Web Application Firewall**

## Disable Web Application Firewall

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments).

1. Go to **Environments**.  

1. Choose the environment where the portal was created.

1. On the **Resources** card, select **Portals**.

1. Choose the portal from the available list, and then select **Manage**.

1. On the **Performance & Protection** card, turn off **Enable Web Application Firewall**
