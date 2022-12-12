---
title: Power Pages system requirements and limits
description: Learn about device platform and web browser requirements, limits, and configuration values for Power Pages.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.reviewer: ndoelman
ms.date: 12/12/2022
ms.subservice: 
ms.author: nenandw
contributors:
  - nickdoelman
  - neerajnandwana-msft

---
# System requirements, limits, and configuration values for Power Pages

This article contains information on supported device platforms, web browser requirements, limits, and configuration values for Power Pages. 

## Supported browsers for running Power Pages sites

| **Browser** | **Supported versions** |  
| --- | --- | 
| Google Chrome|Latest three major releases| 
| Microsoft Edge|Latest three major releases| 
| Mozilla Firefox |Latest three major releases| 
| Apple Safari|13 and later| 

## Supported operating systems for browsers running Power Pages sites

| **Operating system** | **Supported versions** | 
| --- | --- | 
| Windows |Windows 10 or later| 
| macOS|10.13 or later| 
| iOS |iOS 13 or later|
| Android |10 or later |

## Supported web browsers and operating systems for Power Pages design studio

The supported browsers for Power Pages design studio are listed below.

| **Browser**                     | **Operating system**           |
|---------------------------------|--------------------------------|
| Google Chrome (latest version)<br>(recommended)                    | <ul><li>Windows 7 SP1, 8.1, 10, and 11</li><li>macOS</li></ul>      |
| Microsoft Edge (latest version)<br> (recommended)                    | Windows 10, and 11 |

## IP addresses

Requests from Power Pages use IP addresses that depend on the region of the [environment](/power-platform/admin/environments-overview) that the site is in. We don't publish fully qualified domain names available for Power Pages scenarios.

## Required services

This list identifies all services to which Power Pages communicates and their usages. Your network must **not** block these services.

| Domain(s) | Protocols | Uses |
| --- | --- | --- |
| api.bap.microsoft.com<br>api.businessappdiscovery.microsoft.com | https | Environment permissions management |
| management.azure.com | https | Power Apps Management Service |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |Microsoft Authentication Library |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - For getting user info (for example, profile photo) |
| \*.powerapps.com |https | create.powerapps.com, content.powerapps.com, apps.powerapps.com, make.powerapps.com, \*gateway.prod.island.powerapps.com, and \*gateway.prod.cm.powerapps.com |
| \*.blob.core.windows.net |https | Blob storage |
| \*.dynamics.com | https | Microsoft Dataverse |
| *.api.powerplatform.com | https | Required for Power Platform API connectivity used internally by Microsoft products, and Power Platform [programmability and extensibility](/power-platform/admin/programmability-extensibility-overview).

## Proxies
Power Pages doesn't support running with a proxy enabled. This can cause unpredictable behavior. If you encounter issues, disable the proxy, and then try again.

- Some proxies (such as Zscaler, Blue Coat) modify Power Pages requests by removing headers (CORS or authentication headers). Power Pages relies on these headers to load the app.

## Data types size limits

For Microsoft Dataverse data type size limits, you can find information on column types, such as text and image columns, in [Types of columns](/power-apps/maker/data-platform/types-of-fields).


