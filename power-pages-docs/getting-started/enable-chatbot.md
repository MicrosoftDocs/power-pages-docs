---
title: Add an AI-powered chatbot (preview)
description: Learn how to add an AI-powered chatbot to your Power Pages site for quicker customer support and an improved user experience.
ms.topic: how-to
ms.date: 09/07/2023
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: kkendrick
contributors:
  - nickdoelman
  - ProfessorKendrick
  - nageshbhat-msft
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:09/07/2023
  - bap-template
---

# Add an AI-powered chatbot (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

A chatbot with AI can provide quick and efficient customer support to your site's visitors and users, which can improve your site's overall user experience. Power Pages makes it easy to add one. In just minutes, you can create a [Power Virtual Agents](/power-virtual-agents/nlu-boost-conversations) bot on your site that uses *boosted conversations*&mdash;that is, natural language and generative answers&mdash;to answer questions and suggest solutions to issues in a conversational way.

> [!IMPORTANT]
>
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - [Understand the capabilities and limitations of AI-powered Copilot features in Power Pages](../transparency-note.md).
> - Chatbot uses Power Virtual Agents boosted conversations and Bing Search to retrieve information from publicly available URLs. Your use of Bing Search is governed by the [Microsoft Services Agreement](https://go.microsoft.com/fwlink/?linkid=2178408) and [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Prerequisites

To use AI-powered Copilot features in Power Pages:

- Your environment must be located in the United States.
- Your browser language must be set to US-English.
- Your tenant administrator must turn on the setting **Publish bots with boosted conversations** in the Power Platform admin center.

## Add a chatbot

1. Go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **Integrations,** select **Chatbot (preview)**

    :::image type="content" source="media/enable-chatbot/select-chatbot.png" alt-text="Screenshot of the Chatbot (preview) page in Power Pages.":::

1. Turn on **Create and test chatbot**.

    Power Pages creates a [bot with boosted conversation](/power-virtual-agents/nlu-boost-conversations) for you in Power Virtual Agents. 

1. To make the chatbot available to visitors and users, turn on **Publish chatbot on site**.

    If your tenant admin hasn't turned on publishing boosted bots, the **Publish chatbot on site** setting isn't available.

After you publish the chatbot on your site, the site URL is passed to Bing for indexing. The indexing process can take up to a day, but you can [force Bing to index your site's content immediately](force-bing-index.md).

## Customize your chatbot

When you create a chatbot for a website, the bot uses the hosting site's content to generate responses. Bing indexing is used for unauthenticated public site content, while Dataverse Copilot handles the indexing of private and authenticated user-specific content. 

Authenticated site users receive tailored, summarized answers that align with their web roles. To further improve the content model for authenticated site users, refine the data by following these steps: 

1. Open the chatbot.
1. Under **Refine your data**, choose the **Make changes** button.
1. Select **Choose tables lookup control** to select or deselect the tables. 
    - You can select multiple tables in this section. Ensure that any table you select here's used on the site. 
    - On subsequent pages, you must specify the page where the table is used for generating the citation URL. 
1. Choose **Next**. 
1. Under the **Choose table**, select the table that contains the columns and page link you wish to select.
    - You can select one table at a time. 
1. Under **Add page link**, select the page where table is used.  

    > [!NOTE]
    >
    > - Make sure you select the correct page where the table is used. Choosing the wrong table will result in the bot providing an incorrect citation URL for the answers.
    > - The page must use 'id' as the query string parameter; the citation URL will not function correctly if any other parameter name is used. 

1. Under **Choose columns**, select the list of columns that is used in page. 

    > [!NOTE]
    > Only a column with multiline text is available to choose.  

1. Select **Next** and review the selection. 
1. Choose **Save** to submit the changes. 

## Customize chatbot appearances

You can customize the chatbot's style by overriding the default Cascade Style Sheet (CSS) classes. To do so, add a style tag to the header template and follow these steps to override the values. 

1. Go to site's code editor.
1. From **Explorer navigation**, expand the **web-templates** folder. 
1. Open **Header.html**. 
1. Add your style tag. 
1. Override the respective styles.

### Chatbot widget

:::image type="content" source="media/enable-chatbot/open-chat-window-css.svg" alt-text="A screenshot of the chatbot widget.":::

Chatbot collapsed icon:

```css
.pva-embedded-web-chat-widget {
    	background-color: #484644;
	border: 1px solid #FFFFFF;	
}
```

Tooltip:

```css
.pva-embedded-web-chat-widget .pva-embedded-web-chat-widget-tooltip-text {
	background: white;
	color: #323130;
}
```
### Chatbot elements

Reference the CSS samples provided for examples of how to customize your chatbot's elements.

:::image type="content" source="media/enable-chatbot/chatbot-css.svg" alt-text="A screenshot of a chatbot with individual elements annotated.":::

#### 1. Header

```css
.pages-chatbot-header 
{ 
	background: #77a145;  
	color: #ffffff; 
}
```

#### 2. Height and Width

```css
.pva-embedded-web-chat[data-minimized='false'] {
 	height: 80%;
	width: 25%;
	max-width: 400px;
	max-height: 740px;
}
```

#### 3. Bot window

```css
.pva-embedded-web-chat-window { 
  background: white;  
} 
```

#### 4. Bubble from bot

Background color: 

```css
.webchat__bubble:not(.webchat__bubble--from-user) .webchat__bubble__content { 
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

#### 65. Bubble from user

Background color:

```css
.webchat__bubble.webchat__bubble--from-user .webchat__bubble__content { 
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

#### 7. Privacy message

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

## Known issues

- You can't change your site's custom domain after you add a chatbot. Instead, turn off the chatbot, change the custom domain, and then turn the chatbot on again.
- Although you can turn on the chatbot feature on sites that you create outside the United States, the chatbot might not be created.
- If you turn off the chatbot feature, allow a few minutes for background operations to complete before you turn it on again.

### See also

- [Create an AI-generated webpage using Copilot (preview)](../getting-started/create-page-copilot.md)
- [Create a form in a webpage using a Copilot (preview)](../getting-started/add-form-copilot.md)
- [Use Copilot to generate text and it to a webpage (preview)](../getting-started/add-text-copilot.md)
- [Force Bing webmaster to index your site (preview)](../getting-started/force-bing-index.md)
- [Add AI-generated code using Copilot (preview)](../configure/add-code-copilot.md)
