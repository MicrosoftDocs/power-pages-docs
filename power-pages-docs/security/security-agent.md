---
title: Power Pages Security Agent Overview and Capabilities
description: Power Pages Security Agent helps secure websites with automated vulnerability scans, real-time traffic monitoring, and guided mitigation workflows.
author: shwetamurkute
contributors:
ms.topic: concept-article
ms.date: 06/09/2025
ms.author: smurkute
ms.reviewer: smurkute
---

# Power Pages security agent

Power Pages security agent (preview) is an AI-powered feature built into the Power Pages design studio. 

## Overview

The security agent helps makers proactively secure their websites with minimal manual effort. The Security Agent works in the background to scan your website for common vulnerabilities, monitor live traffic patterns for anomalies, and guide you through resolving issues as they arise.

Whether you are new to web security or a seasoned admin, the security agent simplifies how you protect your external-facing sites with built-in intelligence, guided fixes, and real-time alerts, all without leaving the studio.

> [!NOTE]
> This feature is in **public preview** and will continue to evolve based on feedback.

## Capabilities

As part of the public preview, the Security Agent offers two primary capabilities to help makers secure their Power Pages sites:

- **Automated Security Scan**  
  Every two weeks, the agent runs a scheduled scan using the OWASP ZAP engine to detect common vulnerabilities across 37 predefined security rules. These include misconfigured headers, XSS risks, and exposed server information. When issues are found, the agent generates alerts and presents guided mitigation workflows to help makers resolve them.

- **Site traffic monitoring**  
  The agent monitors live traffic using Microsoft Sentinel signals and historical traffic data. When it detects suspicious spikes or clustered activity, it generates alerts and presents mitigation workflows.

Some recommendations are AI-generated, especially for complex issues like correcting CSP configurations or suggesting custom WAF rules. Others follow standard rule-based logic for known security best practices.

## How does it work?

The Power Pages Website Security Agent is designed to work behind the scenes while keeping makers fully in control. Here’s how the end-to-end flow works:

### 1. Configure the Security Agent

From the **Security Agent** tab in the Design Studio’s Security workspace, makers can:

- Choose which capabilities to enable (e.g., Automated Scanning, Traffic Monitoring).

- Select how to receive alerts, via in-product notifications, email, or Microsoft Teams.

This setup ensures the agent runs only what’s needed and notifies makers through their preferred channel.

:::image type="content" source="media/security-agent/security-agent-option.png" alt-text="Screenshot of the security agent configuration tab in Power Pages design studio.":::

:::image type="content" source="media/security-agent/monitor-site-traffic.png" alt-text="Screenshot of security agent configuration options in Power Pages showing details of site traffic.":::

### 2. Detect vulnerabilities or anomalies

Once enabled:

- **Automated Scans** run every two weeks using the ZAP engine and check against 37 OWASP-based rules.

- **Traffic Monitoring** runs continuously using Microsoft Sentinel signals and historical traffic patterns.

When issues are found, alerts are triggered automatically.

### 3. View and respond to alerts

All alerts appear in the **Overview** screen. For each alert:

- A **guided fix flow** is provided.

- Makers are shown **one or more recommended actions** based on the issue type

:::image type="content" source="media/security-agent/alerts-overview-screen.png" alt-text="Screenshot of Security Agent alert overview and guided fix flow in Power Pages.":::

### 4. Apply fixes directly in the Studio

Makers can:

- Review plain-language explanations for each recommendation.

- Accept or edit Suggested values.

- Take actions directly, through one-click settings, embedded VS Code, or external documentation links.

Each fix applied updates the alert status and helps keep the site secure.




