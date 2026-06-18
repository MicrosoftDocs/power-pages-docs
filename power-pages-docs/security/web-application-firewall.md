---
title: Web Application Firewall overview 
description: Learn about Web Application Firewall for Power Pages.
author: nageshbhat-msft
ms.author: nabha
ms.topic: concept-article
ms.custom: nabha
ms.date: 06/18/2026
ms.reviewer: smurkute
contributors:
    - nageshbhat-msft
---

# Web Application Firewall (WAF) for Power Pages 

Web Application Firewall (WAF) provides centralized protection for Power Pages sites, defending against common exploits and vulnerabilities by preventing malicious attacks before they enter the network. By utilizing WAF, Power Pages sites receive global protection at a scale without sacrificing performance.

:::image type="content" source="media/web-application-firewall/waf-overview.png" alt-text="Diagram of the Web Application Firewall applied to Power Pages.":::

> [!IMPORTANT]
> The Power Pages platform-level IP Restrictions feature (under **Site Details** > **Security**) isn't supported when WAF is enabled. To filter traffic by IP while WAF is active, use WAF custom rules instead. Learn more in [Configure WAF custom rules](web-application-firewall-custom-rule-sets.md).

## How Web Application Firewall works

WAF for Power Pages is powered by [Azure Front Door](/azure/frontdoor/standard-premium/overview), Microsoft's global edge network. When you enable WAF, your site traffic is routed through Azure Front Door where it's inspected for malicious patterns before reaching your site.

### Custom domain requirements

If your site uses a custom domain (for example, `www.contoso.com`), enabling WAF requires a one-time domain ownership validation:

- When you enable WAF, Power Pages provisions an Azure Front Door profile for your site and routes your traffic through it. Front Door inspects each request against the WAF rule set before forwarding it to your site.
- This proves you own the domain before routing traffic through WAF.
- Validation typically completes within minutes to 48 hours.

Learn more about TXT record instructions, in [Add a custom domain - Domain validation](../admin/add-custom-domain.md#add-the-txt-record-for-domain-validation).

> [!NOTE]
> This validation step applies only when you've added a custom domain. Sites accessed via their auto-generated Power Pages URL don't require validation.

## WAF and Content Delivery Network (CDN)

[!INCLUDE [waf-cdn-relationship](../includes/waf-cdn-relationship.md)]

Learn more about caching configuration, in [Configure Content Delivery Network](../configure/configure-cdn.md).

## WAF mode for Power Pages

Web Application Firewall is powered by Azure Front Door, and the policy is configured using an Azure Front Door profile with **Prevention** mode enabled. In **Prevention** mode, requests matching the rules defined in the managed rule set are blocked.

## WAF managed rule sets for Power Pages

[The WAF managed rule sets](configure-managed-rules.md) for Power Pages are a subset of Azure-managed rule sets and are updated as needed to protect against new attack signatures.

The rule sets protect against the following threat categories:

- Cross-site scripting

- Local file inclusion

- Remote file inclusion

- Session fixation

- Protocol attackers

- Protocol enforcement

## WAF custom rule sets for Power Pages

[WAF custom rules](web-application-firewall-custom-rule-sets.md) empower users to craft their own regulations tailored to specific scenarios. These rules can be customized to either allow or block requests or to implement rate limits across the following categories: 

- Geo location 
- IP address 
- Request URI 

### Next steps

[Configure Web Application Firewall for Power Pages](configure-web-application-firewall.md)

### See also

- [Configure managed rules in Web Application Firewall for Power Pages](configure-managed-rules.md)
- [Configure Web Application Firewall custom rules](web-application-firewall-custom-rule-sets.md)
- [Configure Content Delivery Network](../configure/configure-cdn.md)
- [Add a custom domain](../admin/add-custom-domain.md)
