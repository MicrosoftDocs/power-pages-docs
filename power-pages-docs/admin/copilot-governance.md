---
title: Disable Generative AI features for users (preview)
description: Learn how to disable generative AI features for your users of your Microsoft Power Pages websites.
author: vamseedillimsft
ms.topic: conceptual
ms.date: 09/13/2024
ms.author: vamseedilli
ms.reviewer: dmartens
ms.collection:
 - bap-ai-copilot
contributors:
    - dmartens
    - tapanm
---

# Disable Generative AI features for users (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

As an administrator, you can choose to disable Generative AI features for your website users. This setting allows you to control which websites can have AI powered experiences for their users.

> [!IMPORTANT]
>
> - This is a preview feature.
> - Preview features aren’t meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2189520), and are available before an official release so that customers can get early access and provide feedback.
> - This feature is being gradually rolled out across regions and may not be available yet in your region.

## AI-enabled experiences supported in websites

The following AI powered experiences are supported in Power Pages websites today, which simplify and enhance the user experience for your website visitors:

### Intelligent forms

Simplify the form filling experience for users by extracting relevant information from attachments and automatically filling fields. This feature also allows users to rewrite their multi-line text inputs using AI draft assistance. Learn more at [Enable AI form fill assistance on a form (preview)](../getting-started/add-form.md#enable-ai-form-fill-assistance-on-a-form-preview).

### List summary

Allows users to get an AI generated summary of a list (table) that is on the site. Learn more about list summary at [Add AI summary list](../getting-started/add-ai-summary-list.md).

### Search summarization

Power Pages Site Search with Generative AI provides site users with summarized responses to their natural language queries. It also uses a semantic search approach instead of traditional keyword-based methods, providing more relevant and contextualized results. Learn more about search summarization at [Power Pages search with generative AI (preview)](/power-pages/configure/search/generative-ai).

### Site copilot

Power Pages site copilot can provide quick and efficient customer support to your site's visitors and users, which can improve your site's overall user experience. Learn more about Site copilot at [Add a copilot to your Power Pages site](/power-pages/getting-started/enable-chatbot).

> [!NOTE]
> The following AI-powered experiences are governed separately and are not covered by this control:
>
> - [Site copilot](/microsoft-copilot-studio/security-and-governance)
> - [Maker experiences](../configure/ai-copilot-overview.md)

## Admin experience

You can disable and enable AI powered experiences for your site users using the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. From the left-hand menu, navigate to **Resources** and select **Power Pages Sites**.

1. Select **Governance Controls**.

   :::image type="content" source="media/copilot-governance/governance-controls.png" alt-text="Screenshot showing the governance controls button in the Power Platform admin center.":::

1. Choose **Enable Generative AI usage in websites** from the list.

1. A slide-out panel appears. You can enable AI features in:

   | Option | Description |
   |--------|-------------|
   | All sites | Selecting **All sites** enables AI powered experiences for your site users in all the websites in the tenant |
   | All sites except specific sites | Selecting **All sites except specific sites** enables AI powered experiences in all the websites in the tenant except the sites that you choose. This selection overrides any maker configurations that enable AI experiences and prevents users from accessing AI features in the sites that you blocked. |
   | Specific sites | Selecting **Specific sites** enables AI powered experiences only in the websites that you choose. This selection overrides any maker configurations that enable AI experiences. The selection prevents users from accessing AI features in all sites in the tenant except the specific sites allowed. |
   | None of the sites | Selecting **None of the sites** blocks AI powered experiences in all the websites in the tenant. This selection overrides any maker configurations that enable AI experiences and prevents users from accessing AI features in all the sites in the tenant. |

1. Select the sites and choose **OK**.

1. Select **Save**. A message confirming success appears in green below the Governance Controls ribbon menu.

## Maker experience

Once an admin completes the steps in the previous section, users are blocked from using AI experiences based on the admin's choice.

For existing sites, makers can enable AI-powered experiences. However, if the admin blocks these features, Design Studio shows a banner error message. This message tells the makers that an organizational policy is blocking the generative AI features.

## User experience

When generative AI experiences are blocked in a site for users, they fall back to the standard experience. For example, users see a regular search and don't get a generative AI powered search summary. Users don't see any messaging about organizational policies or governance controls.

### Related information

[Power Pages governance](coe-portals.md)
