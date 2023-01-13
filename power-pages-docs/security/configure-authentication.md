---
title: Configure authentication in Power Pages
description: Learn how to configure authentication in Power Pages and review common identity providers.
author: nickdoelman

ms.topic: conceptual
ms.custom: 
ms.date: 1/13/2023
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Configure authentication

As you build your site, you may wish to control access both to pages and data to specific users. Power Pages uses Microsoft Dataverse contact records to associate to authenticated Power Pages site users.

:::image type="content" source="media/configure-authentication/login-page.png" alt-text="A Power Pages sign-in page.":::

Users must be assigned to web roles to gain permissions beyond unauthenticated users. To configure permissions for a web role, configure its webpage access and website access control rules. Power Pages allows users to sign in with their choice of an external account based on [ASP.NET Identity](https://www.asp.net/identity). Though not recommended, Power Pages also allows a local contact membership provider-based account for users to sign in.

> [!NOTE]
> Users must have a unique email address. If two or more contact records (including deactivated contact records) have the same email address, the contacts won't be able to authenticate on the portal.

## Common identity providers in Power Pages

The following table lists common identity providers, the protocol that can be used with the provider, and the relevant documentation.

> [!IMPORTANT]
> Configuration information about common providers for protocols such as OpenID Connect and SAML 2.0 are given as examples. You can use the provider of your choice for the given protocol, and follow similar steps to configure your preferred provider.

| **Provider** | **Protocol** | **Documentation** |
|-------------------------|-------------------------|-------------------------|
| Azure Active Directory (Azure AD) | OpenID Connect | Azure AD with OpenID Connect |
| Azure AD | SAML 2.0 | Azure AD with SAML 2.0 |
| Azure AD | WS-Federation | Azure AD with WS-Federation |
| Azure AD B2C | OpenID Connect | Azure AD B2C with OpenID Connect<br />Azure AD B2C with OpenID Connect (manual configuration)|
| Azure Directory Federation Services (AD FS) | SAML 2.0 | AD FS with SAML 2.0 |
| AD FS | WS-Federation | AD FS with WS-Federation |
| Microsoft | OAuth 2.0 | Microsoft |
| LinkedIn | OAuth 2.0 | LinkedIn |
| Facebook | OAuth 2.0 | Facebook |
| Google | OAuth 2.0 | Google |
| Twitter | OAuth 2.0 | Twitter <br />**Note**: Twitter authentication for portals is temporarily unavailable because of the compatibility issues. |
| Local authentication<br />(not recommended) | Not applicable | Local authentication |


## Migrate your website to a new identity provider

If you're already using an existing identity provider, you may wish to migrate your website to use another identity provider. More information: Migrate identity providers.

## Open registration

Power Pages administrators have several options for controlling account sign-up behavior. Open registration is the least restrictive sign-up configuration, where the website allows a user account to be registered by providing a user identity. Alternative configurations might require users to provide an invitation code or valid email address to register with the site. Whatever the registration configuration, both local and external accounts participate equally in the registration workflow. Users can choose which type of account they want to register.

Users can select an external identity from a list of identity providers during sign-up, or create a local account by providing a user name and password (not recommended). If an external identity is selected, the user is required to sign in through the chosen identity provider to prove that they own the external account. In either case, a new contact record is created in the Dataverse environment and the user is immediately registered and authenticated with the Power Pages site.

With open registration enabled, users aren't required to provide an invitation code to complete the sign-up process.

### Next steps

Get started with configuring the authentication for your portal

### See also

Configure the Azure AD B2C provider for portals 
Configure an OAuth 2.0 provider for portals
Configure an OpenID Connect provider for portals
Configure a SAML 2.0 provider for portals
Configure a WS-Federation provider for portals 
Authentication and user management in Power Apps portals
[Get started with configuring your portal authentication](/power-apps/maker/portals/configure/use-simplified-authentication-configuration)

