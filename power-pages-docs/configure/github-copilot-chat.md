---
title: Use Copilot for Power Pages participant within GitHub Copilot Chat for Visual Studio Code (preview)
description: Utilize @powerpages in GitHub Copilot Chat for seamless Power Pages coding assistance within Visual Studio Code. Enhance productivity without switching context.
author: neerajnandwana-msft

ms.topic: conceptual
ms.date: 09/16/2024
ms.subservice:
ms.author: nenandw
ms.reviewer: dmartens
contributors:
  - DanaMartens
  - neerajnandwana-msft
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-title
  - ai-seo-date:07/19/2024
  - ai-gen-desc
---

# Use Copilot for Power Pages (@powerpages) participant within GitHub Copilot Chat for Visual Studio Code (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The [GitHub Copilot Chat for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) architecture enables Visual Studio Code (VS Code) extensions to integrate their tools seamlessly with the GitHub Copilot Chat experience. This integration is achieved by creating chat extensions that use the GitHub Copilot Chat extension API, adding a Chat participant to the VS Code environment.

This feature allows @powerpages to be a participant in the Power Platform Tools VS Code extension. Users can now utilize the [Power Pages AI Code capabilities](add-code-copilot.md) by adding the @powerpages participant within GitHub Copilot chat without leaving their current work context. This integration ensures that users can make the most out of both Copilot capabilities.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

:::image type="content" source="media/github-copilot-chat/powerpages-participant-response.png" alt-text="Screenshot of a response from the Power Pages participant in GitHub Copilot within Visual Studio Code." lightbox="media/github-copilot-chat/powerpages-participant-response.png":::

## Prerequisites

Before you can start using the Power Platform Tools VS Code extension with GitHub Copilot Chat, verify the following prerequisites:

- [VS Code](https://code.visualstudio.com) installed on your machine
- [Power Platform Tools VS Code extension](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.powerplatform-vscode) installed
- [GitHub Copilot Chat extension](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) installed and configured

## Use the @powerpages participant in GitHub Copilot Chat for VS Code

Once the Power Platform Tools VS Code extension is installed along with GitHub Copilot Chat extension, you can start using the @powerpages participant within GitHub Copilot chat to receive targeted coding assistance for Power Pages.

To add the @powerpages participant to a chat:

1. **Open website content in VS Code:**

    Download website content using Power Platform CLI. To authenticate against a Microsoft Dataverse environment, and to download website content, refer to the tutorial [Use Microsoft Power Platform CLI with Power Pages - download website content](power-platform-cli-tutorial.md#step-3-download-website-content).

    The Power Platform Tools Extension automatically enables using Microsoft Power Platform CLI commands from within Visual Studio Code through [Visual Studio Code Integrated Terminal](https://code.visualstudio.com/docs/editor/integrated-terminal).

1. **Activate GitHub Copilot Chat:**

    1. Open the Copilot chat interface by selecting the Chat icon in the left navigation bar.

        :::image type="content" source="media/github-copilot-chat/copilot-chat-icon.png" alt-text="Screenshot of the Copilot chat icon in Visual Studio Code.":::

    1. Verify the Copilot chat is active.

        :::image type="content" source="media/github-copilot-chat/github-copilot-chat.png" alt-text="Screenshot of the GitHub Copilot chat experience in Visual Studio Code.":::

1. **Add the @powerpages participant:**

    In the Copilot chat, type *@powerpages* followed by your request. For example, you could say `@powerpages write JavaScript code for form field validation to verify the phone field value is in the valid format` or ask `@powerpages Explain the following code {% include 'Page Copy'%}`. Copilot provides responses tailored to Power Pages, helping you with [writing](add-code-copilot.md#use-copilot-to-generate-code) or [explaining](add-code-copilot.md#use-explain-to-understand-code) code.

    :::image type="content" source="media/github-copilot-chat/power-pages-participant.png" alt-text="Screenshot of adding the powerpages participant to the GitHub Copilot chat in Visual Studio Code.":::

## Related information

- [Power Platform Tools VS Code Extension](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.powerplatform-vscode)
- [GitHub Copilot](https://aka.ms/github-copilot)
