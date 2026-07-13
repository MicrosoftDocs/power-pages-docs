---
title: Configure managed rules in Power Pages WAF
description: Learn how to configure managed rules and bot protection in Power Pages Web Application Firewall (WAF) to secure your site from threats and automated bots.
author: shwetamurkute
contributors:
ms.topic: concept-article
ms.date: 07/13/2026
ms.author: nabha
ms.reviewer: smurkute
---

# Configure managed rules in Web Application Firewall

When you enable the [Web Application Firewall (WAF)](web-application-firewall.md) for your Power Pages site, a subset of Azure managed rules relevant to Power Pages is turned on by default. For more information on rules and rule groups, see [Web Application Firewall DRS rule groups and rules](/azure/web-application-firewall/afds/waf-front-door-drs?tabs=bot#bot).

## Prerequisites 

- You must be an admin to configure custom rules.
- [Web Application Firewall](web-application-firewall.md) must be enabled for the site.
- You can't configure Web Application Firewall managed rules in China and the UAE region.

## Enable or disable managed rules in WAF for Power Pages sites

If your site has advanced customizations, certain rules can inadvertently block valid requests. Review the [WAF logs](/power-pages/security/web-application-firewall-logs) and  disable the required rules.

To enable or disable managed rules:

1. Go to the [Security workspace](/power-pages/getting-started/use-security-workspace).

1. Select **Web Application Firewall**.

1. On the right, select the **Managed rules** tab.

1. To disable a rule, select it and then select **Disable**.

1. To enable a specific managed rule that's currently disabled, select **Add new rule**, choose **Managed**, and select the rule you want to enable.

1. Select **Save**.

## Configure bot protection rules

Bot protection rules help block requests that come from automated bots. Bots typically fall into these categories:

- Good bots, like search engine crawlers.
- Bad bots, like malicious scrapers and spam bots.
- Unknown bots, which don't identify themselves clearly.

When you turn on bot protection rules, the system blocks requests that match these rules based on your configuration.

To configure bot protection rules:

1. Go to the [Security workspace](/power-pages/getting-started/use-security-workspace).

1. Select **Web Application Firewall**.

1. On the right, select the **Managed rules** tab.

1. Select **Add new rule**, and then select **Bot protection rules** (Good bots, Bad
   bots, or Unknown bots).

1. Select **Save**.

## Upgrade managed and bot protection rules

When newer versions of the Microsoft Default Rule Set (DRS) or Microsoft Bot Manager Rule Set are available, Power Pages displays an upgrade notification. Upgrading helps ensure your site benefits from the latest security protections, threat intelligence updates, and rule improvements available in Web Application Firewall (WAF).

### What gets upgraded?

Depending on the available update, upgrading can update one or more of the following managed rule sets:
- Microsoft Default Rule Set (DRS)
- Microsoft Bot Manager Rule Set
  
The upgrade updates the latest managed rule definitions used by your site's WAF while preserving your existing custom firewall rules and configuration settings.

> [!NOTE]
> Upgrading managed rule sets is a one-way operation. After the latest rule set versions are applied, you can't roll back to a previous version.

### See also

[Websites - Create Waf Rules using REST API](/rest/api/power-platform/powerpages/websites/create-waf-rules)
