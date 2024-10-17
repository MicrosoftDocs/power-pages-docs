---
title: Add a copilot to your Power Pages Site
description: Learn how to add a copilot to a Power Pages site for quicker customer support and an improved user experience.
ms.topic: how-to
ms.date: 10/17/2024
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

Enhance your Power Pages site with a copilot for instant customer support. Integrate a copilot in minutes to provide natural language responses to visitor questions, improving user experience, and boosting satisfaction.

## Introduction

Follow this guide to add a preconfigured copilot that uses generative answers for natural language responses:

**Already have a copilot in Microsoft Copilot Studio?** [Update Power Pages to use it](pva-bot-how-to.md).<br>
**Default setup:** Answers questions based on your site's information.<br>
**Extend capabilities:** Configure the copilot to [generate answers from public data using Bing search](force-bing-index.md).<br>
**Use Dynamics 365 Customer Service?** [Configure Omnichannel with your copilot](../configure/omnichannel.md) to transition customers to a live agent when needed.

## Prerequisites

To use AI-powered copilot features in Power Pages:

- Your tenant administrator must turn on the setting [Publish Copilots with AI features](/microsoft-copilot-studio/security-and-governance) in the Power Platform admin center.
- Copilot uses Microsoft Copilot Studio generative answers. Learn more about generative answers in Copilot Studio in [Knowledge sources overview](/microsoft-copilot-studio/nlu-boost-conversations#whats-supported).

## Add a copilot

Follow these steps to manually add a copilot:

> [!NOTE]
> If a site meets the conditions outlined in the prerequisite section, the copilot will be added to the site during site provisioning. If you prefer not to have the copilot created by default, the [service admins](/power-platform/admin/use-service-admin-role-manage-tenant) can turn off this capability at the tenant level. Learn more in [manage copilot provisioning](/power-pages/getting-started/manage-copilot-provisioning).  

1. Go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **Copilot**, select **Add copilot**.

    :::image type="content" source="media/enable-chatbot/select-copilot.png" alt-text="Screenshot of the copilot page in Power Pages.":::

1. Turn on **Create copilot**.

    Power Pages creates a [copilot with generative answers conversation](/microsoft-copilot-studio/nlu-boost-conversations) for you in Copilot Studio.

1. To make the copilot available to visitors and users, turn on **Enable copilot on site**.

    If your tenant admin didn't turn on publishing copilots with AI features, the **Enable copilot on site** option isn't available.

## Known issues

- To change your site's custom domain after adding a copilot, first turn off the copilot, update the custom domain, and then turn the copilot back on.
- If you turn off the copilot feature, allow a few minutes for background operations to complete before you turn it on again.

## Next steps

[Customize your copilot](../getting-started/customize-your-copilot.md)

## Related information

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Generate answers from public data using Bing search](../getting-started/force-bing-index.md)
- [Manage copilot provisioning](../getting-started/manage-copilot-provisioning.md)
- [Responsible AI - FAQ for site copilot](../faqs-chatbot.md)
