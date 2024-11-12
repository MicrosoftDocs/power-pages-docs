---
title: Add a copilot to your Power Pages site
description: Learn how to add a copilot to a Microsoft Power Pages site for quicker customer support and an improved user experience.
ms.topic: how-to
ms.date: 10/24/2024
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

# Add a copilot to your Power Pages site

A copilot enhances your Microsoft Power Pages site by providing instantaneous support to your users. Within minutes, you can integrate a copilot to provide natural-language responses to visitor questions, improve the user experience, and boost satisfaction.

By default, [a copilot that you add to your Power Pages site](#add-a-copilot) can answer questions based on the site's information. However, you can extend the default copilot capabilities in the following ways:

- Use a copilot that is created in [Microsoft Copilot Studio](pva-bot-how-to.md).
- [Configure the copilot to use Bing search to generate answers from public data](force-bing-index.md).
- Use [Omnichannel in Dynamics 365 Customer Service with your copilot](../configure/omnichannel.md), and transition customers to a live agent as required.

:::image type="content" source="media/enable-chatbot/site-copilot.png" alt-text="Screenshot of a copilot in a Power Pages site.":::

## Prerequisites

Before you can use AI-powered copilot features in Power Pages, the following conditions must be met:

- Your tenant administrator must turn on the [Publish Copilots with AI features](/microsoft-copilot-studio/security-and-governance) setting in the Power Platform admin center.
- Copilot uses Copilot Studio generative answers. Learn more about quotas and limits in [Quotas, limits, app registration, certificates, and configuration values for Copilot Studio](/microsoft-copilot-studio/requirements-quotas).

## Add a copilot

Follow these steps to manually add a copilot:

1. In Power Pages, go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **Copilot**, select **Add copilot**.

    :::image type="content" source="media/enable-chatbot/select-copilot.png" alt-text="Screenshot of the Add copilot to site page in Power Pages.":::

1. Turn on the **Create copilot** option.

    Power Pages creates a [copilot with generative answers conversation](/microsoft-copilot-studio/nlu-boost-conversations) for you in Copilot Studio.

1. To make the copilot available to visitors and users, turn on the **Enable copilot on site** option.

    The **Enable copilot on site** option is available only if your tenant admin turned on the **Publish Copilots with AI features** setting.

> [!NOTE]
> - If a site meets the conditions that are outlined in the [Prerequisites](#prerequisites) section, the copilot is added to the site during site provisioning. If you don't want the copilot to be created by default, [service admins](/power-platform/admin/use-service-admin-role-manage-tenant) can turn off this capability at the tenant level. Learn more in [Manage copilot provisioning](/power-pages/getting-started/manage-copilot-provisioning).
> - To change your site's custom domain after you add a copilot, first turn off the copilot, and then update the custom domain. When you're finished, turn the copilot back on.
> - If you turn off the copilot feature, wait a few minutes for background operations to be completed before you turn it back on.

## Next steps

[Customize your copilot](../getting-started/customize-your-copilot.md)

## Related information

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Generate answers from public data using Bing search](../getting-started/force-bing-index.md)
- [Manage copilot provisioning](../getting-started/manage-copilot-provisioning.md)
- [Responsible AI: FAQ for site copilot](../faqs-chatbot.md)
- [Add an AI-Powered chatbot with Power Pages](https://youtu.be/ohANXe1bfos?feature=shared)
