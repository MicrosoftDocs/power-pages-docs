---
title: Configure omnichannel with Power Pages site copilot (preview)
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

[Omnichannel](/dynamics365/customer-service/implement/introduction-omnichannel) provides enterprise to instantly connect and engage with their customers via live chat. Configuring omnichannel with Power Pages site copilot allow end users to escalate interaction with live agent when copilot doesn't able to answer the queries or user expecting a response which is not designed in the site.

# Prerequisite

- [Add copilot to your site](../getting-started/enable-chatbot.md#add-a-copilot) in Power Pages design studio.
- Install Dynamics 365 customer service app in the environment where the site is created.

# Configure agent hand-off in Copilot studio

The copilot added with Power Pages Studio lacks the necessary instructions for transferring calls to omnichannel. To achieve this functionality, you must manually configure the copilot in Copilot Studio.

1. Go to the [Set up workspace](setup-workspace.md).
1. Under **Integrations,** select **Add copilot (preview)**.
1. Choose **View copilot analytics** from the **Copilot analytics** section.
1. Navigate to **Topics**
1. Select **System**, then choose **Escalate**.
1. Select  **+ after Message**.
1. Hover over **Topic management** and select **Transfer conversation**.

    ![A screenshot of a computer Description automatically generated](media/image1.png)

1. Add the message that needs to shown to the end user while transferring the call.

    Ex : Call transferred from chatbot to human agent

1. Select **Save**.
1. Navigate to **Customer engagement hub** under **Settings**

    ![A screenshot of a computer Description automatically generated](media/image2.png)

1. Select **Omnichannel**, then **Connect**.

    ![A screenshot of a computer Description automatically generated](media/image3.png)

1. Select the **Publish** button.

# Complete chatbot setup in Customer Service Admin Centre

1. Open [Customer Service Admin Center](https://learn.microsoft.com/en-us/dynamics365/customer-service/implement/cs-admin-center)

1. Navigate to **Guided channel setup** and **+ Start new**

    ![A screenshot of a computer Description automatically generated](media/image4.png)

1. Follow the steps provided in the guided channel setup to complete onboarding.

During the setup process choose chose chat and link the existing bot created from Pages studio.

![A screenshot of a computer Description automatically generated](media/image5.png)

1. Copy the script displayed in the **chat setup complete** step.

You need this script to host the live widget on Power pages site

![A screenshot of a computer Description automatically generated](media/image6.png)

# Enable Omnichannel live widget in Power Pages

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