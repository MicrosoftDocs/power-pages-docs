---
title: Customize your copilot
description: Learn how to customize the copilot experience in Microsoft Power Pages with this step-by-step guide.
ms.topic: how-to
ms.date: 10/22/2024
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection: 
  - bap-ai-copilot
contributors:
  - nageshbhat-msft
  - DanaMartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:09/07/2023
  - bap-template
---

# Customize your copilot

When you create a copilot for a website, the copilot uses the content from the hosting site to generate responses. Dataverse indexes site content and configured tables, which Copilot Studio summarizes to generate responses.

Authenticated site users receive tailored, summarized answers that align with their web roles. To improve the content model for authenticated site users, refine the data by following these steps:

1. Go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **Copilot**, select **Add copilot**.
1. Under **Refine your data**, choose the **Make changes** button.
1. Select **Choose tables lookup control** to select or deselect the tables.
    - You can select multiple tables in this section. Ensure any table you select here is used on the site.
    - On subsequent pages, specify the page where the table is used for generating the citation URL.
1. Select **Next**.
1. Under **Choose tables**, select the table that contains the columns and page link you wish to select. The table doesn't appear unless it has at least one multi-line column.
    - You can select one table at a time.
1. Under **Add page link**, select the page where the table is used.  

    > [!NOTE]
    >
    > - Ensure you select the correct page where the table is used. Choosing the wrong table will result in the bot providing an incorrect citation URL for the answers.
    > - The page must use 'id' as the query string parameter. The citation URL doesn't function correctly if you use any other parameter name.

1. Under **Choose columns**, select the list of columns that are used in the page. Only columns with multiline text are available to choose.  

1. Select **Next** and review your selection.
1. Select **Save** to submit the changes.

## Customize copilot appearances

You can customize the copilot's style by overriding the default Cascading Style Sheet (CSS) classes. To do so, add a style tag to the header template and follow these steps to override the values.

1. Go to the site's [code editor](../configure/visual-studio-code-editor.md).
1. From **Explorer navigation**, expand the **web-templates** folder.
1. Open **Header.html**.
1. Add your style tag.
    :::image type="content" source="media/enable-chatbot/code-editor.png" alt-text="A screenshot of Visual Studio with a folder, file, and CSS selector emphasized.":::
1. Override the respective styles.

### Copilot widget

:::image type="content" source="media/enable-chatbot/open-chat-window-css.svg" alt-text="A screenshot of the chatbot widget.":::

Copilot collapsed icon:

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

### Copilot elements

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

#### 2. Height and width

```css
.pva-embedded-web-chat[data-minimized='false'] {
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

#### 4. Bubble from copilot

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

#### 5. Bubble from user

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

### Related information

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Generate answers from public data using Bing search](../getting-started/force-bing-index.md)
- [Responsible AI: FAQ for site copilot](../faqs-chatbot.md)
