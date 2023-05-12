---
title: Enable chatbot in a Power Pages site (preview)
description: Learn how to enable chatbot in your Power Pages site.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/23/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Enable chatbot in a Power Pages site (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

A chatbot with AI can provide quick and efficient customer support to end users. It can answer their queries and provide solutions to their problems in a conversational manner, which can improve overall user experience. Now you can enable [Power Virtual Agents](/power-virtual-agents/nlu-boost-conversations) with a boost conversation powered chat bot on your site to assist end-users with quicker resolution of their queries.

:::image type="content" source="media/enable-chatbot/chatbot-preview.gif" alt-text="A GIF animation that explains how to add a chatbot to a page" border="false":::

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - To understand capabilities and limitations of AI-powered and Copilot features in Power Pages, see [Responsible AI transparency notes for Power Pages](../transparency-note.md).
> - Chatbot uses Power Virtual Agents boosted conversations capability and Bing Search to retrieve information from publicly available URLs. Your use of Bing Search is governed by the [Microsoft Services Agreement](https://go.microsoft.com/fwlink/?linkid=2178408) and [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Prerequisites

- Chatbot feature is available only for the site created in US region.
- You can enable this feature for the site created in English base language.
- To enable the chatbot, the site should be public. More information: [Site visibility in Power Pages](../security/site-visibility.md)
- Tenant Administrator can turn off the chatbot feature on Power Pages site by preventing [publishing of the bot](/power-virtual-agents/nlu-boost-conversations#publishing)
- Adding or changing the custom domain for a Power Pages site after the chatbot has been created isn't supported. Instead, disable the chatbot and enable it after making the custom domain changes.

## Enable chatbot

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/)

1. On the left-pane, select on **Set up**.

1. Under **Integrations,** select on **Chatbot (preview)**

    :::image type="content" source="media/enable-chatbot/select-chatbot.png" alt-text="A screenshot of Chatbot (preview) under Integrations." border="true":::

1. Toggle **Create and test chatbot** to create a bot for this site.

    > [!NOTE]
    > When you create a chatbot on the Power Pages site, a bot with boosted conversation is created in Power Virtual Agents.

    When you enable the chatbot on site, the site URL is passed to Bing for indexing. This process may take several hours to a day. To trigger Bing to index your site's content immediately, you can use Bing Webmaster. Learn more: [Force Bing webmaster to index your site](force-bing-index.md)

1. Test the chatbot by opening it Power Virtual Agents studio.

1. Publish the chatbot on Power Pages site.

## Publishing Chatbot

Publishing the chatbot on site is governed at **Power Platform Admin Center**. If you'd like to publish a bot, you need to ask your admin to enable it for your tenant in the **Power Platform admin center**. More information: [Publish chatbot with boosted conversations](/power-virtual-agents/nlu-boost-conversations#publishing)

## Advanced customization

The chatbot component is rendered using a web template called Power Virtual Agents.

:::image type="content" source="media/enable-chatbot/chatbot-web-template.png" alt-text="A screenshot of chatbot web template." border="false":::

You can change the values for the following parameters inside the **window.PvaEmbeddedWebChat.renderWebChat()** function.

:::image type="content" source="media/enable-chatbot/chatbot-parameters.png" alt-text="A screenshot of Chatbot Widget with each part numbered for reference." border="true":::

| Number | Parameter | Value |
|-------------------------|-------------------------|-------------------------|
| 1 | width | Uses variable "chatWidth". To change, update the width in pixels:<br /></br>let chatWidth = "320 px"; |
| 2 | height | Uses variable "chatHeight". To change, update the height in pixels:<br /></br>let chatHeight = "480 px"; |
| 3 | headerText | Title of the bot. By default, this parameter uses the bot's name. To change, add "headerText" parameter with the bot header value:<br /></br>"headerText": 'Contoso chatbot'; |
| 4: fontColor<br /></br>5: backgroundColor | webChatHeaderStyleOptions | Determines header style for the chatbot component, such as color of font and background. To change, update "webChatHeaderStyleOptions" parameter with the values for "fontColor" and "backgroundColor" properties:<br /></br>"webChatHeaderStyleOptions": {"fontColor":'black',"backgroundColor":'white'} |
| 6: backgroundColor<br /></br>7: bubbleBackgroundcolor<br /></br>8: bubbleTextColor<br /></br>9: bubbleFromUserBackground<br /></br>10: bubbleFromUserTextColor | webChatCanvasStyleOptions | Determines the chat canvas style for chatbot component, such as the background and bubble backgrounds from the chatbot and the user. To change, update "webChatCanvasStyleOptions" parameters with the values for "backgroundColor", "bubbleBackgroundcolor", "bubbleTextColor", "bubbleFromUserBackground", and "bubbleFromUserTextColor" properties:<br /></br>"webChatCanvasStyleOptions": {"backgroundColor": "#123FFF","bubbleBackground":"#2340F0","bubbleTextColor": "#323130","bubbleFromUserBackground": "#412644","bubbleFromUserTextColor": "#F345FF"} |
| 11: backgroundColor<br /></br>12: iconColor | webChatWidgetStyleOptions | Determines the style for the ChatWidget component, such as color of the icon and background. To change, update "webChatWidgetStyleOptions" parameter with the values for "backgroundColor" and "iconColor" properties:<br /></br>"webChatWidgetStyleOptions": {"backgroundColor": "#486744","iconColor": "#DF234F"} |

After changing the web template, ensure you select Sync configuration to update the configuration and reflect the changes.

## Known issues

- While you can enable the chatbot feature on sites created in non-US regions, the creation of the chatbot may not be successful.
- There's some background operation being performed after disabling the chatbot. If you try to enable the chatbot immediately after disabling it, it may result in failure.

### See also

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Force Bing webmaster to index your site](force-bing-index.md)
- [Create a form in a webpage using a Copilot](add-form-copilot.md)
- [Use Copilot to generate text and it to a webpage](add-text-copilot.md)