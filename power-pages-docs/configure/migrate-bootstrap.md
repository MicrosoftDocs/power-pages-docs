---
title: Migrate existing sites to Bootstrap version 5 (preview)
description: Learn how to migrate your Power Pages sites to Bootstrap version 5.
author: ankitavish 
ms.topic: how-to
ms.custom: 
ms.date: 09/19/2023
ms.subservice:
ms.author: avishwakarma 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Migrate existing sites to Bootstrap version 5 (preview)

Bootstrap version 5 offers additional functionality and support beyond what is available for Bootstrap version 3. For this reason, you may wish to migrate your existing sites to Bootstrap version 5.

> [!NOTE]
>
> - You can migrate any of your existing Power Pages version 3 sites regardless of the template used for initial site creation.
> - Developer environments are recommended to run the migration tool and test the changes with respect to the production website.

## Pre-requisites

- PAC CLI 1.26.6 is required in order to migrate your sites to Bootstrap version 5.
- If your site uses SVG files, you must enable .svg file support for your site's environment before you begin. To enable .svg file support:

    1. Choose the gear icon in top bar and then choose **advanced** settings

    1. Select the dropdown next to settings and choose **System** > **Administration**. 

    1. Go to **System settings** and remove .svg from **Set blocked file extensions for attachments**.

- Before you run the migration tool, you must [install Microsoft Power Platform CLI using Power Platform Tools for Visual Studio Code](/power-platform/developer/cli/introduction#install-using-power-platform-tools-for-visual-studio-code). 

>[!NOTE]
> We strongly recommend creating two of your Bootstrap version 3 sites in your environment.  You'll use one of these sites for the migration. The duplicate site is used as a reference to compare against the migrated site.

## Step 1. Download the website folder

1. Open a command prompt.

1. Use the [pac auth create --url](/power-platform/developer/cli/reference/auth#basic-create) command to authenticate to the Dataverse organization you will use to download the website record for migration.

1. Use the [pac paportal list command](/power-platform/developer/cli/reference/paportal) to generate a list of websites in the current organization.

1. Use the [pac paportal download command](/power-platform/developer/cli/reference/paportal) to download the website folder.

## Step 2: Run the migration tool

1. Use the `bootstrap-migrate` command to run the tool on the downloaded website folder.

    ```pac paportal bootstrap-migrate -p "WebsiteFolderPath"```

    This command creates a new folder after migration with **V5** appended to the folder name. 

## Step 3. Review your changes(optional)

If you created a duplicate site as advised, you may wish to compare your original site against the version 5 site generated in step 2.

To compare your version 3 and version 5 sites:

1. Open the **V5** folder you created in Step 2. 

1. Open an html or css file to compare the difference.

1. In VS code, select **Ctrl** + **Shift** + **P** to open a command prompt and use the `Bootstrap Diff` command to compare the changes.

    Both files will open. Your version 3 file will open on the right, and the version 5 file open on the left. 

    Changes are highlighted for your review. Hover over a highlighted change to show tooltips related to your changes.

### Step 4: Upload the migrated website record

1.  Use the [pac paportal upload](/power-platform/developer/cli/reference/paportal) command to upload the migrated website record to the organization. 

After you upload your website record, the migrated site will be a Bootstrap version 5 website. We recommend that you [compare the site against your version 3 site](#step-3-review-your-changesoptional) one more time. Based on this comparison, modify Bootstrap version 5 site as needed to meet your requirements.

