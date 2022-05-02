---
title: Power Pages security
description: Learn how to secure your Power Pages sites.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/29/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Power Pages security

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

An important consideration when building public facing web sites is to ensure that critical business information is only accessible by the correct stakeholders.

Power Pages has a robust security model to ensure that business information is properly protected. The following key components are used to provide and protect access in Power Pages:

- Authenticated user
- Web roles
- Table permissions
- Page permissions

## Authenticated users

Users can be provided access to your site through authentication. Power Pages users are represented by Microsoft Dataverse contact records. Power Pages can be integrated with a number of authentication providers such as Azure AD B2C, Microsoft, LinkedIn and others.

Authenticated users can then be assigned to web roles that will provide specific access to information on the site.

More information: [Configure Authentication](configure-portal-authentication.md)

## Web roles

Web roles can be created to allow users to perform any special actions or access any protected content and data on the site. Web roles link to users, table permissions, and page permissions. Since contacts can be assigned multiple web roles, they can be provided cumulative access to site resources.

All authenticated users (contacts) are automatically assigned to the **Authenticated Users** web role.

A site can be visited by anonymous users (unauthenticated) and given access to assets through the **Anonymous Users** web role.

More information: [Configure web roles](create-web-roles.md)

## Table permissions

Accessing Dataverse information through [lists](../getting-started/add-list.md), [forms](../getting-started/add-form.md), [Liquid](../configure/liquid-overview.md) and the [Web API](../configure/web-api-overview.md) are by default protected by **Table permissions**. You can configure table permissions to allow different levels of access and privileges to Dataverse records. Table permissions are associated to web roles to provide appropriate access to users.

More information: [Configure table permissions](table-permissions.md)

## Page permissions

Individual pages containing content or other components can also be protected by configuring page permissions that are associated with web roles to allow access.

More information: [Page permissions](page-security.md)

## Site Security

Power Pages provides features to ensure your sites stay secure: 

- [Azure Front Door](/power-apps/maker/portals/azure-front-door)


## See Also


[Azure security](/azure/security/)