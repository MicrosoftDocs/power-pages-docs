---
title: Migrate existing sites to Bootstrap version 5 (preview)
description: Learn how to migrate your Power Pages sites to Bootstrap version 5.
author: ankitavish 
ms.topic: how-to
ms.custom: 
ms.date: 09/20/2023
ms.subservice:
ms.author: avishwakarma 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Migrate existing sites to Bootstrap version 5 (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Bootstrap version 5 offers more functionality and support beyond what is available for Bootstrap version 3 as well as minor UX/UI changes such as modified breadcrumb icons and changes to spacing, colors, and margins. For this reason, you may wish to migrate your existing sites to Bootstrap version 5.

In this article, learn about how to migrate your existing site from using Bootstrap version 3 to use Bootstrap version 5. Since the migration steps require the use of Microsoft Power Platform CLI, ensure you understand how to use Power Platform CLI in Power Pages. More information: [Microsoft Power Platform CLI support for Power Pages](power-platform-cli.md), [Tutorial: Use Microsoft Power Platform CLI with Power Pages](power-platform-cli-tutorial.md), [`pac powerpages`](/power-platform/developer/cli/reference/powerpages)

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - You can migrate any of your existing Power Pages version 3 sites regardless of the template used for initial site creation.
> - Consider testing the migration using [developer sites](../getting-started/developer-sites.md) before you migrate a production site.

## Prerequisites

- You must install [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction#install-using-power-platform-tools-for-visual-studio-code) with version 1.26.6 or higher to migrate your sites to Bootstrap version 5. More information: [Install latest Power Platform CLI](/power-platform/developer/cli/introduction#update-power-platform-cli-for-windowsmacoslinux)
- If your site uses SVG files, ensure your Power Platform environment is configured to allow .svg file name extensions using [**Set blocked file extensions for attachments** in System Settings](/power-platform/admin/system-settings-dialog-box-general-tab).
- Consider creating two versions of your Power Pages site using Bootstrap version 3. Use one of them for migration and the other as a reference to compare against the migrated site.

## Step 1. Download the website folder

> [!NOTE]
> - Starting with the Power Platform CLI version 1.27, the `pac paportal` command is changed to `pac powerpages`. `paportal` continues to work, but we recommend using `powerpages` going forward.
> - If you're using the Power Platform CLI version 1.26.6, ensure you use `pac paportal` instead of `pac powerpages` for following steps.

1. Open a command prompt.

1. Use the following command to authenticate to the Dataverse organization for your Power Platform environment to download the website record for migration.

    `pac auth create -u [Dataverse URL]`
    
    **Example:**
    
    `pac auth create -u https://contoso-org.crm.dynamics.com`

    More information: [`pac auth create`](/power-platform/developer/cli/reference/auth)

1. Use the following command to generate a list of websites in the current organization.

    `pac powerpages list`

    More information: [`pac powerpages list`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-list)

1. Use the following command to download the website folder.

    `pac powerpages download --path [PATH] -id [WebSiteId-GUID]`
    
    **Example**
    
    `pac powerpages download --path c:\pac-powerpages\downloads -id
    d44574f9-acc3-4ccc-8d8d-85cf5b7ad141`
    
    For the **id** parameter, use the **WebSiteId** returned from the output of the previous step.

    More information: [`pac powerpages download`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-download)

## Step 2. Run the migration tool

Use the following command `bootstrap-migrate` command to run the tool on the downloaded website folder.

`pac powerpages bootstrap-migrate -p "WebsiteFolderPath"`

This command creates a new folder after migration with **V5** appended to the folder name.

> [!NOTE]
> You can replace existing folder with Bootstrap version 3 using the [upload command](#step-4-upload-the-migrated-website-record) if you want to revert from Bootstrap version 5 later.

More information: [`pac powerpages bootstrap-migrate`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-bootstrap-migrate)

## Step 3. Review your changes

If you created a copy of your existing site, compare your original site against the version 5 site generated in the previous step.

To compare your Bootstrap version 3 and version 5 sites:

1. Open the **V5** folder you created in the previous step.

1. Open an html or css file to compare the difference.

1. In Visual Studio Code, select **Ctrl** + **Shift** + **P** to open a command prompt and use the `Bootstrap Diff` command to compare the changes.

    Both files open. Your version 3 file opens on the right side of the screen, and the version 5 file open on the left side of the screen.

    Changes are highlighted for your review. Hover over a highlighted change to show tooltips related to your changes.

### Step 4: Upload the migrated website record

Use the following command to upload the migrated website record to the organization.

`pac powerpages upload --path [Folder-location]`

**Example**

`pac powerpages upload --path C:\pac-portals\downloads\custom-portal\`

More information: [`pac powerpages upload`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-upload)

After you upload your website record, the migrated site will be a Bootstrap version 5 website. We recommend that you [compare the site against your version 3 site](#step-3-review-your-changes) one more time. Based on this comparison, modify Bootstrap version 5 site as needed to meet your requirements.

### See also

- [Bootstrap overview](bootstrap-overview.md)
- [Enable Bootstrap version 5 in your environment (preview)](bootstrap-version-5.md)
- [Manage CSS files](manage-css.md)
