---
title: Configure Microsoft Entra ID Authentication for Power Pages Agent
description: 'Learn how to configure Microsoft Entra ID authentication in Copilot Studio and enable secure access through a Power Pages site'
author: JoshuaPartlow
contributors: null
ms.topic: how-to
ms.date: 02/23/2026
ms.author: joshuapa
ms.reviewer: joshuapa
---

# Configure Microsoft Entra ID authentication for Power Pages agent

When you provision an agent from Power Pages, it uses the default Generic OAuth 2 authentication with the implicit flow. In this configuration, the agent:

- Can be accessed only from the Power Pages site
- Supports all identity providers configured for the site

Some organizations require authentication exclusively through Microsoft Entra ID and want to test the agent directly in Copilot Studio. This article describes how to configure Microsoft Entra ID authentication in Copilot Studio and enable secure access through a Power Pages site.

## Prerequisites

Before you begin, ensure that:

- A site agent is created / added to Power Pages. For more information, see Add an agent from the setup workspace.
- You have a Microsoft 365 administrator account with permission to create and manage app registrations in Microsoft Entra ID.

## Overview of configuration process

The configuration consists of the following steps:

1. Create a new app registration for Copilot Studio authentication.
1. Update the Power Pages site–associated app registration to pass the SSO token.
1. Configure authentication settings in Copilot Studio.
1. Update Power Pages site settings.
1. Add the Copilot authentication app client ID to the bot consumer record.

## Step 1: Update the Power Pages site app registation

1. Open your Power Pages site in edit mode.
1. Go to the Setup workspace.
1. Copy the Application ID associated with the site.
1. In the Azure portal, locate the app registration with the same Application ID.

### Add required API permissions

Add the following delegated permissions and then grant admin consent:

- Microsoft Graph
  - email
  - openid
  - profile
- Power Platform API
  - CopilotStudio.Copilots.Invoke

## Step 2: Configure Microsoft Entra ID for agent

Refer to detailed steps in [Configure user authentication with Microsoft Entra ID](/microsoft-copilot-studio/configuration-authentication-azure-ad?tabs=fic-auth) for configuring authentication for an agent associated with Power Pages.

The App registration used to configure the agent should allow token exchange between Power Pages site and agent. To enable that:

1. In the Azure portal, go to **Microsoft Entra ID** > **App registrations** > **Select the App registration configured for the agent**.
1. Under **Authentication** > **Redirect URI**, add the following platform:
   **Single-page application (SPA)** and enter Power Pages site URL (e.g. `https://contoso.powerappsportals.com`).

### Add API permissions

1. Go to to **API permissions > Add a permission** and add the following delegated permissions:

- **Power Platform API**
  - CopilotStudio.Copilots.Invoke  

1. Select **Grant admin consent**.

### Enable Single sign-on

1. Go to **Expose an API**.
1. Go to **Authorized client applications**.
1. Add the Power Pages site app (client ID).
1. Select Authorized scopes checkbox
1. Click Add permission
1. Copy th escope
1. Go to **Agent > Settings> Security** and paste the copied scope under **Token exchange URL (required for SSO)**

## Step 3: Update custom scopes of Power Pages site App registration

This step is an optional one required to call Power Pages API from the agent. If you have created an agent from a Power Pages site, then you must:

1. In the Azure portal, go to **Microsoft Entra ID > App registrations > Select the App registration configured for Power Pages site**.
1. Go to **API permissions > Add a permission**.
1. Add the delegated permissions of app registration created for agent. Search for the client ID and then select the permission (e.g. `Test.Read`).
1. Select **Grant admin consent**.
1. Go to **Expose an API** and click the Edit button next to **Application ID URI**.

   > [!NOTE]
   > The Application ID URI must be in format `api://<client id of the current application>`. This value might be different. Modify this value to properly reflect the current application.

1. Copy the scope.
1. Go to **Agent > Settings > Security** and paste the copied scope next to the existing scope.  

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
