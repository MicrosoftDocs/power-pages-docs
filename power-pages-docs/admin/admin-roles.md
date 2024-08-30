---
title: Roles required for Power Pages administration
description: Learn about the roles and permissions required to do different administrative tasks for Power Pages.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 08/30/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: kkendrick
contributors:
    - neerajnandwana-msft
    - vamseedillimsft
    - nickdoelman
    - ProfessorKendrick
---

# Roles required for website administration

Different administrative tasks in Power Pages can be performed by members of different roles. The admin and security roles required to do these tasks vary depending on the affected area.

For example, some tasks might require the user to be a member of admin roles in [Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?preserve-view=true&view=o365-worldwide), and others might need membership to security roles in the [Microsoft Power Platform environment](/power-platform/admin/database-security).

In this article, you learn about the roles and permissions required to do different administrative tasks for Power Pages.

> [!IMPORTANT]
> To perform a task which requires an admin role, a user must be directly assigned to the required role. These roles are not inherited from security group membership or through privileged identity management (PIM).

## Required roles and permissions

The following table lists different administrative tasks for Power Pages, and the roles required to do that task. Users who are members of those roles can perform the corresponding task.

| Task | Required roles |
| - | - |
| [Add a custom domain name](add-custom-domain.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul>   |
| [Update the Dynamics 365 instance of an add-on website](update-dynamics365-instance.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Manage authentication key](manage-auth-key.md) | [Website app owner](#website-app-owner) and any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Convert an existing website to capacity-based model](convert-site.md) |  [Website app owner](#website-app-owner) and any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Convert a website from trial to production](convert-site.md#convert-a-website-from-trial-to-production) | [Website app owner](#website-app-owner) and any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Create a website](../getting-started/create-manage.md) | Required roles and permissions in Microsoft Power Platform (**all** are required):<ul><li>A user account with [Read-Write Access Mode](#read-write-access-mode).</li><li>[System administrator](#system-administrator) role. </li><li>[Permissions to register an app](/azure/active-directory/develop/howto-create-service-principal-portal#permissions-required-for-registering-an-app) in Microsoft Entra are required.</br><li>Is [website creation disabled](/power-apps/maker/portals/control-portal-creation) in the tenant? </li><ul><li> If **Yes**, in **addition** to the previously mentioned roles and permissions, a user also needs at least one of the following roles to create a website: [Dynamics 365 administrator](#dynamics-365-administrator), or [Power Platform administrator](#power-platform-administrator).</li></ul></ul>|
|[Edit a website](../getting-started/use-design-studio.md) |By default, Power Pages design studio only allows [system administrators](../admin/admin-roles.md#system-administrator) to edit websites.<br /><br />The [system customizer](../admin/admin-roles.md#system-customizer) role can be assigned and updated to allow other makers and developers to edit sites in your environment using design studio. You must [bypass custom business logic](/power-apps/developer/data-platform/bypass-custom-business-logic?tabs=sdk) and [adjust privileges](/power-platform/admin/security-roles-privileges). System customizers need organization access (Read, Write, Append, Create, Delete, and Append to) for the Note table.|
| [Download the public key of a website](get-public-key.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Import metadata translation](import-metadata-translation.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Delete a website](delete-website.md) | [Website app owner](#website-app-owner) and any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Update solutions](update-solution.md) | User account with [Read-Write Access Mode](#read-write-access-mode) and [System administrator](#system-administrator) |
| [View website error logs](view-portal-error-log.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| Restart a website | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Install Project Service Automation extension](../templates/dynamics-365-apps/integrate-project-service-automation.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Install Field Service extension](../templates/dynamics-365-apps/integrate-field-service.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Disable custom errors](view-portal-error-log.md#disable-custom-error) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Enable diagnostic logging](view-portal-error-log.md#enable-diagnostic-logging) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Change base URL](change-base-url.md) | [Website app owner](#website-app-owner) and any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> </ul> |
| [Update to Power Pages domain](/power-apps/maker/portals/admin/update-portal-domain) | [Website app owner](#website-app-owner) and any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Enable maintenance mode](enable-maintenance-mode.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Set up SSL](manage-custom-certificates.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Manage SSL certificates](add-custom-domain.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Set up SharePoint integration](../configure/manage-sharepoint-documents.md) | <ul><li> [Global administrator](#global-administrator) </li> </ul> |
| [Set up Power BI integration](set-up-power-bi-integration.md) | <ul><li> [Global administrator](#global-administrator)</li><li>See also: [Create security group and add to Power BI account](set-up-power-bi-integration.md#create-security-group-and-add-to-power-bi-account)</li></ul> |
| [Run site checker](site-checker.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Set up IP address restriction](ip-address-restrict.md) | Any one of the following roles: <ul> <li> [Website owner](#website-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> </ul> |
| [Configure content delivery network](../configure/configure-cdn.md) |Any one of the following roles: <ul><li>[System administrator](#system-administrator)</li><li>[Dynamics 365 administrator](#dynamics-365-administrator)</li><li>[Power Platform administrator](#power-platform-administrator)</li> </ul> |

## Manage membership of the required roles

This section describes how to manage the membership of the required roles in the preceding table for different kinds of administrative tasks in Power Pages.

### Dynamics 365 administrator

*Dynamics 365 administrator* is a Microsoft Power Platform service admin role. This role can do admin functions on Microsoft Power Platform because they have the system admin role.

To assign a user the Dynamics 365 administrator role, go to [Assign a service admin role to a user](/power-platform/admin/use-service-admin-role-manage-tenant#assign-a-service-admin-role-to-a-user).

### Global administrator

*Global administrator* is a Microsoft 365 admin role. A person who purchases the Microsoft business subscription is a global administrator. A global administrator has unlimited control over products in the subscription and access to most data.

To assign a user the global administrator role, go to [Assign admin roles in Microsoft 365](/microsoft-365/admin/add-users/assign-admin-roles?preserve-view=true&view=o365-worldwide).

More information: [About admin roles in Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?preserve-view=true&view=o365-worldwide)

### Website app owner

A *website app owner* is a user who owns the website [application registration](/azure/active-directory/develop/quickstart-register-app) in the [Azure portal](https://portal.azure.com).

#### To add an app owner for the website app in the Azure portal

1. Sign in to the [Azure portal](https://portal.azure.com).

1. Search for and select **Microsoft Entra ID**.

1. Under **Manage**, select **App registrations**.

1. Select the website app from the list of available applications. This application is called `Portals-<<website name>>`.

1. Under **Manage**, select **Owners**.

1. Select **Add owners**.

1. Select a user.

1. Select **Select**.

The user is added as an owner of the website app.

### Website owner

The *website owner* is the user who created the Power Pages website. This role can't be managed and can't be changed.

### Read-Write Access Mode

This is a user account in Microsoft Power Platform with **Access Mode** set to *Read-Write*. More information: [Create a Read-Write user account](/power-platform/admin/create-users-assign-online-security-roles#create-a-read-write-user-account)

### System administrator

*System administrator* is a Microsoft Power Platform security role. This role has full permissions to customize and administer a Microsoft Power Platform environment.

To assign a user the System administrator Power Platform role, go to [Configure user security to resources in an environment](/power-platform/admin/database-security).

### System customizer

*System customizer* is a Microsoft Power Platform security role. This role has full permissions to customize a Microsoft Power Platform environment.

To assign a user the System Customizer Power Platform role, go to [Configure user security to resources in an environment](/power-platform/admin/database-security).

### Power Platform administrator

*Power Platform administrator* is a Microsoft Power Platform service admin role. This role can perform admin functions on Microsoft Power Platform because they have the system admin role.

To assign a user the Power Platform administrator role, go to [Assign a service admin role to a user](/power-platform/admin/use-service-admin-role-manage-tenant#assign-a-service-admin-role-to-a-user).

### Limitations

The platform uses the Microsoft Graph service to retrieve role information. Currently, Microsoft Graph doesn't return these roles when assigned through a security group. Until this issue is resolved, ensure that roles are assigned directly to users rather than through a security group.

### Related information

[Use the admin center](admin-overview.md)  
[Portal Management app](../configure/portal-management-app.md)  
[Site settings](/power-apps/maker/portals/configure/configure-site-settings)
