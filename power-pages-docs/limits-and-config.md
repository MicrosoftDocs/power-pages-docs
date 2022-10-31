---
title: Power Pages system requirements and limits
description: Learn about device platform and web browser requirements, limits, and configuration values for Power Pages.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.reviewer: ndoelman
ms.date: 10/31/2022
ms.subservice: 
ms.author: nenandw
contributors:
  - tapanm-msft
  - lancedmicrosoft
  - alaug
  - amchern
---
# System requirements, limits, and configuration values for Power Pages

This article contains information on supported device platforms, web browser requirements, limits, and configuration values for Power Pages. 

## Supported browsers for running Power Pages

| **Browser** | **Supported versions** |  **App type** |
| --- | --- | --- |
| Google Chrome|Latest three major releases| Power Pages sites, and component designers<sup>1</sup>.  |
| Microsoft Edge|Latest three major releases| Power Pages sites, app and component designers<sup>1</sup>.  |
| Mozilla Firefox |Latest three major releases| Power Pages sites  |
| Apple Safari|13 and later| Power Pages sites  |

<sup>1</sup>App and component designers include Power Pages home page, Power Pages design studio, and Visual Studio Code for the Web.

## Supported operating systems for browsers running Power Pages

| **Operating system** | **Supported versions** |  **App type**  |
| --- | --- | ---|
| Windows |Windows 10 or later| Power Pages sites, app and component designers<sup>1</sup>.   |
| macOS|10.13 or later| Power Pages sites, app and component designers<sup>1</sup>.   |
| iOS |iOS 13 or later| Power Pages sites.  |
| Android |10 or later | Power Pages sites.  |

<sup>1</sup>App and component designers include Power Pages home page, Power Pages design studio, and Visual Studio Code for the Web.

## Request limits

These limits apply to each single outgoing request:

| Name | Limit |
| --- | --- |
| Timeout |180 Seconds |
| Retry attempts |4 |

> [!NOTE]
> The retry value may vary. For certain error conditions, it's not necessary to retry.

## IP addresses

Requests from Power Pages use IP addresses that depend on the region of the [environment](/power-platform/admin/environments-overview) that the site is in. We don't publish fully qualified domain names available for Power Pages scenarios.

## Required services

This list identifies all services to which Power Pages communicates and their usages. Your network must **not** block these services.

| Domain(s) | Protocols | Uses |
| --- | --- | --- |
| api.bap.microsoft.com<br/>api.businessappdiscovery.microsoft.com | https | Environment permissions management|
| management.azure.com |https |Power Apps Management Service |
| msmanaged-na.azure-apim.net |https |Runtime of Connectors/Apis |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |Microsoft Authentication Library |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - For getting user info (for example, profile photo) |
| gallery.azure.com |https |Sample and Template apps |
| \*.azure-apim.net |https |Api Hubs - Different subdomains for each locale |
| \*.powerapps.com |https | create.powerapps.com, content.powerapps.com, apps.powerapps.com, make.powerapps.com, \*gateway.prod.island.powerapps.com, and \*gateway.prod.cm.powerapps.com |
| \*.azureedge.net |https | create.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.blob.core.windows.net |https | Blob storage |
| \*.flow.microsoft.com | https | create.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.dynamics.com | https | Microsoft Dataverse |
| vortex.data.microsoft.com |https |Telemetry |
| localhost | https | Power Apps Mobile|
| 127.0.0.1 | http | Power Apps Mobile|
| ecs.office.com | https | Retrieve feature flags for Power Apps |
| config.edge.skype.com | https | Retrieve feature flags for Power Apps (backup)|
| \*.api.powerplatform.com | https | Required for Power Platform API connectivity used internally by Microsoft products, and Power Platform [programmability and extensibility](/power-platform/admin/programmability-extensibility-overview).|
| *.powerapps.us | https | Required for Power Pages for Government Community Cloud (GCC).<sup>1</sup>  |
| *.powerapps.us | https | Required for Power Pages for Government Community Cloud (GCC High).<sup>2</sup> |
| *.appsplatform.us | https | Required for Power Pages for Power Apps Department of Defense (DoD).<sup>3</sup> |

<sup>1</sup> Replaces domain name `gov.content.powerapps.us` used prior to July 2022. <br>
<sup>2</sup> Replaces domain name `high.content.powerapps.us` used prior to July 2022. <br>
<sup>3</sup> Replaces domain name `content.appsplatform.us` used prior to July 2022.

## Proxies
Power Pages does not support running with a proxy enabled. This can cause unpredictable behavior. If you encounter issues, disable the proxy and then try again.

- Some proxies (such as Zscaler, Blue Coat) modify Power Pages requests by removing headers (CORS or authentication headers). Power Pages relies on these headers to load the app.
- Some proxies (such as Microsoft Defender for Cloud Apps, McAfee) may intercept and change the URL of an app or embedded app. For example, if there is a Dynamics 365 app that is running under domain **org.crm.dynamics.com** or a canvas app that is running under domain **apps.powerapps.com**, the platform will not support a proxy that change these domains to a custom domain such as **mycustomdomain.com**. This can cause unpredictable behavior when the platform tries to retrieve tokens that are necessary to run the app.

## Data types size limits

For Microsoft Dataverse data type size limits, you can find information on column types, such as text and image columns, in [Types of columns](/power-apps/maker/data-platform/types-of-fields).


