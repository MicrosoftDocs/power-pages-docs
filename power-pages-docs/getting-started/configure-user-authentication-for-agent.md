---
title: Configure user authentication for an agent
description: 'User authentication for agents: Learn how to set up single sign-on, token passthrough, and token-based authentication for Power Pages agents.'
author: DanaMartens
contributors: null
ms.topic: how-to
ms.date: 02/23/2026
ms.author: dmartens
ms.reviewer: dmartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:06/20/2025
---
# Configure user authentication for an agent

Power Pages supports multiple authentication methods to help you control how users access agents on your site. This article explains how to configure user authentication for agents, including single sign-on (SSO), token passthrough, and token-based authentication. Use these options to provide a seamless and secure sign-in experience for your users.

When you associate an agent with Power Pages, the site lets users use single sign-on (SSO), so they don't need to sign in separately to use the agent. 

## No Authentication

   The agent can be accessed without requiring user authentication. This option is the default setting when an agent is created from a form.

    > [!NOTE]
    > Power Pages doesn't support [Authenticate with Microsoft](/microsoft-copilot-studio/configuration-end-user-authentication#authenticate-with-microsoft) user authentication.


## Authenticate manually

Power Pages supports single sign-on for all authentication providers available in Copilot Studio.

### Authenticate with Microsoft Entra ID

Select this service provider if the agent is intended to be accessible only to site users authenticated through Microsoft Entra ID. For detailed configuration refer [Configure Microsoft ENtra ID with Power Pages](). 

### Authenticate with Generic OAuth 2

Use this service provider when the Power Pages site is configured with an identity provider that complies with the [OAuth 2 standard](/entra/identity-platform/v2-oauth2-auth-code-flow). The site can support authenticated or unauthenticated users and multiple OAuth 2.0 compliant identity providers. Configure agent authentication using token passthrough or token based authentication to match the Power Pages authentication setup.

1. **Token passthrough Authentication**

    The agent relies on Power Pages’ authentication service. When configured with the implicit flow, the agent supports all identity providers set up in the Power Pages site including un-authenticated users. 

    > [!NOTE]
    > Agents configured with token passthrough authentication can't be tested directly within of Microsoft Copilot Studio, as they require sign-in through the Power Pages site.

    To configure token [passthrough authentication](/microsoft-copilot-studio/configure-sso-3p), update all values as **placeholder**

     To enable this setup, add the following site settings:
   
    | Authentication/BearerAuthentication/Enabled | True |
    | :------------------------------------------ | :--- |

1. **Token based authentication**

    In this method, Power Pages passes the authenticated user’s token to the Copilot Studio. Microsoft Copilot Studio handles authentication. This setup allows the agent to be tested directly within Copilot Studio.

    For detailed configuration steps, refer to the [*Security Configuration*](/microsoft-copilot-studio/configuration-end-user-authentication#authenticate-manually) documentation in Copilot Studio.

    To enable this setup, add the following site settings:

    | Setting                                             | Value      |
    | :-------------------------------------------------- | :--------- |
    | Authentication/ApplicationCookie/SlidingExpiration   | True       |
    | Authentication/BearerAuthentication/Enabled         | True       |
    | Authentication/BearerAuthentication/Provider        | Provider name  <br>Provider name extracted from existing settings for the provider  <br>Authentication/OpenIdConnect/{ProviderName}/Issuer  <br>For example, if the setting for Azure AD had **Authentication/OpenIdConnect/AzureAD/Issuer, then AzureAD is the provider** |

## Related information

- [Add an agent - overview](add-agent-overview.md)
- [Add an agent to your Power Pages site](enable-agent.md)
- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
