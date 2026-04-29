---
title: Identity provisioning in Power Pages
description: Learn how Power Pages uses a platform-managed identity model to provision and operate sites securely without requiring manual Microsoft Entra app registrations or certificate management.
ms.date: 04/29/2026
ms.topic: conceptual
author: smurkute
ms.author: smurkute
ms.reviewer: danamartens
contributors:
ms.custom:
  - bap-template
---

# Identity provisioning in Power Pages

Power Pages uses a platform-managed identity model to provision and operate sites securely. With this model, Power Pages creates and manages the identity required for a site to authenticate with Microsoft Dataverse and other Power Platform services.

For new sites, makers and administrators no longer need to create, configure, or maintain Microsoft Entra (Azure AD) app registrations, manage certificates, or rotate authentication keys. These responsibilities are handled by the platform. This approach improves security and reliability by reducing required privileges, removing user-owned identity artifacts, and eliminating operational overhead.

## Site identity for new Power Pages sites

Previously, creating a Power Pages site could require Microsoft Entra app registration permissions because the site's application was registered under a maker's or administrator's identity. This could lead to provisioning failures, elevated privilege requirements, ongoing operational overhead, and can make the site inaccessible if the authentication key isn't renewed in time.

Now Power Pages sites use the platform-managed identity model by default. During site creation, Power Pages automatically provisions a Microsoft-managed identity, using a [Federated Identity Credential](/graph/api/resources/federatedidentitycredentials-overview?view=graph-rest-1.0&preserve-view=true) (FIC) on the Microsoft Entra application instead of an X.509 certificate (user-based).

With FIC, the Dataverse platform issues a token that is exchanged with Microsoft Entra ID via workload identity federation, eliminating the certificate entirely. This removes the need for periodic authentication key renewal, as there's no certificate to expire.

### For makers

- Microsoft Entra app registration permissions aren't required to create a site.
- Site creation experience is unchanged, but it's more reliable and less likely to fail due to missing permissions.
- No additional identity setup is required in Microsoft Entra.

### For administrators

- New sites don't create user-owned app registrations.
- Manual management of certificates or authentication keys isn't required.
- Identity lifecycle management is centralized in the platform. Credential lifecycle and security, including certificate and authentication key renewal, is handled automatically by the Power Pages platform. No manual renewal actions are required.

## Environment requirements and provisioning behavior

The identity model used during site creation depends on the **Power Pages Core package version** installed in the environment.

Environments running **Power Pages Core package version 1.0.2409.xx or later** use the platform-managed identity model for new site creation. No additional configuration is required in these environments. Earlier package versions fall back to the previous user-based identity model.

If site creation fails with the error *You don't have permission to create Azure Active Directory*, use one of the following options:

- **Update the Power Pages Core package (recommended).** Updating to version 1.0.2409.xx or later enables new site creation using the platform-managed identity model.
- **Grant Microsoft Entra app registration permissions (previous model).** This allows site creation by using the previous user-based identity model, where the site's Microsoft Entra application is registered under a maker's or administrator's identity.

> [!NOTE]
> The workaround of granting Microsoft Entra app registration permissions requires elevated Microsoft Entra permissions and ongoing manual certificate and authentication key management. It is suggested as a temporary option when a package update is not immediately possible.

## Existing Power Pages sites

Sites created before the platform-managed identity model continue to use the previous user-based identity model.

These sites continue to function without change. Site behavior and end-user access aren't affected. No immediate action is required from makers or administrators for existing sites.

The Power Pages team is working on a future approach to support migration of existing sites. When available, guidance will be published in Microsoft Learn.

## Summary

- New Power Pages sites use the platform-managed identity model by default.
- Microsoft Entra app registration permissions and manual credential management aren't required for new sites.
- Credential lifecycle and security are handled automatically by Power Pages.
- Power Pages Core package version determines which provisioning model is used.
- Existing sites continue to operate without disruption, with future migration guidance to be shared through Microsoft Learn.

### See also

[Power Pages security](power-pages-security.md)  
[Manage your site's authentication key](../admin/manage-auth-key.md)