---
title: Power Pages connectivity to a Microsoft Dataverse
description: Learn how Power Pages connects to a Power Platform environment with Dataverse, connectivity architecture, and the authentication key used for connectivity.
ms.topic: concept-article
ms.custom: 
ms.date: 04/11/2023
ms.subservice: 
ms.author: pudupa
author: PramithaU
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---

# Power Pages connectivity to a Microsoft Dataverse

Microsoft Dataverse is a key component for any Power Pages website. It acts as both metadata store for the website storing all website configuration like webpages, content snippets, site settings, user metadata and the data store for business data. This document describes how the application server hosting the website connects to a Power Platform environment with Dataverse.

To start with one of the core principles to remember is that an end user of Power Pages website isn't a Dataverse user, and Dataverse role based access control concepts doesn't apply to the end user on the Power Pages website. All the users of Power Pages are stored in the Dataverse **contact** table and the data access of these users is controlled through [web roles](../security/create-web-roles.md) which is the role based access control layer for Power Pages users.

## Server to Server Connection

Power Pages connects to Dataverse utilizing a server to server (S2S) connection. This S2S connection is established utilizing a Microsoft Entra application that is created in the customer's Microsoft Entra when a website is created.  
Each website has its own application that follows following naming convention (Portals – {{portalid}}). Different naming conventions have been used previously and may still be reflected in your Microsoft Entra. The ID of this application can also be found in the [Set up workspace](../configure/setup-workspace.md) for that website and can be used to find this application in Microsoft Entra (in the application registration tab).  

> [!NOTE]
> - This application should not be modified or deleted as doing that may break the S2S connection between the website and Dataverse which can lead to website functionality being affected.
> - This application is also used for the default Microsoft Entra Login provider on the website.

During the website creation process, an authentication key (X509 certificate) is also generated automatically and added to the Microsoft Entra application and application server. This key allows the application server to get the required access token to authenticate to Dataverse.

> [!NOTE]
> This authentication key has an expiry of two years and should be updated every two years to ensure that website can connect to Dataverse. In order to update the key, refer to following documentation: [Manage website authentication key](manage-auth-key.md).

Following diagram describes how the end to end connection happens between the website and Dataverse.

:::image type="content" source="media/connectivity/website-dataverse-connectivity.png" alt-text="Dataverse to website connectivity.":::

## Integration with Dataverse

In order to establish the S2S connection, the Microsoft Entra application created during site creation is also integrated with the Dataverse organization.

Depending on when the site was created, the connection is established using the Dataverse **SYSTEM** user or a **Dataverse application user**.

For more information on the **SYSTEM** user, see [System and application users](/power-platform/admin/system-application-users). All the records created, updated, and deleted by a website user appears as being done by the **SYSTEM** user in Dataverse.

Going forward, sites will be utilizing the [Dataverse Application user](/power-platform/admin/manage-application-users) to connect to Dataverse. You'll be able to view the application user by going to the Power Platform admin center, selecting the environment, and in the **Access** section, selecting the **S2S apps**. The application user will be in the format `# Portals-<<site name>>`.

:::image type="content" source="media/connectivity/application-user.png" alt-text="Application user.":::
 
The application user would be created during creation of the website and will have following permissions:

- Dataverse security roles
    - Portal Application User
    - Service Deleter
    - Service Writer

- Column Security profile
    - System Administrator

> [!WARNING]
> Security roles and column security profiles should not be modified as that can lead to functional issues in your website.

## Migration to application user

Migration from **SYSTEM** user to **application user** for existing websites is ongoing and will continue in 2023. Customers will be notified through the [Microsoft 365 message center](/microsoft-365/admin/manage/message-center) and emails to the system admin of an organization about the specific migration window for their existing website.  

In order to prepare for this migration, customers should review their customizations and ensure that no dependency on **SYSTEM** user is taken. 

While there are several types of these customizations that can exist, following are most common:

- Using the [fetchxml Liquid tag](../configure/liquid//template-tags.md#fetchxml) in website where a specific filter is added to filter record owned by **SYSTEM** user.  
    - This type of fetchxml should be rewritten to remove filter by the **SYSTEM** user and rather proper [table permissions](../security/table-permissions.md) and [webroles](../security/create-web-roles.md) should be used to secure the records.

- Dataverse processes such as [Dataverse real-time workflows](/power-apps/maker/data-platform/overview-realtime-workflows) which are owned by the **SYSTEM** user. The workflows should be modified to be owned by the application user.

## See Also
- [Power Pages lifecycle](lifecycle.md)
- [Power Pages architecture](architecture.md)
