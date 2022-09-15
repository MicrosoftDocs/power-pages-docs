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

Web Application Firewall (WAF) provides centralized protection Power Pages sites, defending against common exploits and vulnerabilities by preventing malicious attacks before they enter the network.  Power Pages sites receive global protection at a scale without sacrificing performance.

## WAF Policy

Web Application Firewall is powered by Azure Front Door (AFD), and the policy is configured using an AFD profile with **Prevention** mode enabled. 

>[!NOTE]
> In **Prevention** mode, requests matching the rules defined in the managed rule set are blocked.

## WAF manged rule sets for Power Pages

Power Pages' WAF managed rule sets are a subset of Azure-managed rule sets and are updated as needed to protect against new attack signatures.

The Azure-managed Default Rule Set includes rules to protect against the following threat categories:

- Cross-site scripting

- Local file inclusion

- Remote file inclusion

- Session fixation

- Protocol attackers

- Protocol enforcement

