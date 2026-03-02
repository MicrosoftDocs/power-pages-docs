---
title: Configure Microsoft Entra ID Authentication for Power Pages Agent
description: 'Learn how to configure Microsoft Entra ID authentication in Copilot Studio and enable secure access through a Power Pages site'
author: nageshbhat-msft
ms.author: nabha
contributors: null
ms.topic: how-to
ms.date: 02/23/2026
ms.reviewer: joshuapa
---

# Configure Microsoft Entra ID authentication for Power Pages agent

When you provision an agent from Power Pages, it uses the default Generic OAuth 2 authentication with the implicit flow. In this configuration, the agent:

- Can be accessed only from the Power Pages site
- Supports all identity providers configured for the site

Some organizations require authentication exclusively through Microsoft Entra ID and want to test the agent directly in Copilot Studio. This article describes how to configure Microsoft Entra ID authentication in Copilot Studio and enable secure access through a Power Pages site.

## Prerequisites

Before you begin, ensure that:

- A site agent is created / added to Power Pages. For more information, see [Add an agent](/getting-started/enable-agent?#add-an-agent) from the setup workspace.
- You have a Microsoft 365 administrator account with permission to create and manage app registrations in Microsoft Entra ID.

## Overview of configuration process

This configuration uses two app registrations: one that is preconfigured during Power Pages site provisioning (Site App), and another that is created during setup (Agent App) and used to configure the agent.
The configuration consists of the following steps:

1. Create a new app registration for Copilot Studio authentication.
1. Update the Power Pages site–associated app registration to pass the SSO token.
1. Configure authentication settings in Copilot Studio.
1. Update Power Pages site settings.
1. Add the Copilot authentication app client ID to the bot consumer record.


## Step 1: Update the Power Pages site app registation

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).
1. Select the **+ Edit**.
1. Navigate to the **Set up** workspace.
1. Copy the Application ID associated with the site.
   <Image>
1. In the Azure portal, locate the app registration with the same Application ID.

### Add required API permissions

Add the following delegated permissions:
1. Under **Manage** select **API Permissions**
2. Select **Add permission** and then select **Microsoft Graph**.
3. Select **Delegated permissions**.
4. Expand **OpenId permissions** and turn on **openid** and **profile**.
5. Select **Add permissions**
6. Select **Add permission** and select **APIs my organization uses**
7. Search **Power Platform API** and select
8. Select **Delegated permissions**
9. Expand **CopilotStudio** and select **CopilotStudio.Copilots.Invoke**
10. Select **Add permissions**
11. Click **Grant admin consent**.

## Step 2: Configure Microsoft Entra ID for agent

Refer to detailed steps in [Configure user authentication with Microsoft Entra ID](/microsoft-copilot-studio/configuration-authentication-azure-ad?tabs=fic-auth) for configuring authentication for an agent associated with Power Pages.

The App registration used to configure the agent should allow token exchange between Power Pages site and agent. To enable that:

### Add the redirect URL

You will be adding Power Pages site url as redirect URL to the App configured configured for agent.
1. Under **Manage** select **Authentication**
2. Under **Redirect URI Configuration**, select **Add Redirect URI** , and then select **Single-page Application**.
3. Enter Power Pages site URL (e.g. `https://contoso.powerappsportals.com`).

### Add API permissions

1. Under **Manage** select **API Permissions**
2. Select **Add permission** and select **APIs my organization uses**
3. Search **Power Platform API** and select
4. Select **Delegated permissions**
5. Expand **CopilotStudio** and select **CopilotStudio.Copilots.Invoke**
6. Select **Add permissions**
7. Click **Grant admin consent**.

### Enable Single sign-on

1. Under **Manage** select **Expose an API**.
1. Under **Authorized client applications** select **Add a client application**
1. Add the Power Pages site Application (client) ID.
1. Select **Authorized scopes** checkbox
1. Click **Add permission**
1. Copy the scope

## Step 3: Update custom scopes of Power Pages site App registration

This step is an optional one required to call Power Pages API from the agent. If you have created an agent from a Power Pages site, then you must:

1. In the Azure portal, select **Site App** registration.
1. Under **Manage** select **API permissions**.
2. Select **Add a permission** and select **APIs my organization uses**
3. Search for Agent App Application (client) ID and select
4. Select **Delegated permissions**
5. Expand **Test** and select scope name defined in Agent App (e.g. `Test.Read`).
6. Select **Add permission**
1. Select **Grant admin consent**.
1. Select **Expose an API** and click the Edit button next to **Application ID URI**.

   > [!NOTE]
   > The Application ID URI must be in format `api://<client id of the current application>`. This value might be different. Modify this value to properly reflect the current application.

1. Copy the scope.

## Step 4: Update the scopes in Agent security configuration
You have copied two scopes, one from each app registration. These scopes enable single sign-on (SSO) for the Power Pages site and grant the agent permission to access the Power Pages Web API.
1. Open **Agent** added to site
2. Under **Settings**, select **Security > Authentication**.
3. Paste the Agent App scope under **Token exchange URL (required for SSO)**
   <Image>
5. Paste the Site App scope next to the existing scope.
   <Image>
7. Select **Save**.
8. Close *Settings** page
9. **Publish** agent
   
   
## Step 4: Configure Power Pages site settings

In power pages, add or update the following site settings:

| Name | Value |
| --- | --- |
| Authentication/BearerAuthentication/Enabled | true |
| Authentication/BearerAuthentication/Provider | AzureAD |
| Authentication/BearerAuthentication/UseEntraV2Issuer | true |
| Authentication/BearerAuthentication/ValidIssuer | `https://login.microsoftonline.com/<tenant-id>/v2.0` |
| SiteCopilot/PVA/AuthenticationMethod | OpenIdConnect |

## Step 5: Add the Copilot authentication client ID to the bot consumer

1. Open the Power Pages site in edit mode.
1. Go to the **Data** workspace.
1. Locate the **Site Component** or **Bot Consumer** table (based on your site data model).
1. Open the corresponding bot consumer record.
1. Add the following value to the configjson node: `"clientId": "<AgentAppClientID>"` as shown in the folowing exampl.

   ```json
     {"botschemaname":"cr720_agentSchema","configjson":"{\"clientId\":\"00000000-0000-0000-0000-000000000000\",\"version\":\"v2\" }" ,"adx_botconsumer_adx_webrole":["00000000-0000-0000-0000-000000000000"] } 
   ```

1. Save the record.
  
## Related information

- [Add an agent - overview](add-agent-overview.md)
- [Add an agent to your Power Pages site](enable-agent.md)
- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
- [Configure user authentication for an agent](configure-user-authentication-for-agent.md)
