---
title: Migrate Power Pages website configuration
description: Learn how to migrate Power Pages website configuration.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 06/09/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - nickdoelman
    - vashr
---

# Migrate website configuration

Power Pages website development involves several configurations and customizations to achieve a desired experience for website end users.

After you have completed development or configuration of your website instance, you might want to migrate your latest website configuration from development to testing or the production environments. 

Migration involves exporting the existing configuration from the source Microsoft Dataverse environment, and then importing it into the target Dataverse environment.

## Prepare the target environment

You will need to prepare the target environment if you are using the standard data model. An environment using the [enhanced data model](../admin/enhanced-data-model.md) will not require these steps and you can proceed to [transferring the website configuration](#transfer-the-website-configuration-to-target-environment).

> [!NOTE]
> - Preparing the target environment is a one-time process. You will need to provision a new website in order to install the managed Power Pages solutions on Dataverse as well as configure the Power Pages web application. The process also installs default website metadata which will be replaced with the website metadata from your source environment.
> - Ensure that the target environment's maximum attachment size is set to the same or greater size as your source environment.
> - The maximum size of files is determined by the **Maximum file size** setting in the [system settings email tab](/power-platform/admin/system-settings-dialog-box-email-tab) in the environment system settings dialog box.
> - Note the difference between developer, trial, and production **websites** and developer, trial, sandbox, and production **environments**.
> - You can [migrate](migrate-site-configuration.md) a trial, developer, production website to another trial, developer, or production website on the same or another environment. Note that a production **website** will need to be provisioned on a sandbox or production **environment**.

1. [Provision a new website](../getting-started/create-manage.md) in your target environment. Use the same [website template](../templates/index.md) as you provisioned on your source environment. For example, if you provisioned a site using the **Dynamics 365 Customer Self-Service** template on your source environment, provision the site using the **Dynamics 365 Customer Self-Service** template on your target environment.

1. On the *target* environment, using the [Portal Management app](../configure/portal-management-app.md), delete the newly created website record. This will remove the default website configuration data from the target environment.

    :::image type="content" source="media/migrate-portal-config/delete-website.png" alt-text="Delete website record.":::

1. On the *target* environment, in Power Apps, delete the portal app. This will remove the website currently configured to render the default site.

    > [!NOTE]
    > Do not delete the Portal Management app!

    :::image type="content" source="media/migrate-portal-config/delete-portal.png" alt-text="Delete portal app.":::

## Transfer the website configuration to target environment

[Transfer](#transfer-website-metadata) the site metadata from the source environment using the Power Platform CLI, the Configuration Migration Tool, or using [solutions](../configure/power-pages-solutions.md).

## Reactivating site on target environment

Once the website has been transferred to the target environment, you will need to reactivate the website.

1. On the target environment, on the Power Pages home screen, select **Inactive sites**, you should see the website you migrated to the environment.

1. Select **Reactivate**.

    :::image type="content" source="media/migrate-portal-config/reactivate-website.png" alt-text="Reactivate website.":::

1. You can specify the **Reactivated website** name and **Create a web address** or leave default values.

1. Select **Done**.

1. The website updates from the source environment should be reflected in this new target environment. Going forward, you should be able to transfer configuration from your source to target environments by transferring the website configuration data.

> [!NOTE]
> A website appearing in the **Inactive sites** list on the Power Pages home page will appear in the list of **Active Websites** in the [Portal Management app](../configure/portal-management-app.md).

## Transfer website metadata

# [Solutions](#tab/sol)

If your website is configured using the [enhanced data model](../admin/enhanced-data-model.md) you can transfer the website configuration using Power Platform solutions. For more information, go to [Using solutions with Power Pages](../configure/power-pages-solutions.md).

> [!NOTE]
> Make sure the target environment is also has the [enhanced data model](../admin/enhanced-data-model.md) enabled.

# [Power Platform CLI](#tab/CLI)

### Transfer website configuration using Power Platform CLI

The Microsoft Power Platform CLI provides many features specifically for [Power Pages](/power-apps/maker/portals/power-apps-cli). These commands allow you to download site configuration from a source environment and transfer it to a target environment. These commands can also be incorporated into your ALM processes.

1. Create Power Platform CLI authentication profiles to connect to both your source and target environments. You can give them a name to easily identify the target and source environments.

    ```powershell
    pac auth create --name [name] --url [environment url]
    ```

    **Example**

    ```powershell
    pac auth create --name PORTALDEV --url https://contoso-org.crm.dynamics.com
    ```

1. When the authentication profiles are created, they'll have an associated index that can be determined using the list command.

    ```powershell
    pac auth list
    ```

    :::image type="content" source="media/migrate-portal-config/pac-auth-list.png" alt-text="List of environments.":::

1. Select the Power Platform CLI authentication profile connected to the source environment.

    ```powershell
    pac auth select --index [source environment index]
    ```

    **Example**

    ```powershell
    pac auth select --index 1
    ```

1. Determine the website ID for the source site.

    ```powershell
    pac paportal list
    ```

    :::image type="content" source="media/migrate-portal-config/portal-list.png" alt-text="List of websites.":::

1. Download the website configuration data to your local workstation. Use the *--overwrite* option set to *true* if you have previous downloaded website configuration to the same path.

    ```powershell
    pac paportal download --path [path] --webSiteId [website id]
    ```

    **Example**

    ```powershell
    pac paportal download --path c:\paportals\ --webSiteId db9db518-ea5c-ec11-8f8f-00224804e6cd
    ```

1. Select the Power Platform CLI authentication profile connected to the target environment.

    ```powershell
    pac auth select --index [target environment index]
    ```

    **Example**

    ```powershell
    pac auth select --index 2
    ```

1. Upload the website configuration data to the target environment.

    ```powershell
    pac paportal upload --path [path]
    ```

    **Example**

    ```powershell
    pac paportal upload --path "C:\paportals\portaldev"
    ```

> [!NOTE]
> - The Power Platform CLI tool does not migrate Dataverse tables or table schema. Migration may fail with missing elements such as tables and fields when configuration data is mismatched with selected schema.
> - During import, ensure the destination environment contains the same website template type already installed with any additional customizations such as tables, fields, forms or views imported separately as solutions.

# [Configuration Migration Tool](#tab/CMT)

### Transfer website configuration using the Configuration Migration Tool

>[!NOTE]
> The preferred method is to use [solutions](../configure/power-pages-solutions.md) or the [Power Platform CLI](#transfer-website-configuration-using-power-platform-cli) to transfer website metadata.

To export configuration data, you would need to use the Configuration Migration tool and a website-specific configuration schema file. For more information about this tool, see [Manage configuration data](/power-platform/admin/manage-configuration-data).

> [!NOTE]
> - We recommend you to use the latest version of the Configuration Migration tool. The Configuration Migration tool can be downloaded from NuGet. More information for downloading the tool: [Download tools from NuGet](/dynamics365/customer-engagement/developer/download-tools-nuget).
> - The minimum solution version of websites supported by schema files for configuration migration is 8.4.0.275. However, we recommend that you use the latest solution version.
> - Source and destination organizations must have same default language for the migration to work successfully.

Schema files are available for the following website types:

- **Websites created in an environment with Dataverse**
    - [Custom portal (Blank portal)](https://go.microsoft.com/fwlink/p/?linkid=2110477)
    - [Custom portal (Blank portal)](https://go.microsoft.com/fwlink/p/?linkid=2162831) (for version [9.2.2103.x](/power-apps/maker/portals/versions/package-version-9.2.2103))
    - [Custom portal (Blank portal)](https://go.microsoft.com/fwlink/?linkid=2186536) (for version [9.3.2201.x](/power-apps/maker/portals/versions/package-version-9.2.2103) or higher)

- **Websites created in an environment containing customer engagement apps (such as Dynamics 365 Sales and Dynamics 365 Customer Service)**
    - [Custom portal (Blank portal)](https://go.microsoft.com/fwlink/p/?linkid=2019804)
    - [Custom portal (Blank portal)](https://go.microsoft.com/fwlink/p/?linkid=2162733) (for version [9.2.2103.x](/power-apps/maker/portals/versions/package-version-9.2.2103))
    - [Custom portal (Blank portal)](https://go.microsoft.com/fwlink/?linkid=2186261) (for version [9.3.2201.x](/power-apps/maker/portals/versions/package-version-9.3.2201) or higher)
    - [Community portal](https://go.microsoft.com/fwlink/p/?linkid=2019704)
    - [Customer Self-Service portal](https://go.microsoft.com/fwlink/p/?linkid=2019705)
    - [Partner portal](https://go.microsoft.com/fwlink/p/?linkid=2019803)
    - [Employee Self-Service portal](https://go.microsoft.com/fwlink/p/?linkid=2019802)

The default schema files contain information about website tables, relationships, and uniqueness definitions for each entity. More information: [Export website configuration data](#export-website-configuration-data)

After exporting the configuration data, you must import it into the target environment. More information: [Import website configuration data](#import-website-configuration-data)

> [!NOTE]
> - The Configuration Migration tool uses schema to export and import configuration data. The tool does not migrate Dataverse tables or table schema. Migration may fail with missing elements such as tables and fields when configuration data has mismatch with selected schema.
> - During export, ensure the source environment contains website tables as specified in Configuration Migration tool schema file. You can still alter the schema files to add, remove, and modify tables, attributes, and so on to migrate subset of configuration data.
> - During import, ensure the destination environment contains the same website type already installed with any additional customizations such as tables, fields, forms or views imported separately as solutions.

## Export website configuration data

You can export website configuration data from a source system by using website-specific configuration schema files.

1. Download the Configuration Migration tool and extract to the desired folder.

1. Download website configuration schema file using links provided above for your website template type.

1. Double-click the **DataMigrationUtility.exe** file in the 
`<your_folder>\Tools\ConfigurationMigration` folder to run the Configuration Migration tool, choose **Export data** in the main screen, and then select **Continue**.

    > [!div class=mx-imgBorder]
    > ![Export configuration data.](media/migrate-portal-config/export-config-data.png "Export configuration data")

1. On the **Login** screen, provide authentication details to connect to your Dataverse environment from where you want to export data. If you have multiple organizations on the Dataverse environment from where to export the data, select the **Display list of available organizations** check box, and then select **Login**.

1. If you have multiple organizations, and you had selected the **Display list of available organizations** check box in the previous step, the next screen allows you to choose the organization that you want to connect to. Select a Dataverse environment to connect to.

    > [!NOTE]
    > If you do not have multiple organizations, this screen is not displayed.

1. In **Schema file**, browse and select the website-specific configuration schema file to be used for the data export.

1. In **Save to data file**, specify the name and location of the data file to be exported.

    > [!div class=mx-imgBorder]
    > ![Specify schema and target files.](media/migrate-portal-config/export-config-file-name.png "Specify schema and target files")

1. Select **Export Data**. The screen displays the export progress status and the location of the exported file at the bottom of the screen once the export is complete.

    > [!div class=mx-imgBorder]
    > ![Progress of configuration data export.](media/migrate-portal-config/export-config-status.png "Progress of configuration data export")

1. Select **Exit** to close the tool.

## Import website configuration data

1. Run the Configuration Migration tool and choose **Import data** in the main screen, and then select **Continue**.

    > [!div class=mx-imgBorder]
    > ![Import configuration data.](media/migrate-portal-config/import-config-data.png "Import configuration data")

1. On the **Login** screen, provide authentication details to connect to your Dataverse environment from where you want to export data. If you have multiple organizations on the Dataverse environment from where to export the data, select the **Display list of available organizations** check box, and then select **Login**.

1. If you have multiple organizations, and you had selected the **Display list of available organizations** check box in the previous step, the next screen allows you to choose the organization that you want to connect to. Select a Dataverse environment to connect to.

    > [!NOTE]
    > - If you do not have multiple organizations, this screen is not displayed.
    > - Ensure that the portal solution is already installed for the organization where you plan to import the configurations.

1. The next screen prompts you to provide the data file (.zip) to be imported. Browse to the data file, select it, and then select **Import Data**.

    > [!div class=mx-imgBorder]
    > ![Progress of configuration data import.](media/migrate-portal-config/import-config-status.png "Progress of configuration data import")

1. The next screen displays the import status of your records. The data import is done in multiple passes to first import the foundation data while queuing up the dependent data, and then import the dependent data in the subsequent passes to handle any data dependencies or linkages. This action ensures clean and consistent data import.

1. Select **Exit** to close the tool.

---

### Create new website using migrated data

If the migration process is updating an existing website, the updates should now be visible in the target environment. 

If the migration is for a new website, the migrated website will be listed in the **Inactive sites** tab on the Power Pages home page.

1. On the target environment, on the Power Pages home screen, select **Inactive sites**, you should see the website you migrated to the environment.

1. Select **Reactivate**.

    :::image type="content" source="media/migrate-portal-config/reactivate-website.png" alt-text="Reactivate website.":::

1. You can specify the **Reactivated website** name and **Create a web address** or leave default values.

1. Select **Done**.

## Tenant-to-tenant migration

PowerPages doesn't support tenant-to-tenant migration. To migrate a website from one tenant to another, you must follow these steps:

1. [Reset](/power-apps/maker/portals/admin/reset-portal) your website in the source tenant.

1. Provision a [new website](../getting-started/create-manage.md) in an environment.

1. Migrate website configurations and customizations using the [steps](#transfer-website-metadata) explained in this article earlier.

### See also

- [Power Pages support for Microsoft Power Platform CLI](/power-apps/maker/portals/power-apps-cli).
- Tenant-to-tenant migration of a [Power Platform environment](/power-platform/admin/move-environment-tenant).
- Tenant-to-tenant migration of [model-driven apps](/dynamics365/admin/move-instance-tenant) in Dynamics 365 such as Sales, Customer Service, Marketing, Field Service, and Project Service Automation.
