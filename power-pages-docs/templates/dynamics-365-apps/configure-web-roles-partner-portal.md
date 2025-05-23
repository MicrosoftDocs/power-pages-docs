---
title: Configure web roles for a partner relationship management (PRM) site
description: Learn how to add web roles for a partner site.
author: murugesh1985
ms.topic: how-to
ms.custom: 
ms.date: 04/10/2023
ms.subservice: 
ms.author: murugeshs
ms.reviewer: danamartens
contributors:
    - dileepsinghmicrosoft
---

# Configure web roles for a partner relationship management (PRM) site

Web roles for the Partner Relationship Management (PRM) site grant specific access to the different areas of the site. By assigning the appropriate roles, you can grant your primary partner contacts the right permissions to manage their team members and streamline their processes.

- **Partner administrator**: Partner administrators are contacts who serve as the primary contact for a partner account. They are responsible for adding and deactivating their team members and for any administrative activities related to their partner account information. Partner administrators can:
  - View, accept, and reject all distributed opportunities
  - View, manage, and perform actions on all managed opportunities
  - Manage partner account information, associated partner contacts, and their web roles
  - Manage partner contact roles Create and edit customer accounts
  - Create and edit customer contacts
  - Create and edit new opportunities

- **Partner manager**: Partner managers are contacts who manage opportunities distributed by the parent company. They are responsible for accepting or rejecting distributed opportunities and sharing accepted opportunities with team members. Partner managers can:
  - View, accept, and reject all distributed opportunities
  - View, manage, and perform actions on all managed opportunities
  - Manage partner account information
  - Create and edit customer accounts
  - Create and edit customer contacts
  - Create and edit new opportunities

- **Partner seller**: Partner sellers are contacts who manage and perform actions on opportunities. They can view and perform actions on opportunities that are shared with them, but will not be able to view opportunities that they are not associated with. Partner Sellers can:
  - View, manage, and perform actions on managed opportunities that have been shared with them
  - Create and edit customer accounts
  - Create and edit customer contacts
  - Create and edit new opportunities

## Create a partner account on a PRM site
You can use partner accounts to keep track of your various partners. We recommend creating a separate account for each partner so that you can manage each partner organization separately. To create a partner account, 

1. Go to **Sales &gt; Accounts** (within Microsoft Dataverse - Account Form).
2. Choose **New** and fill in your information.
3. In the **Partner Information** tab, use the **Classification** field and select the Partner.
4. Select **Save**.

## Associate partner contacts with an account

Contacts become partner contacts when they are associated with a partner account. To associate a contact with a partner account when creating or editing a contact, enter the name of a partner account in the Account Name field.

## Assign a permission set to a web role for sites
Website Access Permissions is a permission set, associated with a web role, that permits front-side editing of the various content managed elements within the site other than just webpages. The permission settings determine which components can be managed in the site. More Information: [Configure web roles](../../security/create-web-roles.md)  


|             Name             |                                                                                                                   Description                                                                                                                   |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Manage Content Snippets    |                          Allows the editing of Snippet controls. More Information: [Content snippets](../../configure/content-snippets.md)                        |
|     Manage Site Markers      |    Allows the editing of hyperlinks that use site markers.                                                                                      |
|     Manage Web Link Sets     | Allows the editing of web link sets, including adding and removing web links from a web link set. More Information: [Manage web links](/power-apps/maker/portals/configure/manage-web-links) |
| Preview Unpublished Entities |                                                                            Allows the viewing of site-exposed tables that have a publishing state of **Draft**.                                                                             |
|                              |                                                                                                                                                                                                                                                 |

To add website access permission to a web role, just create a new Website Access entity, give it the permission set you want, name it, associate with the website in question, save, and then associate it with the web role(s) you desire.

### See also

- [Provide access to external audiences](../../security/external-access.md)
- [Assign table permissions](../../security/assign-table-permissions.md)
- [Configure web roles](../../security/create-web-roles.md) 
