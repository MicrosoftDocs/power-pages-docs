---
title: Configure Omnichannel with Power Pages site agent
description: Learn how to configure Omnichannel with Power Pages site agent for seamless live agent escalation.
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
  - ai-seo-date:04/19/2024
---
# Configure Omnichannel with Power Pages site agent

[Omnichannel](/dynamics365/customer-service/implement/introduction-omnichannel) lets enterprises instantly connect and engage with their customers via live chat. If the agent can't resolve their queries or they need a response beyond the site's programmed capabilities, the site agent enables a seamless transition to a live agent for help.

## Prerequisites

- [Add an agent to your site](../getting-started/enable-chatbot.md#add-a-copilot) in the Power Pages design studio.
- Install the Dynamics 365 Customer Service app in the environment where the site is created.

## Configure agent hand-off in Copilot Studio

The agent added with Power Pages Studio doesn't include instructions for transferring calls to Omnichannel.

To enable this functionality, configure the agent manually in Copilot Studio. You can access Copilot Studio directly from the Power Pages design studio.

1. Go to [Set up workspace](setup-workspace.md).
1. Under **Copilot,** select **Add agent**.
1. From the **Agent analytics** section, choose **View agent analytics**.

    :::image type="content" source="media/omnichannel/view-copilot-analytics.svg" alt-text="A screenshot of Add copilot to a site in the Set up workspace with the View copilot analytics link emphasized.":::

### Configure an agent manually in Copilot Studio

1. In Copilot Studio, select **Topics** from the left-hand menu.
1. Select the **System** tab, and then choose **Escalate**.
1. Select  the **+** icon below the Message tile.
1. Hover over **Topic management**, and then select **Transfer conversation**.
1. Enter the message you'd like displayed to the end user while transferring the call in the **Message to agent** text entry field. For example, `Call transferred from chatbot to human agent.`

    :::image type="content" source="media/omnichannel/message-to-agent.svg" alt-text="A screenshot of a Transfer conversation in Copilot Studio with the Message to agent text entry field emphasized.":::

1. Select **Save** to apply your changes.
1. In the left-hand menu, select **Settings**, and then select **Customer engagement hub**.
1. Select **Omnichannel**, then **Connect**.
1. When the Status shows as *Connected*, select the **Close** button.
1. In the left-hand menu, choose **Publish**.
1. Select **Publish**.

## Complete chatbot setup in Customer Service Admin Center

1. Open the [Customer Service admin center](/dynamics365/customer-service/implement/cs-admin-center).

1. Go to **Guided channel setup**, and then select **+ Start new**.

1. To finish onboarding, follow the steps in the guided channel setup.

    During setup, select chat and link the existing bot created in the Power Pages design studio.

1. Copy the script shown in the **chat setup complete** step.

    :::image type="content" source="media/omnichannel/chat-widget-code-snippet.svg" alt-text="Screenshot of the Customer Service Admin Center showing the script for adding the chat widget to the customer webpage.":::

    You need this script to host the live widget on a Power Pages site.

## Enable Omnichannel live widget in Power Pages

1. Open the [Portal Management app](portal-management-app.md) for the selected site.
1. Open the Header [web template](web-templates.md) for the associated site.
1. Use the [substitution liquid tag](liquid/template-tags.md#substitution) to add the live widget script you copied when you [completed the chatbot setup](#complete-chatbot-setup-in-customer-service-admin-center).

    :::image type="content" source="media/omnichannel/substitution-liquid-tag.png" alt-text="Screenshot of the substitution liquid tag content displayed in the Header web template inside the Portal Management app.":::

1. Save the template.
1. In the left-hand menu, select **Site Settings**.
1. Choose **+ New**.
1. Create "*SiteCopilot/EnableOmniChannelWidget"* site setting and set value to `true`.
1. Save and preview the site.

## Related information

[Responsible AI: FAQ for site agent](../faqs-chatbot.md)