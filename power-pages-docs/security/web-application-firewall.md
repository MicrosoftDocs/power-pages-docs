---
title: Web Application Firewall for Power Pages
description: Learn about Web Application Firewall for Power Pages.
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

# Web Application Firewall (WAF) for Power Pages

Web Application Firewall (WAF) provides centralized protection for Power Pages sites, defending against common exploits and vulnerabilities by preventing malicious attacks before they enter the network.  Power Pages sites receive global protection at a scale without sacrificing performance.

## WAF mode

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

