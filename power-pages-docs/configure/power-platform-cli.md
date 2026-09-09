---
title: Power Platform CLI support for Power Pages
description: Learn how to work with Power Platform CLI for CI/CD (Continuous Integration/Continuous Deployment) improvements of a Power Pages site.
author: neerajnandwana-msft

ms.topic: concept-article
ms.custom: 
ms.date: 09/08/2026
ms.subservice: 
ms.author: nenandw
ms.reviewer: smurkute
contributors:
    - neerajnandwana-msft
    - DanaMartens
---

# Microsoft Power Platform CLI support for Power Pages

Microsoft Power Platform CLI (command-line interface) is a simple, single-stop developer command-line interface that empowers developers and app makers to create code components.

Microsoft Power Platform CLI tooling is the first step toward a comprehensive application life-cycle management (ALM) story where the enterprise developers and ISVs can create, build, debug, and publish their extensions and customizations quickly and efficiently. Learn more in [What is Microsoft Power Platform CLI?](/power-platform/developer/cli/introduction)

By using this feature, Microsoft Power Platform CLI enables CI/CD (Continuous Integration/Continuous
Deployment) of a Power Pages site configuration. You can now check in the website configuration to source control and move the website configuration to any environment by using Microsoft Power Platform CLI.

> [!NOTE]
> - This feature is generally available starting with Power Platform CLI version 1.9.8. To learn about installing the latest version, see [Install Microsoft Power Platform CLI](/power-platform/developer/cli/introduction).
> - By using Power Platform CLI version 1.32, the `pac powerpages` command was changed to `pac pages`. By using pac cli version 1.27, the `pac paportal` command was changed to `pac powerpages`. Both `powerpages` and `paportal` continue to work, but use `pages` going forward.

### Why use Microsoft Power Platform CLI for website development?

With the Microsoft Power Platform CLI, you can now use offline-like capability for website customization by making changes to the website content. And once all
customizations or changes are saved, you can upload the website configuration back to Microsoft Dataverse. When you download website content using Microsoft Power Platform CLI, the content is structured in YAML and HTML formats making it easy to customize, enabling a pro-development experience.

Here's a list of features and capabilities that portals benefits from with the support for Microsoft Power Platform CLI:

#### Ease of use

- Support for download/upload of website configuration data to/from the local file system

- Build on existing Microsoft Power Platform CLI tool.

#### Application lifecycle management (ALM)

- Track changes to website configuration within an organization

- Move configuration files across organizations or tenants

#### Pro-dev and enterprise support

- Helps integrate seamlessly with any source control tools, such as "git"

- Easily set up CI/CD pipelines

## Install Microsoft Power Platform CLI

For step-by-step instructions, refer to [Install Microsoft Power Platform CLI](/power-platform/developer/cli/introduction#install-microsoft-power-platform-cli).

## Supported tables

Portals support for Microsoft Power Platform CLI is limited to the following tables.

:::row:::
   :::column span="":::
      adx_ad
   :::column-end:::
   :::column span="":::
      adx_adplacement
   :::column-end:::
   :::column span="":::
      adx_blog
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_blogpost
   :::column-end:::
   :::column span="":::
      adx_botconsumer
   :::column-end:::
   :::column span="":::
      adx_communityforum
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_communityforumaccesspermission
   :::column-end:::
   :::column span="":::
      adx_contentsnippet
   :::column-end:::
   :::column span="":::
      adx_entityform
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_entityformmetadata
   :::column-end:::
   :::column span="":::
      adx_entitylist
   :::column-end:::
   :::column span="":::
      adx_entitypermission
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_forumthreadtype
   :::column-end:::
   :::column span="":::
      adx_pagetemplate
   :::column-end:::
   :::column span="":::
      adx_poll
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_polloption
   :::column-end:::
   :::column span="":::
      adx_pollplacement
   :::column-end:::
   :::column span="":::
      adx_portallanguage
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_publishingstate
   :::column-end:::
   :::column span="":::
      adx_redirect
   :::column-end:::
   :::column span="":::
      adx_shortcut
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_sitemarker
   :::column-end:::
   :::column span="":::
      adx_sitesetting
   :::column-end:::
   :::column span="":::
      adx_tag
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_urlhistory
   :::column-end:::
   :::column span="":::
      adx_webfile
   :::column-end:::
   :::column span="":::
      adx_webform
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_webformmetadata
   :::column-end:::
   :::column span="":::
      adx_webformstep
   :::column-end:::
   :::column span="":::
      adx_weblink
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_weblinkset
   :::column-end:::
   :::column span="":::
      adx_webpage
   :::column-end:::
   :::column span="":::
      adx_webpageaccesscontrolrule
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_webrole
   :::column-end:::
   :::column span="":::
      adx_website
   :::column-end:::
   :::column span="":::
      adx_websiteaccess
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      adx_websitebinding (only download)
   :::column-end:::
   :::column span="":::
      adx_websitelanguage
   :::column-end:::
   :::column span="":::
      adx_webtemplate
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      annotation
   :::column-end:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
   :::column-end:::
:::row-end:::

> [!IMPORTANT]
> - You can't customize custom tables and portal template-specific tables (such as blog, community, or ideas portal) by using Microsoft Power Platform CLI.
> - Power Platform CLI doesn't download image file attachments to ad (adx_ad) records. As a workaround, use the **Image URL** field, or add an HTML reference in the **Copy** field to a [web file](/power-apps/maker/portals/configure/web-files) record that contains an image file.

## Install and verify Microsoft Power Platform CLI for portals

To learn about installing Microsoft Power Platform CLI, see [Install Microsoft Power Platform CLI](/power-platform/developer/cli/introduction).

After installing Microsoft Power Platform CLI, open a command prompt and run *pac* to verify that the output contains "paportal" - the command for
    Power Apps portals.

:::image type="content" source="media/power-apps-cli/confirm-paportal.png" alt-text="Confirm paportal command in Microsoft Power Platform CLI.":::

## Microsoft Power Platform CLI commands for Power Pages

Use the `pac pages` command group to manage Power Pages websites.

The following table describes the available commands and their parameters.

### Parameters

|Property Name|Description|Example|
|-------------|-----------|-------|
|[list](/power-platform/developer/cli/reference/paportal#pac-paportal-list)|Lists all portal websites from the current Dataverse environment.<br/><br/> Add the `-v` parameter to indicate if the site is using the standard or [enhanced data model](../admin/enhanced-data-model.md) |`pac pages list`|
|[download](/power-platform/developer/cli/reference/paportal#pac-paportal-download)|Download portal website content from the current Dataverse environment. It has the following parameters: <br/> - *path*: Path where the website content is downloaded (alias: `-p`)<br/> - *webSiteId*: Portal website ID to download (alias: `-id`)<br/> - *overwrite*: (Optional) true - to overwrite existing content; false - to fail if the folder already has website content (alias: `-o`)<br/> - *modelVersion*: `1` or `2` to indicate if the site data to be downloaded uses the standard (1) or [enhanced data model](../admin/enhanced-data-model.md) (2). |`pac pages download --path "C:\portals" --webSiteId f88b70cc-580b-4f1a-87c3-41debefeb902 --modelVersion 2`|
|[upload](/power-platform/developer/cli/reference/paportal#pac-paportal-upload)|Upload portal website content to the current Dataverse environment. It has the following parameter: <br/> - *path*: Path where the website content is stored (alias: `-p`) <br/> -*deploymentProfile*: Upload portal data with environment details defined through [profile variables](#use-deployment-profile) in the *deployment-profiles/[profile-name].deployment.yaml* file<br/> - *modelVersion*: `1` or `2` to indicate if the site data to be uploaded uses the standard (1) or [enhanced data model](../admin/enhanced-data-model.md) (2).<br/> - *forceUploadAll*: Pushes *all* local files to the environment. Use this parameter when you think the remote state is corrupt, out of sync, or when the last download came from a different branch.|`pac pages upload --path "C:\portals\starter-portal" --deploymentProfile "profile-name" --modelVersion 2`|
|[`clone`](/power-platform/developer/cli/reference/pages#pac-pages-clone)|Creates Power Pages website content based on existing website content. It has the following parameters:<br/>- *path*: Path of the existing website content (alias: `-p`).<br/>- *outputDirectory*: Path where the cloned Power Pages website content is saved (alias: `-od`).<br/>- *overwrite*: (Optional) Overwrites the existing folder at the output path (alias: `-o`).<br/>- *name*: (Optional) Name for the cloned Power Pages website (alias: `-n`). If you don't specify this parameter, the name defaults to `Copy of <original-site-name>`.|`pac pages clone --path "C:\portals\starter-portal" --outputDirectory "C:\portals\starter-portal-copy" --name "Copy of Starter Portal"`|
|`create-site`|Creates a Power Pages website. It has the following parameters:<br/>- *environment*: (Optional) Target Dataverse environment GUID or absolute HTTPS URL (alias: `-env`). If you don't specify this parameter, the active organization for the current authentication profile is used.<br/>- *name*: Website name (alias: `-n`).<br/>- *subdomain*: Subdomain for the website URL (alias: `-sd`).<br/>- *template*: Website template name (alias: `-t`). Supported values are `StarterLayout1`, `StarterLayout2`, `StarterLayout3`, `StarterLayout4`, `StarterLayout5`, `BlankPage`, `BookMeetings`, `FAQ`, `ProgramRegistration`, `BuildingPermit`, `Community`, `EventPortal`, `CustomerSelfServicePortal`, `EmployeeSelfServicePortal`, `PartnerPortal`, `CustomerPortal`, and `FieldService`.<br/>- *baseLanguage*: Language ID for the website base language, such as `1033` for English (alias: `-l`).<br/>- *websiteRecordId*: (Optional) Dataverse website record ID (alias: `-wrid`).|`pac pages create-site --name "Contoso site" --subdomain "contoso" --template StarterLayout1 --baseLanguage 1033`|
|`delete-site`|Deletes a Power Pages website. It has the following parameters:<br/>- *environment*: (Optional) Target Dataverse environment GUID or absolute HTTPS URL (alias: `-env`). If you don't specify this parameter, the active organization for the current authentication profile is used.<br/>- *portalId*: Power Pages portal ID to delete (alias: `-id`).<br/>- *confirm*: Confirms the website deletion (alias: `-y`). This switch is required to delete the website.|`pac pages delete-site --portalId 9f8c7b6a-5d4e-3c2b-1a09-8f7e6d5c4b3a --confirm`|
|`restart-site`|Restarts a Power Pages website. It has the following parameters:<br/>- *environment*: (Optional) Target Dataverse environment GUID or absolute HTTPS URL (alias: `-env`). If you don't specify this parameter, the active organization for the current authentication profile is used.<br/>- *portalId*: Website unique identifier (ID) (alias: `-id`).|`pac pages restart-site --portalId 9f8c7b6a-5d4e-3c2b-1a09-8f7e6d5c4b3a`|

> [!NOTE]
> - When you download a portal from **Environment A** and upload it to **Environment B**, the PAC CLI performs a **full upload**. This behavior occurs because change tracking uses **[Manifest Files](#manifest-files)**, which don't carry state information across environments. 
> - Delta uploads—where only modified files are uploaded—are supported only when both the download and upload operations happen within the **same environment**. In this case, PAC CLI detects local changes and uploads only the updated files. To learn more about how change tracking works, see [Manifest Files](#manifest-files).
> - Use **--forceUploadAll** in these situations. (This parameter is currently CLI-only. Azure DevOps tasks don't surface it yet.)
>   - **Pipeline state drift** (you rebased or cherry-picked commits, so the last server state no longer matches your branch). 
>   - **Suspected delta failure** (for example, only partial changes appear after a normal `upload`).

#### Use deployment profile

The **deploymentProfile** switch allows you to define a set of variables for the environment in YAML format. For example, you can have different deployment profiles (such as dev, test, prod) that have different schema details defined in the profile.

If you're creating test profile, create a file under **deployment-profiles** with the name `test.deployment.yml` (that is, \<profileTag\>.deployment.yml). Run the command with the tag (\<profileTag\>) to use this profile:

`pac pages upload --path "C:\portals\starter-portal" --deploymentProfile test --modelVersion 2`

In this file, you can include the table (entity) name with table ID, list of attributes, and the values that you want to override while uploading the portal configuration by using the `deploymentProfile` parameter.

You can also use the `OS` variable to access the operating system's environment variables.

Here's an example of the `test.deployment.yml` profile YAML file that has unique schema details:

```yml
adx_sitesetting:
    - adx_sitesettingid: 4ad86900-b5d7-43ac-1234-482529724970
      adx_value: ${OS.FacebookAppId} 
      adx_name: Authentication/OpenAuth/Facebook/AppId
    - adx_sitesettingid: 5ad86900-b5d7-43ac-8359-482529724979
      adx_value: contoso_sample
      adx_name: Authentication/OpenAuth/Facebook/Secret
adx_contentsnippet:
    - adx_contentsnippetid: b0a1bc03-0df1-4688-86e8-c67b34476510
      adx_name: PowerBI/contoso/sales
      adx_value:  https://powerbi.com/group/contoso/sales
```

> [!NOTE]
> To learn about all commands used in CLI in addition to portals, go to [Common commands in Microsoft Power Platform CLI](/power-platform/developer/cli/introduction#common-commands).

## Manifest files

When you download the website content by using the [pac pages download](/power-platform/developer/cli/reference/paportal#pac-paportal-download) CLI command, you also get two manifest files:
- Environment manifest file (`org-url-manifest.yml`)
- Delete tracking manifest file (`manifest.yml`)

### Environment manifest file (`org-url-manifest.yml`)

The environment manifest file is generated every time you run the [pac pages download](/power-platform/developer/cli/reference/paportal#pac-paportal-download) command.

After each download, the PAC CLI tool reads the existing environment manifest file, updates the entries you deleted in the environment, or creates the environment manifest file if it doesn't exist.

When you run the [pac pages upload](/power-platform/developer/cli/reference/paportal#pac-paportal-upload) command to upload the portal website content, it reads the environment manifest file, identifies the changes you made since the last download, and uploads only the updated content. This process optimizes the upload process because you upload only updated website content instead of all content.

The environment manifest file is read-only when it connects to the same environment (environment URL matches with file name), to avoid accidental changes. 

> [!NOTE]
> - The environment manifest file isn't designed to track the changes when deploying the website to different environments.
> - The environment manifest file is designed to be used by developers for deploying locally in their developer environment and should be added to git ignore list.

### Delete tracking manifest file (manifest.yml)

Use this file to track deleted records from the environment.

When you download website content by using the [pac pages download](/power-platform/developer/cli/reference/paportal#pac-paportal-download) command, it adds the deleted records from the [environment manifest file (org-url-manifest.yml)](#environment-manifest-file-org-url-manifestyml) to the manifest.yml file. When you upload the website content by using the [pac pages upload](/power-platform/developer/cli/reference/paportal#pac-paportal-upload) command, it deletes the files from the environment, even if it's a different environment.
This file isn't deleted, and it gets used regardless of which environment you're connected to.
Consider this file when pushing changes to the source control to handle deleting items in the target environment.

> [!NOTE]
> To delete the site content records in one environment and also delete the same content records in another environment by using the PAC CLI, run the [pac pages download](/power-platform/developer/cli/reference/paportal#pac-paportal-download) command *before* and *after* deleting the website record content. The manifest.yml file tracks these changes and removes the corresponding records in the target environment when you run the [pac pages upload](/power-platform/developer/cli/reference/paportal#pac-paportal-upload) command.

## Use the Visual Studio Code extension

You can also use the VS Code extension **Power Platform VS Code Extension** to benefit from the built-in Liquid language support in IntelliSense, code completion assistance, and hinting. You can also interact with the Microsoft Power Platform CLI by using the VS Code Integrated Terminal. For more information, see [Use the Visual Studio Code extension (preview)](vs-code-extension.md).

## More considerations

- You get an error if your file path exceeds the maximum path length limitation. Learn more in [Maximum path length limitation in Windows](/windows/win32/fileio/maximum-file-path-limitation).
- For duplicate records such as a duplicate web page name, Microsoft Power Platform CLI creates two different folders - one with the name of the web page, and the other with the same name prefixed with a hash code. For example, `My-page` and `My-page-**hash-code**`.

## Next steps

[Tutorial: Use Microsoft Power Platform CLI with portals](power-platform-cli-tutorial.md)

### See also

- [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction)
- [Use the Visual Studio Code extension (preview)](vs-code-extension.md)
