---
title: Web Application Firewall on Power Pages
description: Learn about Web Application Firewall on Power Pages.
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

# Web Application Firewall (WAF)

Web Application Firewall (WAF) for Power Pages provides centralized protection of your website and defends against common exploits and vulnerabilities. By preventing malicious attacks close to the attack sources before they enter the network, your Power Pages sites receive global protection at a scale without sacrificing performance.

## Policy and Rules

Web Application Firewall for Power Pages is powered by Azure Front Door (AFD). The policy is configured using an AFD profile with **Prevention** mode. In **Prevention** mode, requests matching the rules defined in the managed rule set are blocked.

### Managed rule sets

Power Pages managed rule sets are the subset of Azure-managed rule sets, which provide an easy way to deploy protection against common security threats. Since these rule sets are managed by Azure and enabled by Power Pages, the rules are updated as needed to protect against new attack signatures.

The Azure-managed Default Rule Set includes rules to protect against the following threat categories:

- Cross-site scripting

- Local file inclusion

- Remote file inclusion

- Session fixation

- Protocol attackers

- Protocol enforcement

