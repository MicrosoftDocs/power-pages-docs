---
title: Migrate standard data model sites to enhanced data model (preview)
description: Learn how to migrate your standard data model site to the enhanced data model in Power Pages.
author:  gitanjalisingh33msft
ms.topic: conceptual
ms.custom: 
ms.date: 11/03/2023
ms.subservice:
ms.author: gisingh 
ms.reviewer: kkendrick
contributors:
    - gitanjalisingh33msft
    - professorkendrick
---

# Migrate standard data model sites to enhanced data model (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

In this article, learn how to migrate your existing standard data model site to enhanced data model. Since the migration steps require the use of Microsoft Power Platform CLI, ensure you understand how to use Power Platform CLI in Power Pages. More information: [Microsoft Power Platform CLI support for Power Pages](../configure/power-platform-cli.md), (../configure/power-platform-cli-tutorial.md), [`pac powerpages`](/power-platform/developer/cli/reference/powerpages)

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisites

- You must install [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction#install-using-power-platform-tools-for-visual-studio-code) with version 1.26.6 or higher to migrate your sites to enhanced data model. More information: [Install latest Power Platform CLI](/power-platform/developer/cli/introduction#update-power-platform-cli-for-windowsmacoslinux)
- Dataverse base portal package [9.3.2307.x](/power-apps/maker/portals/versions/package-version-9.3.2209)or higher. 
- Power Pages Core package 1.0.2309.63 or higher. More information: [Update the Power Pages solution](update-solution.md)

## Step 1. Download and check customization for existing standard site metadata

1. Open a command prompt.

1. Use the following command to authenticate to the Dataverse organization for your Power Platform environment to download the website record for migration.

    ```pac auth create -u [Dataverse URL]```

    **Example**

    ```pac auth create -u https://contoso-org.crm.dynamics.com```

    More information: [pac auth create](/power-platform/developer/cli/reference/auth)

1. Use the following command to generate a list of websites in the current organization.

    ```pac powerpages list```

    More information: [pac powerpages list](/power-platform/developer/cli/reference/powerpages#pac-powerpages-list)

1. Use the following command to download the customization report.

    ```pac powerpages migrate-datamodel -id [WebSiteId-GUID] -downloadCustomizationreport [PATH]```

    **Example**

   ``` pac powerpages migrate-datamodel -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b  --downloadCustomizationreport "c:\\pac-powerpages\\downloads"```

If you find any customization in the downloaded report, follow the guidance in the report to fix it post-migration to enhanced data model. More information: [Considerations for site customization when migrating sites from standard to enhanced data model](#considerations-for-site-customization-when-migrating-sites-from-standard-to-enhanced-data-model)

## Step 2. Migrate the site data from standard to enhanced data model

Use the following command to migrate your site data to the enhanced data model.

`migrate-datamodel`

**Example**

```pac powerpages migrate-datamodel -id [WebSiteId-GUID] –mode [type-of-data] ```

The **Mode** can have 3 values:

- **configurationData**: migrate the metadata for website. 
    More information: [List of tables to store configuration data](enhanced-data-model.md#virtual-tables)

- **configurationDataReferences**: migrate the transactional data for website. 
    More information: [List of tables to store nonconfiguration data](enhanced-data-model.md#nonconfiguration-tables)

- **all**: migrate both types of data.

### Supported templates for migration

Pass the site **Template Name** for the site. Sites with following templates are supported for migration:

- Starter layout 1-5
- Application processing
- Blank page
- Program registration
- Schedule and manage meetings

**Example**

```pac powerpages migrate-datamodel -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b –mode all ```

## Step 3. Verify the migration status  

Use the following command to verify your site's migration status:

```pac powerpages migrate-datamodel --checkMigrationStatus -id [WebSiteId-GUID]```

**Example**

```pac powerpages migrate-datamodel --checkMigrationStatus -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b  --```

> [!NOTE] 
> If your site migration is taking longer than anticipated, it may be due to the volume of data. If your command prompt closes, open a new command prompt and use the command in this step to verify your site's status.

## Step 4. Update site data model version after successful data migration

Use the following command update site data model version:

```pac powerpages migrate-datamodel --updateDatamodelVersion -id [WebSiteId-GUID] -portalId [Portal-GUID]```

> [!NOTE#]
> You can find the Portal id by navigating to the website with '/\_services/about' appended to the URL of the website. In order to view these options, user should have a web role with all [website access permissions](../security/website-access-permission.md) assigned.

**Example**

```pac powerpages migrate-datamodel --updateDatamodelVersion -id 8fd85fc0-3be4-ed11-8848-000d3af37e5b - portalId d44574f9-acc3-4ccc-8d8d-85cf5b7ad141```

## Revert migrated site from enhanced to standard data model

Use the following command to revert a standard data model site to enhanced data model after migration:

```pac powerpages migrate-datamodel --revertToStandardDataModel -id [WebSiteId-GUID] -portalId [Portal-GUID]```

**Example**

```pac paportal migrate-datamodel --revertToStandardDataModel -id 'f88b70cc-580b-4f1a-87c3-41debefeb902' -portalid '8fd85fc0-3be4-ed11-8848-000d3af37e5b'```

## Migrate a production site from standard to enhanced data model

Before migrating a production site, we recommend creating full copy of the production site. We also recommend production site migration be conducted during nonbusiness hours.

Use these steps to migrate your production site to the enhanced data model:

1. Try out the migration on the site in the copied environment using the PAC CLI commands.
1. Add site configuration data to managed solution and import it production environment.
1. Use PAC CLI commands to migrate nonconfiguration data and finish it by updating data model version for production.

> [!NOTE]
> For migration the source and production website id are same.

## Considerations for site customization when migrating sites from standard to enhanced data model 

 This section provides guidance fixing customization for a site migration from standard to enhanced data model. 

There are five types of site customizations on adx metadata tables: 

- [Custom columns on adx metadata tables](#custom-columns-on-adx-metadata-tables)
- [Relationship between custom tables and adx tables](#relationship-between-custom-tables-and-adx-tables)
- [Adx table references in liquid code snippet](#adx-table-references-in-liquid-code-snippet)
- [Adx table references in fetch xml](#adx-table-references-in-fetch-xml)
- [Custom workflow and plugins on adx tables](#custom-workflow-and-plugins-on-adx-tables)

> [!NOTE] 
> All customization related fixes will be done after migration to the enhanced data model.

### Custom columns on adx metadata tables 

To fix this customization, create a relationship between system tables and new custom table and migrate the data to the new table. 

### Relationship between custom tables and adx tables

To fix this customization, create a relationship between custom tables and system tables.

### Adx table references in liquid code snippet

To fix this customization, replace the adx table references in liquid code with enhanced data model virtual tables mspp references.  

### Adx table references in fetch xml

To fix this customization, replace the adx table references in fetch xml with enhanced data model virtual tables mspp references.  

### Custom workflow and plugins on adx tables

To fix this customization, the workflow and plugin logic needs to refactored and re-registered on the site's respective table. 
