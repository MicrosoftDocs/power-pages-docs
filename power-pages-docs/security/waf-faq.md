---
title: FAQ for configuring Web Application Firewall in Power Pages
description: Learn about frequently asked questions and answers to configure Web Application Firewall rules in Power Pages.
author: nageshbhat-msft
ms.topic: faq
ms.date: 07/11/2024
ms.author: nabha
ms.reviewer: danamartens
contributors:
  - ProfessorKendrick
  - nageshbhat-msft
---

# FAQ for configuring Web Application Firewall in Power Pages

In this article, you learn about frequently asked questions related to configuring Web Application Firewall (WAF) in Power Pages.

## I want to set up a WAF rule to ensure that my site only receives traffic from customers accessing it from the United States

To configure WAF rule in this case, you need to create two rules in the following order:

| Parameter | Setting |
| - | - |
| Rule type | Match |
| Match type | Geo location |
| Match variable | RemoteAddr |
| Country or region | United States |
| Traffic settings | Allow |

| Parameter | Setting |
| - | - |
| Rule type | Match |
| Match type | Request URI |
| Match value | / |
| Traffic settings | Deny |

When the firewall receives traffic from the United States, the first rule is evaluated, and subsequent rules are discarded. If requests come from outside the United States, the first rule isn't evaluated, and the second rule is applied, blocking all requests.

## My site receives an average of 1,500 requests in 5 minutes. I want to configure a WAF rule to protect my site by preventing any DDoS attack. How should I set up my WAF rules?

Configure the rules with the following settings:

| Parameter | Setting |
| - | - |
| Rule name | Allow1500RequestsIn5Mins |
| Rule type | Rate limit |
| Rate limit in minutes | 5 minutes |
| Requests allowed within rate limit | 1500 |
| Match type | Request URI |
| Match value | / |
| Traffic settings | Deny |

## My site has been experiencing abnormal traffic for the past day. How can I analyze this traffic pattern and safeguard my site from potential attackers?

When you activate WAF for your site, all requests are logged and available for analysis. Download the WAF logs to examine the traffic patterns; these logs contain client IPs, socket IPs, and request URIs. You can then create custom rules using the IP address Match type to block identified IPs or ranges, or utilize Rate limit rules with specific URL parts to enforce regular threshold limits over one-minute intervals.
