---
title: Overview of authentication in Power Pages
description: Learn how to configure authentication in Power Pages and review common identity providers.
author: nickdoelman

ms.topic: conceptual
ms.custom: 
ms.date: 2/16/2023
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Overview of authentication in Power Pages

As you build your site, you may wish to control access both to pages and data to specific users. Power Pages uses [Microsoft Dataverse contact records](/power-apps/developer/data-platform/customer-entities-account-contact) to associate to authenticated Power Pages site users.

Users must be assigned to web roles to gain permissions beyond unauthenticated users. To configure permissions for [web roles](../create-web-roles.md), configure [page permissions](../page-permissions.md). Power Pages allows users to sign in with their choice of an external account based on [ASP.NET Identity](https://www.asp.net/identity). Though not recommended, Power Pages also allows a local contact membership provider-based account for users to sign in.

> [!NOTE]
> Users must have a unique email address. If two or more contact records (including deactivated contact records) have the same email address, the contacts won't be able to authenticate on the portal.

## Common identity providers

The following table lists common identity providers, the protocol that can be used with the provider, and the relevant documentation.

> [!IMPORTANT]
> Configuration information about common providers for protocols such as OpenID Connect and SAML 2.0 are given as examples. You can use the provider of your choice for the given protocol, and follow similar steps to configure your preferred provider.

| **Provider** | **Protocol** | **Documentation** |
|-------------------------|-------------------------|-------------------------|
| Azure Active Directory (Azure AD) | OpenID Connect | [Configure an OpenID Connect provider with Azure AD](openid-settings.md)|
| Azure AD | SAML 2.0 | [Configure a SAML 2.0 provider with Azure AD](saml2-settings-azure-ad.md)|
| Azure AD | WS-Federation | [Configure a WS-Federation provider with Azure AD](ws-federation-settings-azure-ad.md)|
| Azure AD B2C | OpenID Connect |[Configure the Azure Active Directory B2C provider (using interface in preview)](azure-ad-b2c-provider.md)<br />[Configure the Azure Active Directory B2C provider manually](azure-ad-b2c-provider-manual.md)|
| Azure Directory Federation Services (AD FS) | SAML 2.0 | [Configure a SAML 2.0 provider with AD FS](saml2-settings.md)|
| AD FS | WS-Federation | [AD FS with WS-Federation](ws-federation-settings.md)|
| Microsoft | OAuth 2.0 | [Configure the Microsoft provider for Power Pages](oauth2-microsoft.md)|
| LinkedIn | OAuth 2.0 | [Configure the LinkedIn provider for Power Pages](oauth2-linkedin.md)|
| Facebook | OAuth 2.0 | [Configure the Facebook provider for portals](oauth2-facebook.md)|
| Google | OAuth 2.0 | [Configure the Google provider for portals](oauth2-google.md)|
| Twitter | OAuth 2.0 | [Configure the Twitter provider for portals](oauth2-twitter.md)|
| Local authentication<br />(not recommended) | Not applicable | [Local authentication](set-authentication-identity.md) |


## Migrate your website to a new identity provider

If you're already using an existing identity provider, you may wish to migrate your website to use another identity provider. More information: [Migrate identity providers to Azure AD B2C](migrate-identity-providers.md)

## Open registration

Power Pages administrators have several options for controlling account sign-up behavior. Open registration is the least restrictive sign-up configuration, where the website allows a user account to be registered by providing a user identity. Alternative configurations might require users to provide an invitation code or valid email address to register with the site. Whatever the registration configuration, both local and external accounts participate equally in the registration workflow. Users can choose which type of account they want to register.

Users can select an external identity from a list of identity providers during sign-up, or create a local account by providing a user name and password (not recommended). If an external identity is selected, the user is required to sign in through the chosen identity provider to prove that they own the external account. In either case, a new contact record is created in the Dataverse environment and the user is immediately registered and authenticated with the Power Pages site.

With open registration enabled, users aren't required to provide an invitation code to complete the sign-up process.

## Next Steps


### See also

[Customize the Azure AD B2C user interface for portals](azure-ad-b2c.md)
[Configure an OAuth 2.0 provider for Power Pages](oauth2-provider.md)
[Configure an OpenID Connect provider for Power Pages](openid-provider.md)
[Configure a SAML 2.0 provider for Power Pages](saml2-provider.md)
[Configure a WS-Federation provider for Power Pages](ws-federation-provider.md)

