---
title: Customize your agent
description: Learn how to customize an agent experience in Microsoft Power Pages in this step-by-step guide.
ms.topic: how-to
ms.date: 07/23/2025
ms.update-cycle: 180-days
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

# Customize your agent

When you create an agent for a website, it uses the content from the hosting site to generate responses. Microsoft Dataverse indexes site content and configured tables. Copilot Studio summarizes the indexed content and tables to generate responses.

Authenticated site users get tailored, summarized answers aligned with their web roles. Improve the content model for authenticated site users by refining the data with these steps:

1. In Power Pages, go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **Copilot**, select **Add agent**.
1. Under **Refine your data**, select **Make changes**.
1. Select **Choose tables lookup control** to choose or clear tables.

    - You can select multiple tables in this section. Ensure that every table you choose is used on the site.
    - On subsequent pages, specify the page where the table is used to generate the citation URL.

1. Select **Next**.
1. Under **Choose tables**, select the table that contains the columns and the page link that you want to select. A table appears only if it has at least one multiline column.

    You can select only one table at a time.

1. Under **Add page link**, select the page where the table is used.

    > [!NOTE]
    > - Ensure that you select the correct page. Otherwise, the bot provides an incorrect citation URL for the answers.
    > - The page must use `id` as the query string parameter. If you use any other parameter name, the citation URL doesn't work correctly.

1. Under **Choose columns**, select the columns used on the page. Only columns with multiline text are available for selection.
1. Select **Next**, and review your selection.
1. Select **Save** to submit the changes.

## Customize the agent appearance

You can customize the agent's style by overriding the default Cascading Style Sheet (CSS) classes. To do this, add a `style` element to the header template and override the values by following these steps:

1. Open the site's [code editor](../configure/visual-studio-code-editor.md).
1. In the **Explorer** navigation, expand the **web-templates** folder.
1. Open **Header.html**.
1. Add your `style` or `script` element.

    :::image type="content" source="media/enable-chatbot/code-editor.png" alt-text="Screenshot of Visual Studio, highlighting the web-templates folder, the Header.html file, and the style element with a CSS selector.":::

1. Override the appropriate styles.

### Agent widget

If you have an existing agent created prior to July 2025, you may have a different agent experience than the latest.

# [Classic](#tab/classic)

:::image type="content" source="media/enable-chatbot/open-chat-window-css.svg" alt-text="Screenshot of the classic chatbot widget.":::

Agent collapsed icon:

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

Icon image:

```script
<script>
document.addEventListener('DOMContentLoaded', function() {
   var buttons = document.getElementsByClassName("pva-embedded-web-chat-widget");
    buttons[0].innerHTML = '<img src="<image URL>" height= "70px" width = "70px" />';
}, false);
</script>
```

 > [!NOTE]
 > Replace `<image URL>` with the actual image source URL. Use an external path or upload an image to the [Web File](../configure/web-files.md) table and use its URL.

# [New](#tab/new)

:::image type="content" source="media/enable-chatbot/open-chat-window-css.svg" alt-text="Screenshot of the chatbot widget.":::

Agent collapsed icon:

```css
.pva-embedded-web-chat-widget {
  background-color: #484644;
  border: 1px solid #FFFFFF;
}
```

Tooltip:

```css
.pva-embedded-web-chat-widget-tooltip-text {
  background: white;
  color: #323130;
}
```

Icon image:

```script
<script>
document.addEventListener('DOMContentLoaded', function() {
   var buttons = document.getElementsByClassName("pva-embedded-web-chat-widget");
    buttons[0].innerHTML = '<img src="<image URL>" height= "70px" width = "70px" />';
}, false);
</script>
```

 > [!NOTE]
 > Replace `<image URL>` with the actual image source URL. Use an external path or upload an image to the [Web File](../configure/web-files.md) table and use its URL.

---

### Agent elements

The CSS samples in this section provide examples that show how to customize each of the numbered chatbot elements in the following screenshot. Select the tab that matches the experience for your agent.

# [Classic](#tab/classic)

:::image type="content" source="media/enable-chatbot/chatbot-css-legacy.svg" alt-text="Screenshot of a classic chatbot with individual elements called out and numbered.":::

### 1 - Header

```css
.pages-chatbot-header
{
    background: #77a145;
    color: #ffffff;
}
```

### 2- Height and width settings

```css
.pva-embedded-web-chat[data-minimized='false'] {
    height: 80%;
    width: 25%;
    max-width: 400px;
    max-height: 740px;
}
```

### 3 - Agent window

```css
.pva-embedded-web-chat-window {
    background: white;
}
```

### 4 - Bubble from an agent

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

### 5 - Bubble from the user

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

### 6 - Reference links

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

### 7 - Privacy message settings

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

# [New](#tab/new)

:::image type="content" source="media/enable-chatbot/chatbot-css.png" alt-text="Screenshot of a chatbot with individual elements called out and numbered.":::

### 1 - Header

```css
.pages-chatbot-header {
  background: #77a145;
  color: #ffffff;
}
```

### 2 - Height and width settings

```css
.pva-embedded-web-chat-window-container {
  height: 80%;
  width: 25%;
  max-width: 400px;
  max-height: 740px;
}
```

### 3 - Copilot window

```css
.pva-embedded-web-chat-window {
  background: white;
}
```

### 4 - Bubble from the copilot

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

### 5 - Bubble from the user

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

### 6 - Reference links

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

### 7 - Privacy message settings

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

---

## Related information

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Generate answers from public data using Bing search](../getting-started/force-bing-index.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
