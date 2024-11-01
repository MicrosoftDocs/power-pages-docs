---
title: Web Application Firewall DRS rule groups and rules for Power Pages
description: Learn about Web Application Firewall DRS rule groups and rules for Power Pages.
author: nageshbhat
ms.topic: conceptual
ms.custom: 
ms.date: 10/10/2022
ms.author: nabha
ms.reviewer: danamartens
contributors:
    - nageshbhat-msft
---

# Web Application Firewall DRS rule groups and rules for Power Pages

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Web Application Firewall managed rule sets for Power Pages are a subset of Azure-managed [DRS 2.0 rule sets](/azure/web-application-firewall/afds/waf-front-door-drs?tabs=drs20#drs-20).

The following rule groups and rules are available using Web Application Firewall for Power Pages.

> [!NOTE]
> The rule groups below are subject to change.

| Rule set | Rule IDs available in Power Pages | Description |
| -- | -- | -- |
| General | 200002 | This rule group protects against improperly formed requests. <br> More information: [Rule group: General](/azure/web-application-firewall/afds/waf-front-door-drs#general-20)
| METHOD-ENFORCEMENT | 911100 | This rule group protects against unauthorized method calls using lock-down methods (PUT, PATCH). <br> More information: [Rule group: METHOD-ENFORCEMENT](/azure/web-application-firewall/afds/waf-front-door-drs#drs911-20)
| PROTOCOL-ENFORCEMENT | 920100, 920100, 920121, 920160, 920170, 920171, 920190, 920200, 920210, 920220, 920240, 920260 | This rule group protects against protocol and encoding issues. <br> More information: [Rule group: PROTOCOL-ENFORCEMENT](/azure/web-application-firewall/afds/waf-front-door-drs#drs920-20) | 
| PROTOCOL-ATTACK | 921110, 921120, 921130, 921140, 921150, 921151, 921160 | This rule group offers protection against header injection, request smuggling, and response splitting. <br> More information: [Rule group: PROTOCOL-ATTACK](/azure/web-application-firewall/afds/waf-front-door-drs#drs921-20) | 
| LFI - Local File Inclusion | 930110 | This rule group protects against file and path attacks. <br> More information: [Rule group: LFI - Local File Inclusion](/azure/web-application-firewall/afds/waf-front-door-drs#drs930-20) | 
| RFI - Remote File Inclusion | 931100, 931110, 931120 | This rule group protects against remote file inclusion (RFI) attacks. <br> More information: [Rule group: RFI - Remote File Inclusion](/azure/web-application-firewall/afds/waf-front-door-drs#drs931-20) | 
| XSS - Cross-site Scripting | 941101, 941110, 941140, 941170, 941180, 941190, 941200, 941210, 941220, 941230 | This rule group protects against cross-site scripting attacks. <br> More information: [Rule group: XSS - Cross-site Scripting](/azure/web-application-firewall/afds/waf-front-door-drs#drs941-20) | 
| SESSION-FIXATION | 943100, 943110, 943120 | This rule group protects against session-fixation attacks. <br> More information: [Rule group: SESSION-FIXATION](/azure/web-application-firewall/afds/waf-front-door-drs#drs943-20) | 
| MS-ThreatIntel-WebShells | 99005002, 99005003, 99005004 | This rule group protects against Web shell attacks. <br> More information: [Rule group: MS-ThreatIntel-WebShells](/azure/web-application-firewall/afds/waf-front-door-drs#drs9905-20) | 
| MS-ThreatIntel-AppSec | 99030001, 99030002 | This rule group protects against AppSec attacks. <br> More information: [Rule group: MS-ThreatIntel-AppSec](/azure/web-application-firewall/afds/waf-front-door-drs#drs9903-20) |

### See also

- [Web Application Firewall DRS rule groups and rules](/azure/web-application-firewall/afds/waf-front-door-drs)
- [Web Application Firewall (WAF) for Power Pages](web-application-firewall.md)
- [Configure Web Application Firewall for Power Pages](configure-web-application-firewall.md)
