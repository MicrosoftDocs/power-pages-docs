---
title: Add an agent to your Power Pages site
description: Learn how to add an agent to a Microsoft Power Pages site for quicker customer support and an improved user experience.
ms.topic: how-to
ms.date: 06/17/2025
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
---

# Add an agent to your Power Pages site

An agent enhances your Microsoft Power Pages site by providing instantaneous support to your users. Within minutes, you can integrate an agent to provide natural-language responses to visitor questions, improve the user experience, and boost satisfaction.

By default, [an agent that you add to your Power Pages site](#add-an-agent) can answer questions based on the site's information. However, you can extend the default agent capabilities in the following ways:

- Use an agent created in [Microsoft Copilot Studio](pva-bot-how-to.md).
- [Configure an agent to use Bing search to generate answers from public data](force-bing-index.md).
- Use [Omnichannel in Dynamics 365 Customer Service with your agent](../configure/omnichannel.md), and transition customers to a live agent as required.

:::image type="content" source="media/enable-chatbot/site-copilot.png" alt-text="Screenshot of an agent in a Power Pages site.":::

## Prerequisites

To use AI-powered agent features in Power Pages, make sure the following conditions are met:

- The tenant admin needs to turn on the [Publish Copilots with AI features](/microsoft-copilot-studio/security-and-governance) setting in the Power Platform admin center.
- Copilot uses Copilot Studio generative answers. Learn more about quotas and limits in [Quotas, limits, app registration, certificates, and configuration values for Copilot Studio](/microsoft-copilot-studio/requirements-quotas).

## Add an agent

Follow these steps to add an agent manually:

1. In Power Pages, go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **Copilot**, select **Add agent**.

    :::image type="content" source="media/enable-chatbot/select-copilot.png" alt-text="Screenshot of the Add an agent to site page in Power Pages.":::

1. Turn on the **Create agent** option.

    Power Pages creates an [agent with generative answers conversation](/microsoft-copilot-studio/nlu-boost-conversations) in Copilot Studio.

1. To make an agent available to visitors and users, turn on the **Enable agent on site** option.

    The **Enable agent on site** option is available only if the tenant admin turns on the **Publish Copilots with AI features** setting.

> [!NOTE]
> - If a site meets the conditions outlined in the [Prerequisites](#prerequisites) section, an agent is added to the site during site provisioning. If you don't want an agent to be created by default, [service admins](/power-platform/admin/use-service-admin-role-manage-tenant) can turn off this capability at the tenant level. Learn more in [Manage agent provisioning](/power-pages/getting-started/manage-copilot-provisioning).
> - To change your site's custom domain after you add an agent, turn off the agent, update the custom domain, and then turn the agent back on.
> - If you turn off the agent feature, wait a few minutes for background operations to finish before turning it back on.

## Next steps

[Customize your agent](../getting-started/customize-your-copilot.md)

## Related information

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Generate answers from public data using Bing search](../getting-started/force-bing-index.md)
- [Manage agent provisioning](../getting-started/manage-copilot-provisioning.md)
- [Responsible AI: FAQ for site agent](../faqs-chatbot.md)
- [Add an AI-powered chatbot with Power Pages (video)](https://youtu.be/ohANXe1bfos?feature=shared)
