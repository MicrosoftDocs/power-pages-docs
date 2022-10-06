---
title: Web Application Firewall DRS rule groups and rules for Power Pages (preview)
description: Learn about Web Application Firewall DRS rule groups and rules for Power Pages.
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

# Web Application Firewall DRS rule groups and rules for Power Pages (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Web Application Firewall managed rule sets for Power Pages are a subset of Azure-managed [DRS 2.0 rule sets](/azure/web-application-firewall/afds/waf-front-door-drs?tabs=drs20#drs-20). Each group contains multiple rules, and you can disable individual rules or entire rule groups.

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

<!---

## General

The General rule group protects against improperly formed requests.

| **RuleId** | **Description**                                 |
|------------|-------------------------------------------------|
| 200002     | Failed to parse request body                    |

## METHOD-ENFORCEMENT

The METHOD-ENFORCEMENT rule group protects against unauthorized method calls using lock-down methods (PUT, PATCH).

| **RuleId** | **Description**                 |
|------------|---------------------------------|
| 911100     | Method isn't allowed by policy  |

## PROTOCOL-ENFORCEMENT

The PROTOCOL-ENFORCEMENT rule group protects against protocol and encoding issues.

| **RuleId** | **Description**                                     |
|------------|-----------------------------------------------------|
| 920100     | Invalid HTTP Request Line                           |
| 920121     | Attempted multipart/form-data bypass                |
| 920160     | Content-Length HTTP header isn't numeric            |
| 920170     | GET or HEAD Request with Body Content               |
| 920171     | GET or HEAD Request with Transfer-Encoding          |
| 920190     | Range: Invalid Last Byte Value                      |
| 920200     | Range: Too many fields (6 or more)                  |
| 920210     | Multiple/Conflicting Connection Header Data Found   |
| 920220     | URL Encoding Abuse Attack Attempt                   |
| 920240     | URL Encoding Abuse Attack Attempt                   |
| 920260     | Unicode Full/Half Width Abuse Attack Attempt        |

## PROTOCOL-ATTACK

The PROTOCOL-ATTACK rule group offers protection against header injection, request smuggling, and response splitting.

| **RuleId** | **Description**                                                           |
|------------|---------------------------------------------------------------------------|
| 921110     | HTTP Request Smuggling Attack                                             |
| 921120     | HTTP Response Splitting Attack                                            |
| 921130     | HTTP Response Splitting Attack                                            |
| 921140     | HTTP Header Injection Attack via headers                                  |
| 921150     | HTTP Header Injection Attack via payload (CR/LF detected)                 |
| 921151     | HTTP Header Injection Attack via payload (CR/LF detected)                 |
| 921160     | HTTP Header Injection Attack via payload (CR/LF and header-name detected) |

## LFI - Local File Inclusion

The Local File Inclusion rule group protects against file and path attacks.

| **RuleId** | **Description**              |
|------------|------------------------------|
| 930110     | Path Traversal Attack (/../) |

## RFI - Remote File Inclusion

The Remote File Inclusion rule group protects against remote file inclusion (RFI) attacks.

| **RuleId** | **Description**                                                                                      |
|------------|------------------------------------------------------------------------------------------------------|
| 931100     | Possible Remote File Inclusion (RFI) Attack: URL Parameter using IP Address                          |
| 931110     | Possible Remote File Inclusion (RFI) Attack: Common RFI Vulnerable Parameter Name used w/URL Payload |
| 931120     | Possible Remote File Inclusion (RFI) Attack: URL Payload Used w/Trailing Question Mark Character (?) |

## XSS - Cross-site Scripting

The Cross-site Scripting rule group protects against cross-site scripting attacks.

| **RuleId** | **Description**                                    |
|------------|----------------------------------------------------|
| 941101     | XSS Attack Detected via libinjection               |
| 941110     | XSS Filter - Category 1: Script Tag Vector         |
| 941140     | XSS Filter - Category 4: JavaScript URI Vector     |
| 941170     | NoScript XSS InjectionChecker: Attribute Injection |
| 941180     | Node-Validator Allowlist Keywords                  |
| 941190     | XSS Using style sheets                             |
| 941200     | XSS using VML frames                               |
| 941210     | XSS using obfuscated JavaScript                    |
| 941220     | XSS using obfuscated VB Script                     |
| 941230     | XSS using 'embed' tag                              |

## SESSION-FIXATION

The SESSION-FIXATION rule group protects against session-fixation attacks.

| **RuleId** | **Description**                                                                     |
|------------|-------------------------------------------------------------------------------------|
| 943100     | Possible Session Fixation Attack: Setting Cookie Values in HTML                     |
| 943110     | Possible Session Fixation Attack: SessionID Parameter Name with Off-Domain Referrer |
| 943120     | Possible Session Fixation Attack: SessionID Parameter Name with No Referrer         |

## MS-ThreatIntel-WebShells

The MS-ThreatIntel-WebShells rule group protects against Web shell attacks.

| **RuleId** | **Description**                                |
|------------|------------------------------------------------|
| 99005002   | Web Shell Interaction Attempt (POST)           |
| 99005003   | Web Shell Upload Attempt (POST) - CHOPPER PHP  |
| 99005004   | Web Shell Upload Attempt (POST) - CHOPPER ASPX |

## MS-ThreatIntel-AppSec

The MS-ThreatIntel-AppSec rule group protects against AppSec attacks.

| **RuleId** | **Description**                                    |
|------------|----------------------------------------------------|
| 99030001   | Path Traversal Evasion in Headers (/.././../)      |
| 99030002   | Path Traversal Evasion in Request Body (/.././../) |

-->

### See also

- [Web Application Firewall DRS rule groups and rules](/azure/web-application-firewall/afds/waf-front-door-drs)
- [Web Application Firewall (WAF) for Power Pages (preview)](web-application-firewall.md)
- [Configure Web Application Firewall for Power Pages (preview)](configure-web-application-firewall.md)