---
title: FAQ for Security Agent
description: Learn about the features, intended uses, limitations, and operational factors of the Power Pages website security agent for securing public-facing websites.
author: shwetamurkute
ms.update-cycle: 180-days
ms.custom: responsible-ai-faqs
contributors:
ms.topic: faq
ms.date: 07/23/2025
ms.author: smurkute
ms.reviewer: smurkute
---

# FAQ for security agent

This FAQ outlines the impact of AI-powered features in Power Pages website security agent, including its features, intended uses, limitations, and operational considerations for securing public-facing websites.

## What is Power Pages security agent?

The Power Pages website security agent is an AI-assisted system integrated into Microsoft Power Pages design studio that helps makers proactively secure their public-facing websites. It combines scheduled vulnerability scanning, real-time traffic anomaly detection, and guided
remediation to assist non-security-expert makers in maintaining a secure posture.

The system takes as input the results of security scans (via OWASP ZAP), real-time telemetry from Microsoft Sentinel, and historical traffic data. Based on this, it generates alerts and guided fix flows. These flows may include rule-based actions or AI-generated configuration
recommendations. The output is a contextualized remediation experience that includes suggestions, editable configurations, and system-triggered alerts delivered via user-preferred channels.

## What can Power Pages website security agent do?

The system supports several core functions:

- **Scheduled Security Scanning:** Runs every 2 weeks against 37 OWASP-aligned rules using ZAP. It detects misconfigured headers, XSS risks, and exposed information.

- **Real-time Anomaly Detection:** Monitors live traffic patterns with Microsoft Sentinel to detect suspicious behavior (e.g., traffic spikes or IP clusters).

- **Guided Fix Flows:** Presents multi-step remediation guidance within the design studio. Some suggested fixes are rule-based and some are AI generated.

- **Alert Notification:** Delivers alerts via in-product notifications, email, or Microsoft Teams depending on user configuration.

## What is/are Power Pages website security agent's intended use(s)?

The intended use of the security agent is to assist makers in proactively maintaining their website's security posture. It is designed for:

- Detecting vulnerabilities automatically

- Monitoring traffic patterns to identify possible threats

- Offering transparent, editable, and contextual security recommendations.

- Enabling quick and informed decision-making on remediation steps.

## How was Power Pages website security agent evaluated? What metrics are used to measure performance?

The capability was evaluated over custom datasets for offensive and malicious prompts and responses. The evaluation was done through both automated and dedicated manual sessions that were designed to expand the test suite.

## What are the limitations of Power Pages website security agent? How can users minimize the impact of these limitations?

- AI-generated suggestions may occasionally be overly conservative or not applicable to complex edge cases.

- The agent does not automatically apply fixes, it provides recommendations, but the final decision and action rest with the maker.

**Recommendations to mitigate limitations:**

- Use AI suggestions as a starting point and validate before applying to live sites.

- Combine Security Agent with other organizational security controls for full coverage.

## What operational factors and settings allow for effective and responsible use of the security agent?

- **Customizability:** Makers can enable/disable use cases such as scans and anomaly detection.

- **Notification Preferences:** Makers can configure how alerts are delivered (in-product, email, Teams).

- **Transparency:** All AI suggestions are editable, with plain-language rationale provided.

- **Granularity:** Guided fix flows are structured into steps, with actionable options at each stage.

## How do I provide feedback on Power Pages Website Security Agent?

Makers can provide:

- Thumbs up/down feedback on each AI recommendation within the studio.

- Optional comments to explain feedback.

- Broader feedback via standard Microsoft support channels.

## What data does Power Pages Website Security Agent collect, and how is it used?

The Security Agent does **not collect or store any customer content or personal data** outside the customer’s environment.

- For Content Security Policy (CSP) fixes: Only recommendations based on your current CSP headers are generated and saved within your own environment.

- For DDoS mitigation: The system analyses one month of historical traffic data and Sentinel alerts, and the custom WAF suggestions are saved within your own environment.

- All AI-generated suggestions are based on metadata and system configurations, not user-generated content.

- No data is used for model training, and there is no long-term retention of customer data by Microsoft as part of this feature.
