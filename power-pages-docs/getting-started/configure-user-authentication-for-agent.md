---
title: Configure user authentication for an agent
description: 'User authentication for agents: Learn how to set up single sign-on, token passthrough, and token-based authentication for Power Pages agents.'
author: DanaMartens
contributors: null
ms.topic: how-to
ms.date: 06/20/2025
ms.author: dmartens
ms.reviewer: dmartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:06/20/2025
---
# Configure user authentication for an agent

Power Pages supports multiple authentication methods to help you control how users access agents on your site. This article explains how to configure user authentication for agents, including single sign-on (SSO), token passthrough, and token-based authentication. Use these options to provide a seamless and secure sign-in experience for your users.

## Authentication options

When you associate an agent with Power Pages, the site lets users use single sign-on (SSO), so they don't need to sign in separately to use the agent. Power Pages supports these authentication types:

1. **No Authentication**

    The agent can be accessed without requiring user authentication. This option is the default setting when an agent is created from a form.

1. **Token passthrough Authentication**

    The agent relies on Power Pages’ authentication service. When configured with the implicit flow, the agent supports all identity providers set up in the Power Pages site.

    > [!NOTE]
    > Agents configured with token passthrough authentication can't be tested directly within of Microsoft Copilot Studio, as they require sign-in through the Power Pages site.

    To configure token [passthrough authentication](/microsoft-copilot-studio/configure-sso-3p), Select service provider as **Generic OAuth 2** and update all other values as **placeholder**

    | Authentication/BearerAuthentication/Enabled | True |
    | :------------------------------------------ | :--- |

1. **Token based authentication**

    In this method, Power Pages passes the authenticated user’s token to the Copilot Studio. Microsoft Copilot Studio handles authentication. This setup allows the agent to be tested directly within Copilot Studio.

    Select **Generic OAuth 2** as the service provider. Power Pages doesn't currently support other service providers.

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
