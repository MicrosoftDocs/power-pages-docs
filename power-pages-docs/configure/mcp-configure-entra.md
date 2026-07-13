---
title: Setup identity provider for MCP in Power Pages
description: Learn how to configure Microsoft Entra ID or Microsoft Entra External ID for your Power Pages site. Follow step-by-step instructions to set up identity providers and API scopes.
author: shwetamurkute
ms.author: vipingulati
ms.reviewer: smurkute
ms.date: 07/13/2026
ms.topic: how-to
ms.collection: bap-ai-copilot
---


# Set up identity provider for MCP in Power Pages

This article shows you how to set up Microsoft Entra ID or Microsoft Entra External ID as an identity provider for your Power Pages site and configure it to expose the MCP scope. This is the first step for implementing MCP server in Power Pages.

You can choose between two options:
- **Microsoft Entra ID**: Standard identity provider with simpler configuration
- **Microsoft Entra External ID**: External customer identity and access management (CIAM) solution

## Prerequisites

Before you begin, ensure you have:

- A functional Power Pages site
- Maker or admin access to the Power Pages environment
- Access to an MCP protocol-compatible client (VS Code, Microsoft Copilot Studio)
- Access to the Microsoft Entra admin center with permissions to create app registrations


## Configure identity provider

In this section, you configure delegated access that MCP clients need to authenticate by using the Power Pages MCP server.

### [Microsoft Entra ID](#tab/entra-id)

If you want to use Microsoft Entra ID, follow the steps in the following sections to add a custom scope, create a new app registration, and assign delegated permissions. 

#### Expose a custom scope 

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/#home), and go to **App Registration**.
1. Copy the application ID of the portal from [Power Pages design studio](https://make.powerpages.microsoft.com) **Site Details** and paste it in the search bar. Select the application.
1. On the overview page of the application, expand **Manage**, select **Expose an API**, and then select **Add a scope**.
1. On the **Add a Scope** pane, configure the following settings:
   - **Scope name**: Enter an appropriate scope name.
   - **Who can consent**: Select the option that works best for your organization.
   - **Admin consent display name**: Enter an appropriate display name.
   - **Admin consent description**: Enter an appropriate description.
   - Select **Add scope** to complete.

#### Create a new app registration

1. Go to **App Registration**, and then select **New Registration**.
1. Enter a friendly name for your application (for example, MCP-Demo-Testing), and then select **Register**.

#### Assign delegated permissions to app registration 

1. Select **API permissions**, and then select **Add a permission**.
1. On the **Request API permissions** tab, select **APIs my organization uses**, search for the name of the Microsoft Entra ID app that you created earlier, and select it.
   :::image type="content" source="media/mcp-overview/api-search.png" alt-text="Screenshot of the API selection showing the search results for the organization's APIs.":::
1. Select the check box next to **MCP** and select **Add permissions**.
    :::image type="content" source="media/mcp-overview/select-permission.png" alt-text="Screenshot of the request API permissions with mcp checkbox selected.":::
1. From the left navigation, select **API permissions** again, and then select **Add a permission**. 
1. Select **Microsoft APIs** and then select **Microsoft Graph**.
   :::image type="content" source="media/mcp-overview/api-graph.png" alt-text="Screenshot of Request API permissions panel showing Microsoft APIs tab with Microsoft Graph option.":::
1. Select **Delegated permissions**, select the check boxes next to **openid** and **profile**, and then select **Add permissions**.
    :::image type="content" source="media/mcp-overview/delegated-permissions.png" alt-text="Screenshot showing delegated permissions selection with openid and profile permissions selected.":::
1. Select **Grant admin consent for [your tenant]**, and then select **Yes** to finish the permissions setup.

### [Microsoft Entra External ID](#tab/entra-external-id)

If you want to use Microsoft Entra External ID, follow the steps in this section to add a custom scope, create a new app registration, and assign delegated permissions. 

#### Expose a custom scope

1. In the [Microsoft Entra admin center](https://entra.microsoft.com/#home), select **App registrations** from the navigation pane.
1. Select the existing Microsoft Entra External ID application in your external tenant (the same one you previously used to configure the External ID identity provider). You can refer to [Configure site settings in Power Pages](/power-pages/security/authentication/entra-external-id#step-3-configure-site-settings-in-power-pages) to locate your application.
1. Select the application, select **Expose an API**, and then select **Add a scope**.
   :::image type="content" source="media/mcp-overview/entra-admin-expose-api.png" alt-text="Screenshot showing the Expose an API section with Add a scope button." lightbox="media/mcp-overview/entra-admin-expose-api.png":::
1. In the **Scope name** field, enter a friendly name, for example `mcp`, and configure the following settings:
   - **Who can consent**: Select the option that works for your organization.
   - **Admin consent display name**: Enter an appropriate display name.
   - **Admin consent description**: Enter an appropriate description.
   - Select **Add scope** to complete.

#### Create a new app registration

1. Select **App registrations**, and then select **New registration**.
1. Enter a name for your application and then select **Register**.
1. Create a user flow by following the steps in [create a user flow](../security/authentication/entra-external-id.md#create-a-user-flow).
1. Add your application to the user flow by following the steps in [add your application to the user flow](../security/authentication/entra-external-id.md#add-your-application-to-the-user-flow).
1. In the [Microsoft Entra admin center](https://entra.microsoft.com/#home), go to **App registrations**, select **All applications**, and locate the application you created.

#### Assign delegated permissions to app registration     

1. Select **API permissions**, and then select **Add a permission**.
1. On the **Request API permissions** tab, select **APIs my organization uses**, search for the name of the Microsoft Entra External ID app that you created earlier, and select it.
   :::image type="content" source="media/mcp-overview/api-search.png" alt-text="Screenshot of the API selection showing the search results for the organization's APIs.":::
1. Select the check box next to **MCP** and select **Add permissions**.
    :::image type="content" source="media/mcp-overview/select-permission.png" alt-text="Screenshot of the request API permissions with mcp checkbox selected.":::
1. From the left navigation, select **API permissions** again, and then select **Add a permission**. 
1. Select **Microsoft APIs** and then select **Microsoft Graph**.
   :::image type="content" source="media/mcp-overview/api-graph.png" alt-text="Screenshot of Request API permissions panel showing Microsoft APIs tab with Microsoft Graph option.":::
1. Select **Delegated permissions**, select the check boxes next to **openid** and **profile**, and then select **Add permissions**.
    :::image type="content" source="media/mcp-overview/delegated-permissions.png" alt-text="Screenshot showing delegated permissions selection with openid and profile permissions selected.":::
1. Select **Grant admin consent for [your tenant]**, and then select **Yes** to finish the permissions setup.

---


## Next steps

After you create and configure the third party app registration, configure the site settings for MCP server. 

> [!div class="nextstepaction"]
> [Configure site settings for MCP server](mcp-configure-site-settings.md)
