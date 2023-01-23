---
title: "How to: Embed a chatbot on a webpage"
description: Learn how to embed a Power Virtual Agent chatbot on a webpage in Power Pages.
author: ckwan-ms
ms.topic: guidance
ms.custom: 
ms.date: 01/23/2023
ms.subservice:
ms.author: ckwan 
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ckwan-ms
---

# How to: Embed a chatbot on a webpage

The Power Pages design studio does not have the ability to directly add a chatbot component to a webpage. 

While you can [add a chatbot](/power-apps/maker/portals/add-chatbot) using the legacy portal Studio for websites created in Power Apps, the following steps provide an alternative method to embed a Power Virtual Agent chatbot on a Power Pages webpage.

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](../getting-started/trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](../getting-started/create-manage.md).
- A Power Virtual Agents subscription or trial. [Sign up for a Power Virtual Agents trial](/power-virtual-agents/sign-up-individual).
- A Power Virtual Agents chatbot. [Create and delete Power Virtual Agents bots](/power-virtual-agents/authoring-first-bot).

## Configure a channel for your chatbot

In the following steps we will get the chatbot embed code that we will use to embed into Power Pages.

1. The Power Virtual Agents home page, select **Publish** from the side menu.

1. In the **Optimize your bot** section, choose **Go to Channels**.

    :::image type="content" source="media/pva/pva-channels.png" alt-text="Select PVA channels.":::

1. In the **Channels** section, select **Custom website**.

1. In the slide-out panel in the **Default embed code** section, select and copy the code in the `<iframe></iframe>` HTML tags.

    :::image type="content" source="media/pva/embedcode.png" alt-text="Copying the embed code.":::

## Embed a chatbot to a webpage using the code editor

The following steps will show you how to embed the chatbot code on a webpage.

1. Go to [Power Pages](https://aka.ms/mpp).

1. Select **Edit** on the site you want to add a page. If you don't have a site, [create a site](../getting-started/create-manage.md) before continuing.

1. Locate or create a webpage where you want to host the chatbot.

1. Add a [section](../getting-started/add-sections.md) where you want to place the chatbot.

    > [!NOTE]
    > You may have to adjust the section height to accommodate your chatbot.

1. Select **Edit code**, followed by **Open Visual Studio Code**. This will open the Visual Studio for the Web interface.

1. Paste the `<iframe></iframe>` code you copied earlier in between the `<div></div>` tags of the section of the page.

    :::image type="content" source="media/pva/vscode-pva.png" alt-text="Adding PVA using VS Code for the Web.":::

1. Select **CTRL-S** to save the code.

1. In the Power Pages design studio, select **Sync** to update the webpage.

1. The chatbot should appear on the canvas.

## Testing your chatbot on Power Pages

1. Select **Preview**, followed by **Desktop** to preview the site

1. You should be able to view and interact with your chatbot.

    :::image type="content" source="media/pva/chatbot.png" alt-text="Use chatbot on webpage.":::

## See Also

- [Power Virtual Agents](/power-virtual-agents/)
- [Edit code with Visual Studio Code for the Web](../configure/visual-studio-code-editor.md)
