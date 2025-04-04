---
title: Use the Visual Studio Code extension 
description: Learn about how to use the Visual Studio Code extension for Power Pages and integrate with Microsoft Power Platform CLI for CI/CD.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 01/15/2025
ms.subservice: 
ms.author: nenandw
ms.reviewer: dmartens
contributors:
    - neerajnandwana-msft
---

# Use the Visual Studio Code extension

Visual Studio Code is a lightweight, powerful source code editor for Windows, macOS, and Linux. It supports JavaScript, TypeScript, and Node.js and has a rich ecosystem of extensions for other languages like C++, C#, Java, Python, PHP, and Go, and runtimes like .NET and Unity. Learn more about Visual Studio Code in [Get started with VS Code](https://code.visualstudio.com/docs/getstarted/introvideos).

Visual Studio Code allows you to extend your capability through
[extensions](https://code.visualstudio.com/docs/introvideos/extend). Visual Studio Code
extensions can add more features to the overall experience. With the release of
this feature, you can now use the Visual Studio Code extension to work with Power Pages.

### Visual Studio Code extension for Power Pages

The **Power Platform Tools** adds the capability to configure websites using Visual Studio Code, and use the built-in Liquid language [IntelliSense](https://code.visualstudio.com/docs/editor/intellisense) enabling help with code completion, assistance, and hinting while customizing websites interface using Visual Studio Code. Using the Visual Studio Code extension, you can also configure portals through the [Microsoft Power Platform CLI](power-platform-cli.md).

> [!NOTE]
> - You need to ensure that [node.js](https://nodejs.org/en/download) is downloaded and installed on the same workstation as Visual Studio Code for the Power Pages features to work.
> - Make sure that only **Power Platform Tools** are installed and not both **Power Platform Tools** and **Power Platform Tools [PREVIEW]**. See [known issues](../known-issues.md#visual-studio-code-extension-for-power-pages) for details.

:::image type="content" source="media/vs-code-extension/install-pp-tools.gif" alt-text="Animation that explains how to install and set Power Platform Tools.":::

## Prerequisites

Before using the Visual Studio Code extension for Power Pages, you must:

- Download, install, and configure Visual Studio Code. More information: [Download Visual Studio Code](https://code.visualstudio.com/Download)

- Configure your environment and system for Power Pages CI/CD support using CLI. More information: [Microsoft Power Platform CLI (preview)](power-platform-cli.md)

## Install Visual Studio Code extension

After you install Visual Studio Code, you need to install the extension for the Power Platform tools plug-in for Visual Studio Code.

To install the Visual Studio Code extension:

1. Open Visual Studio Code.

1. Select **Extensions** from the left pane.

    :::image type="content" source="media/vs-code-extension/extensions.png" alt-text="Visual Studio Code extension.":::

1. Select the **Settings** icon from the top-right on the extensions pane.

1. Search for and select **Power Platform Tools**.

    :::image type="content" source="media/vs-code-extension/vs-code-extension.png" alt-text="Select Power Platform Tools.":::

1. Select **Install**.

1. Verify the extension is installed successfully from the status messages.

> [!TIP]
> The Power Platform Tools Extension automatically enables using Microsoft Power Platform CLI commands from within Visual Studio Code through [Visual Studio Integrated Terminal](https://code.visualstudio.com/docs/editor/integrated-terminal).

## Power Pages Actions 

Power Pages Actions streamline site management and reduce reliance on [Microsoft Power Platform CLI commands](power-platform-cli-tutorial.md#step-3-download-website-content). Power Pages Actions is available in the pane titled **Power Pages Actions** in the Explorer sidebar of Visual Studio Code.

Within this pane, sites are categorized as follows:

- **Active Sites**: Sites that are currently available and active in the selected environment.
- **Inactive Sites**: Sites that are present in the environment but not currently active.
- **Other Sites**: Sites downloaded locally but not yet associated with the selected environment.

### Changing environments

To switch environments:

1. Select on the **Change Environment** button within the Power Pages Actions pane.

:::image type="content" source="media/vs-code-extension/changeEnv.png" alt-text="Change environment for sites":::

1. Select your desired environment from the displayed list.

When you select an environment, the list of sites updates automatically.

### Actions for sites

Different types of sites provide context-specific actions that you can access by right-clicking.

#### Active Sites actions

Right-click on Active Sites to access the following actions:

- **Preview**: Clears the cache and opens the site within VS Code for immediate preview.
- **Upload**: Uploads local changes back to your environment.
- **Download**: Downloads the site content to a local folder for offline editing.
- **Site Details**: Displays detailed information about the site.
- **Reveal in Explorer**: Navigates to the local directory containing the site's code.
- **Open in Power Pages Studio**: Open site in Power Pages studio. 

#### Inactive Sites actions

Inactive Sites provide these actions:

- **Open Site Management**: Opens the site within the Power Pages management application.
- **Site Details**: Provides detailed information about the selected site like website ID, website URL, data model version and more.

#### Other Sites actions

Sites stored locally but not yet in your environment offer the following actions:

- **Upload Site**: Uploads the local site to your connected environment. After uploading, the site appears in the Inactive Sites list, where you can activate it from Power Pages home.
- **Reveal in Explorer**: Navigates to the local directory containing the site's code.

## File icons

The Visual Studio Code extension for Power Pages automatically identifies and shows icons for files and folders inside the downloaded website content.

:::image type="content" source="media/vs-code-extension/file-icons.png" alt-text="List of files in a starter template with website-specific file icon theme.":::

Visual Studio Code uses the default [file icon theme](https://code.visualstudio.com/docs/getstarted/themes#_file-icon-themes) which doesn’t show Power Pages specific icons. To view file icons specific to your websites, you have to update the Visual Studio Code instance to use the Power Pages specific file icon theme.

To enable a portals-specific file-icon theme:

1. Open Visual Studio Code.

1. Go to **File** > **Preferences** > **Theme** > **File Icon Theme**

1. Select the theme for **PowerApps portals Icons**.

    :::image type="content" source="media/vs-code-extension/select-theme-icons.png" alt-text="Screenshot shows selecting the theme for Power Apps Portals Icons.":::

## Live preview

The Visual Studio Code extension enables a live preview option to view the Power Pages content page inside the Visual Studio Code interface during the development experience.

To see the preview, select :::image type="content" source="media/vs-code-extension/preview-symbol.png" alt-text="Screenshot of the preview button."::: from the top-right when having an HTML file open in edit mode.

:::image type="content" source="media/vs-code-extension/page-preview.png" alt-text="Screenshot of the page preview.":::

The preview pane opens on the right side of the page being edited.

:::image type="content" source="media/vs-code-extension/preview-studio.png" alt-text="Screenshot showing the file list, open file in Visual Studio Code editor, and a preview on the right-side.":::

The preview feature requires that the other files are also open in the same Visual Studio Code session that makes up the HTML markup for the preview to show. For example, if only the HTML file is opened without the folder structure opened using Visual Studio Code, the following message appears.

:::image type="content" source="media/vs-code-extension/preview-failed.png" alt-text="Screenshot shows running the contributed command: 'microsoft-powerapps-portals.preview-show' failed.":::

When this problem occurs, open the folder using **File > Open folder** and select the downloaded website content folder to open before you try to preview again.

## Autocomplete

The autocomplete capability in the Visual Studio Code extension shows the current context being edited, and the relevant autocomplete elements through IntelliSense.

:::image type="content" source="media/vs-code-extension/auto-complete.png" alt-text="Screenshot with an example of autocomplete for the page template ID.":::

### Liquid tags

When customizing downloaded content using Visual Studio Code, you can now use IntelliSense for Power Pages [Liquid tags](liquid/liquid-tags.md).

Start typing to see a list of Liquid tags. Select a tag to format it correctly and continue with your input.

:::image type="content" source="media/vs-code-extension/liquid-tag-completion.png" alt-text="Screenshot of a snippet with an example of Liquid tag completion.":::

### Liquid objects

You can see [Liquid object](liquid/liquid-objects.md) code completions by entering `{{ }}`. With the cursor placed between the brackets, select `<CTRL + space>` to display a list of Liquid objects that you can select. If the object has more properties, you can enter a **.** and then select `<CTRL + space>` again to see specific properties of the Liquid object.

:::image type="content" source="media/vs-code-extension/liquid-object.png" alt-text="Screenshot shows entering a Liquid object.":::

### Template tags

You can see Power Pages web template suggestions by place your cursor in the `{include ' '}` statement and select `<CTRL> - space`. A list of existing web templates appear for you to select.

:::image type="content" source="media/vs-code-extension/template-tags.png" alt-text="Screenshot of template tags.":::

## Create, delete, and rename website objects

From within Visual Studio Code, you're able to create, delete, and rename the following website components:

- Web pages
- Page templates
- Web templates
- Content snippets
- New assets (Web files)

### Create operations

You can use the context menu options to create new website components. Right-click one of the supported objects, choose **Power Pages**, and select the website object type you wish to create.

Alternatively, you can use the Visual Studio Code command palette by selecting `Ctrl + Shift + P`.

:::image type="content" source="media/vs-code-extension/create-object.png" alt-text="Create a new object.":::

You need to specify more parameters to create the object.

| Object    | Parameters |
|-|-|
| Web pages | Name, page template, parent page |
| Page templates | Name, web template |
| Web templates | Name |
| Content snippets | Name, and if the snippet will be HTML or text. |
|New assets (Web files) | Name, parent page, and select file to upload. |

### Rename and delete operations

From the file navigation, you can use the context menu to rename or delete Power Pages components.

> [!NOTE]
> Deleted objects can be restored from the desktop recycle bin.

## Limitations

The following limitations currently apply to the Power Platform Tools for portals:

- [Autocomplete](#autocomplete) features only support limited functionality.
- [Live preview](#live-preview) doesn't support custom themes or Liquid objects.

### Related information

[Power Pages support for Microsoft Power Platform CLI (preview)](power-platform-cli.md)
