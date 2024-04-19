---
title: Configure Omnichannel with Power Pages site copilot (preview)
description: 
ms.topic: how-to
ms.date: 04/11/2024
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection: 
  - bap-ai-copilot
contributors:
  - ProfessorKendrick
  - nageshbhat-msft
---
# Configure Omnichannel with Power Pages site copilot (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

[Omnichannel](/dynamics365/customer-service/implement/introduction-omnichannel) provides enterprise to instantly connect and engage with their customers via live chat. Configuring omnichannel with Power Pages site copilot allow end users to escalate interaction with live agent when copilot doesn't able to answer the queries or user expecting a response which is not designed in the site.

> [!IMPORTANT]
>
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - To understand the capabilities and limitations of this feature, see [FAQ for copilot](../faqs-chatbot.md).

## Prerequisites

- [Add copilot to your site](../getting-started/enable-chatbot.md#add-a-copilot) in Power Pages design studio.
- Install Dynamics 365 customer service app in the environment where the site is created.

## Configure agent hand-off in Copilot studio

The copilot added with Power Pages Studio lacks the necessary instructions for transferring calls to Omnichannel. To achieve this functionality, you must [configure the copilot manually in Copilot Studio.](#configure-a-copilot-manually-in-copilot-studio). 

You can access Copilot Studio directly from the [Set up workspace](setup-workspace.md) in Power Pages design studio:

1. Under **Integrations,** select **Add copilot (preview)**.
1. From the **Copilot analytics** section, choose **View copilot analytics**.

### Configure a copilot manually in Copilot Studio

1. In Copilot Studio, select **Topics** from the left-hand menu.
1. Select the **System** tab, then choose **Escalate**.
1. Select  the **+** icon below the Message tile.
1. Hover over **Topic management** and select **Transfer conversation**.
1. Type the message you'd like displayed to the end user while transferring the call in the **Message to agent** text entry field.

    Ex : Call transferred from chatbot to human agent

    //ADD SCREENSHOT HERE

1. Select **Save**.
1. In the left-hand menu, choose **Settings**, then select **Customer engagement hub**.
1. Select **Omnichannel**, then **Connect**.
1. Once the Status is Connected, choose the **Close** button.
1. In the left-hand menu, choose **Publish** and then select the **Publish** button.

## Complete chatbot setup in Customer Service Admin Center

1. Open the [Customer Service admin center](/dynamics365/customer-service/implement/cs-admin-center).

1. Navigate to **Guided channel setup** and **+ Start new**

    ![A screenshot of a computer Description automatically generated](media/image4.png)

1. Follow the steps provided in the guided channel setup to complete onboarding.

During the setup process choose chose chat and link the existing bot created from Pages studio.

![A screenshot of a computer Description automatically generated](media/image5.png)

1. Copy the script displayed in the **chat setup complete** step.

You need this script to host the live widget on Power pages site

![A screenshot of a computer Description automatically generated](media/image6.png)

## Enable Omnichannel live widget in Power Pages

1. Open the [Portal Management app overview](portal-management-app.md) for the selected site

1. Open Header Web Template of the associated site

1. Add the live widget script copied in the previous steps as shown below between substitution liquid tag

    {% substitution %}

    {% endsubstitution %}

    ![A screenshot of a computer Description automatically generated](media/image7.png)

1. Save template

1. Navigate to **Site Settings** and click **+New**

1. Create "*SiteCopilot/EnableOmniChannelWidget"* site setting and set value to true

    ![A screenshot of a computer Description automatically generated](media/image8.png)

1. Save and preview the site