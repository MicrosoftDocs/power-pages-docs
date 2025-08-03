---
title: Build an agent from a form
description: Learn how to create, configure, and customize AI agents directly from Power Pages forms, including authentication, security, and appearance options.
author: DanaMartens
contributors:
ms.topic: how-to
ms.date: 07/31/2025
ms.author: dmartens
ms.reviewer: dmartens
---
# Build an agent from a form (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Power Pages agent builder lets you create AI agents directly from forms in Power Pages. These agents integrate with [Copilot Studio](/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) and use knowledge, actions, and business logic from the form.

With minimal steps, you build agents using existing form fields and logic, and automatically use Power Pages' built-in authorization and security roles. You can also enhance and fine-tune these agents in Copilot Studio to unlock advanced capabilities.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Prerequisite

- The tenant admin needs to turn on the [agent](../admin/copilot-hub.md) feature for Power Pages.

- Agents in Power Pages use the Microsoft Copilot Studio agent. Check that the tenant has enough message quotas for agents. Learn more about quotas in [Quotas and limits for Copilot Studio](/microsoft-copilot-studio/requirements-quotas).

## Create an agent

Create an agent directly from forms to streamline the manual process.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com).

1. Find your site, and select **Edit**.

1. In the **Pages** workspace, select a web page with a [basic form](../configure/basic-forms.md).

1. Select the form.

1. Select **Agent**.

    :::image type="content" source="media/build-agent-from-form/agent-button.png" alt-text="Screenshot of clicking the Agent button in a Power Pages form to build an agent.":::

    The *Add Agent* dialog opens. Create a new agent or extend an existing one for the selected form. The dialog has these configuration options:

1. Describe the purpose of the form, and give instructions to the agent. These instructions help the agent know when to trigger based on user input.

1. Select the optional checkbox to let the agent autofill the form using information from an uploaded image or PDF file.

1. Enter a name for the new agent, or select an existing agent from Microsoft Copilot Studio.

    > [!NOTE]
    > Only agents created from Power Pages are available for selection.

1. Select **Continue**. If you choose to create a new agent, Microsoft Copilot Studio creates it. If you select an existing agent, Microsoft Copilot Studio updates it.

    By default, authentication isn't set up when you create an agent in Microsoft Copilot Studio. Set up [authentication](configure-user-authentication-for-agent.md) manually in the Copilot Studio editor.

1. Under **Choose Roles for this Agent**, select **Add Roles** to assign web roles, and control which users can use the agent based on their assigned roles.

1. Under **Tables and columns for Web API**, select the checkbox to let the agent use table permissions for the table related to the form. The agent uses the [Power Pages Web API](../configure/web-api-overview.md), which needs extra site settings. Selecting this checkbox automatically creates the required site setting.

    > [!NOTE]
    > This configuration lets the agent use all fields in the selected table. To limit access to specific fields, update the [site settings](../configure/web-api-overview.md#site-settings-for-the-web-api) in the [Management App](/power-pages/configure/portal-management-app).

1. Select **Continue**.
1. Select **Publish** to make the agent available from the Power Pages site.

## Known issues

If proper authentication is not configured for an agent hosted on a private site, the agent may incorrectly respond that a record was created successfully, even though no record was actually created. To avoid this issue, always configure Microsoft Entra as the identity provider for agents hosted on private sites.

### Related information

- [Add an agent - overview](add-agent-overview.md)
- [Add an agent to your Power Pages site](enable-agent.md)
- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
- [Add an AI-powered chatbot with Power Pages (video)](https://youtu.be/ohANXe1bfos?feature=shared)
