---
title: Web Application Firewall overview
description: Learn about Web Application Firewall for Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 10/06/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Web Application Firewall (WAF) for Power Pages

[!INCLUDEcc-beta-prerelease-disclaimer]

Web Application Firewall (WAF) provides centralized protection for Power Pages sites, defending against common exploits and vulnerabilities by preventing malicious attacks before they enter the network.  By utilizing WAF, Power Pages sites receive global protection at a scale without sacrificing performance.

:::image type="content" source="media/web-application-firewall/waf-overview.png" alt-text="Diagram of the Web Application Firewall applied to Power Pages.":::

[!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## WAF mode for Power Pages

Web Application Firewall is powered by Azure Front Door (AFD), and the policy is configured using an AFD profile with **Prevention** mode enabled. In **Prevention** mode, requests matching the rules defined in the managed rule set are blocked.

## WAF managed rule sets for Power Pages

The WAF managed rule sets for Power Pages are a subset of Azure-managed rule sets and are updated as needed to protect against new attack signatures.

The rule sets protect against the following threat categories:

- Cross-site scripting

- Local file inclusion

- Remote file inclusion

- Session fixation

- Protocol attackers

- Protocol enforcement

