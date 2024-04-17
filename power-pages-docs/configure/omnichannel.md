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

[Omnichannel](https://learn.microsoft.com/en-us/dynamics365/customer-service/implement/introduction-omnichannel) provides enterprise to instantly connect and engage with their customers via live chat. Configuring omnichannel with Power Pages site copilot allow end users to escalate interaction with live agent when copilot doesn't able to answer the queries or user expecting a response which is not designed in the site.

Below steps detail out configuring the omnichannel with Power Pages site copilot

# Pre-requisite

-   You must [add copilot to site](https://learn.microsoft.com/en-us/power-pages/getting-started/enable-chatbot#add-a-chatbot) in Power Pages studio

-   Dynamics 365 customer service app should be installed in the environment where site is created.

# Configure agent hand-off in Copilot studio

The copilot added with Power Pages Studio lacks the necessary instructions for transferring calls to omnichannel. To achieve this functionality, manual configuration through Copilot Studio is required.

1.  Go to the [Set up workspace](https://learn.microsoft.com/en-us/power-pages/configure/setup-workspace).

2.  Under **Integrations,** select **Add copilot (preview)**

3.  Click **View copilot analytics** link in **Copilot analytics** section

4.  Navigate to **Topics**

5.  Select **System** tab & click on **Escalate** topic

6.  Click on **+ after** **Message** node

7.  Mouse hover **Topic management** menu **and** select **Transfer conversation** node

![A screenshot of a computer Description automatically generated](media/image1.png)

8.  Add message that needs to shown to the end user while transferring the call

Ex : Call transferred from chatbot to human agent

9.  Click **Save**

10. Navigate to **Customer engagement hub** under **Settings**

![A screenshot of a computer Description automatically generated](media/image2.png)

11. Select **Omnichannel** and click on **connect**

![A screenshot of a computer Description automatically generated](media/image3.png)

12. Navigate to **Publish** and click on **Publish** button.

# Complete chatbot setup in Customer Service Admin Centre

1.  Open [Customer Service Admin Center](https://learn.microsoft.com/en-us/dynamics365/customer-service/implement/cs-admin-center)

2.  Navigate to **Guided channel setup** and **+ Start new**

![A screenshot of a computer Description automatically generated](media/image4.png)

3.  Follow the steps provided in the guided channel setup to complete onboarding.

During the setup process choose chose chat and link the existing bot created from Pages studio.

![A screenshot of a computer Description automatically generated](media/image5.png)

4.  Copy the script displayed in the **chat setup complete** step.

You need this script to host the live widget on Power pages site

![A screenshot of a computer Description automatically generated](media/image6.png)

# Enable Omni channel live widget in Power Pages

1.  Open [Power Pages Management App](https://learn.microsoft.com/en-us/power-pages/configure/portal-management-app) for the selected site

2.  Open Header Web Template of the associated site

3.  Add the live widget script copied in the previous steps as shown below between substitution liquid tag

{% substitution %}

{% endsubstitution %}

![A screenshot of a computer Description automatically generated](media/image7.png)

4.  Save template

5.  Navigate to **Site Settings** and click **+New**

6.  Create "*SiteCopilot/EnableOmniChannelWidget"* site setting and set value to true

![A screenshot of a computer Description automatically generated](media/image8.png)

7.  Save and preview the site