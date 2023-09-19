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
> - You can migrate any of your existing Power Pages version 3 sites regardless of the template used for initial site creation.
> - Developer environments are recommended to run the migration tool and test the changes with respect to the production website.

## Pre-requisite

- PAC CLI 1.26.6 is required in order to migrate your sites to Bootstrap version 5.
- If your site uses SVG files, you must enable .svg file support for your site's environment before you begin. To enable .svg file support:

    1. Choose the gear icon in top bar and then choose **advanced** settings

    1. Select the dropdown next to settings and choose system > administration. 

    1. Go to system settings and remove .svg from **Set blocked file extensions for attachments**

- Before you run the migration tool, you must install [Power Platform tools for Visual Studio Code](/power-platform/developer/cli/introduction). To install these tools: 
    1. Authenticate to the Dataverse Org from where the website record will be downloaded for migration.

        1. Open the command prompt.

        1. Command: pac auth create --url https://dataverseOrg.crm10.dynamics.com

        1. PAC CLI Auth ref: [Pac Auth](/power-platform/developer/cli/reference/auth)

## Use the migration tool

We strongly recommend creating two of your Bootstrap version 3 sites in your environment.  You'll use one of these sites for the migration. The duplicate site is used as a reference to compare against the migrated site.

### Step 1: Download the website folder

You'll begin by generating a list of websites in the current organization by using the command **pac paportal list**.

Next, use the PAC CLI download command [PAC CLI Doc](/power-platform/developer/cli/reference/paportal#pac-paportal-download) to download the website folder.

    Command Prompt: pac paportal download -p "DownloadDestinationPath" -id "WebsiteID"

    >[!NOTE] 
    > 
    > - **-p** refers to the folder path 
    > - **-id** refers to the website id

### Step 2: Run the migration tool on the website folder

Use the bootstrap-migrate command to run the tool on the downloaded website folder.

    Command : pac paportal bootstrap-migrate -p "WebsiteFolderPath"

A new folder is created after running the migration with **V5** appended to the name of the folder.

### Step 3 (optional): Review the diffs using the custom VS code extension: BootstrapMigrationDiff

1.  Open the V5 folder which was created after the migration process in VS Code

2.  Open a html/css file to compare the difference.

    1.  Ex: check the header web template.

    2.  Go to "web templates/header". Open the header source html file: "Header.webtemplate.source.html"

3.  Run the bootstrap diff extension to compare the changes.

    1.  In VS code execute "Ctrl + Shift + P" to open the command palette.

    2.  In the command palette execute the command "**Bootstrap Diff**".

    3.  On execution V3 file will open on the right alongside the V5 file in a different window, with the changes being highlighted.

    4.  V5 file on the left will also show the breaking change as a tooltip when you hover over the highlighted change.

### Step 4: Upload the migrated website record

1.  Use the PAC CLI upload command to upload the migrated website record to the org

    1.  Command : pac paportal upload -p "MigratedWebsiteFolderPath"

### Step 5: Comparing the two websites

1.  After uploading, the migrated site will be a Bootstrap v5 compliant website.

2.  Compare the diffs using the diff extension and compare the rendering of Site 1 (on Bootstrap v3) and Site 2 (on Bootstrap v5).

3.  Based on the above comparisons, you can make changes to the code of Bootstrap v5 site as needed based on the changes introduced with Bootstrap v5.

