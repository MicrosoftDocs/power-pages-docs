---
title: Configure user authentication for an agent
description: 'User authentication for agents: Learn how to set up single sign-on, token passthrough, and token-based authentication for Power Pages agents.'
author: DanaMartens
contributors: null
ms.topic: how-to
ms.date: 03/05/2026
ms.author: dmartens
ms.reviewer: dmartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:06/20/2025
---
# Configure user authentication for an agent

Power Pages supports multiple authentication options so you can control how users access agents on your site. This article describes how to set up agent authentication, including single sign-on (SSO), token passthrough, and token-based authentication, to provide a seamless and secure sign-in experience.

When you associate an agent with Power Pages, your site can use SSO so users can access the agent without signing in again.


## No authentication

Users can access the agent without authentication. This option is the default setting when you create an agent from a form.

> [!NOTE]
> Power Pages doesn't support [Authenticate with Microsoft](/microsoft-copilot-studio/configuration-end-user-authentication#authenticate-with-microsoft) user authentication.

## Authenticate manually

Power Pages supports single sign-on for all authentication providers available in Copilot Studio.

### Authenticate with Microsoft Entra ID

Select this service provider if you want the agent to be accessible only to site users authenticated through Microsoft Entra ID. For detailed configuration, see [Configure Microsoft Entra ID with Power Pages](configure-entra-id-authentication-for-agent.md).

### Authenticate with Generic OAuth 2

Use this service provider when you configure the Power Pages site with an identity provider that complies with the [OAuth 2 standard](/entra/identity-platform/v2-oauth2-auth-code-flow). The site can support authenticated or unauthenticated users and multiple OAuth 2.0 compliant identity providers. Configure agent authentication by using token passthrough or token-based authentication to match the Power Pages authentication setup.

#### Token passthrough authentication

The agent relies on Power Pages’ authentication service. When you configure the agent by using the implicit flow, the agent supports all identity providers that you set up in the Power Pages site, including unauthenticated users. 

> [!NOTE]
> You can't test agents that you configure with token passthrough authentication directly within Microsoft Copilot Studio, as they require sign-in through the Power Pages site.

To configure token [passthrough authentication](/microsoft-copilot-studio/configure-sso-3p), update all values as **placeholder**.

To enable this setup, add the following site settings:

| Authentication/BearerAuthentication/Enabled | True |
| :------------------------------------------ | :--- |

#### Token based authentication

In this method, Power Pages passes the authenticated user’s token to the Copilot Studio. Microsoft Copilot Studio handles authentication. This setup allows you to test the agent directly within Copilot Studio.

For detailed configuration steps, see the [*Security Configuration*](/microsoft-copilot-studio/configuration-end-user-authentication#authenticate-manually) documentation in Copilot Studio.

To enable this setup, add the following site settings:

   | Setting                                             | Value      |
   | :-------------------------------------------------- | :--------- |
   | Authentication/ApplicationCookie/SlidingExpiration  | True       |
   | Authentication/BearerAuthentication/Enabled         | True       |
   | Authentication/BearerAuthentication/Provider        | Provider name  <br>Provider name extracted from existing settings for the provider  <br>Authentication/OpenIdConnect/{ProviderName}/Issuer  <br>For example, if the setting for Azure AD had **Authentication/OpenIdConnect/AzureAD/Issuer, then AzureAD is the provider** |

## Related information

- [Add an agent - overview](add-agent-overview.md)
- [Add an agent to your Power Pages site](enable-agent.md)
- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
