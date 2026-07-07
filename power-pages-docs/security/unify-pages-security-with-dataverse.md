---
title: Enable enhanced authorization (preview)
description: Learn how to enable enhanced authorization in Power Pages to align with Dataverse's native security model and manage secure access to tables and records.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 07/06/2026
ms.topic: concept-article
---

# Enable enhanced authorization (preview) 

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Web roles in Power Pages provide a way to manage secure access to Dataverse tables for specific site users.   
In the standard authorization model, Power Pages evaluates table and record permissions after data retrieval from Dataverse by using the Power Pages application user that runs with elevated privilege, which can introduce additional performance overhead due to multiple roundtrips for permission evaluation and also limit transparency, as customers do not have native visibility or auditability into requests executed on behalf of end users. 

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

When you enable enhanced authorization, permission evaluation shifts directly to Dataverse. In this model, Dataverse evaluates permissions based on the site user's roles and returns only the records the user is allowed to access. This change removes the extra permission checking layer at Power Pages and ensures alignment with Dataverse's native security model. 

> [!Important]
> Dataverse operations execute on behalf of the site user by using impersonation rather than the application user. If any plugin is registered, it runs as the calling user unless explicitly configured otherwise. 

## How enhanced authorization works

When enhanced authorization is enabled, Power Pages continues to use site users (contacts) and web roles to define access. These constructs are mapped to Dataverse security constructs so that access can be enforced directly at Dataverse.

> [!NOTE]
> When auditing is enabled on a Dataverse table, any operation performed from the Power Pages site tracks under the respective site user. 

### Site users and system users

- Each user accessing the site is represented as a contact record in Dataverse.
- With enhanced authorization enabled, each contact is mapped to a corresponding system user in Dataverse. Multiple system user records can be created for a single contact if the same user has access to more than one site.
- This system user representation is used to evaluate permissions during data access.

> [!Note]
> When enhanced authorization is enabled, Power Pages creates system user for each contact record to enable authorization in Dataverse. These system users are managed internally, don't provide direct access to Dataverse, and don't require additional licensing. Access continues to be governed by Power Pages licensing. 

### Web roles and security roles

- Makers define access using web roles in Power Pages.
- With enhanced authorization:
  - Each web role is associated with a corresponding Dataverse security role
  - Permissions defined in web roles (such as table and column access) are reflected in these security roles

This mapping ensures that existing role definitions continue to work while enabling enforcement through Dataverse.

> [!Note]
> [Column level permissions](column-permissions.md) that you configure in the Power Pages for Web API are bypassed, and Dataverse column security profiles are used instead. 

### User registration and setup

When a user registers or accesses the site:
- A contact record is created or updated
- A corresponding system user representation is created or associated for that site
- The user is assigned one or more web roles, which determine the security roles applied

This process is handled automatically and doesn't require additional configuration.

## Enable enhanced authorization 

### Prerequisites

To enable enhanced authorization, ensure that your environment is running the latest supported versions of the required platform solutions:
- Power Pages Core: version 1.1.2605.258 or later
- Dataverse Base Portal: version 9.3.2605.265 or later

To verify the installed versions and upgrade the solutions if needed, see [Update the Power Pages solution](../admin/update-solution.md).


Follow these steps to enable the enhanced authorization model: 

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) and select the environment. 

1. Open the Power Pages Admin center by selecting the ellipsis (...) next to the site and selecting **Admin center** in the drop-down. 

1. Select **Edit** next to the site details. 

1. Select the **Enable Enhanced Authorization** check box and save. 
:::image type="content" source="media/unify-pages/enhanced-authorization.png" alt-text="Screenshot of admin center page showing how to enable enhanced authorization":::


### See also

[Column security profile (preview)](column-security-profile.md)  
[Implement privacy protections](../configure/implement-privacy.md)  
[Configuring table permissions](table-permissions.md)
