---
title: Configure Microsoft Entra ID Authentication for Power Pages Agent
description: 'Learn how to configure Microsoft Entra ID authentication in Copilot Studio and enable secure access through a Power Pages site'
author: nageshbhat-msft
ms.author: nabha
contributors: null
ms.topic: how-to
ms.date: 03/05/2026
ms.reviewer: joshuapa
---

# Configure Microsoft Entra ID authentication

Microsoft Copilot Studio agents created from Power Pages use Generic OAuth 2 authentication with implicit flow by default. This configuration limits access to the Power Pages site and supports all configured identity providers.

If your organization requires Microsoft Entra ID-exclusive authentication and you need to test agents directly in Copilot Studio, you can configure Microsoft Entra ID authentication. This configuration enables:

- Secure authentication through Microsoft Entra ID
- Direct testing capabilities in Copilot Studio  
- Single sign-on (SSO) integration with Power Pages

This article walks you through the configuration process, which involves creating app registrations, configuring permissions, and updating site settings to establish secure authentication between your Power Pages site and Copilot Studio agent.

## Prerequisites

Before you begin, ensure that:

- You created or added a site agent to Power Pages. For more information, see [Add an agent](enable-agent.md#add-an-agent) from the setup workspace.
- You have a Microsoft 365 administrator account with permission to create and manage app registrations in Microsoft Entra ID.

## Overview of configuration process

This configuration uses two app registrations. One that is preconfigured during Power Pages site provisioning (site App), and another that you create during setup (agent App) and use to configure the agent.
The configuration consists of the following steps:

1. Create a new app registration for Copilot Studio authentication.
1. Update the Power Pages site–associated app registration to pass the SSO token.
1. Configure authentication settings in Copilot Studio.
1. Update Power Pages site settings.
1. Add the Copilot authentication app client ID to the bot consumer record.


## Step 1: Update the Power Pages site app registration

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select **+ Edit**.
1. Go to the **Set up** workspace.
1. Copy the Application ID associated with the site.
   :::image type="content" source="media/create-entra-id-for-agent/site-detail-app-id.png" alt-text="Screenshot showing Application ID in site detail":::
1. In the Azure portal, find the app registration with the same Application ID.

### Add required API permissions

Add the following delegated permissions:
1. Under **Manage**, select **API Permissions**.
2. Select **Add permission** and then select **Microsoft Graph**.
3. Select **Delegated permissions**.
4. Expand **OpenId permissions** and turn on **openid** and **profile**.
5. Select **Add permissions**.
6. Select **Add permission** and select **APIs my organization uses**.
7. Search **Power Platform API** and select it.
8. Select **Delegated permissions**.
9. Expand **CopilotStudio** and select **CopilotStudio.Copilots.Invoke**.
10. Select **Add permissions**.
11. Select **Grant admin consent**.
   :::image type="content" source="media/create-entra-id-for-agent/azure-grant-consent.png" alt-text="Screenshot showing grant admin consent option in Azure portal":::

## Step 2: Configure Microsoft Entra ID for agent

Refer to detailed steps in [Configure user authentication with Microsoft Entra ID](/microsoft-copilot-studio/configuration-authentication-azure-ad?tabs=fic-auth) for configuring authentication for an agent associated with Power Pages.

The app registration you use to configure the agent should allow token exchange between Power Pages site and agent. Follow these steps to enable it:

### Add the redirect URL

Add the Power Pages site URL as the redirect URL to the app you configured for the agent.
1. Under **Manage**, select **Authentication**.
2. Under **Redirect URI Configuration**, select **Add Redirect URI** , and then select **Single-page Application**.
3. Enter the Power Pages site URL (for example, `https://contoso.powerappsportals.com`).

### Add API permissions

1. Under **Manage**, select **API Permissions**.
2. Select **Add permission** and select **APIs my organization uses**.
3. Search for **Power Platform API** and select it.
4. Select **Delegated permissions**.
5. Expand **CopilotStudio** and select **CopilotStudio.Copilots.Invoke**.
6. Select **Add permissions**.
7. Select **Grant admin consent**.

### Enable single sign-on

1. Under **Manage**, select **Expose an API**.
1. Under **Authorized client applications**, select **Add a client application**.
1. Add the Power Pages site Application (client) ID.
1. Select **Authorized scopes** checkbox.
1. Select **Add permission**.
1. Copy the scope.

## Step 3: Update custom scopes of Power Pages site App registration

This step is optional and required to call Power Pages API from the agent. If you created an agent from a Power Pages site, you must:

1. In the Azure portal, select **Site App** registration.
1. Under **Manage**, select **API permissions**.
1. Select **Add a permission** and select **APIs my organization uses**.
1. Search for Agent App Application (client) ID and select it.
4. Select **Delegated permissions**.
1. Expand **Test** and select scope name defined in Agent App (for example, `Test.Read`).
1. Select **Add permission**.
1. Select **Grant admin consent**.
1. Select **Expose an API** and select the **Edit** button next to **Application ID URI**.

   > [!NOTE]
   > The Application ID URI must be in the format `api://<client id of the current application>`. This value might be different. Modify this value to properly reflect the current application.

1. Copy the scope.

## Step 4: Update scopes in Agent security configuration
You copied two scopes, one from each app registration. These scopes enable single sign-on (SSO) for the Power Pages site and grant the agent permission to access the Power Pages Web API.
1. Open **Agent** added to site.
2. Under **Settings**, select **Security** > **Authentication**.
3. Paste the Agent App scope under **Token exchange URL (required for SSO)**.
   :::image type="content" source="media/create-entra-id-for-agent/copilot-studio-token-exchange-url.png" alt-text="Screenshot showing token exchange url option in Copilot studio":::
5. Paste the Site App scope next to the existing scope.
   :::image type="content" source="media/create-entra-id-for-agent/copilot-studio-scopes.png" alt-text="Screenshot showing Scopes option in Copilot studio":::
7. Select **Save**.
8. Close the **Settings** page.
9. **Publish** agent.
   
   
## Step 5: Configure Power Pages site settings

In Power Pages, add or update the following site settings:

| Name | Value |
| --- | --- |
| Authentication/BearerAuthentication/Enabled | true |
| Authentication/BearerAuthentication/Provider | AzureAD |
| Authentication/BearerAuthentication/UseEntraV2Issuer | true |
| Authentication/BearerAuthentication/ValidIssuer | `https://login.microsoftonline.com/<tenant-id>/v2.0` |
| SiteCopilot/PVA/AuthenticationMethod | OpenIdConnect |

## Step 6: Add the Copilot authentication client ID to the bot consumer

1. Open the Power Pages site in edit mode.
1. Determine [site datamodel](/admin/enhanced-data-model#determine-whether-your-site-is-using-the-standard-or-enhanced-data-model)
1. Go to the [Data workspace](use-data-workspace.md)
1. Update Agent App ClientId to corresponding agent record

# [Standard data model](#tab/standard)

1. Search for and select the **Bot consumer** table.
1. Locate the row with the selected website name and agent schema name.
1. Add the following value `"clientId": "<AgentAppClientID>"` as shown in the following example.

   ```json
     {"botSchemaName":"cr720_agentSchema","clientId":"00000000-0000-0000-0000-000000000000"}
   ```
1. Save the record.
   
# [Enhanced data model](#tab/enhanced)

1. Search for and select the **Site Component** table.
1. Find the **Component Type** column and select the filter icon next to it.
1. Filter the records by selecting the **Bot Consumer** option.
1. Locate the row with the selected website name in the **Power Pages Site id** column and agent schema name.
1. Choose **Edit row using form**.
1. In **Content**, add the following value to the `configjson` node: `"clientId": "<AgentAppClientID>"` as shown in the following example.

   ```json
     {"botschemaname":"cr720_agentSchema","configjson":"{\"clientId\":\"00000000-0000-0000-0000-000000000000\",\"version\":\"v2\" }" ,"adx_botconsumer_adx_webrole":["00000000-0000-0000-0000-000000000000"] } 
   ```
1. Choose **Save & Close**.
1. Add the following value to the `configjson` node: `"clientId": "<AgentAppClientID>"` as shown in the following example.

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
