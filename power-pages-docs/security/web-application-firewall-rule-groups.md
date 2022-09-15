---
title: Web Application Firewall DRS rule groups and rules on Power Pages
description: Learn about Web Application Firewall DRS rule groups and rules on Power Pages.
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

# Web Application Firewall DRS rule groups and rules on Power Pages

Power Pages' Web Application Firewall managed rule sets are a subset of Azure-managed rule sets.

## Azure managed rule sets for Power Pages

There are several Azure managed [DRS 2.0](/azure/web-application-firewall/afds/waf-front-door-drs?tabs=drs20#drs-20) rules set enabled for Power Pages.

| **Rule group**                                           | **Description**                                                             |
|----------------------------------------------------------|-----------------------------------------------------------------------------|
| [General](#general)                                      | General group                                                               |
| [METHOD-ENFORCEMENT](#method-enforcement)                | Lock-down methods (PUT, PATCH)                                              |
| [PROTOCOL-ENFORCEMENT](#protocol-enforcement)            | Protect against protocol and encoding issues                                |
| [PROTOCOL-ATTACK](#protocol-attack)                      | Protect against header injection, request smuggling, and response splitting |
| [APPLICATION-ATTACK-LFI](#lfi---local-file-inclusion)    | Protect against file and path attacks                                       |
| [APPLICATION-ATTACK-RFI](#rfi---remote-file-inclusion)   | Protect against remote file inclusion (RFI) attacks                         |
| [APPLICATION-ATTACK-XSS](#xss---cross-site-scripting)    | Protect against cross-site scripting attacks                                |
| [APPLICATION-ATTACK-SESSION-FIXATION](#session-fixation) | Protect against session-fixation attacks                                    |
| [MS-ThreatIntel-WebShells](#ms-threatintel-webshells)    | Protect against Web shell attacks                                           |
| [MS-ThreatIntel-AppSec](#ms-threatintel-appsec)          | Protect against AppSec attacks                                              |

## WAF rule groups and rules for Power Pages

The following rule groups and rules are available using Web Application Firewall for Power Pages

### General

| **RuleId** | **Description**                                 |
|------------|-------------------------------------------------|
| 200002     | Failed to parse request body.                   |
| 200003     | Multipart request body failed strict validation |

### METHOD-ENFORCEMENT

| **RuleId** | **Description**                 |
|------------|---------------------------------|
| 911100     | Method isn't allowed by policy |

### PROTOCOL-ENFORCEMENT

| **RuleId** | **Description**                                     |
|------------|-----------------------------------------------------|
| 920100     | Invalid HTTP Request Line                           |
| 920121     | Attempted multipart/form-data bypass                |
| 920160     | Content-Length HTTP header isn't numeric.          |
| 920170     | GET or HEAD Request with Body Content.              |
| 920171     | GET or HEAD Request with Transfer-Encoding.         |
| 920180     | POST request missing Content-Length Header.         |
| 920190     | Range: Invalid Last Byte Value.                     |
| 920200     | Range: Too many fields (6 or more)                  |
| 920201     | Range: Too many fields for pdf request (35 or more) |
| 920210     | Multiple/Conflicting Connection Header Data Found.  |
| 920220     | URL Encoding Abuse Attack Attempt                   |
| 920240     | URL Encoding Abuse Attack Attempt                   |
| 920260     | Unicode Full/Half Width Abuse Attack Attempt        |

### PROTOCOL-ATTACK

| **RuleId** | **Description**                                                           |
|------------|---------------------------------------------------------------------------|
| 921110     | HTTP Request Smuggling Attack                                             |
| 921120     | HTTP Response Splitting Attack                                            |
| 921130     | HTTP Response Splitting Attack                                            |
| 921140     | HTTP Header Injection Attack via headers                                  |
| 921150     | HTTP Header Injection Attack via payload (CR/LF detected)                 |
| 921151     | HTTP Header Injection Attack via payload (CR/LF detected)                 |
| 921160     | HTTP Header Injection Attack via payload (CR/LF and header-name detected) |

### LFI - Local File Inclusion

| **RuleId** | **Description**              |
|------------|------------------------------|
| 930100     | Path Traversal Attack (/../) |
| 930110     | Path Traversal Attack (/../) |
| 930120     | OS File Access Attempt       |

### RFI - Remote File Inclusion

| **RuleId** | **Description**                                                                                      |
|------------|------------------------------------------------------------------------------------------------------|
| 931100     | Possible Remote File Inclusion (RFI) Attack: URL Parameter using IP Address                          |
| 931110     | Possible Remote File Inclusion (RFI) Attack: Common RFI Vulnerable Parameter Name used w/URL Payload |
| 931120     | Possible Remote File Inclusion (RFI) Attack: URL Payload Used w/Trailing Question Mark Character (?) |

### XSS - Cross-site Scripting

| **RuleId** | **Description**                                    |
|------------|----------------------------------------------------|
| 941101     | XSS Attack Detected via libinjection.              |
| 941110     | XSS Filter - Category 1: Script Tag Vector         |
| 941120     | XSS Filter - Category 2: Event Handler Vector      |
| 941140     | XSS Filter - Category 4: JavaScript URI Vector     |
| 941170     | NoScript XSS InjectionChecker: Attribute Injection |
| 941180     | Node-Validator Blacklist Keywords                  |
| 941190     | XSS Using style sheets                             |
| 941200     | XSS using VML frames                               |
| 941210     | XSS using obfuscated JavaScript                    |
| 941220     | XSS using obfuscated VB Script                     |
| 941230     | XSS using 'embed' tag                              |

### SESSION-FIXATION

| **RuleId** | **Description**                                                                     |
|------------|-------------------------------------------------------------------------------------|
| 943100     | Possible Session Fixation Attack: Setting Cookie Values in HTML                     |
| 943110     | Possible Session Fixation Attack: SessionID Parameter Name with Off-Domain Referrer |
| 943120     | Possible Session Fixation Attack: SessionID Parameter Name with No Referrer         |

### MS-ThreatIntel-WebShells

| **RuleId** | **Description**                                |
|------------|------------------------------------------------|
| 99005002   | Web Shell Interaction Attempt (POST)           |
| 99005003   | Web Shell Upload Attempt (POST) - CHOPPER PHP  |
| 99005004   | Web Shell Upload Attempt (POST) - CHOPPER ASPX |
| 99005006   | Spring4Shell Interaction Attempt               |

### MS-ThreatIntel-AppSec

| **RuleId** | **Description**                                    |
|------------|----------------------------------------------------|
| 99030001   | Path Traversal Evasion in Headers (/.././../)      |
| 99030002   | Path Traversal Evasion in Request Body (/.././../) |
