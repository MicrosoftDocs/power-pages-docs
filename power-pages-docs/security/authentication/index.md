---
title: Overview of authentication in Power Pages
description: Learn about site user authentication in Microsoft Power Pages and review common identity providers.
ms.date: 09/18/2024
ms.topic: conceptual
author: nickdoelman
ms.author: kkendrick
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
ms.custom: bap-template
---

# Overview of authentication in Power Pages

You may want to limit access to your site's pages and data to specific users. You can configure [page permissions](../page-security.md) to protect specific pages. Power Pages uses [Microsoft Dataverse contact records](/power-apps/developer/data-platform/customer-entities-account-contact) to associate authenticated Power Pages site users.

To get more permissions than unauthenticated users have, users must be assigned to [web roles](../create-web-roles.md) that give them specific permissions on the site. Power Pages allows users to sign in with their choice of an external account based on [ASP.NET Identity](https://www.asp.net/identity). Users can also sign in using a local contact membership provider-based account, although we don't recommend it.

> [!NOTE]
> Users must have a unique email address. If two or more contact records&mdash;including deactivated contact records&mdash;have the same email address, the contacts can't authenticate on the website.

## Common identity providers

The following table lists common identity providers, the protocol you can use with the provider, and relevant documentation.

> [!IMPORTANT]
> Configuration information about common providers for protocols such as OpenID Connect and SAML 2.0 are given as examples. You can use the provider of your choice for the given protocol. Follow similar steps to configure your preferred provider.

| Provider | Protocol | Documentation |
|----------|----------|---------------|
| Microsoft Entra ID | OpenID Connect | [Configure an OpenID Connect provider with Microsoft Entra ID](openid-settings.md) |
| Microsoft Entra ID | SAML 2.0 | [Configure a SAML 2.0 provider with Microsoft Entra ID](saml2-settings-azure-ad.md) |
| Microsoft Entra ID | WS-Federation | [Configure a WS-Federation provider with Microsoft Entra ID](ws-federation-settings-azure-ad.md) |
| Microsoft Entra External ID | OpenID Connect | [Configure an OpenID Connect provider with Microsoft Entra External ID](entra-external-id.md) |
| Azure AD B2C | OpenID Connect | [Configure the Azure AD B2C provider](/power-apps/maker/portals/configure/configure-azure-ad-b2c-provider)<br/>[Configure the Azure AD B2C provider manually](/power-apps/maker/portals/configure/configure-azure-ad-b2c-provider-manual) |
| Azure Directory Federation Services (AD FS) | SAML 2.0 | [Configure a SAML 2.0 provider with AD FS](saml2-settings.md) |
| AD FS | WS-Federation | [AD FS with WS-Federation](ws-federation-settings.md)|
| Microsoft | OAuth 2.0 | [Configure the Microsoft provider](oauth2-microsoft.md) |
| LinkedIn | OAuth 2.0 | [Configure the LinkedIn provider](oauth2-linkedin.md) |
| Facebook | OAuth 2.0 | [Configure the Facebook provider](oauth2-facebook.md) |
| Google | OAuth 2.0 | [Configure the Google provider](/power-apps/maker/portals/configure/configure-oauth2-google) |
| Twitter | OAuth 2.0 | [Configure the Twitter provider](oauth2-twitter.md) |
| Local authentication<br />(not recommended) | Not applicable | [Local authentication](set-authentication-identity.md) |

## Migrate your website to a new identity provider

If you're already using an identity provider, you can [migrate your website to use a different one](migrate-identity-providers.md).

## Open registration

Power Pages administrators have several ways to control account sign-up. Open registration, the least restrictive option, allows a user to register an account by providing a user identity, invitation code, or valid email address, depending on the configuration. Both local and external accounts participate equally in the open registration workflow. Users can choose which type of account they want to register.

Users can select an external identity from a list of identity providers or create a local account with a user name and password. We don't recommend the local account option. If users select an external identity, they must sign in through their chosen identity provider to prove they own the external account. In either case, registration creates a contact record in the Dataverse environment and the user is immediately registered and authenticated on the Power Pages site.

With open registration enabled, users aren't required to provide an invitation code to complete the sign-up process.

### See also

[Customize the Azure AD B2C user interface](/power-apps/maker/portals/configure/azure-ad-b2c)  
[Configure an OAuth 2.0 provider](oauth2-provider.md)  
[Configure an OpenID Connect provider](openid-provider.md)  
[Configure a SAML 2.0 provider](saml2-provider.md)  
[Configure a WS-Federation provider](ws-federation-provider.md)