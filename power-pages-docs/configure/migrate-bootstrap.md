---
title: Migrate existing sites to Bootstrap version 5
description: Learn how to migrate your existing Power Pages sites to Bootstrap version 5 with the help of the Microsoft Power Platform CLI.
ms.topic: how-to
ms.date: 01/31/2025
ms.subservice:
author: ankitavish
ms.author: avishwakarma
ms.reviewer: dmartens
contributors:
  - DanaMartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:11/16/2023
  - bap-template
---

# Migrate existing sites to Bootstrap version 5

[Bootstrap version 5](https://getbootstrap.com/docs/5.0/getting-started/introduction/) offers new features and updates that make your Power Pages sites more responsive and easier to customize.

> [!IMPORTANT]
>
> - You can migrate any of your Bootstrap version 3 sites to version 5 regardless of the template that was used to create them.
> - When you migrate existing Bootstrap version 3 sites to version 5, you can use either the standard data model or the [enhanced data model](../admin/enhanced-data-model.md).
> - Consider testing the migration with a [developer site](../getting-started/developer-sites.md).
> - To check the current version of Bootstrap, see the *bootstrap.min.css* [web file](web-files.md) for your website.

To migrate your Bootstrap version 3 site, follow these steps:

1. [Download the website folder](#download-the-website-folder).
1. [Run the migration tool on the folder](#run-the-migration-tool-on-the-folder).
1. [Review your changes](#review-your-changes).
1. [Upload the migrated website record](#upload-the-migrated-website-record).
1. [Clear the server-side cache](#clear-the-server-side-cache).

Since the migration steps require the use of the Microsoft Power Platform CLI, be sure you understand how to use it in Power Pages:

- [Microsoft Power Platform CLI support for Power Pages](power-platform-cli.md)
- [Tutorial: Use Microsoft Power Platform CLI with Power Pages](power-platform-cli-tutorial.md)
- [`pac powerpages`](/power-platform/developer/cli/reference/powerpages)

## Prerequisites

- Install [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction#install-using-power-platform-tools-for-visual-studio-code) version 1.28.2 or later.

- If your site uses SVG files, make sure that the [**Set blocked file extensions for attachments**](/power-platform/admin/system-settings-dialog-box-general-tab) system setting in your Power Platform environment allows the ".svg" extension.

- Consider creating two versions of your Power Pages site using Bootstrap version 3. Migrate one of them and use the other as a reference to [compare with the migrated site](#review-your-changes).

## Download the website folder

Starting with Microsoft Power Platform CLI version 1.27, the `pac paportal` command changed to `pac powerpages`. `paportal` still works, but we recommend that you use `powerpages` going forward. That's the form we use in the following instructions. If you're using Microsoft Power Platform CLI version 1.26.6, make sure that you use `pac paportal` instead of `pac powerpages`.

1. Open a command prompt.

1. Enter the following command to authenticate to the Dataverse organization for your Power Platform environment: `pac auth create -u [Dataverse URL]`

    **Example:** `pac auth create -u https://contoso-org.crm.dynamics.com`

    More information: [`pac auth create`](/power-platform/developer/cli/reference/auth)

1. Enter the following command to generate a list of websites in the organization: `pac powerpages list`

    Note the **WebSiteId** of the site you plan to migrate.

    More information: [`pac powerpages list`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-list)

1. Enter the following command to download the website folder: `pac powerpages download --path [PATH] -id [WebSiteId-GUID]`

    **Example**: `pac powerpages download --path "c:\pac-powerpages\downloads" -id d44574f9-acc3-4ccc-8d8d-85cf5b7ad141`

    For the **id** parameter, use the **WebSiteId** that you noted in the previous step.

    More information: [`pac powerpages download`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-download)

## Run the migration tool on the folder

Enter the following command to run the migration tool on the website folder that you downloaded: `pac powerpages bootstrap-migrate -p "WebsiteFolderPath"`

**Example**: `pac powerpages bootstrap-migrate -p "c:\pac-powerpages\downloads\bootstrap-dev-site"`

The command creates a folder with "V5" appended to the folder name.

To revert to version 3 from Bootstrap version 5, use the [upload command](#upload-the-migrated-website-record) to replace the version 5 folder with a Bootstrap version 3 folder.

More information: [`pac powerpages bootstrap-migrate`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-bootstrap-migrate)

Note: Make sure the folder and file names in the path aren't so long that they exceed the 256 character limit for Windows. Otherwise, the migration will terminate prematurely

## Review your changes

If you created a copy of your site before you migrated it, compare it with the version 5 site.

1. Open the **V5** folder you created in the previous step.

1. Open an HTML or CSS file.

1. In Visual Studio Code, press Ctrl+Shift+P to open a command prompt. Enter `bootstrap diff`.

1. The version 3 file and the version 5 file open. Hover over each highlighted change to review it.

## Upload the migrated website record

Enter the following command to upload the migrated website record to the organization: `pac powerpages upload --path [Folder-location]`

**Example**: `pac powerpages upload --path C:\pac-portals\downloads\custom-portal\`

More information: [`pac powerpages upload`](/power-platform/developer/cli/reference/powerpages#pac-powerpages-upload)

After you upload the record, the migrated site is a Bootstrap version 5 website. We recommend that you [compare the site with your version 3 site](#review-your-changes) one more time, and modify the Bootstrap version 5 site as needed.

## Clear the server-side cache

[Clear the server-side cache for the metadata/configuration and data tables](../admin/clear-server-side-cache.md).

### See also

- [Bootstrap overview](bootstrap-overview.md)
- [Create new sites with Bootstrap version 5](bootstrap-version-5.md)
- [Manage CSS files](manage-css.md)
