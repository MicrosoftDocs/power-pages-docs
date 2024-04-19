---
title: Configure Omnichannel with Power Pages site copilot (preview)
description: Configure Omnichannel with Power Pages site copilot to escalate interactions with live agents.
ms.topic: how-to
ms.date: 04/19/2024
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection:
  - bap-ai-copilot
contributors:
  - ProfessorKendrick
  - nageshbhat-msft
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:04/19/2024
---
# Configure Omnichannel with Power Pages site copilot (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

[Omnichannel](/dynamics365/customer-service/implement/introduction-omnichannel) provides enterprise to instantly connect and engage with their customers via live chat. Omnichannel with Power Pages site copilot allows your end users to escalate interaction with live agent when copilot isn't able to answer the queries or the user is expecting a response that isn't designed in the site.

> [!IMPORTANT]
>
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - To understand the capabilities and limitations of this feature, see [FAQ for copilot](../faqs-chatbot.md).

## Prerequisites

- [Add a copilot to your site](../getting-started/enable-chatbot.md#add-a-copilot) in Power Pages design studio.
- Install Dynamics 365 customer service app in the environment where the site is created.

## Configure agent hand-off in Copilot studio

The copilot added with Power Pages Studio lacks the necessary instructions for transferring calls to Omnichannel. 

To achieve this functionality, you must configure the copilot manually in Copilot Studio. You can access Copilot Studio directly from the Power Pages design studio.

1. Go to the [Set up workspace](setup-workspace.md).
1. Under **Integrations,** select **Add copilot (preview)**.
1. From the **Copilot analytics** section, choose **View copilot analytics**.

    :::image type="content" source="media/omnichannel/view-copilot-analytics.svg" alt-text="A screenshot of Add copilot to a site in the Set up workspace with the View copilot analytics link emphasized.":::

### Configure a copilot manually in Copilot Studio

1. In Copilot Studio, select **Topics** from the left-hand menu.
1. Select the **System** tab, then choose **Escalate**.
1. Select  the **+** icon below the Message tile.
1. Hover over **Topic management** and select **Transfer conversation**.
1. Type the message you'd like displayed to the end user while transferring the call in the **Message to agent** text entry field. For example, `Call transferred from chatbot to human agent.`

    :::image type="content" source="media/omnichannel/message-to-agent.svg" alt-text="A screenshot of a Transfer conversation in Copilot Studio with the Message to agent text entry field emphasized.":::

1. Select **Save**.
1. In the left-hand menu, choose **Settings**, then select **Customer engagement hub**.
1. Select **Omnichannel**, then **Connect**.
1. Once the Status shows as *Connected*, choose the **Close** button.
1. In the left-hand menu, choose **Publish**.
1. Select the **Publish** button.

## Complete chatbot setup in Customer Service Admin Center

1. Open the [Customer Service admin center](/dynamics365/customer-service/implement/cs-admin-center).

1. Navigate to **Guided channel setup** and **+ Start new**.

1. Follow the steps provided in the guided channel setup to complete onboarding.

    During the setup process, choose chat and link the existing bot created from the Power Pages design studio.

1. Copy the script displayed in the **chat setup complete** step.

You need this script to host the live widget on Power pages site.

## Enable Omnichannel live widget in Power Pages

1. Open the [Portal Management app](portal-management-app.md) for the selected site.
1. Open Header [web template](web-templates.md) of the associated site.
1. Use the [substitution liquid tag](liquid/template-tags.md#substitution) to add the live widget script you copied when you [completed the chatbot setup](#complete-chatbot-setup-in-customer-service-admin-center).
1. Save the template.
1. In the left-hand menu, select **Site Settings**.
1. Choose **+ New**.
1. Create "*SiteCopilot/EnableOmniChannelWidget"* site setting and set value to `true`.
1. Save and preview the site.