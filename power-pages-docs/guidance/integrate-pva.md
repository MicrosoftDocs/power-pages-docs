---
title: "How to: Embed a chatbot on a webpage"
description: Learn how to embed a Power Virtual Agent chatbot on a webpage in Power Pages.
author: neerajnandwana-msft
ms.topic: guidance
ms.custom: 
ms.date: 01/23/2023
ms.subservice:
ms.author: nenandw 
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - neerajnandwana-msft
---

# How to: Embed a chatbot on a webpage

The Power Pages design studio does not have the ability to directly add a chatbot component to a webpage. 

> [!NOTE]
> You can [add a chatbot](/power-apps/maker/portals/add-chatbot) using the legacy portal Studio for websites created in Power Apps.

The following steps provide an alternative pro-developer method to embed a Power Virtual Agent chatbot on a Power Pages webpage.

> [!CAUTION]
> Adding a chatbot with this method has the following limitations:
> - You will only be able to edit the bot attributes by modifying the Power Virtual Agents web template.
> - You will only be able to enable the chatbot for the entire site.
> - You will not be able to enable the chatbot only for specific pages.

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](../getting-started/trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](../getting-started/create-manage.md).
- A Power Virtual Agents subscription or trial. [Sign up for a Power Virtual Agents trial](/power-virtual-agents/sign-up-individual).
- A Power Virtual Agents chatbot. [Create and delete Power Virtual Agents bots](/power-virtual-agents/authoring-first-bot).

## Locate environment id and chatbot id

In the following steps we will get the chatbot environment id and chatbot id that we will use to embed into Power Pages.

1. The Power Virtual Agents home page, select **Publish** from the side menu.

1. In the **Optimize your bot** section, choose **Go to Channels**.

    :::image type="content" source="media/pva/pva-channels.png" alt-text="Select PVA channels.":::

1. In the **Channels** section, select **Custom website**.

1. In the slide-out panel in the **Default embed code** section, select and copy the GUID following the `/environments/` path (this is the **environment id**) and the code following the `/bots/` path (this is the **chatbot id**).

    :::image type="content" source="media/pva/embedcode.png" alt-text="Copying the embed code.":::

## Update the Power Virtual Agents web template

In order to surface a chatbot on site created in Power Pages, you will need to modify the Power Virtual Agents web template.

1. Launch the [Portals Management app](../configure/portal-management-app.md).

1. Locate the **Web Templates** section under the **Content** area, and choose the **Power Virtual Agents** web template.

1. Make the following changes to the web template:

    1. Comment out the `var botConfig = {{botConfig}}` line.

        ```html
        //var botConfig = {{botConfig}}
        ```

    1. Immediately following this line, add the following code:

        ```html
        var botConfig = { 
                        "webChatHeaderStyleOptions": { 
                            "fontColor": "#2E456B", 
                            "backgroundColor": "#FEA002" 
                            }, 
                        "webChatCanvasStyleOptions": { 
                            "backgroundColor": "#FFFFFF", 
                            "bubbleBackground": "#88ABA2", 
                            "bubbleTextColor": "#505254", 
                            "bubbleFromUserBackground": "#88ABA2", 
                            "bubbleFromUserTextColor": "#505254" 
                            }, 
                        "webChatWidgetStyleOptions": { 
                            "iconColor": "#2E456B", 
                            "backgroundColor": "#FEA002" 
                            } 
                        }; 
        ```    
    1. Replace the values for the `botSchemaName` and `environmentId` with the values you copied from the chatbot embed code.
    
        Old values:
        ```html
        "botSchemaName": "{{ botconsumer.adx_botschemaname }}",
        "environmentId": "{{ env.Id }}",
        ```
        
        Updated values (example):
        ```html
        "botSchemaName": "new_bot_aff793eefd684ab08b5867034fe6dfec",
        "environmentId": "2b8b33f0-be5d-efa0-86a7-c7395204ed15",
        ```
1. Select **Save**.

1. The updated web template should look like the following:

```html
<!-- Power virtual agents web template V2.0-->
{% assign botconsumer = entities.adx_botconsumer[bot_consumer_id] %}
{% assign env = environment %}
{% assign languageCode = website.selected_language.code %}
{% assign botConfig = botconsumer.adx_configjson %}
<div class="pva-floating-style">
    <div name="webChat"></div>
    <script type="text/javascript" id="pvaChatInlineScript">
        var script = document.createElement('script');
        script.onload = function() {
            //var botConfig = {{botConfig}};
            var botConfig = { 
                            "webChatHeaderStyleOptions": { 
                                "fontColor": "#2E456B", 
                                "backgroundColor": "#FEA002" 
                                }, 
                            "webChatCanvasStyleOptions": { 
                                "backgroundColor": "#FFFFFF", 
                                "bubbleBackground": "#88ABA2", 
                                "bubbleTextColor": "#505254", 
                                "bubbleFromUserBackground": "#88ABA2", 
                                "bubbleFromUserTextColor": "#505254" 
                                }, 
                            "webChatWidgetStyleOptions": { 
                                    "iconColor": "#2E456B", 
                                    "backgroundColor": "#FEA002" 
                                } 
                            }; 
            // Learn more about advanced configuration: https://go.microsoft.com/fwlink/?linkid=2147420
            const webChatHeaderStyleOptions = botConfig?.webChatHeaderStyleOptions;
            const webChatCanvasStyleOptions = botConfig?.webChatCanvasStyleOptions;
            const webChatWidgetStyleOptions = botConfig?.webChatWidgetStyleOptions;
            const botTitle = botConfig?.headerText;
            let chatWidth = "320px";
            let chatHeight =  "480px";
            window.PvaEmbeddedWebChat.renderWebChat(
            {
                "container": document.getElementsByName('webChat')[0],
                "botSchemaName": "new_bot_aff793eefd684ab08b5867034fe6dfec",
                "environmentId": "2b8b33f0-be5d-efa0-86a7-c7395204ed15",
                "width": chatWidth,
                "height": chatHeight,
                "client": "msportals", // client and version is needed for the ease of future breaking changes
                "version": "v1",
                "headerText": botTitle,
                "webChatCanvasStyleOptions": webChatCanvasStyleOptions,
                "webChatHeaderStyleOptions": webChatHeaderStyleOptions,
                "webChatWidgetStyleOptions": webChatWidgetStyleOptions,
                "accessibilityLanguage": "{{languageCode}}"
            });
        }
        script.src = "https://embed.powerva.microsoft.com/webchat/embedded.js?client=msportals&version=v1";
        document.getElementsByTagName('head')[0].appendChild(script);
    </script>
</div>
```

## Modify the website header

Code will need to be added to the header in order to surface the chatbot on the Power Pages site.

1. Go to [Power Pages](https://aka.ms/mpp).

1. Select **Edit** on the site you want to add the chatbot. 

1. In the design studio Pages workspace, select the header section on the canvas and select **Edit code**.

    :::image type="content" source="media/pva/edit-header-code.png" alt-text="Edit header code.":::

1. Select **Open Visual Studio Code**

1. Using the **chatbot id** you copied from Power Virtual Agents, paste the following line of code at the end of the **Header.html** file:

    ```html
    {% include 'Power Virtual Agents' bot_consumer_id: "new_bot_aff793eefd684ab08b5867034fe6dfec" %} 
    ```

1. Select **CTRL-S** to save the code.

    :::image type="content" source="media/pva/vscode-pva.png" alt-text="Adding PVA using VS Code for the Web.":::

1. In the Power Pages design studio, select **Sync** to update the webpage.

1. The chatbot should appear on the canvas.

## Testing your chatbot on Power Pages

1. Select **Preview**, followed by **Desktop** to preview the site

1. You should be able to view and interact with your chatbot.

    :::image type="content" source="media/pva/chatbot.png" alt-text="Use chatbot on webpage.":::

## See Also

- [Power Virtual Agents](/power-virtual-agents/)
- [Edit code with Visual Studio Code for the Web](../configure/visual-studio-code-editor.md)
