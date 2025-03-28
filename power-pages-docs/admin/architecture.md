---
title: Power Pages architecture 
description: Learn about how Power Pages architecture
ms.topic: conceptual
ms.custom: 
ms.date: 04/03/2023
ms.subservice: 
author: PramithaU
ms.author: pudupa
ms.reviewer: danamartens
contributors:
    - dileepsinghmicrosoft
---

# Power Pages architecture

Power Pages provides a secure, scalable and highly available platform to build business critical websites for variety of use cases.

Each production Power Pages website follows the same architecture that is optimized for scalability and high availability. Following diagram describes the architecture that is used to host each Power Pages website.

:::image type="content" source="media/architecture/architecture.png" alt-text="Power Pages architecture.":::

The following are the key components of each Power Pages Website setup:

## Content delivery network (CDN)

Content delivery network (CDN) helps improve performance and scalability of the website by reducing the network latency for end users as well as by caching static files and serving them from an edge network.  
Power Pages provides an out of the box [CDN capability](../configure/configure-cdn.md) which isn't enabled by default but can be enabled by a site administrator.
If you require more control, Power Pages also supports external content deliver network providers like Azure front door, Akamai, Cloudflare, Imperva, and others that can be configured with your Power Pages website. This [sample documentation](../configure/azure-front-door.md) describes how an Azure front door based content delivery network can be configured with Power Pages website

## Web Application Firewall (WAF)

A Web Application Firewall (WAF) helps improves security posture of a website by analyzing traffic and protecting website against common attacks like cross site scripting, SQL injection, file inclusion, and others.
Similar to [content delivery network](#content-delivery-network-cdn), Power Pages provides an out of the box [web application firewall](../security/web-application-firewall.md) which is enabled by a site administrator.  
If you require more control over web application firewall configuration, Power Pages also supports bringing in customer owned web application firewall providers like Azure front door, Akamai, Cloudflare, Imperva, and others.

## Power Pages Site deployment

### Azure Traffic Manager
    
Each Power Pages production website comes configured with an Azure traffic manager instance that is set in active/passive mode to direct the end user traffic to appropriate Application server. This feature enables both high availability and disaster recovery.

### Application Servers

Each Power Pages production websites consists of at least two application server nodes hosted in different Azure Data center regions to provide high availability and disaster recovery. Azure Traffic manager constantly monitors these nodes and direct traffic to the node that is available. Location of Azure Data center region determines the location of the Power Platform environment to which the site belongs. 

For example: If the environment location is Europe, then application servers would be in North Europe and West Europe data centers. Primary region of a site is determined by the primary region of the Power Platform organization to keep minimal latency between Dataverse and the website. Scaling of these application servers is done automatically based on the Power Pages licensing capacity assigned to the environment.

### Dataverse

Microsoft Dataverse is a key component for any Power Pages website. It acts as both Metadata store for the website storing all website configuration like webpages, content snippets, site settings, user metadata, and others and the data store for business data.  
Power Pages website connects to Dataverse instance utilizing a Server to Server connection. 

More details about the Power Pages website architecture can be read in the [Architecture whitepaper](../guidance/white-papers/architecture.md).

## See Also
- [Power Pages lifecycle](lifecycle.md)
- [Power Pages connectivity to a Microsoft Dataverse](connectivity.md)