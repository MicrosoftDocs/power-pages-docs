---
title: Power Pages connectivity to a Microsoft Dataverse environment
description: Learn how Power Pages connects to a Microsoft Dataverse environment, connectivity architecture, and the authentication key used for connectivity.
author: dileepsinghmicrosoft

ms.topic: conceptual
ms.custom: 
ms.date: 04/03/2023
ms.subservice: 
ms.author: dileeps
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Power Pages connectivity to a Microsoft Dataverse Environment

Microsoft Dataverse is a key component for any Power Pages website. It acts as both metadata store for the website storing all website configuration like webpages, content snippets, site settings, user metadata as well as the data store for business data. This document describes how the application server hosting the website connects to a Dataverse organization.

To start with one of the core principles to remember is that an end user of Power Pages website is not a Dataverse user and Dataverse role based access control (RBAC) concepts doesn't apply to the end user on the Power Pages Website. All the users of Power Pages are stored in the Dataverse **contact** table and the data access of these users is controlled through [web roles](../security/create-web-roles.md) which is the role based access control layer for Power Pages users.

**Server to Server Connection**

Power Pages connects to Dataverse utilizing a server to server (S2S) connection. This S2S connection is established utilizing an Azure Active Directory application which is created in the customer's Azure Active Directory when a website is created.  
Each website has its own application which follows following naming convention (Portals – {{portalid}}). Different naming conventions have been used previously and may still be reflected in your Azure Active Directory. The Id of this application can also be found in the [Set up workspace](../configure/setup-workspace.md) for that website and can be used to find this application in Azure Active directory (in the application registration tab).  

> [!NOTE]
> - This application should not be modified or deleted as doing that may break the S2S connection between the website and Dataverse which can lead to website functionality being affected.
> - This application is also used for the default Azure AD Login provider on the website.

During the website creation process, an authentication key (X509 certificate) is also generated automatically and added to the Azure AD application as well as application server. This key allows the application server to get the required access token to authenticate to Dataverse.

> [!NOTE]
> This authentication key has an expiry of two years and should be updated every two years to ensure that website can connect to Dataverse. In order to update the key, refer to following documentation: [Manage website authentication key](manage-auth-key.md).

Following diagram describes how the end to end connection happens between the website and Dataverse.

:::image type="content" source="media/connectivity/website-dataverse-connectivity.png" alt-text="Dataverse to website connectivity.":::

**Integration with Dataverse User**

In order to establish the S2S connection, the Azure AD application created during site creation is also integrated with the Dataverse organization.

This integration is done utilizing the Dataverse **SYSTEM** user. For more information on the **SYSTEM** user, see [System and application users](/power-platform/admin/system-application-users). All the records created, updated, and deleted by a website user appears as being done by the **SYSTEM** user in Dataverse.


However, as part of recently announced changes , in the future sites will be utilizing [Dataverse Application user](https://learn.microsoft.com/en-us/power-platform/admin/manage-application-users) to connect to dataverse. This Application user would be created during creation of the website and will have following permissions

9.  OOB Security roles

<!-- -->

1.  Portal Application User

2.  Service Reader

3.  Service Writer

ii\) OOB Column Security profile

1.  System Administrator

/\*{Note} – OOB security roles and column security profiles should not be modified as that can lead to functional issues in your website\*/

Migration from "SYSTEM" user to "Application user" for existing websites is ongoing and will continue in CY 2023. Customers would be notified through M365 message center and emails to System admin of organization about the specific migration window for their existing website.  
In order to prepare for this migration, customers should review their customizations and ensure that no dependency on "SYSTEM" user is taken. While there are several type of these customizations which can exist, following are most common

1.  Using fetchxml (liquid tag) in website where a specific filter is added to filter record owned by "SYSTEM" user.  
    This type of fetchxml should rewritten to remove filter by "SYSTEM" user and rather proper table permissions/webroles should be used to secure the records.

2.  Dataverse processes (sync/async workflows) which are owned by "SYSTEM" user. This should be modified to be owned by application user.
