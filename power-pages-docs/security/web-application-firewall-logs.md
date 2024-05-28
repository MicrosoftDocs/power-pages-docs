---
title: Web Application Firewall logs
description: Discover how to access and download web application firewall logs in Power Pages.
author: nageshbhat-msft
ms.topic: conceptual
ms.date: 05/28/2024
ms.author: nabha
ms.reviewer: kkendrick
contributors:
  - ProfessorKendrick
  - nageshbhat-msft
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:05/18/2024
---
# Web Application Firewall logs

When you activate [Web Application Firewall (WAF) for Power Pages](web-application-firewall.md) in Power Pages, each request's logs are captured and stored in your Dataverse instance. To access these logs, follow these steps: 

1. Navigate to the Security workspace.
1. Select the **Download firewall logs** button. 
1. Specify the start and end dates. 

>[!NOTE]
> By specifying the start and end dates, you can download only the relevant logs. By default, logs for the past 30 days are retained in Dataverse. You can modify this retention period by adjusting the settings in the configuration menu, located next to the 'Download firewall logs' button. You can extend the retention period up to 90 days, or choose to disable the capturing of firewall logs entirely. 

## Prerequisites

- Power Pages Core version 1.0.2403.2 or later.

## Firewall log schema 

Firewall logs for Power Pages are stored within the Dataverse instance associated with the site's environment. These logs are presented in the **Power Pages Log** table, which includes the following columns: 

| Column Name  | Description  |
|-------------------------|-------------------------|
| Name  | Power Pages site name  |
| Client IP  | Represents the client IP address associated with the request being processed.  |
| Content  | This column contains the detail of each rule execution.<br /><br />**clientIP**: Represents the client IP address associated with the request being processed. <br />**clientPort**: Represents the client port associated with the request being processed.<br />**socketIP**: Represents the socket IP address associated with the TCP connection that the current request originated from. <br />**requesturl**: site url being requested <br />**requestpath**: Partial path of the request <br />**ruleName**: Firewall rule being evaluated <br />**action** : allow/block<br />**trackingReference**: Unique reference for each request logged by firewall. <br />**details:** details of the rule evaluation   |
| Portal ID  | Website ID associated with the request site url  |
| Request Path  | Partial path of the request  |
| Request Url  | site url being requested  |
| Type  | WAFLog  |
|   |   |