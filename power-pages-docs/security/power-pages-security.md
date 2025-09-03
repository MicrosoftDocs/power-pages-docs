---
title: Power Pages security
description: Learn how to secure the websites you create with Microsoft Power Pages.
ms.date: 11/13/2024
ms.topic: overview
author: dmartens
ms.author: dmartens
ms.reviewer: danamartens
contributors:
    - avishwakarma
ms.custom: bap-template
---

# Power Pages security

An important consideration when you build public-facing websites is how to make sure that only the correct stakeholders can access critical business data. Use the [Security workspace](../getting-started/use-security-workspace.md) in design studio to monitor, protect, and manage your Power Pages sites.

To make sure your business information is properly protected, Power Pages has a robust security model that encompasses the following key components:

- [Site visibility](#site-visibility)
- [Authenticated users](#authenticated-users)
- [Web roles](#web-roles)
- [Table permissions](#table-permissions)
- [Page permissions](#page-permissions)
- [HTTPS Headers](#https-headers)
- [Security Scan (preview)](#security-scan-preview)

## Site visibility

The [site visibility](site-visibility.md) setting controls who can access the sites you create in Power Pages. By default, all Power Pages sites are available to users who are internal to your organization. The extra layer of security that Microsoft Entra authentication provides helps to prevent accidental leaks of partially developed website data and designs.

When your website is ready to go live, change the site visibility to public. The public setting makes the site accessible to everyone over the Internet anonymously or to users authenticated through identity providers. 

## Authenticated users

Microsoft Dataverse contact records represent Power Pages users. Users can get access to your site through [authentication](authentication/index.md). You can integrate Power Pages with authentication providers like Microsoft Entra External ID, Microsoft, and LinkedIn. Authenticated users can be assigned web roles that provide specific access to information on the site. 

## Web roles

[Web roles](create-web-roles.md) allow users to perform special actions or access protected content and data on the site. Web roles link to users, table permissions, and page permissions. Because users can be assigned multiple web roles, they can get cumulative access to site resources.

All authenticated users, or contacts, are automatically assigned to the Authenticated Users web role. Anonymous, or unauthenticated, users can visit a site and get access to assets through the Anonymous Users web role. 

## Table permissions

Access to Dataverse information through [lists](../getting-started/add-list.md), [forms](../getting-started/add-form.md), [Liquid](../configure/liquid-overview.md), and the [Web API](../configure/web-api-overview.md) is protected by table permissions. You can [configure table permissions](table-permissions.md) to allow different levels of access and privileges to Dataverse records. Table permissions are associated with web roles to provide appropriate access to users. 

## Page permissions

[Page permissions](page-security.md) that are associated with web roles to allow access can protect content and components on individual pages. 

## HTTPS headers

The cross-origin resource sharing (CORS) protocol consists of a set of headers that indicates whether a response can be shared with another domain. You can configure CORS support in Power Pages using the Portal Management app by adding and configuring the site settings. 

For more information, go to [HTTP headers](site-checker-security.md#http-headers).

## Security scan (preview)

[Security scan](security-scan.md) allows makers to perform thorough evaluations of their websites, detect common security threats, such as cross-site scripting (XSS) or the use of insecure libraries, and offers solutions for efficient resolution of these threats to improve security for your site.

## More website security

You can integrate Power Pages sites with any web application firewall infrastructure, such as [Azure Front Door](../configure/azure-front-door.md), to provide extra protection against common web application attacks. 

## Deep dive: architecture and security

The following white papers allow you to explore Power Pages architecture and security at a deeper level.

| White paper | Description | Date |
| - | - | - |
| [Power Pages Architecture white paper](/power-pages/guidance/white-papers/architecture) | This white paper provides a comprehensive view of the capabilities of the Power Pages platform. It describes the architectural elements that enable Power Pages to scale, offer high reliability and availability, and protect business data to offer enterprise-grade compliance and security. | October 2022 |
| [Power Pages Security white paper](/power-pages/guidance/white-papers/security) | This white paper describes how Power Pages offers enterprise-grade security and the tools and capabilities it offers for administrators and makers to harden security for their external applications. | October 2022 |

### See also

[Power Platform security](/power-platform/admin/security/)  
[Azure security](/azure/security/)  
[Intro to Power Pages security (video)](https://youtu.be/ojAll5jmxss?feature=shared)
