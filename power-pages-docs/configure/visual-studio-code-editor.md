---
title: Edit code with Visual Studio Code for the Web (preview)
description: Learn how to customize pages by using the Visual Studio Code for the Web editor.
author: neerajnandwana-msft
ms.topic: how-to
ms.custom: 
ms.date: 08/02/2023
ms.subservice:
ms.author: nenandw 
ms.reviewer: dmartens
contributors:
    - neerajnandwana-msft
---

# Edit code with Visual Studio Code for the Web (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

From the design studio, you can edit site code using **Visual Studio Code for the Web**. This feature allows you to edit static content, HTML, CSS, [Liquid](liquid/liquid-overview.md), and [JavaScript](add-custom-javascript.md) for the following website metadata:

| Metadata | Content |
| - | - |
| Advanced forms ([multistep forms](multistep-form-properties.md)) | JavaScript |
| [Basic forms](basic-forms.md) | JavaScript |
| [Content snippets](content-snippets.md) | All supported content snippet content |
| [Lists](lists.md) | JavaScript |
| [Web files](web-files.md) | View and download media files. Edit text (code) files. |
| [Web pages](web-page.md) | All supported content (per language), JavaScript, and CSS |
| [Web templates](web-templates.md) | All supported content |

> [!NOTE]
> You will not be able to create metadata records, only add and edit content, code, and view/download file attachments.

Visual Studio Code for the Web provides a free, zero-install Microsoft Visual Studio Code experience running entirely in your browser, allowing you to browse site code and make lightweight code changes quickly and safely. More information: [Visual Studio Code for the Web experience.](https://code.visualstudio.com/docs/editor/vscode-web)

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

:::image type="content" source="media/visual-studio-code-editor/vs-code-demo.gif" alt-text="Demo of using Visual Studio Code for Web to edit Power Pages site.":::

> [!NOTE]
> - First time **Visual Studio Code for the Web** load may take some time as it will be installing required extensions for this feature. 
> - File Create, Delete and Rename operations are not supported. 
> - This feature utilizes **Power Platform Tools** web extension. Web extensions are restricted by the browser sandbox and therefore have limitations compared to normal extensions.
>   - Power Platform CLI is not supported.
>   - Power Platform Tools web extension features are limited to Power Pages code editing experience.
>   - This feature is not available in Government Community Cloud (GCC), Government Community Cloud (GCC High), and Department of Defense (DoD).  Users in these regions will use the [Portals Management app](portal-management-app.md) for editing code. See [Editing code in the Portals Management app](#editing-code-in-the-portals-management-app) for more information.

## Edit code available in design studio

You can start editing your site's code using Visual Studio Code for the Web from the Power Pages home page by choosing the **Edit site code** option from the **Edit** drop down menu.  

You can also edit code in the design studio from the following areas:

- [Edit web page code from Pages workspace](#edit-web-page-code-from-pages-workspace)
- [Header template code from Pages workspace](#header-template-code-from-pages-workspace)
- [Edit custom CSS code from Styling workspace](#edit-custom-css-code-from-styling-workspace)
- Edit custom JavaScript code for multistep forms
- Edit custom JavaScript code for basic forms
- Edit custom JavaScript for lists
- Edit content snippets
- Edit web templates
- View and download media web files (images)
- Edit text based web files (CSS, JavaScript, other)

Let's take a look how to edit code using these areas.

### Edit web page code from Pages workspace

When you open Power Pages design studio, you see **Edit code** option in Pages menu<sup>1</sup> and upper-right corner of the screen<sup>2</sup>. 

:::image type="content" source="media/visual-studio-code-editor/edit-code-pages.png" alt-text="Edit code from Pages workspace.":::

### Header template code from Pages workspace

Select **Edit site header** and then select **Edit code** to open code editor.

:::image type="content" source="media/visual-studio-code-editor/pages-header-edit.png" alt-text="Edit code from Pages header.":::

### Edit custom CSS code from Styling workspace

Go to **Styling workspace** and select available custom CSS **Edit code** menu to open code editor.

:::image type="content" source="media/visual-studio-code-editor/edit-code-custom-css.png" alt-text="Edit code from Custom CSS.":::

## Merge conflict notification

If you are collaborating with other developers, there may be situations where you'll be working on the same source code. In the event you attempt to save changes to an outdated file you'll get a notification to **Compare** or **Overwrite** changes.

Comparing the code will show current code alongside your code and allow you to revert to the existing changes, accept each change individually or use your changes and overwrite the existing contents.

:::image type="content" source="media/visual-studio-code-editor/merge-conflicts.png" alt-text="Merge conflicts in code.":::

You'll be able to review the latest content and either merge or overwrite the code or discard the changes.

## Tutorial: Edit site code using Visual Studio Code for the Web

In this tutorial, you walk through editing the site code using Visual Studio Code for Web.

### Step 1: Edit site code using Visual Studio Code for the Web

1. Open your site in [Power Pages design studio](../getting-started/use-design-studio.md)

1. On the top right corner, select **Edit code**

    :::image type="content" source="media/visual-studio-code-editor/launch-code-editor.png" alt-text="Opening in Visual Studio Code from the design studio.":::

1. Select **Open Visual Studio Code** from the confirmation dialog.

1. Sign in to Visual Studio Code using your environments credentials.

1. Wait for **Power Platform Tools** web extension to initialize, and web page code to load in left-pane.

### Step 2: Update content and code

1. The explorer on the left-side of the screen loads respective website configuration metadata that can be edited using Visual Code for the Web.

    :::image type="content" source="media/visual-studio-code-editor/vscode-file-explorer.png" alt-text="Explorer menu for an untitled workspace showing web files.":::

1. Make changes to the respective metadata files and press ***Ctrl+S*** to save the changes.

1. Go to design studio and select **Sync** to pull all the updates in your current design studio session.

    :::image type="content" source="media/visual-studio-code-editor/sync-code.png" alt-text="Interface to allow user to select Sync button to synchronize changes made in Visual Studio Code to design studio.":::

1. Select **Preview** to see changes on the Power Pages site.

## Using Visual Studio Code for the Web or Visual Studio Code Desktop

Users can edit, debug, and preview changes to page edits using Visual Studio Code for the Web without needing to use external tools. Visual Studio Code Desktop provides other advanced features for editing all site metadata and integrating with GitHub, frameworks, and continuous integration/continuous development (CI/CD) processes.

| Feature | VS Code for the Web | VS Code Desktop |
| - | - | - |
| Create new website configuration metadata records | No | Limited to web pages, page templates, web templates, content snippets, and web files. |
| Direct site editing | Yes | No |
| Site metadata editing | Limited to editing web pages, content snippets, basic forms, multi-step forms, lists, and web templates. | All Power Pages metadata configuration |
| Site preview | Planned | Planned |
| [Power Platform CLI](/power-platform/developer/cli/introduction) support | No | Yes |
| Advanced CPU and storage bound workflow - ReactJS or other framework build tool support | No | Yes |
| GitHub integration with capabilities such as code check-in, check-out, managing conflicts, and merge. | No | Yes |

## Editing code in the Portals Management app

> [!NOTE]
> - Using Visual Studio Code for the Web to edit websites is not supported in Government Community Cloud (GCC), Government Community Cloud (GCC High), and Department of Defense (DoD). Users in these regions can use the [Portals Management app](portal-management-app.md) to make their changes.

If the region doesn't support the **Visual Studio Code for the Web**, selecting the code editor icon &lt;/&gt; in the command bar will open the **Portals Management app**.

Navigate to the corresponding **Web Pages**, **Basic Forms**, **Multistep Forms**, **Lists**, or **Web Templates** records to edit code.

| Type | Code location |
| - | - |
| Web page | Select web page record. </br> Select web page content record from the **Localized Content** section. </br>Page copy can be edited in the **Copy (HTML)** field on the **General** tab.</br>**Custom JavaScript** and **Custom CSS** code can be edited from the **Advanced** tab. |
| Basic form | Select the basic form record.</br>Edit **Custom JavaScript** on the **Additional Settings** tab. |
| Multistep form | Select the multistep form record.</br>Select the multistep form step from the **Form Steps** tab.</br>Edit **Custom JavaScript** on the **Form Options** tab. |
| List | Select the list record.</br>Edit **Custom JavaScript** on the **Options** tab. |
| Web template | Select the web template record.</br>Edit **Source** on the **General** tab. |

Save the record, and preview your website to test your code.

## See also

- [Use Visual Studio Code and Microsoft Power Platform CLI](power-platform-cli-tutorial.md)
