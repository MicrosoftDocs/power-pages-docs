---
title: Use the Visual Studio Code extension 
description: Learn about how to use the Visual Studio Code extension for Power Pages and integrate with Microsoft Power Platform CLI for CI/CD.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/24/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: kkendrick
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Use the Visual Studio Code extension

Visual Studio Code is a lightweight but powerful source code editor that runs on your desktop and is available for Windows, macOS, and Linux. It
comes with built-in support for JavaScript, TypeScript, and Node.js and has a
rich ecosystem of extensions for other languages (such as C++, C\#, Java,
Python, PHP, and Go) and runtimes (such as .NET and Unity). For more information, see [Get
started with VS Code](https://code.visualstudio.com/docs/getstarted/introvideos).

Visual Studio Code allows you to extend your capability through
[extensions](https://code.visualstudio.com/docs/introvideos/extend). Visual Studio Code
extensions can add more features to the overall experience. With the release of
this feature, you can now use the Visual Studio Code extension to work with Power Pages.

### Visual Studio Code extension for Power Pages

The **Power Platform Tools** adds the capability to configure websites using Visual Studio Code, and use the built-in Liquid language [IntelliSense](https://code.visualstudio.com/docs/editor/intellisense) enabling help with code completion, assistance, and hinting while customizing websites interface using Visual Studio Code. Using the Visual Studio Code extension, you can also configure portals through the [Microsoft Power Platform CLI](power-platform-cli.md).

> [!NOTE]
> - You will need to ensure that [node.js](https://nodejs.org/en/download) is downloaded and installed on the same workstation as Visual Studio Code for the Power Pages features to work.
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

## Download website content

To authenticate against a Microsoft Dataverse environment, and to download
website content, refer to the tutorial [Use Microsoft Power Platform CLI with Power Pages - download website content](power-platform-cli-tutorial.md#step-3-download-website-content).

> [!TIP]
> The Power Platform Tools Extension automatically enables using Microsoft Power Platform CLI commands from within Visual Studio Code through [Visual Studio Integrated Terminal](https://code.visualstudio.com/docs/editor/integrated-terminal).

## File icons

The Visual Studio Code extension for Power Pages automatically identifies and shows icons for files and folders inside the downloaded website content.

:::image type="content" source="media/vs-code-extension/file-icons.png" alt-text="List of files in a starter template with website-specific file icon theme.":::

Visual Studio Code uses the default [file icon theme](https://code.visualstudio.com/docs/getstarted/themes#_file-icon-themes) which doesn’t show Power Pages specific icons. To view file icons specific to your websites, you’ll have to update the Visual Studio Code instance to use the Power Pages specific file icon theme.

To enable a portals-specific file-icon theme:

1. Open Visual Studio Code.

1. Go to **File** > **Preferences** > **Theme** > **File Icon Theme**

1. Select the theme for **PowerApps portals Icons**.

    :::image type="content" source="media/vs-code-extension/select-theme-icons.png" alt-text="Select the theme for Power Apps Portals Icons.":::

## Live preview

The Visual Studio Code extension enables a live preview option to view the Power Pages content page inside the Visual Studio Code interface during the development experience.

To see the preview, select :::image type="content" source="media/vs-code-extension/preview-symbol.png" alt-text="Preview button."::: from the top-right when having an HTML file open in edit mode.

:::image type="content" source="media/vs-code-extension/page-preview.png" alt-text="Page preview.":::

The preview pane opens on the right side of the page being edited.

:::image type="content" source="media/vs-code-extension/preview-studio.png" alt-text="A screen with file list, open file in Visual Studio Code editor, and a preview on the right-side.":::

The preview feature requires that the other files are also open in the same Visual Studio Code session that makes up the HTML markup for the preview to show. For example, if only the HTML file is opened without the folder structure opened using Visual Studio Code, you’ll see the following message.

:::image type="content" source="media/vs-code-extension/preview-failed.png" alt-text="Running the contributed command: 'microsoft-powerapps-portals.preview-show' failed.":::

When this problem occurs, open the folder using **File > Open folder** and select the downloaded website content folder to open before you try to preview again.

## Autocomplete

The autocomplete capability in the Visual Studio Code extension shows the current context being edited, and the relevant autocomplete elements through IntelliSense.

:::image type="content" source="media/vs-code-extension/auto-complete.png" alt-text="An example of autocomplete for the page template ID.":::

### Liquid tags

When customizing downloaded content using Visual Studio Code, you can now use IntelliSense for Power Pages [Liquid tags](liquid/liquid-tags.md).

Start by typing and a list of Liquid tags will appear, once you select the tag, it will be correctly formatted and ready for more input.

:::image type="content" source="media/vs-code-extension/liquid-tag-completion.png" alt-text="Snippet with an example of Liquid tag completion.":::

### Liquid objects

You can see [Liquid object](liquid/liquid-objects.md) code completions by entering `{{ }}`. With the cursor placed between the brackets, select `<CTRL + space>` to display a list of Liquid objects that you can select. If the object has more properties, you can enter a **.** and then select `<CTRL + space>` again to see specific properties of the Liquid object.

:::image type="content" source="media/vs-code-extension/liquid-object.png" alt-text="Entering a Liquid object.":::


### Template tags

You can see Power Pages web template suggestions by place your cursor in the `{include ' '}` statement and select `<CTRL> - space`. A list of existing web templates will appear for you to select.

:::image type="content" source="media/vs-code-extension/template-tags.png" alt-text="Template tags.":::

## Create, delete, and rename website objects

From within Visual Studio Code, you're able to create, delete, and rename the following website components:

- Web pages
- Page templates
- Web templates
- Content snippets
- New assets (Web files)

### Create operations

You can use the context menu options to create new website components, right-select one of the supported objects, choose **Power Pages** and select the website object type you wish to create.

Alternatively, you can use the Visual Studio Code command palette by selecting `Ctrl + Shift + P`.

:::image type="content" source="media/vs-code-extension/create-object.png" alt-text="Create a new object.":::

You'll need to specify more parameters to create the object.

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

### See also

[Power Pages support for Microsoft Power Platform CLI (preview)](power-platform-cli.md)
