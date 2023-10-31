---
title: Migrate standard data model sites to enhanced data model (preview)
description: Learn how to use the enhanced data model in a Power Pages site.
author:  gitanjalisingh33msft
ms.topic: conceptual
ms.custom: 
ms.date: 10/31/2023
ms.subservice:
ms.author:  
ms.reviewer: kkendrick
contributors:
    - gitanjalisingh33msft
    - professorkendrick
---

# Migrate standard data model sites to enhanced data model (preview)

In this article, learn about how to migrate your existing standard data model site to enhanced data model. Since the migration steps require the use of Microsoft Power Platform CLI, ensure you understand how to use Power Platform CLI in Power Pages. More information: [Microsoft Power Platform CLI support for Power Pages](https://learn.microsoft.com/en-us/power-pages/configure/power-platform-cli), [Tutorial: Use Microsoft Power Platform CLI with Power Pages](https://learn.microsoft.com/en-us/power-pages/configure/power-platform-cli-tutorial), [pac powerpages](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/powerpages)

## Prerequisites

- You must install [Microsoft Power Platform CLI](https://learn.microsoft.com/en-us/power-platform/developer/cli/introduction#install-using-power-platform-tools-for-visual-studio-code) with version 1.26.6 or higher to migrate your sites to enhanced data model. More information: [Install latest Power Platform CLI](https://learn.microsoft.com/en-us/power-platform/developer/cli/introduction#update-power-platform-cli-for-windowsmacoslinux)

- Dataverse base portal package [9.3.2307.x](https://learn.microsoft.com/en-us/power-apps/maker/portals/versions/package-version-9.3.2209) or higher. 

- Power Pages Core package 1.0.2309.63 or higher. More information: [Update the Power Pages solution](update-solution.md)

## Step 1: Download and check customization for existing standard site metadata.

1. Open a command prompt.

1. Use the following command to authenticate to the Dataverse organization for your Power Platform environment to download the website record for migration.

    pac auth create -u \[Dataverse URL\]

    **Example:**

    pac auth create -u https://contoso-org.crm.dynamics.com

    More information: [pac auth create](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/auth)

1. Use the following command to generate a list of websites in the current organization.

    pac powerpages list

    More information: [pac powerpages list](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/powerpages#pac-powerpages-list)

1. Use the following command to download the customization report.

    pac powerpages **datamodel-migrate** -id \[WebSiteId-GUID\] -**downloadCustomizationreport** \[PATH\]

    **Example:**

    pac powerpages **datamodel-migrate** -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b  --**downloadCustomizationreport** "c:\\pac-powerpages\\downloads"

If you find any customization in the downloaded report, follow guidance present in report to fix it post site migration to enhanced data model. You can also check the guidance here. \[Add link of guidance doc\]

## Step 2: Migrate the site data from standard to enhanced data model.

Use the following command datamodel-migrate

pac powerpages **datamodel-migrate** -id \[WebSiteId-GUID\] –**mode** \[type-of-data\] -**templateName** \[Website-template-name\]

**Mode:** It can have 3 values

- **configurationData**: migrate the metadata for website. [List of tables store configuration data.](https://learn.microsoft.com/en-us/power-pages/admin/enhanced-data-model#virtual-tables)

- **configurationDataReferences**: migrate the transactional data for website. [List of tables store non configuration data.](https://learn.microsoft.com/en-us/power-pages/admin/enhanced-data-model#nonconfiguration-tables)

- **all**: migrate both types of data.

**Template Name:** Pass the site template name for site. Site with following template are supported for migration:

- Starter layout 1-5
- Application processing
- Blank page
-Program registration
- Schedule and manage meetings

**Example:**

pac powerpages **datamodel-migrate** -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b –**mode** all -**templateName "**Starter layout 1**"**

## Step 3: Verify the migration status.

To verify the status of a site migration that is experiencing longer than anticipated duration due to a substantial volume of data, and in which the command prompt unexpectedly closes.

Use the following command 

pac powerpages **datamodel-migrate** --**checkMigrationStatus** -id\[WebSiteId-GUID\]

**Example:**

pac powerpages **datamodel-migrate** --**checkMigrationStatus** -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b  --

## Step 4: Update site data model version after successful data migration.

Use the following command update site data model version

pac powerpages **datamodel-migrate** --**updateDatamodelVersion** -id \[WebSiteId-GUID\]\] -**portalId**\[Portal-GUID\]

**Note**: You can find the Portal id by navigating to the website with '/\_services/about' appended to the URL of the website. In order to view these options, user should have a webrole with all [website access permissions](https://learn.microsoft.com/en-us/power-pages/security/website-access-permission) assigned.

**Example:**

pac powerpages **datamodel-migrate** --**updateDatamodelVersion** -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b  \] - **portalId** d44574f9-acc3-4ccc-8d8d-85cf5b7ad141

## Revert migrated site from enhanced to standard data model

Use the following command to revert standard data model site to enhanced data model post migration:

pac powerpages **datamodel-migrate** --**revertToStandardDataModel** -id \[WebSiteId-GUID\]\] -**portalId**\[Portal-GUID\]

**Example:**

pac paportal **datamodel-migrate** --**revertToStandardDataModel** -id 'f88b70cc-580b-4f1a-87c3-41debefeb902' -portalid '8fd85fc0-3be4-ed11-8848-000d3af37e5b'

## Migrate a production site from standard to enhanced data model

We recommend creating full copy of the production site and try out the migration on copied version of environment before production site migration and also plan the production site migration in non-business hours.

Below are the steps to migrate production site to enhanced data model:

Step 1: Try out the migration on site in the copied environment using the above mentioned PAC CLI commands.

Step 2: Add site configuration data to managed solution and import it production environment.

Step 3: Use PAC CLI commands to migrate non-configuration data and finish it by updating data model version for production.

Note: For migration the source and production website id are same.
