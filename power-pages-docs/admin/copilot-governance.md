---
title: Disable Generative AI features your Pages users
description: "Learn how to disable generative AI features for your Microsoft Pages users."
author: danamartens
ms.topic: conceptual
ms.date: 09/05/2024
ms.author: dmartens
ms.reviewer: dmartens
contributors:
    - dmartens
    - tapanm
---

# Disable Generative AI features for Pages users

As an administrator, you can choose to disable Generative AI features for your Pages websites' end users. This setting allows you to control which websites can have AI powered experiences for their users.

1. [Admin experience](/power-pages/security/disable-anonymous-access#admin-experience)

2. [Maker experience](/power-pages/security/disable-anonymous-access#maker-experience)

3. [End user experience](/power-pages/security/disable-anonymous-access#end-user-experience)

> [!IMPORTANT]
>
> - This is a preview feature.
> - Preview features aren't meant for production use and may have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.
> - This feature is being gradually rolled out across regions and may not be available yet in your region.

## AI enabled experiences supported in Pages websites

The following AI powered experiences are supported in Pages websites today, which simplify and enhance the user experience for your website visitors:

### Intelligent forms

Simplifies form filling experience for end users by extracting relevant information from attachments and auto-filling fields. Also, allows end users to rewrite their multi-line text inputs using AI draft assistance. Learn More ()

### List summary

Allows end users to get an AI generated summary of the list/ table that is on the site. Learn More ()

### Search summarization

Power Pages Site Search with Generative AI provides site users with summarized responses to their natural language queries. It also uses a semantic search approach in contrast to the traditional keyword-based methods, offering more relevant and contextualized results. For more information, see [Power Pages search with generative AI (preview)](/power-pages/configure/search/generative-ai).

### Summarization API

Power Pages summarization API lets end users get an AI generated summary of the content in the page. This API is built on top of the Power Pages Web API that provides data summarization on dataverse tables used in the pages. Learn More ()

### Site copilot

Power Pages site copilot can provide quick and efficient customer support to your site's visitors and users, which can improve your site's overall user experience. For more information, see [Add a copilot to your Power Pages site](/power-pages/getting-started/enable-chatbot)

> [!NOTE]
> The following AI powered experiences are not under the purview of this control and have separate governance controls:
>
> - Site copilot
> - Maker experiences

## Admin experience

You can disable and enable AI powered experiences for your site users using the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. From the left-hand menu, navigate to **Resources** and choose **Power Pages Sites**.

1. Select **Governance Controls** from the top ribbon menu.

   :::image type="content" source="media/copilot-governance/governance-controls.png" alt-text="Screenshot showing governance controls.":::

1. Choose '**Enable Generative AI usage in websites'** from the list.

1. A slide-out panel appears. You can enable AI features in:

   | Option | Description |
   |--------|-------------|
   | All sites | Selecting **All sites** enables AI powered experiences for your site users in all the websites in the tenant |
   | All sites except specific sites | Selecting **All sites except specific sites** enables AI powered experiences in all the websites in the tenant EXCEPT the sites that you choose. This selection overrides any maker configurations that enable AI experiences and prevents end users from accessing AI features in the sites that you blocked. |
   | Specific sites | Selecting **Specific sites** enables AI powered experiences ONLY in the websites that you choose. This selection overrides any maker configurations that enable AI experiences and prevents end users from accessing AI features in all the sites in the tenant except the specific sites that you allowed. |
   | None of the sites | Selecting **None of the sites** blocks AI powered experiences in all the websites in the tenant. This selection overrides any maker configurations that enable AI experiences and prevents end users from accessing AI features in all the sites in the tenant. |

1. Select the sites and choose **OK**.

1. Select **Save**. A message confirming success appears in green below the Governance Controls ribbon menu.

## Maker experience

Once an admin completes the steps in the previous section, end users are blocked from using AI experiences based on the admin's choice.

For existing sites where AI powered experiences are enabled by makers but is blocked by admin, a banner error message is displayed in Design Studio for the makers, indicating that an org policy is blocking Generative AI features.

## End user experience

When Gen AI experiences are blocked in a site for end users, the end users simply fall back to the standard experience. For example, end users will see regular search and not get a Gen AI powered search summary. The end users will NOT see any messaging about org policies or governance controls.
