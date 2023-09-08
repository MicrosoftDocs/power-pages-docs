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

A chatbot with AI can provide quick and efficient customer support to your site's visitors and users, which can improve your site's overall user experience. Power Pages makes it easy to add one. With a couple of clicks, you can create a [Power Virtual Agents](/power-virtual-agents/nlu-boost-conversations) bot on your site that uses *boosted conversations*&mdash;that is, natural language and generative answers&mdash;to answer questions and suggest solutions to issues in a conversational way.

:::image type="content" source="media/enable-chatbot/chatbot-preview.gif" alt-text="A GIF animation that explains how to add a chatbot to a page" border="false":::<!-- EDITOR'S NOTE: Please replace the animated gif with a video IAW our new image guidelines, https://review.learn.microsoft.com/en-us/bacx/screenshots-for-bap?branch=main. -->

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
- [Your site's visibility](../security/site-visibility.md) must be public.
- Your tenant administrator must turn on the setting **Publish bots with boosted conversations** in the Power Platform admin center.

## Add a chatbot

1. Go to the [Set up workspace](setup-workspace.md).
1. Under **Integrations,** select **Chatbot (preview)**

    :::image type="content" source="media/enable-chatbot/select-chatbot.png" alt-text="Screenshot of the Chatbot (preview) page in Power Pages.":::

1. Turn on **Create and test chatbot**.

    Power Pages creates a [bot with boosted conversation](/power-virtual-agents/nlu-boost-conversations) for you in Power Virtual Agents. To test it, open the bot in the Power Virtual Agents studio.

1. To make the chatbot available to visitors and users, turn on **Publish chatbot on site**.

    If your tenant admin hasn't turned on publishing boosted bots, the **Publish chatbot on site** setting isn't available.

After you publish the chatbot on your site, the site URL is passed to Bing for indexing. The indexing process may take up to a day, but you can [force Bing to index your site's content immediately](force-bing-index.md).

## Customize your chatbot

The "look and feel" of your chatbot component is controlled by a web template called **Power Virtual Agents**. To change your chatbot's appearance, change the values of parameters in the `window.PvaEmbeddedWebChat.renderWebChat()` function in the template.

1. In the Power Pages design studio, select **More items** (**&vellip;**) > **Portal Management**.
1. In the sitemap under **Content**, select **Web Templates**.
1. Select the **Power Virtual Agents** template for your site.
1. In the **Source** box, edit the values under the `window.PvaEmbeddedWebChat.renderWebChat` function, which starts on line 20.
1. Select **Save & Close**.
1. Return to the Power Pages studio and select **Sync** to update your site's configuration and reflect your changes.

### Chatbot appearance parameters

The following screenshot and table describe the parameters you can change to customize the appearance of your chatbot. Line numbers given refer to the default Power Virtual Agents web template.

:::image type="content" source="media/enable-chatbot/chatbot-parameters.png" alt-text="Screenshot of the Power Pages chatbot, with each part numbered for reference.":::<!-- EDITOR'S NOTE: Where are 11 and 12? Also, please change the appearance of the numbered callouts in this screenshot IAW our new screenshot guidelines, https://review.learn.microsoft.com/en-us/bacx/screenshots-for-bap?branch=main. -->

| Number | Parameter | Value |
|-------------------------|-------------------------|-------------------------|
| 1 | width | Uses the value of the variable `chatWidth` (line 18), which is expressed in pixels. The default is `320px`. |
| 2 | height | Uses the value of the variable `chatHeight` (line 19), which is expressed in pixels. The default is `480px`. |
| 3 | headerText | Sets the title of the bot. The default is the bot's name. To change it, replace the default value `botTitle` with your text enclosed in quotation marks; for example,<br/>`"headerText": "Contoso bot",` |
| 4, 5 | webChatHeaderStyleOptions:<br/>fontColor (4), backgroundColor (5) | Styles the colors of the header text and background. To change them, add the `fontColor` and `backgroundColor` properties, enclosed in curly brackets and with color names or hex values enclosed in quotation marks, to the `webChatHeaderStyleOptions` parameter; for example:<br/>`"webChatHeaderStyleOptions": {"fontColor": "black","backgroundColor":"white"},` |
| 6&ndash;10 | webChatCanvasStyleOptions:<br/>backgroundColor (6),<br/>bubbleBackgroundcolor (7),<br/>bubbleTextColor (8),<br/>bubbleFromUserBackground (9),<br/>bubbleFromUserTextColor (10) | Styles the colors of the background and bubble backgrounds in the chat canvas, or the conversation between the chatbot and the user. To change them, add the `backgroundColor`, `bubbleBackgroundcolor`, `bubbleTextColor`, `bubbleFromUserBackground`, and `bubbleFromUserTextColor` properties, enclosed in curly brackets and with color names or hex values enclosed in quotation marks, to the `webChatCanvasStyleOptions` parameter; for example:<br/>`"webChatCanvasStyleOptions": {"backgroundColor": "#123FFF","bubbleBackground":"#2340F0","bubbleTextColor": "#323130","bubbleFromUserBackground": "#412644","bubbleFromUserTextColor": "#F345FF"},` |
| 11, 12 | webChatWidgetStyleOptions:<br/>backgroundColor (11), iconColor (12) | Styles the colors of the icon and background of the ChatWidget component. To change them, add the `backgroundColor` and `iconColor` properties, enclosed in curly brackets and with color names or hex values enclosed in quotation marks, to the `webChatWidgetStyleOptions` parameter; for example:<br/>`"webChatWidgetStyleOptions": {"backgroundColor": "#486744","iconColor": "#DF234F"},` |

## Known issues

- You can't change your site's custom domain after you add a chatbot. Instead, turn off the chatbot, change the custom domain, and then turn the chatbot on again.
- Although you can turn on the chatbot feature on sites that you create outside the United States, the chatbot may not be created.
- If you turn off the chatbot feature, allow a few minutes for background operations to complete before you turn it on again.

### See also

- [Overview of AI-powered and Copilot features in Power Pages (preview)](../configure/ai-copilot-overview.md)
- [Add an AI-generated form using Copilot (preview)](../getting-started/add-form-copilot.md)
- [Add AI-generated text using Copilot (preview)](../getting-started/add-text-copilot.md)
- [Get your site indexed faster (preview)](../getting-started/force-bing-index.md)
- [Publish a chatbot with boosted conversations](/power-virtual-agents/nlu-boost-conversations#disable-bot-publishing)
