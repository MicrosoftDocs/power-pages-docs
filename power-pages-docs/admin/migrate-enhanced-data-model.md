---
title: Migrate standard data model sites to enhanced data model
description: Learn how to migrate your standard data model site to the enhanced data model in Power Pages.
author:  neerajnandwana-msft
ms.topic: upgrade-and-migration-article
ms.custom: 
ms.date: 08/28/2026
ms.subservice:
ms.author: nenandw 
ms.reviewer: smurkute
contributors:
    - gitanjalisingh33msft
    - neerajnandwana-msft
ai-usage: ai-assisted
---

# Standard to enhanced data model migration overview

The Microsoft Power Platform CLI migration utility moves an existing Power Pages site's supported configuration and related records from the standard data model to the enhanced data model, and then switches the site to use the migrated configuration.

The standard data model stores Power Pages site configuration across tables that use the adx\_ prefix. The enhanced data model stores site configuration in the **Site Component** table (powerpagecomponent) and identifies each component by its component type. Understanding how the migration utility works, which templates it supports, and which customizations it doesn't update automatically helps you decide when and how to move a site.

Reviewing the enhanced data model [benefits](./enhanced-data-model.md#benefits) explains why you might consider migrating a site.

It's important to note that not all adx_\* tables move into `powerpagecomponent`. Only the metadata adx_\* tables — the ones that describe the structure and authoring surface of the site, such as `adx_webpage`, `adx_webtemplate`, `adx_contentsnippet`, `adx_sitesetting`, `adx_pagetemplate`, `adx_weblink`, `adx_entityform`, and `adx_entitylist` — are consolidated into `powerpagecomponent` (with their per-row properties moved into the content JSON column).

The transactional / runtime adx_\* tables — the ones that capture end-user activity at runtime, such as `adx_invitation`, `adx_inviteredemption`, `adx_portalcomment`, `adx_externalidentity`, and the entity-form / advanced-form submission and log tables — are not migrated into `powerpagecomponent`; they remain on their existing schemas and keep storing runtime data as before. What changes for those transactional tables is that their lookups to metadata records get rewired during the references migration so that they point at the new `powerpagecomponent` rows instead of the legacy metadata adx_\* rows.

Existing sites authored on standard data model continue to run on adx_\* tables, so each site must be migrated to benefit from enhanced data model. Migration moves the site's configuration metadata into the enhanced data model `powerpagecomponent` shape, rewires transactional references onto those new metadata records, and flips the site record to serve from enhanced data model. It is also where customizations — custom adx_\* columns, Liquid that reads adx_\* attributes, FetchXML over adx_* tables, plugins, and workflows — are surfaced and remediated, because those customizations don't carry over automatically and must be rewritten or restructured to work against enhanced data model.

## Prerequisites

* [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction#install-using-power-platform-tools-for-visual-studio-code) **version 2.11.2 or later**, which runs the site download, migration, status, activation, and rollback commands. For more information, see [Install latest Power Platform CLI](/power-platform/developer/cli/introduction#update-power-platform-cli-for-windowsmacoslinux).
* Dataverse base portal package `CDSBasePortal` **9.3.2607.x or later**, which provides the required base portal components.
* Power Pages Core package `PowerPages_Core` **1.0.2605.x or later**, which provides the required Power Pages runtime components. [Update the Power Pages solution](update-solution.md).
* The System Administrator, Dynamics 365 Administrator, or Power Platform Administrator role, which is required to switch or revert the active data model.
* Familiarity with [Power Platform CLI for Power Pages](../configure/power-platform-cli.md).
* [Background operations](/power-platform/admin/admin-mode#set-administration-mode) enabled if the environment is in administration mode.

## Migration utility capabilities

The migration utility copies supported site configuration and related records to the enhanced data model. After migration finishes, the active site switches to the enhanced data model and is validated before it returns to normal use.

The migration utility:

* Generates a report of customizations that might require manual changes.
* Migrates supported site configuration and related records.
* Lets you check migration status before switching the active data model.
* Lets you revert the site to the standard data model if validation identifies a critical issue.

> [!IMPORTANT]
> The migration utility doesn't automatically update every customization that directly depends on standard data model tables. Review the customization report, fix affected custom code, and test the migrated site before production use.

## Supported templates

You can migrate existing standard data model sites that were created from the following templates:

* Starter layout 1-5
* Application processing
* Blank page
* Program registration
* Schedule and manage meetings
* FAQ
* Community Portal (Dynamics 365)
* Customer Self-Service Portal (Dynamics 365)
* Employee Self-Service Portal (Dynamics 365)
* Partner Portal (Dynamics 365)

> [!NOTE]
> Creating new sites with the enhanced data model and migrating existing sites are separate capabilities. If a site's original template isn't listed here, don't run the migration utility for that site.

## Before you begin

Additional planning considerations:

* The **Switch to enhanced data model** environment setting controls the data model used for new sites. Turning on the setting doesn't migrate existing sites.
* Run the migration first in a full copy of the production environment. Complete customization remediation and validation before migrating.
* Use your organization's standard backup and restore process to back up the production environment.
* Plan a maintenance window for the final production switch and validation.
* Record the website ID, portal ID, environment URL, CLI version, package versions, migration start time, and command output form as part of the migration record.

### Plan the environment sequence

Migration supports different environments, with a different mode for each environment.

| **Environment** | **Recommended mode** | **What you do** |
|----|----|----|
| Development | `configurationData` | Migrate configuration, review the customization report, remediate customizations, validate, and capture the configuration in a solution. |
| Test or UAT | `configurationDataReferences` | Import the tested solution from development, migrate supported related records, activate the enhanced data model, and validate. |
| Production | `configurationDataReferences` | Import the validated managed solution, migrate supported related records, activate during the maintenance window, and complete production validation. |
| Single environment or simple site | `all` | Migrate configuration and related records in one operation only when you understand the customization impact and don't use the multienvironment solution path. |

### Create a working folder

Use an empty working folder to hold reports, downloaded site source, and comparison files. The following examples use `\<OUTPUT\>` for this location.

```console
mkdir C:\PowerPagesMigration\<site-name>
cd C:\PowerPagesMigration\<site-name>
```

## Migration phases

The migration process consists of four phases:

1. **Pre-checks** — Verify the site, IDs, CLI, packages, template solution, and migration status.
1. **Configuration** — Migrate configuration in development or import tested configuration in downstream environments.
1. **Migrate and activate** — Migrate related records, confirm completion, switch models, and restart.
1. **Validate** — Test behavior, permissions, custom code, and template journeys.

:::image type="content" source="media/enhanced-data-model/enhanced-data-model-migration-process.png" alt-text="Screenshot of a flowchart showing the standard to enhanced data model migration process." lightbox="media/enhanced-data-model/enhanced-data-model-migration-process.png":::

Phase 1 (Site discovery and pre-checks) and Phase 4 (Post-migration validation) run the same way for every site.

Phase 2 and Phase 3 are track-branched - their shape depends on the migration mode, which derives the track from the environment type.  

The **Authoring Track** (mode `configurationData` or `all`) is used for Dev and single-environment setups. The metadata itself is migrated locally and customizations are scanned and fixed against the standard data model source before transactional references move.

The **Downstream Track** (mode `configurationDataReferences`) is used for Test, UAT, and Production environments where configuration metadata is assumed to have arrived via ALM solution import from Dev. Only transactional references migrate in this track. Any customization findings indicate an upstream ALM gap rather than work you should do locally.

## Phase 1: Pre-checks

1. Verify your Power Platform CLI version with `pac --version`. If your version is earlier than the required version, install or update the [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction?tabs=windows) before continuing.
1. Authenticate to the target environment.
    1. Run `pac auth list`.
    1. Run `pac auth who`.
1. Confirm that the active authentication profile points to the environment that contains the site. To select another profile or create a profile, use `pac auth select` or `pac auth create -u "https://contoso.crm.dynamics.com"`.
1. Install Enhanced Data model solutions for your template using one of the following methods:
   1. Provision a site of your template with enhanced data model (EDM) flag enabled in the admin center.
   1. Use the CLI to install with the command `pac application install --application-name "PowerPages_PartnerPortal_V2"`
1. Find the site and record its identifiers with `pac pages list -v`.
1. Record the values shown in the following table.

   | **Value** | **Used for** |
   |----|----|
   | Website ID | All `migrate-datamodel` commands. |
   | Portal ID | Switching to the enhanced data model and reverting to the standard data model. |
   | Friendly name and URL | Confirming that you selected the correct site in the admin center. |
   | Data model version | Must be **Standard**. If it is already **Enhanced**, migration isn't required. |

   > [!IMPORTANT]
   > The portal ID isn't the Power Pages app ID. If the CLI doesn't show the portal ID, it's available in Power Platform admin center under **Resources** > **Power Pages sites** > **Site details**, or append `/_services/about` to the site URL while signed in with the required website access permissions.

1. Check for a previous or in-progress migration with the following command:

   ```powershell
   pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --checkMigrationStatus
   ```

   | **Status** | **Meaning** | **Action** |
   |----|----|----|
   | NotStarted or no tracker | No migration has started. | Continue with the package checks. |
   | Reverted | A previous migration was rolled back. | Review why it was reverted, then continue when ready. |
   | Completed | Migration finished, but the site might not have been switched. | Confirm the active data model. If it is still Standard, continue with activation. |
   | Running | Migration is still processing. | Continue checking status. Don't start another migration for the same site. |
   | Failed | The migration encountered an error. | Collect the command output and environment details, correct the cause, and retry only after the failure is understood. |

   > [!NOTE]
   > If a migration remains Running longer than expected, you need the website ID, environment ID, CLI version, package versions, command output, and migration start time before contacting Microsoft support. An active migration shouldn't be reset unless support or an approved runbook instructs it.

1. Verify required first-party packages with `pac solution list --includeSystemSolutions`.
    1. Confirm that `CDSBasePortal`, `PowerPages_Core`, and the EDM solutions for the site's template are installed at the required versions.
1. If a package is missing or outdated, update it from the Power Platform admin center:
   1. Open the target environment.
   1. Go to **Resources** > **Dynamics 365 apps**.
   1. Find the required package.
   1. Select **Install** or **Upgrade**.
   1. Wait for the operation to finish, then run `pac solution list --includeSystemSolutions` again.

   > [!NOTE]
   > If the template EDM solution isn't available for direct installation, creating a temporary enhanced data model site in the same environment with the same template installs the matching EDM solution. You can delete the temporary site after the solution is confirmed.

1. Generate the customization report with `pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --siteCustomizationReportPath "<OUTPUT>"`. Generating the report doesn't change the site.
1. Open the generated CSV file and review each item that references standard data model tables. Assign an owner and validation step for every required remediation before production migration.

   | **Customization category** | **Plan** |
   |----|----|
   | Custom columns on adx\_ metadata tables | Move the custom data to a supported custom table related to powerpagecomponent. |
   | Relationships to adx\_ metadata tables | Recreate the relationship against the supported enhanced data model table. |
   | Liquid or FetchXML references to adx\_ tables | Update code to use supported Liquid objects, virtual tables, or powerpagecomponent. |
   | Workflows and plug-ins on adx\_ tables | Refactor and register the logic against supported enhanced data model tables. |

   > [!NOTE]
   > A customization report doesn't prove that all site behavior works after migration; validation is still required.

1. Choose the migration mode to determine what the utility migrates in a single operation.

   | **Mode** | **What it migrates** | **When to use it** |
   |----|----|----|
   | configurationData | Supported site configuration metadata, such as pages, web templates, snippets, settings, forms, lists, web roles, and table permissions. | Development, where you remediate configuration and move it through solutions. |
   | configurationDataReferences | Supported records that refer to migrated site configuration. | Test, UAT, and production after the site configuration arrives through a solution import. |
   | all | Both configuration and supported related records. | A single environment or a simple migration that doesn't use the solution-based environment sequence. |

## Phase 2: Site configuration

### Authoring Track: Development or a single environment

1. Download an SDM baseline by running `pac pages download --webSiteId "<WEBSITE_ID>" --modelVersion 1 --path "<OUTPUT>\site-sdm"`. The command creates a child folder named for the site. Record the folder that directly contains `website.yml`.
1. Migrate site configuration by running `pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --mode configurationData`. If you want the single-operation path, replace `configurationData` with `all`.
1. Check migration status by running `pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --checkMigrationStatus`. Use the following PowerShell loop to check status once per minute for up to 30 minutes:

   ```powershell
   $webSiteId = "<WEBSITE_ID>"
   for ($i = 1; $i -le 30; $i++) {
       $output = pac pages migrate-datamodel `
           --webSiteId $webSiteId `
           --checkMigrationStatus 2>&1 | Out-String
       if ($output -match "Completed|Failed|Reverted") {
           Write-Host $output
           break
       }
       Write-Host "Attempt $i/30 - migration is still running."
       Start-Sleep -Seconds 60
   }
   ```

   If the loop ends while the status is still Running, checking continues with `--checkMigrationStatus`. A long-running operation isn't necessarily a failed operation.

1. Remediate reported customizations by using the customization report and the guidance in this article to update affected FetchXML, Liquid, custom columns, relationships, workflows, and plug-ins. Retest each changed component. If you update the downloaded source, upload the site folder that directly contains `website.yml` by running `pac pages upload --path "<OUTPUT>\site-sdm\<site-slug>" --modelVersion 1`.

### Downstream Track: Test, UAT, or production

1. Import the solution that contains the migrated and remediated site configuration. Use Power Platform admin center or your established deployment pipeline.

   ```powershell
   pac solution import --path "<PATH_TO_SOLUTION_ZIP>" --activate-plugins true --publish-changes true
   ```

1. Confirm that the site configuration is present by opening the Power Pages Management app in the target environment. The site record and expected configuration need to be present before related records are migrated.

## Phase 3: Related records and activation

1. Migrate supported related records. If you already used `--mode all`, skip this step. Check status until it reports **Completed**.

   ```powershell
   pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --mode configurationDataReferences
   pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --checkMigrationStatus
   ```

1. Once migration status reports successful completion, switch the active site to the enhanced data model. The standard data model website record is deactivated and the corresponding enhanced data model website record becomes active.

   ```powershell
   pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --updateDatamodelVersion --portalId "<PORTAL_ID>"
   ```

1. Restart the site.
   1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com).
   1. Go to the environment, and then select **Resources** > **Power Pages sites**.
   1. Select the site.
   1. Select **Restart**. If **Restart** isn't available, deactivate and then activate the site.
   1. Wait for the operation to finish before validation.

1. Confirm the active data model by using one or more of these methods:

   1. In Power Platform admin center, select the site and confirm that **Data model** shows **Enhanced**.
   1. Open the site's **Setup** workspace in Power Pages design studio and confirm the displayed data model.
   1. Confirm that advanced configuration opens in the Power Pages Management app.
   1. Run `pac pages list -v` and confirm the data model version.

   > [!TIP]
   > The site URL and visual design don't change just because the active data model changed. To verify migration, use these checks — not the site's appearance.

## Phase 4: Validate the migrated site

Complete validation before reopening a production site to users. Use test accounts for each important user type and web role, and record the result of every critical test.

| **Area** | **What to validate** |
|----|----|
| Pages and content | Home page, representative content pages, web templates, content snippets, web files, navigation, redirects, and multilingual content. |
| Authentication | Sign-in, sign-out, registration, invitations, external identity providers, and access-denied experiences. |
| Authorization | Web roles, table permissions, column permissions, and page access rules allow and deny the expected actions. |
| Forms and lists | Basic forms, multistep forms, lists, form metadata, submissions, related records, and web form sessions used by the site. |
| Dynamics 365 template journeys | The main customer, employee, community, or partner journeys used by your implementation, including template-specific pages and access patterns. |
| Custom code | Liquid, FetchXML, JavaScript, plug-ins, workflows, and integrations identified in the customization report. |
| Site settings and files | Site settings, images, attachments, SVG files, and other web files load correctly. |
| Data and references | Important record counts and supported related records point to the correct migrated site components. |
| Administration and ALM | The site opens in Power Pages Management and can be added to, exported in, and imported from solutions as expected. |

### Check browser diagnostics

Open browser developer tools while testing representative pages. Investigate:

* Console errors that mention `adx\_`, entities, Liquid, or FetchXML.
* HTTP 401 or 403 responses from `\_api`, which can indicate a permission or web-role issue.
* HTTP 500 responses, which can indicate a Liquid, FetchXML, plug-in, or integration failure.

### Migration completion criteria

Consider the migration complete only when the site shows the enhanced data model, critical business journeys pass, expected security behavior is confirmed, and every high-impact customization finding is resolved or accepted.

## Production migration sequence

Use the following production sequence to reduce migration risk:

1. Create a full copy of the production environment for rehearsal.
1. Confirm CLI, package, and template solution prerequisites in the copied environment.
1. Generate and review the customization report.
1. Migrate configuration in the copied development environment.
1. Remediate customizations and capture the validated site configuration in a managed solution.
1. Import the solution into the rehearsal environment, migrate supported related records, activate the enhanced data model, and complete the full validation checklist.
1. Repeat remediation and rehearsal until all critical tests pass.
1. Schedule the production maintenance window, communicate the validation and rollback decision points, and back up production.
1. Confirm production package and template solution prerequisites again.
1. Import the validated managed solution into production.
1. Run `configurationDataReferences`, check migration status, switch the active data model, and restart the site.
1. Run the production validation checklist and return the site to normal use only after critical tests pass.

## Revert a migrated site to the standard data model

If validation identifies a critical issue after activation, use the following command to reactivate the standard data model website record:

```powershell
pac pages migrate-datamodel --webSiteId "<WEBSITE_ID>" --revertToStandardDataModel --portalId "<PORTAL_ID>"
```

After the command finishes:

1. Restart the site from Power Platform admin center.
1. Confirm that the site shows **Standard** as the active data model.
1. Rerun the site's critical validation tests.
1. Preserve the migration report, error details, and remediation notes before attempting another migration.

> [!IMPORTANT]
> Plan the rollback decision before production migration. Review changes made after the enhanced data model switch before reverting, because the standard and enhanced website records are separate records.

## Troubleshooting

| **Message or symptom** | **Likely cause** | **Action** |
|----|----|----|
| `pac powerpages migrate-datamodel` isn't recognized | The command uses the wrong namespace or an outdated CLI. | Update Power Platform CLI and use `pac pages migrate-datamodel`. |
| `CDSBasePortal` or `PowerPages_Core` isn't listed | System solutions weren't included in the command output, or the package isn't installed. | Run `pac solution list --includeSystemSolutions`. Install or upgrade the missing package from Power Platform admin center. |
| Website not supported for migration | The original template isn't supported, package versions are insufficient, or the matching EDM template solution is missing. | Confirm template eligibility, package versions, and the EDM solution listed in the template solution reference. |
| An unknown argument `--webSiteId` was passed for `pac pages upload` | The upload command doesn't accept the website ID argument. | Omit the argument. The site is identified from `website.yml`. |
| Upload targets the wrong site or fails to find the site | The path points to the wrapper folder instead of the site folder. | Use the child folder that directly contains website.yml. |
| Portal ID shows `Unknown` or `N/A` | The site is inactive or the installed CLI doesn't return the value. | Get the portal ID from Power Platform admin center or the site's `/_services/about` page. Don't use the app ID. |
| Migration reports `Completed` but the site still shows `Standard` | The active data model wasn't switched, or the wrong portal ID was used. | Run the activation command with the website ID and correct portal ID, then restart and verify the site. |
| Status remains `Running` | The migration is processing a large volume of data or is blocked. | Continue checking status. Collect the environment, package, CLI, start-time, and command details before contacting support. Don't start a second migration. |
| Status is `Failed` | A package, template, customization, data, or service error stopped the operation. | Save the complete command output, correct the identified cause, and retry only after reviewing the failed migration state. |
| The site opens, but users can't access expected data | Web roles, table permissions, or custom queries don't behave as expected after migration. | Review web roles, table permissions, column permissions, FetchXML, Liquid, and browser network errors. |

## Consideration for site customizations

The customization report identifies direct dependencies on standard data model tables. Complete required remediation before production use.

### Custom columns on metadata tables

If a standard data model table such as `adx_webpage` contains a custom column, create a custom table to store the custom data and add a lookup to `powerpagecomponent`. Migrate the custom values to the new table and update code that reads or writes the column.

### Relationships between custom tables and metadata tables

Recreate custom relationships that point to `adx_` tables so that they point to the appropriate enhanced data model table, commonly `powerpagecomponent`. Update dependent forms, views, plug-ins, flows, and integrations.

### Liquid references to metadata tables

Replace direct `entities['adx_*']` access with a supported Liquid object where one exists. For example, use the `weblinks` Liquid object instead of directly querying `adx_weblinkset` or related tables. Review each use because the returned object and available attributes can differ.

### FetchXML references to metadata tables

Replace direct `adx_` entity references with the corresponding virtual table or query `powerpagecomponent` and filter by `powerpagecomponenttype`

**Standard data model example:**

```xml
<fetch>
  <entity name="adx_webpage">
    <attribute name="adx_name" />
    <filter>
      <condition attribute="adx_partialurl" operator="eq" value="home" />
    </filter>
  </entity>
</fetch>
```

**Enhanced data model example:**

```xml
<fetch>
  <entity name="powerpagecomponent">
    <attribute name="name" />
    <filter type="and">
      <condition attribute="powerpagecomponenttype" operator="eq" value="2" />
      <condition attribute="partialurl" operator="eq" value="home" />
    </filter>
  </entity>
</fetch>
```

### Custom workflows and plug-ins

Refactor custom workflow and plug-in logic registered on `adx_` tables. Register the updated logic on the appropriate enhanced data model table and use the enhanced schema and attributes. Test create, update, delete, and security behavior in a nonproduction environment.

## Command reference

| **Purpose** | **Command** |
|----|----|
| Check CLI version | `pac --version` |
| List authentication profiles | `pac auth list` |
| Create an authentication profile | `pac auth create -u "<ENV_URL>"` |
| List sites and identifiers | `pac pages list -v` |
| List system solutions | `pac solution list --includeSystemSolutions` |
| Check migration status | `pac pages migrate-datamodel --webSiteId "<ID>" --checkMigrationStatus` |
| Download SDM source | `pac pages download --webSiteId "<ID>" --modelVersion 1 --path "<OUT>\site-sdm"` |
| Download EDM source | `pac pages download --webSiteId "<ID>" --modelVersion 2 --path "<OUT>\site-edm"` |
| Generate customization report | `pac pages migrate-datamodel --webSiteId "<ID>" --siteCustomizationReportPath "<OUT>"` |
| Migrate configuration | `pac pages migrate-datamodel --webSiteId "<ID>" --mode configurationData` |
| Migrate related records | `pac pages migrate-datamodel --webSiteId "<ID>" --mode configurationDataReferences` |
| Migrate both categories | `pac pages migrate-datamodel --webSiteId "<ID>" --mode all` |
| Upload site source | `pac pages upload --path "<SITE_ROOT>" --modelVersion 1` |
| Activate EDM | `pac pages migrate-datamodel --webSiteId "<ID>" --updateDatamodelVersion --portalId "<PORTAL_ID>"` |
| Revert to SDM | `pac pages migrate-datamodel --webSiteId "<ID>" --revertToStandardDataModel --portalId "<PORTAL_ID>"` |

## Site component type reference

When you query `powerpagecomponent`, use the following values in the [powerpagecomponenttype](/power-apps/developer/data-platform/reference/entities/powerpagecomponent#BKMK_powerpagecomponenttype) filter.

| **Component** | **Value** | **Component** | **Value** |
|----|----|----|----|
| Publishing State | 1 | Web Page | 2 |
| Web File | 3 | Web Link Set | 4 |
| Web Link | 5 | Page Template | 6 |
| Content Snippet | 7 | Web Template | 8 |
| Site Setting | 9 | Web Page Access Control Rule | 10 |
| Web Role | 11 | Website Access | 12 |
| Site Marker | 13 | Basic Form | 15 |
| Basic Form Metadata | 16 | List | 17 |
| Table Permission | 18 | Advanced Form | 19 |
| Advanced Form Step | 20 | Advanced Form Metadata | 21 |
| Poll Placement | 24 | Ad Placement | 26 |
| Bot Consumer | 27 | Column Permission Profile | 28 |
| Column Permission | 29 | Redirect | 30 |
| Publishing State Transition Rule | 31 | Shortcut | 32 |
| Cloud Flow | 33 | UX Component | 34 |

## EDM template solution reference

Run `pac solution list --includeSystemSolutions` to confirm that the enhanced data model solution for the site's template is installed.

| **Template** | **EDM solution unique name** |
|----|----|
| Starter layout 1 | DefaultPortalTemplate_V2 |
| Starter layout 2 | PowerPages_BlankDesign002_V2 |
| Starter layout 3 | PowerPages_BlankDesign003_V2 |
| Starter layout 4 | PowerPages_BlankDesign004_V2 |
| Starter layout 5 | PowerPages_BlankDesign005_V2 |
| Blank page | PowerPages_BlankTemplate_V2 |
| FAQ | PowerPages_FAQ_V2 |
| Application processing | PowerPages_BuildingPermit_V2 |
| Program registration | PowerPages_ProgramRegistration_V2 |
| Schedule and manage meetings | PowerPages_BookMeeting_V2 |
| Community Portal (Dynamics 365) | PowerPages_CommunityPortal_V2 |
| Customer Self-Service Portal (Dynamics 365) | PowerPages_CustomerPortal_V2 |
| Employee Self-Service Portal (Dynamics 365) | PowerPages_ESSPortal_V2 |
| Partner Portal (Dynamics 365) | PowerPages_PartnerPortal_V2 |

## Related content

* [Enhanced data model](./enhanced-data-model.md)
* [Power Platform CLI reference for Power Pages](/power-platform/developer/cli/reference/pages)
* [Use Power Platform CLI with Power Pages](../configure/power-platform-cli.md)
* [Update Power Pages solutions](./update-solution.md)