---
title: Add an agent from the setup workspace
description: Add an agent to Power Pages for instant, AI-powered help. Improve user experience and resolve questions faster with easy setup instructions.
ms.topic: how-to
ms.date: 03/05/2026
ms.update-cycle: 180-days
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection:
  - bap-ai-copilot
contributors:
  - nageshbhat-msft
  - DanaMartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:09/07/2023
  - bap-template
  - ai-gen-description
---

# Add an agent from the setup workspace


Add an AI-powered agent to your Power Pages site to provide instant, conversational support. This article walks you through adding an agent from the setup workspace so you can answer questions, increase user satisfaction, and reduce support effort. Follow the steps to review prerequisites, choose configuration options, and understand next steps.

By default, [an agent that you add to your Power Pages site](#add-an-agent) answers questions using your site content. You can extend its capabilities in these ways:

- Use an agent created in [Microsoft Copilot Studio](agent-how-to.md).
- [Configure an agent to use Bing search to generate answers from public data](force-bing-index.md).
- Use [Omnichannel in Dynamics 365 Customer Service with your agent](../configure/omnichannel.md) to hand off customers to a live agent as needed.


:::image type="content" source="media/enable-chatbot/site-copilot.png" alt-text="Screenshot of an agent in a Power Pages site.":::

## Prerequisites

To use AI-powered agent features in Power Pages, make sure the following conditions are met:

- The tenant admin turns on the [Publish Copilots with AI features](/microsoft-copilot-studio/security-and-governance) setting in the Power Platform admin center.
- Agents created from Power Pages use the HTTP node to communicate with the site. Make sure the HTTP connector isn't blocked in the selected environment.
- The agent uses Copilot Studio generative answers. Learn more about quotas and limits in [Quotas, limits, app registration, certificates, and configuration values for Copilot Studio](/microsoft-copilot-studio/requirements-quotas).

## Add an agent

You can create a new agent directly from your Power Pages site or add an existing agent available in the current environment. A site can include multiple agents, and you can control their visibility by assigning web roles.

### Create new agent

When you create a new agent from Power Pages, the agent automatically becomes aware of the site context. It can generate responses tailored to site visitors based on their assigned web roles.

Agents created from Power Pages use Generic OAuth 2 authentication with the token pass-through method. This configuration enables the agent to work seamlessly with all identity providers configured for the site, including support for anonymous users.

Follow these steps to create an agent manually:

1. In Power Pages, go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **AI assistance**, select **Agents**.

    :::image type="content" source="media/enable-chatbot/select-agent.png" alt-text="Screenshot of the Add an agent to site page in Power Pages.":::

1. Turn on the **Site agent** option.

    Power Pages creates an [agent with generative answers conversation](/microsoft-copilot-studio/nlu-boost-conversations) in Copilot Studio. The agent is initially created as a trial. After the trial expires, it uses the available Copilot Studio capacity in your environment.

1. To make an agent available to visitors and users, assign the required roles.
   <Image>

### Add an existing agent to site
You can add a custom agent created in Microsoft Copilot Studio to your Power Pages site by selecting **Add agent**. After adding the agent, assign the appropriate web roles to make it available to the intended site users.

> [!NOTE]
> - If a site meets the conditions outlined in the [Prerequisites](#prerequisites) section, an agent is added to the site during site provisioning. If you don't want to create an agent by default, [service admins](/power-platform/admin/use-service-admin-role-manage-tenant) can turn off this capability at the tenant level. To learn more, see [Manage agent provisioning](/power-pages/getting-started/manage-copilot-provisioning).
> - To change your site's custom domain after you add an agent, turn off the agent, update the custom domain, and then turn the agent back on.
> - If you turn off the agent feature, wait a few minutes for background operations to finish before turning it back on.

## Next steps

[Customize your agent](../getting-started/customize-your-agent.md)

## Related information

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Generate answers from public data using Bing search](../getting-started/force-bing-index.md)
- [Manage agent provisioning](../getting-started/manage-agent-provisioning.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
- [Add an AI-powered chatbot with Power Pages (video)](https://youtu.be/ohANXe1bfos?feature=shared)
