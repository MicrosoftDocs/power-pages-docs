---
title: Web Application Firewall DRS rule groups and rules for Power Pages
description: Learn about Web Application Firewall DRS rule groups and rules for Power Pages.
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

# Web Application Firewall DRS rule groups and rules for Power Pages

Power Pages' Web Application Firewall managed rule sets are a subset of Azure-managed [DRS 2.0 rule sets](/azure/web-application-firewall/afds/waf-front-door-drs?tabs=drs20). Each group contains multiple rules, and you can disable individual rules or entire rule groups.

The following rule groups and rules are available using Web Application Firewall for Power Pages

### General

| **RuleId** | **Description**                                 |
|------------|-------------------------------------------------|
| 200002     | Failed to parse request body.                   |
| 200003     | Multipart request body failed strict validation |

### METHOD-ENFORCEMENT

Lock-down methods (PUT, PATCH)

| **RuleId** | **Description**                 |
|------------|---------------------------------|
| 911100     | Method isn't allowed by policy |

### PROTOCOL-ENFORCEMENT

The PROTOCOL-ENFORCEMENT rule group protects against protocol and encoding issues.

| **RuleId** | **Description**                                     |
|------------|-----------------------------------------------------|
| 920100     | Invalid HTTP Request Line                           |
| 920121     | Attempted multipart/form-data bypass                |
| 920160     | Content-Length HTTP header isn't numeric.           |
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

### LFI - Local File Inclusion

The Local File Inclusion rule group protects against file and path attacks.

| **RuleId** | **Description**              |
|------------|------------------------------|
| 930100     | Path Traversal Attack (/../) |
| 930110     | Path Traversal Attack (/../) |
| 930120     | OS File Access Attempt       |

### RFI - Remote File Inclusion

The Remote File Inclusion rule group protects against remote file inclusion (RFI) attacks.

| **RuleId** | **Description**                                                                                      |
|------------|------------------------------------------------------------------------------------------------------|
| 931100     | Possible Remote File Inclusion (RFI) Attack: URL Parameter using IP Address                          |
| 931110     | Possible Remote File Inclusion (RFI) Attack: Common RFI Vulnerable Parameter Name used w/URL Payload |
| 931120     | Possible Remote File Inclusion (RFI) Attack: URL Payload Used w/Trailing Question Mark Character (?) |

### XSS - Cross-site Scripting

The Cross-site Scripting rule group protects against cross-site scripting attacks.

> [!NOTE]
> This article contains references to the term *blacklist*, a term that Microsoft no longer uses. When the term is removed from the software, we’ll remove it from this article.

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

The SESSION-FIXATION rule group protects against session-fixation attacks.

| **RuleId** | **Description**                                                                     |
|------------|-------------------------------------------------------------------------------------|
| 943100     | Possible Session Fixation Attack: Setting Cookie Values in HTML                     |
| 943110     | Possible Session Fixation Attack: SessionID Parameter Name with Off-Domain Referrer |
| 943120     | Possible Session Fixation Attack: SessionID Parameter Name with No Referrer         |

### MS-ThreatIntel-WebShells

The MS-ThreatIntel-WebShells rule group protects against Web shell attacks.

| **RuleId** | **Description**                                |
|------------|------------------------------------------------|
| 99005002   | Web Shell Interaction Attempt (POST)           |
| 99005003   | Web Shell Upload Attempt (POST) - CHOPPER PHP  |
| 99005004   | Web Shell Upload Attempt (POST) - CHOPPER ASPX |
| 99005006   | Spring4Shell Interaction Attempt               |

### MS-ThreatIntel-AppSec

The MS-ThreatIntel-AppSec rule group protects against AppSec attacks.

| **RuleId** | **Description**                                    |
|------------|----------------------------------------------------|
| 99030001   | Path Traversal Evasion in Headers (/.././../)      |
| 99030002   | Path Traversal Evasion in Request Body (/.././../) |
