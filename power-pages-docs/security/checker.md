---
title: Security Checker
description: Learn about Security Checker in Power Pages.
author: 
ms.topic: conceptual
ms.custom: 
ms.date: 7/12/2023
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---
# Security Checker 

In this article, you'll learn about Site Checker diagnostics results for Security issues. 

## Diagnostics

### Web Application firewall enabled 
Enable Web Application Firewall to secure your site. More information: [Configure Web Application Firewall for Power Pages (preview)](configure-web-application-firewall.md)

### No Anonymous access to Dataverse tables 
This check fails if there are one or more table permissions that allow anonymous users to access Dataverse data. Review the table permissions and remove anonymous user access unless your use case requires anonymous access. More information: [Configuring table permissions](table-permissions.md)

### Web Template validation
Web Template Validation is enabled by default, and prevents malicious scripts from running on your website. This check will fail when it is disabled. You can enable Web Template Validation by removing the setting “DisableValidationWebTemplate” or setting the value to false. More information: [Configure site settings for websites](../configure/configure-site-settings.md) 

### HTTP headers
The cross-origin resource sharing (CORS) protocol consists of a set of headers that indicates whether a response can be shared with another domain. You can configure CORS support in Power Pages using the Portal Management app by adding and configuring the site settings. 

The following are site settings are used to configure CORS and their recommended values. 

|Security Check  |Site Setting  |Recommended Value  |
|---------|---------|---------|
|Access-Control-Allow-Origin restriction      |TTP/Access-Control-Allow-Origin          |False or remove the setting          |
|Access-Control-Allow-Credentials restriction      |HTTP/Access-Control-Allow-Credentials          |False or remove the setting         |
|Content Security Policy    |HTTP/Content-Security-Policy          |nonce          |
|X Frame Options configuration     |HTTP/X-Frame-Options          |SAMEORIGIN or DENY          |
|HTTP/X-Content-Type-Options configuration      |HTTP/X-Content-Type-Options         |nosniff          |

Review and switch the headers to recommended values unless your use case requires a non-recommended value. More information: [Set up HTTP headers in Power Pages](../configure/cors-support.md) 


