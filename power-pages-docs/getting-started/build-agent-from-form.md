---
title: Build an agent from a form
description: Learn how to create, configure, and customize AI agents directly from Power Pages forms, including authentication, security, and appearance options.
author: DanaMartens
contributors:
ms.topic: how-to
ms.date: 06/20/2025
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

//Possibly add to separate topic

## Configure user authentication

\<New page\>

When you associate an agent with Power Pages, the site enables **single
sign-on (SSO)**, so users don't need to sign in separately to
use the agent. Power Pages supports these authentication
types:

1. **No Authentication**

    The agent can be accessed without requiring user authentication. This option is the default setting when an agent is created from a form.

1. **Token passthrough Authentication**

    The agent uses Power Pages’ authentication service. When you set up the implicit flow, the agent supports all identity providers set up in the Power Pages site.

    > [!NOTE]
    > Agents configured with token passthrough authentication can't be tested directly within of Microsoft Copilot Studio, as they require sign-in through the Power Pages site.

    To set up token [passthrough authentication](/microsoft-copilot-studio/configure-sso-3p), select the service provider as **Generic OAuth 2** and update all other values as **placeholder**.

    | Authentication/BearerAuthentication/Enabled | True |
    | :------------------------------------------ | :--- |

1. **Token based authentication**

    In this method, Power Pages passes the authenticated user’s token to Copilot Studio. Microsoft Copilot Studio then handles authentication. This setup lets you test the agent directly in Copilot Studio.

    Select **Generic OAuth 2** as the service provider. Power Pages doesn't currently support other service providers.

    For detailed setup steps, see [Security Configuration](/microsoft-copilot-studio/configuration-end-user-authentication#authenticate-manually) in Copilot Studio.

    To enable this setup, add these site settings:

    | Setting                                             | Value      |
    | :-------------------------------------------------- | :--------- |
    | Authentication/ApplicationCookie/SlidingExpiration   | True       |
    | Authentication/BearerAuthentication/Enabled         | True       |
    | Authentication/BearerAuthentication/Provider        | Provider name  <br>Provider name extracted from existing settings for the provider  <br>Authentication/OpenIdConnect/{ProviderName}/Issuer  <br>For example, if the setting for Azure AD had **Authentication/OpenIdConnect/AzureAD/Issuer, then AzureAD is the provider** |

## Add or replace a custom agent created in Microsoft Copilot Studio in Power Pages



## Customize appearance of the agent widget

//Needs to be completed

### Old widget vs new widget

#### Copilot collapsed icon

```css
.pva-embedded-web-chat-widget {
  background-color: #484644;
  border: 1px solid #FFFFFF;
}
```

#### Tooltip

```css
.pva-embedded-web-chat-widget-tooltip-text {
  background: white;
  color: #323130;
}
```


### Agent elements

The CSS samples in this section show how to customize each numbered chatbot element in the following screenshot.

#### 1. Header

```css
.pages-chatbot-header {
  background: #77a145;
  color: #ffffff;
}
```

#### 2. Height and width settings

```css
.pva-embedded-web-chat-window-container {
  height: 80%;
  width: 25%;
  max-width: 400px;
  max-height: 740px;
}
```

#### 3. Copilot window

```css
.pva-embedded-web-chat-window {
  background: white;
}
```

#### 4. Bubble from the copilot

Background color:

```css
.webchat__bubble:not(.webchat__bubble--from-user)
.webchat__bubble__content {
  background-color: #77a145 !important;
  border-radius: 5px !important;
}
```

Text color:

```css
.webchat__bubble:not(.webchat__bubble--from-user) p {
  color: #ffffff;
}
```

#### 5. Bubble from the user

Background color:

```css
.webchat__bubble.webchat__bubble--from-user
.webchat__bubble__content {
  background-color: #797d81 !important;
  border-radius: 5px !important;
}
```

Text color:

```css
.webchat__bubble.webchat__bubble--from-user p {
  color: #ffffff;
}
```

#### 6. Reference links

```css
.webchat__link-definitions__badge {
  color: blue !important;
}

.webchat__link-definitions__list-item-text {
  color: blue !important;
}

.webchat__render-markdown__pure-identifier {
  color: blue !important;
}
```

#### 7. Privacy message settings

Background color:

```css
.pva-privacy-message {
  background: #797d81;
}
```

Text color:

```css
.pva-privacy-message p {
  color: #ffffff;
  font-size: 12px;
  font-weight: 400;
}
```

//THE FOLLOWING CONTENT WILL MOVE TO A SEPARATE TOPIC:

## Develop intelligent components in Pages using Agent SDK

The Agent SDK lets you create intelligent web pages by extending AI capabilities beyond the standard chat widget, while fully honoring Power Pages' end-user authentication and authorization.

The ‘SendActivity’ function facilitates communication between developers
and agents using the Direct Line API. It manages the creation of a
Direct Line connection, handles token management, and sends activities
to the agent. Additionally, it supports handling multiple responses from
the agent using a subscriber function. This function is part of the
\$pages client API and can be used to send messages or invoke events to
the agent.

### Function Signature

The SendActicity function is exposed under the \`\$pages\` client API
and can be called as follows:

> \$pages.agent.SendActivity(
>
> agentSchemaName: string,
>
> inputActivity: [InputActivity](#_InputActivity_Object),
>
> responseSubscriber: [ResponseSubscriber](#_ResponseSubscriber),
>
> errorSubscriber: [ErrorSubscriber](#_ErrorSubscriber)
>
> );

### Parameters

- agentSchemaName: string - The schema name of the agent to send the activity to.

- inputActivity: [InputActivity](bookmark://_InputActivity_Object) - The object with the text or event to send to the agent.

- responseSubscriber: [ResponseSubscriber](bookmark://_ResponseSubscriber) - The callback function that's called with the agent's response whenever a response is received.

- errorSubscriber: [ErrorSubscriber](bookmark://_ErrorSubscriber) - The callback function to handle errors.

Return type: void - The function doesn't return anything.

### Example

To handle agent responses and errors, define responseSubscriber and errorSubscriber as callback functions.

```javascript
const responseSubscriber = (response) => {
  // replace with your response handling
  console.log('Agent response:', response);
};

const errorSubscriber = (error) => {
  // replace with your error handling
  console.error('Error:', error);
};

const agentSchemaName = '<AgentSchemaName>'; // Replace <AgentSchemaName> with your agent schema name
```

### Send a message to the agent

```javascript
const inputActivity = {
  text: 'Hello, agent!', // message to the agent
};

$pages.agent.SendActivity(agentSchemaName, inputActivity, responseSubscriber, errorSubscriber);
```

## Related information

- [Add an agent - overview](add-agent-overview.md)
- [Add an agent to your Power Pages site](enable-agent.md)
- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
- [Add an AI-powered chatbot with Power Pages (video)](https://youtu.be/ohANXe1bfos?feature=shared)
