---
title: Configure Web Application Firewall custom rules
description: 
author: nageshbhat-msft
ms.topic: conceptual
ms.custom: 
ms.date: 04/15/2024
ms.author: nabha
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
    - nageshbhat-msft
---
# Configure Web Application Firewall custom rules

Web Application Firewall custom rules allow you to define your own rules for blocking or allowing specific requests based on various criteria, such as geo-filtering, the source IP address, and the request uri. You can use custom rules to enhance the security of your web applications and also help you optimize the performance of your web applications by filtering out unwanted traffic or reducing false positives. 

Configure the custom rules by navigating to Security workspace 

## Pre-requisite 

You must be administrator to configure custom rules 

Web Application Firewall must be enabled for the site 

 
Click on + Add New Rule 

Enter Rule name 

Select Rule type 

You can define the custom rule by selecting either Match rule or Rate limit. 

Match type: Match rule type will completely allow / block the request based on the rule type defined in the subsequent step.  

Rate limit: Rate limit rule will allow / block number of requests threshold limit and throttle the requests exceeding the threshold limit. 

You can configure the threshold limit in the range of 1 or 5 minutes duration. 

Select Match type 

To create a custom rule, choose one of the options from the Match type dropdown menu: 

Geo location: Allows or blocks requests based on their geographic origin. Useful for preventing attacks from specific regions or countries, or enforcing regional content restrictions. 

IP address: Allows or blocks requests based on their source IP address. Helpful for protecting against specific attackers or bots, or restricting access to authorized users. 

Request URI: Allows or blocks requests based on the requested path or query string. Useful for preventing access to sensitive or restricted areas of the site, or enforcing specific rules for different sections. 

Depending on the selected match type, the configuration options will vary. Update the appropriate settings in the field that appears after selecting the match type 

Select the Traffic settings 

Based on the rules you configure, you can either block the request or allow it using the traffic setting configuration  

Add more rules by clicking + Add new rule button 

Repeat the above steps to configure each rule 

Click Save 

Each request to your site is evaluated against the firewall configurations based on their priority order. You can adjust the order of rule execution by increasing or decreasing their priority. Simply hover over each rule and select the three dots (…) to modify the priority settings. 