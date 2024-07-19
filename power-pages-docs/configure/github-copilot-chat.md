---
title: Use Copilot for Power Pages (@powerpages) participant within GitHub Copilot Chat in Visual Studio Code (preview)
description: Learn how to use Copilot for Power Pages (@powerpages) as a participant within GitHub Copilot Chat in Visual Studio Code.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 7/19/2024
ms.subservice: 
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - DanaMartens
    - neerajnandwana-msft
---

# Use Copilot for Power Pages (@powerpages) participant within GitHub Copilot Chat (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The GitHub Copilot Chat architecture allows Visual Studio Code extensions to seamlessly integrate their tools with the GitHub Copilot Chat experience. This is accomplished through the creation of chat extensions that utilize the GitHub Copilot Chat extension API, contributing a Chat participant to the Visual Studio Code environment.

With this feature, we're enabling @powerpages as a participant in the Power Platform Tools Visual Studio Code extension, so users can use the @powerpages participant within the GitHub Copilot chat to receive Power Pages specific coding assistance, without leaving the context of their current work. This integration ensures that users can make the most out of both Copilot environments.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisites

Before you can start using the Power Platform Tools Visual Studio Code extension with GitHub Copilot Chat, verify the following prerequisites:

- Visual Studio Code installed on your machine
- GitHub Copilot extension installed and configured
- Power Platform Tools Visual Studio Code extension installed

## Installation and setup

1. Install Visual Studio Code:

    If you haven't already, download and install [Visual Studio Code](https://code.visualstudio.com).
1. Install GitHub Copilot Chat Extension:

    Follow the [GitHub Copilot setup guide](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) to install and configure the Copilot extension in Visual Studio Code.
1. Install [Power Platform Tools Visual Studio Code Extension](/power-platform/developer/howto/install-vs-code-extension)

    1. Open Visual Studio Code.
    1. Go to the **Extensions** view by selecting the Extensions icon in the Activity Bar on the side of the window or by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>X</kbd>.
    1. Search for *[Power Platform Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.powerplatform-vscode)*.
    1. Select **Install** to add the Power Platform extension to your Visual Studio Code environment.

## Use @powerpages Participant in GitHub Copilot Chat for VS Code

Once the Power Platform Tools VS Code extension is installed, you can start using the @powerpages participant within the GitHub Copilot chat to receive targeted coding assistance for Power Pages. Here's how:

1. Open a Power Pages Project:

    Open your existing Power Pages project or create a new one in Visual Studio Code.

1. Activate GitHub Copilot Chat:

    1. Open the Copilot chat interface.
    1. Verify the Copilot chat is active.

1. Add the @powerpages participant:

    In the Copilot chat, type *@powerpages* followed by your request. For example, *@powerpages write JavaScript code for form field validation to verify the phone field value is in the valid format*. Copilot provides responses tailored to Power Pages, helping you with writing or explaining code.

## Benefits of using Copilot for Power Pages in GitHub Copilot Chat

- Seamless Workflow: No need to switch contexts between different tools. Get all the help you need directly within VS Code.
- Enhanced Productivity: Use the powerful capabilities of both GitHub Copilot and Power Pages without interruption.
- Targeted Assistance: Receive specialized help for Power Pages, ensuring that your queries are answered accurately and efficiently.

Learn more at [Power Platform Tools VS Code Extension](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.powerplatform-vscode) and [GitHub Copilot](https://aka.ms/github-copilot).
