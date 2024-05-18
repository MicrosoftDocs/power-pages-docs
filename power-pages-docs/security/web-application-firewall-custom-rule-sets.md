---
title: Configure Web Application Firewall custom rules
description: Enhance web application security with custom rules in Web Application Firewall, which allows blocking or allowing specific requests based on set criteria.
author: nageshbhat-msft
ms.topic: conceptual
ms.date: 04/16/2024
ms.author: nabha
ms.reviewer: kkendrick
contributors:
  - ProfessorKendrick
  - nageshbhat-msft
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:05/15/2024
---
# Configure Web Application Firewall custom rules

Web Application Firewall custom rules allow you to define your own rules for blocking or allowing specific requests based on various criteria, such as geo-filtering, the source IP address, and the request uri. You can use custom rules to enhance the security of your web applications and also help you optimize the performance of your web applications by filtering out unwanted traffic or reducing false positives. 

Configure the custom rules by navigating to Security workspace. 

## Prerequisite 

- You must be administrator to configure custom rules. 
- [Web Application Firewall](web-application-firewall.md) must be enabled for the site. 

## Create custom rules
 
1. Select **+ Add New Rule**. 

1. Enter the rule name.

1. Select the rule type.

    You can define the custom rule by selecting either Match rule or Rate limit. 

    - **Match type:** Allows/blocks the request based on the rule type defined in the subsequent step.                                      |
    - **Rate limit:** Allows/blockS the number of requests threshold limit and throttle the requests exceeding the threshold limit.
    
    You can configure the threshold limit between 1 and 5 minutes.

1. Select the match type.

    To create a custom rule, choose one of the options from the Match type dropdown menu: 
    
    - **Geo location:** Allows or blocks requests based on their geographic origin. Useful for preventing attacks from specific regions or countries, or enforcing regional content restrictions. 
    
    - **IP address:** Allows or blocks requests based on their source IP address. Helpful for protecting against specific attackers or bots, or restricting access to authorized users. 
    
    - **Request URI:** Allows or blocks requests based on the requested path or query string. Useful for preventing access to sensitive or restricted areas of the site, or enforcing specific rules for different sections. 

    Depending on the selected match type, the configuration options vary. Update the appropriate settings in the field that appears after selecting the match type 

1. Select the traffic settings.

    Use the traffic setting configuration to block or allow the request based on the rules you configure.

    Choose the **+ Add new rule** button to add additional rules. 
    
    Repeat the above steps to configure each rule.

1. Choose **Save**. 

Each request to your site is evaluated against the firewall configurations based on their priority order. You can adjust the order of rule execution by increasing or decreasing their priority. Simply hover over each rule and select the three dots (…) to modify the priority settings. 

## Match variable 

When an end user makes requests to the Power Pages site, these requests can originate directly from the end user's location/IP or via a proxy server.  

    - **RemoteAddr:** This field denotes the remote address, identifying requests based on the requester's location or IP address. It represents the original client IP, sourced either from the network connection or typically from the X-Forwarded-For request header if the user is behind a proxy. 
    
    - **SocketAddr:** This field denotes the socket address, identifying requests based on a direct connection to the firewall edge. If the client used an HTTP proxy or a load balancer to send the request, the socket address is the IP address of the proxy or load balancer. 