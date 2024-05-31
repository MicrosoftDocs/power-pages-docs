---
title: Tutorial on how to use Power Platform CLI with Power Pages
description: This page provides a walk-through with examples for how to use Power Platform CLI with Power Pages for CI/CD (Continuous Integration/Continuous Deployment).
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 9/27/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: dmartens
contributors:
    - neerajnandwana-msft
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Use Microsoft Power Platform CLI with Power Pages

In this tutorial example, you'll see how to get started with Microsoft Power Platform CLI to update sample website configuration.

> [!NOTE] 
> - This tutorial focuses on the required Microsoft Power Platform CLI commands for Power Pages use. For more information about commands used in Power Platform CLI, read [Common commands](/power-platform/developer/cli/introduction#common-commands).
> - Starting with the Power Platform CLI version 1.27, the `pac paportal` command is changed to `pac powerpages`. `paportal` continues to work, but we recommend using `powerpages` going forward. This article will soon be updated to use `powerpages` instead of `paportal`. 

## Download and install Visual Studio Code

To connect to Power Apps portals, and to use Microsoft Power Platform CLI commands, use
[Visual Studio Code](https://code.visualstudio.com/docs) and the [integrated
terminal](https://code.visualstudio.com/docs/editor/integrated-terminal). The
integrated terminal makes it easy to connect to the Dataverse environment and to
download, change, and upload the portals configuration. You can also use Windows
PowerShell instead.

## Step 1. Authenticate

Before you connect, list, download, or upload any changes for a Power Apps
portal, you must authenticate to the Dataverse environment first. For more
information about authentication using Microsoft Power Platform CLI, go to [pac auth](/power-platform/developer/cli/reference/auth).

To authenticate, open Windows PowerShell and run the [pac auth create](/power-platform/developer/cli/reference/auth) command using
your Dataverse environment URL:

`pac auth create -u [Dataverse URL]`

**Example**

`pac auth create -u https://contoso-org.crm.dynamics.com`

Follow the prompts of authentication to sign in to the environment.

:::image type="content" source="media/power-apps-cli/auth-create.png" alt-text="Example of how to authenticate to a Dataverse environment using Microsoft Power Platform CLI":::

## Step 2. List available websites

Use the [pac paportal list](/power-platform/developer/cli/reference/paportal) command to list the available Power Pages websites in the
Dataverse environment you connected to in the previous step.

`pac paportal list`

:::image type="content" source="media/power-apps-cli/paportal-list.png" alt-text="Example list of websites.":::

## Step 3. Download website content

Download website content from the connected Dataverse environment using the [pac paportal download](/power-platform/developer/cli/reference/paportal) command.

`pac paportal download --path [PATH] -id [WebSiteId-GUID] --modelVersion [DataModel]`

**Example**

`pac paportal download --path c:\pac-portals\downloads -id d44574f9-acc3-4ccc-8d8d-85cf5b7ad141 --modelVersion 2`

For the **id** parameter, use the **WebSiteId** returned from the output of the
previous step.

:::image type="content" source="media/power-apps-cli/paportal-download.png" alt-text="Text used by screen readers.":::

> [!NOTE]
> When you use the Power Platform CLI to upload or download configuration data for a website that uses the enhanced data model, you must use the `modelVersion` parameter. A value of *2* indicates that the enhanced data model should be used. *modelVersion* `1` or `2` to indicate if the site data to be uploaded will use the the standard (1) or [enhanced data model](../admin/enhanced-data-model.md) (2).

## Step 4. Change website content

Change the configuration using Visual Studio Code and save your changes.

> [!NOTE]
> Ensure you update only the supported tables for use with Power Platform 
CLI. For more information, see [Supported tables](power-platform-cli.md#supported-tables).

For example, the default portal page shows text such as this:

:::image type="content" source="media/power-apps-cli/sample-section.png" alt-text="Sample portals page text":::

This text is visible from the webpage html:

:::image type="content" source="media/power-apps-cli/vs-code-page.png" alt-text="Visual Studio Code with text highlighted for change.":::

You can alter this text and save the changes:

:::image type="content" source="media/power-apps-cli/page-updated.png" alt-text="Updated text using Visual Studio Code.":::

> [!TIP]
> You can change the location of the folder path in PowerShell/integrated
terminal to the downloaded location, and enter "*code ."* to open the folder
directly in Visual Studio Code.

## Step 5. Upload the changes

> [!NOTE]
> - If you're uploading to multiple environments, see [upload the changes using deployment profile](#upload-the-changes-using-deployment-profile) to learn how to upload changes using deployment profile.
> - Ensure that the target environment's maximum attachment size is set to the same or greater size as your source environment.
> - The maximum size of files is determined by the **Maximum file size** setting in the [system settings email tab](/power-platform/admin/system-settings-dialog-box-email-tab) in the environment system settings dialog box.

After making the required changes, upload them using the [pac paportal upload](/power-platform/developer/cli/reference/paportal) command:

`pac paportal upload --path [Folder-location] --modelVersion [ModelVersion]`

**Example**

`pac paportal upload --path C:\pac-portals\downloads\custom-portal\ --modelVersion 2` 

:::image type="content" source="media/power-apps-cli/upload.png" alt-text="Starting upload.":::

> [!NOTE]
> Ensure the path for the portals content you entered is correct. By
default, a folder named by the portal (friendly name) is created with downloaded
portals content. For example, if the portal's friendly name is *custom-portal,*
the path for the above command (--path) should be
*C:\\pac-portals\\downloads\\custom-portal*.

The upload only happens for content that's been changed. In this example, since the
change is made to a webpage, content is uploaded only for the adx_webpage
table.

:::image type="content" source="media/power-apps-cli/upload-completed.png" alt-text="Upload completed only for changed content.":::

### Upload the changes using deployment profile

When working with multiple different environments, you may consider using deployment profiles to ensure the changes are uploaded to the correct environment using deployment profile.

1. Create a folder named **deployment-profiles** inside the folder containing the portal content. For example, if the downloaded portal content is inside "starter-portal", deployment profiles folder should be inside this folder.

    :::image type="content" source="media/power-apps-cli-tutorial/deployment-profiles-folder.png" alt-text="Folder for deployment profiles":::

1. Inside deployment profiles folder, create a deployment YAML file that contains the environment-specific changes. For example, development environment can be called "dev.deployment.yml".

    :::image type="content" source="media/power-apps-cli-tutorial/deployment-dev-file.png" alt-text="Deployment profile YAML for dev":::

1. Edit the deployment YAML file using Visual Studio Code with the following format:

    ```yml
    <table-name>:
    - <record-id>: <GUID>
      <column-name>: <Name>
      <column-value>: <Value>
    ```

    For example, the following sample YAML code updates the value for "Browser Title Suffix" from default "Custom Portal" to "Custom Portal (Dev)".

    ```yml
    adx_contentsnippet:
        - adx_contentsnippetid: 76227a41-a33c-4d63-b0f6-cd4ecd116bf8 # Replace with your content snippet ID
          adx_name: Browser Title Suffix # Setting name
          adx_value:  &nbsp;· Custom Portal (Dev) # Setting value
    ```

1. To upload the changes to a different environment using a deployment profile YAML file, [authenticate](#step-1-authenticate) to the target org first.

1. After authenticated and connected to the correct environment, use the [pac paportal upload](/power-platform/developer/cli/reference/paportal) command to upload the content:

    `pac paportal upload --path "C:\portals\starter-portal" --deploymentProfile dev --modelVersion 2`

    > [!NOTE]
    > In the above example, the deployment profile name used is "dev" after following the previous steps to create a dev deployment profile. Change the name from "dev" to any other (such as QA for "qa.deployment.yml", or Test for "test.deployment.yml") if you've used a different filename for your deployment YAML file.

## Step 6. Confirm the changes

To confirm the changes made to the webpage:

1. Select **Sync** in the Power Pages design studio.

1. Browse to the webpage to see the change.

    :::image type="content" source="media/power-apps-cli/changed-section.png" alt-text="View updated page content.":::

1. If you've used deployment profile example [explained previously](#upload-the-changes-using-deployment-profile), the YAML snippet will update the value as shown below.

    :::image type="content" source="media/power-apps-cli-tutorial/browser-title-suffix.png" alt-text="Browser title suffix from Portal Management app":::

    The browser title suffix updated through the above change shows the change when you open the portal in a browser:

    :::image type="content" source="media/power-apps-cli-tutorial/browser-change.png" alt-text="Browser change ":::

This concludes the tutorial. You can repeat the above steps and change the
portals content for other [supported tables](power-platform-cli.md#supported-tables).

## Next steps

[Use the Visual Studio Code extension](vs-code-extension.md)

### See also

- [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction)
- [Use the Visual Studio Code extension](vs-code-extension.md)

