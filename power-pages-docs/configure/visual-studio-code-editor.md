---
title: Edit code with Visual Studio Code for the Web
description: Learn how to customize pages by using the Visual Studio Code for the Web editor.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 09/01/2022
ms.subservice:
ms.author: nenandw 
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
    - ProfessorKendrick
---

# Edit code with Visual Studio Code for the Web

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

From the design studio, you can edit site code using **Visual Studio Code for the Web**. This feature allows you to edit a single page's content, custom CSS, and custom JavaScript.

Visual Studio Code for the Web provides a free, zero-install Microsoft Visual Studio Code experience running entirely in your browser, allowing you to browse site code and make lightweight code changes quickly and safely. For more information: [Visual Studio Code for the Web experience.](https://code.visualstudio.com/docs/editor/vscode-web)

    > [!NOTE]
    > - First time **Visual Studio Code for the Web** load may take some time as it will be installing required extensions for this feature. 
    > - This feature utilizes “Power Platform Tools” as web extension. Web extensions are restricted by the browser sandbox and therefore have limitations compared to normal extensions. 
        - Power Platform CLI is not supported. 
        - “Power Platform Tools” web extension features are limited to Power Pages code editing experience. 

## Edit code available in design studio
Edit code feature will allow users to edit code in following areas
- Edit web page code from **Pages workspace**
- Header template code from **Pages workspace**
- Edit custom CSS code from **Styling workspace**

### Edit web page code from Pages workspace
When you open Power Pages design studio, you will see **Edit code** option in Pages menu^1^ and upper right conner of the screen^2^. 

### Header template code from Pages workspace
Select site header and click **Edit code** to open code editor

### Edit custom CSS code from Styling workspace
Navigate to **Styling workspace** and select available custom CSS **Edit code** menu item to open code editor 

## Tutorial: Edit site code using Visual Studio Code for the Web

### Step 1: Edit site code using Visual Studio Code

1. Open your site in [Power Pages design studio](../getting-started/use-design-studio.md)

1. On the top right corner, select **Edit code**

    :::image type="content" source="media/visual-studio-code-editor/launch-code-editor.png" alt-text="Opening in Visual Studio Code from the design studio.":::

1. Select **Open Visual Studio Code** from the confirmation dialog

1. Sign in to Visual Studio Code using your environments credentials.

1. Wait for PowerPlatform web extension initialization and web page code to load in left file navigation. 

### Step 2: Update web page code

1. The left Explorer will load respective customs CSS and custom JS files along with the web page copy content.

    :::image type="content" source="media/visual-studio-code-editor/vscode-file-explorer.png" alt-text="Explorer menu for an untitled workspace showing web files.":::

1. Make changes to the respective files and press ***Ctrl+s*** to save the changes

1. Navigate to Design Studio and select **Sync**" to pull all the update in Design Studio.

    :::image type="content" source="media/visual-studio-code-editor/sync-code.png" alt-text="Interface to allow user to select Sync button to synchronize changes made in Visual Studio Code to design studio.":::

1. Select **Preview** to see changes on the Power Pages site.

## Using Visual Studio Code for Web or Visual Studio Code desktop

Users can edit, debug, and preview changes to page edits using Visual Studio Code for the Web without needing to use external tools. Visual Studio Code for desktop provides additional advanced features for editing all site metadata as well as integrating with GitHub, frameworks, and continuous integration/continuous development (CI/CD) processes.

| Feature | Visual Studio for Web | Visual Studio Code desktop |
| - | - | - |
| Direct site editing | yes | |
| Site metadata editing | limited to design studio | all |
| Site preview | planned | planned |
| PAC CLI support | | yes |
| Advanced CPU and storage bound workflow</br>-ReactJS or other framework build tool support | | yes |
| GitHub integration</br>-code check in/check out/conflict/merge/etc. | limited | yes |

## See also

- [Use code editor](../getting-started/code-editor.md)
- [Use Visual Studio Code and Microsoft Power Platform CLI](cli-tutorial.md)
