---
title: Use @Powerpages in GitHub Copilot Chat (preview)
description: Utilize @powerpages in GitHub Copilot Chat for seamless Power Pages coding assistance within Visual Studio Code. Enhance productivity without switching context.
author: neerajnandwana-msft

ms.topic: conceptual
ms.date: 7/19/2024
ms.subservice:
ms.author: nabha
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

# Use Copilot for Power Pages (@powerpages) participant within GitHub Copilot Chat (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The GitHub Copilot Chat architecture enables Visual Studio Code extensions to integrate their tools seamlessly with the GitHub Copilot Chat experience. This integration is achieved by creating chat extensions that use the GitHub Copilot Chat extension API, adding a Chat participant to the Visual Studio Code environment.

This feature allows @powerpages to be a participant in the Power Platform Tools Visual Studio Code extension. Users can now utilize the @powerpages participant within the GitHub Copilot chat to receive Power Pages-specific coding assistance without leaving their current work context. This integration ensures that users can make the most out of both Copilot environments.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisites

Before you can start using the Power Platform Tools Visual Studio Code extension with GitHub Copilot Chat, verify the following prerequisites:

- Visual Studio Code installed on your machine
- GitHub Copilot extension installed and configured
- Power Platform Tools Visual Studio Code extension installed

## Installation and setup

1. **Install Visual Studio Code:**

    If you haven't already, download and install [Visual Studio Code](https://code.visualstudio.com).
1. **Install GitHub Copilot Chat Extension:**

    Follow the [GitHub Copilot setup guide](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) to install and configure the Copilot extension in Visual Studio Code.
1. **Install [Power Platform Tools Visual Studio Code Extension](/power-platform/developer/howto/install-vs-code-extension):**

    1. Open Visual Studio Code.
    1. Go to the **Extensions** view by selecting the Extensions icon in the Activity Bar on the left side of the window or by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>X</kbd>.
    1. Search for *[Power Platform Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.powerplatform-vscode)*.
    1. Select **Install** to add the Power Platform extension to your Visual Studio Code environment.

## Use @powerpages participant in GitHub Copilot Chat for VS Code

Once the Power Platform Tools Visual Studio Code extension is installed, you can start using the @powerpages participant within the GitHub Copilot chat to receive targeted coding assistance for Power Pages.

To add the @powerpages participant to a chat:

1. **Open a Power Pages Project:**

    Open your existing Power Pages project or create a new one in Visual Studio Code.

1. **Activate GitHub Copilot Chat:**

    1. Open the Copilot chat interface.
    1. Verify the Copilot chat is active.

1. **Add the @powerpages participant:**

    In the Copilot chat, type *@powerpages* followed by your request. For example, *@powerpages write JavaScript code for form field validation to verify the phone field value is in the valid format*. Copilot provides responses tailored to Power Pages, helping you with writing or explaining code.

## Benefits of using Copilot for Power Pages in GitHub Copilot Chat

The following are some of the benefits of using Copilot for Power Pages in GitHub Copilot Chat:

- **Seamless workflow**

    No need to switch contexts between different tools. Get all the help you need directly within VS Code.
- **Enhanced productivity**
    
    Use the powerful capabilities of both GitHub Copilot and Power Pages without interruption.
- **Targeted assistance**

    Receive specialized help for Power Pages, ensuring that your queries are answered accurately and efficiently.

Learn more at [Power Platform Tools VS Code Extension](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.powerplatform-vscode) and [GitHub Copilot](https://aka.ms/github-copilot).
