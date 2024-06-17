---
title: Web Application Firewall overview 
description: Learn about Web Application Firewall for Power Pages.
author: nageshbhat-msft
ms.topic: conceptual
ms.custom: nabha
ms.date: 05/16/2024
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
    - nageshbhat-msft
---

# Web Application Firewall (WAF) for Power Pages 

Web Application Firewall (WAF) provides centralized protection for Power Pages sites, defending against common exploits and vulnerabilities by preventing malicious attacks before they enter the network. By utilizing WAF, Power Pages sites receive global protection at a scale without sacrificing performance.

:::image type="content" source="media/web-application-firewall/waf-overview.png" alt-text="Diagram of the Web Application Firewall applied to Power Pages.":::

## WAF mode for Power Pages

Web Application Firewall is powered by Azure Front Door, and the policy is configured using an Azure Front Door profile with **Prevention** mode enabled. In **Prevention** mode, requests matching the rules defined in the managed rule set are blocked.

## WAF managed rule sets for Power Pages

[The WAF managed rule sets](web-application-firewall-rule-groups.md) for Power Pages are a subset of Azure-managed rule sets and are updated as needed to protect against new attack signatures.

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

- [Web Application Firewall DRS rule groups and rules for Power Pages](web-application-firewall-rule-groups.md)
- [Configure Web Application Firewall custom rules](web-application-firewall-custom-rule-sets.md)
