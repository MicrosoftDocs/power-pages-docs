---
title: Power Pages architecture 
description: Learn about how Power Pages architecture
ms.topic: concept-article
ms.custom: 
ms.date: 04/28/2026
ms.subservice: 
author: PramithaU
ms.author: pudupa
ms.reviewer: danamartens
contributors:
    - dileepsinghmicrosoft
---

# Power Pages architecture

Power Pages provides a secure, scalable, and highly available platform to build business-critical websites for a variety of use cases.

Each production Power Pages website follows the same architecture that is optimized for scalability and high availability. The following diagram describes the architecture that is used to host each Power Pages website.

:::image type="content" source="media/architecture/architecture.png" alt-text="Power Pages architecture.":::

The following are the key components of each Power Pages Website setup:

## Content delivery network (CDN)

A content delivery network (CDN) helps improve the performance and scalability of the website by reducing network latency for end users and by caching static files and serving them from an edge network.  
Power Pages provides an out-of-the-box [CDN capability](../configure/configure-cdn.md) that isn't enabled by default but can be enabled by a site administrator.
If you require more control, Power Pages also supports external CDN providers like Azure Front Door, Akamai, Cloudflare, Imperva, and others that can be configured with your Power Pages website. This [sample documentation](../configure/azure-front-door.md) describes how an Azure Front Door–based CDN can be configured with a Power Pages website.

## Web Application Firewall (WAF)

A Web Application Firewall (WAF) helps improve the security posture of a website by analyzing traffic and protecting the website against common attacks like cross-site scripting, SQL injection, file inclusion, and others.
Similar to the [content delivery network](#content-delivery-network-cdn), Power Pages provides an out-of-the-box [web application firewall](../security/web-application-firewall.md) that is enabled by a site administrator.  
If you require more control over WAF configuration, Power Pages also supports customer-owned WAF providers like Azure Front Door, Akamai, Cloudflare, Imperva, and others.

## Power Pages Site deployment

### Azure Traffic Manager
    
Each Power Pages production website comes configured with an Azure Traffic Manager instance that is set in active/passive mode to direct end-user traffic to the appropriate application server. This feature enables both high availability and disaster recovery.

### Application Servers

Each Power Pages production website consists of at least two application server nodes hosted in different Azure datacenter regions to provide high availability and disaster recovery. Azure Traffic Manager constantly monitors these nodes and directs traffic to the node that is available. The location of the Azure datacenter region is determined by the location of the Power Platform environment to which the site belongs.

For example, if the environment location is Europe, the application servers would be in the North Europe and West Europe datacenters. The primary region of a site is determined by the primary region of the Power Platform organization to maintain minimal latency between Dataverse and the website. Scaling of these application servers is done automatically based on the Power Pages licensing capacity assigned to the environment.

### Dataverse

Microsoft Dataverse is a key component for any Power Pages website. It acts as both a metadata store for the website—storing all website configuration like webpages, content snippets, site settings, user metadata, and others—and the data store for business data.  
Power Pages websites connect to Dataverse using a server-to-server connection.

More details about the Power Pages website architecture can be found in the [Architecture whitepaper](../guidance/white-papers/architecture.md).

## See also

- [Power Pages lifecycle](lifecycle.md)
- [Power Pages connectivity to Microsoft Dataverse](connectivity.md)
- [How server-side caching works](clear-server-side-cache.md)
- [Configure a CDN for a Power Pages site](../configure/configure-cdn.md)
- [Web Application Firewall for Power Pages](../security/web-application-firewall.md)
- [Configure Azure Front Door with Power Pages](../configure/azure-front-door.md)
- [Performance and optimization](../admin/portal-checker-analysis.md)
