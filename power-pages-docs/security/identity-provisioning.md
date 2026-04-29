---
title: Identity provisioning in Power Pages
description: Learn how Power Pages uses a platform-managed identity model to provision and operate sites securely without requiring manual Microsoft Entra app registrations or certificate management.
ms.date: 04/29/2026
ms.topic: conceptual
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
contributors:
ms.custom:
  - bap-template
---

# Identity provisioning in Power Pages

Power Pages uses a platform-managed identity model to provision and operate sites securely. With this model, Power Pages creates and manages the identity required for a site to authenticate with Microsoft Dataverse and other Power Platform services.

For new sites, makers and administrators no longer need to create, configure, or maintain Microsoft Entra (Azure AD) app registrations, manage certificates, or rotate authentication keys. The platform handles these responsibilities. This approach improves security and reliability by reducing required privileges, removing user-owned identity artifacts, and eliminating operational overhead.

## Site identity for new Power Pages sites

Previously, creating a Power Pages site could require Microsoft Entra app registration permissions because the site's application was registered under a maker's or administrator's identity. This requirement could lead to provisioning failures, elevated privilege requirements, ongoing operational overhead, and can make the site inaccessible if the authentication key isn't renewed in time.

Now Power Pages sites use the platform-managed identity model by default. During site creation, Power Pages automatically provisions a Microsoft-managed identity, using a [Federated Identity Credential](/graph/api/resources/federatedidentitycredentials-overview?view=graph-rest-1.0&preserve-view=true) (FIC) on the Microsoft Entra application instead of an X.509 certificate (user-based).

With FIC, the Dataverse platform issues a token that is exchanged with Microsoft Entra ID via workload identity federation, eliminating the certificate entirely. This approach removes the need for periodic authentication key renewal, as there's no certificate to expire.

### For makers

- Microsoft Entra app registration permissions aren't required to create a site.
- Site creation experience is unchanged, but it's more reliable and less likely to fail due to missing permissions.

### For administrators

- New sites don't create user-owned app registrations.
- Manual management of certificates or authentication keys isn't required.
- The platform centralizes identity lifecycle management. Credential lifecycle and security, including certificate and authentication key renewal, is handled automatically by the Power Pages platform. No manual renewal actions are required.

## Environment requirements and provisioning behavior

The identity model used during site creation depends on the **Power Pages Core package version** installed in the environment.

Environments running **Power Pages Core package version 1.0.2409.xx or later** use the platform-managed identity model for new site creation. No extra configuration is required in these environments. Earlier package versions use the previous user-based identity model.

If site creation fails with the error *You don't have permission to create Azure Active Directory*, use one of the following options:

- **Update the Power Pages Core package (recommended)**: Updating to version 1.0.2409.xx or later enables new site creation by using the platform-managed identity model.
- **Grant Microsoft Entra app registration permissions (previous model)**: This option allows site creation by using the previous user-based identity model, where the site's Microsoft Entra application is registered under a maker's or administrator's identity.

> [!NOTE]
> The workaround of granting Microsoft Entra app registration permissions requires elevated Microsoft Entra permissions and ongoing manual certificate and authentication key management. Consider it as a temporary option when a package update isn't immediately possible.

## Existing Power Pages sites

Sites created before the platform-managed identity model continue to use the previous user-based identity model.

These sites continue to function without change. Site behavior and end-user access aren't affected. Makers or administrators don't need to take any immediate action for existing sites.


## Summary

- New Power Pages sites use the platform-managed identity model by default.
- Microsoft Entra app registration permissions and manual credential management aren't required for new sites.
- Power Pages automatically handles credential lifecycle and security.
- The Power Pages Core package version determines which provisioning model is used.
- Existing sites continue to operate without disruption, and future migration guidance will be shared through Microsoft Learn.

### See also

[Power Pages security](power-pages-security.md)  
[Manage your site's authentication key](../admin/manage-auth-key.md)  
[Admin roles required for Power Pages site administration](../admin/admin-roles.md)  
[Create and manage Power Pages sites](../getting-started/create-manage.md)  
[Known issues](../known-issues.md)  