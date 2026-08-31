---
title: Configure Web Application Firewall for Power Pages 
description: Learn how to configure Web Application Firewall on Power Pages.
author: DanaMartens
ms.topic: how-to
ms.date: 02/19/2026
ms.author: bipuldeora
ms.reviewer: smurkute
contributors:
    - dileepsinghmicrosoft
    - nageshbhat-msft 
ms.custom:
  - sfi-image-nochange
---

# Configure Web Application Firewall for Power Pages 

Web Application Firewall (WAF) is available for production sites created using Power Pages. In this article, you'll learn about how to enable or disable Web Application Firewall for Power Pages sites.

## Prerequisites

You'll need the following before configuring WAF for your Power Pages website.

- You must be an administrator to configure Web Application Firewall.
- The website must be in the Production application type. Trial sites aren't supported.

> [!NOTE]
> - This service isn't available in Singapore Local, China and the UAE region.
> - The **Web Application Firewall** option is enabled by default when you convert a trial site to production. Administrator can choose to opt out before starting the conversion process.
  
## Enable Web Application Firewall for Power Pages sites

1. Go to the [Power Platform Admin Center](../admin/admin-overview.md).

1. Under **Performance & protection** card, turn on **Enable Web Application Firewall**

    :::image type="content" source="media/configure-web-application-firewall/waf-enabled.gif" alt-text="The Performance and Protection card inside design studio with the Enable Web Application Firewall toggle enabled.":::

> [!NOTE]
> To enable Web Application Firewall (WAF) for Power Pages sites using the REST API, see [Websites - Enable WAF](/rest/api/power-platform/powerpages/websites/enable-waf).

## Disable Web Application Firewall for Power Pages sites

1. Go to the [Power Platform Admin Center](../admin/admin-overview.md).

1. On the **Performance & Protection** card, turn off **Enable Web Application Firewall**

    :::image type="content" source="media/configure-web-application-firewall/waf-disabled.gif" alt-text="The Enable Web Application Firewall toggle disabled inside design studio.":::

> [!NOTE]
> To disable Web Application Firewall (WAF) for Power Pages sites using the REST API, see [Websites - Disable Waf](/rest/api/power-platform/powerpages/websites/disable-waf).

### Next steps

[Configure managed rules in Web Application Firewall for Power Pages](configure-managed-rules.md)

### See also

[Web Application Firewall (WAF) for Power Pages](web-application-firewall.md)
