---
title: Use environment variables with site settings
description: Discover the benefits of using environment variables for site settings in Power Pages for dynamic configuration management.
author: DanaMartens
contributors: null
ms.topic: conceptual
ms.date: 02/14/2025
ms.author: pudupa
ms.reviewer: dmartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:01/30/2025
---

# Use environment variables with site settings

Environment variables for site settings let makers and admins manage configuration values flexibly across environments. They enable smoother application lifecycle management (ALM) and deployment processes.

## Solution for enhanced data model

Use environment variables to define site settings values across various environments with the enhanced data model. While the standard data model relies on deployment profiles, the enhanced model allows for dynamic configuration of environment-specific settings using environment variables.

## Key definitions

To understand how environment variables can be used with site settings, familiarize yourself with the following key definitions:

- **Environment variable:** A variable that holds configuration values specific to an environment that the application or features can reference.
  
- **Site settings:** Configurable properties that influence the behavior of a site, such as identity provider site settings, progressive web applications, and advanced settings in the security workspace.
  
- **Environment variable reference:** A pointer to an environment variable within a site setting that enables dynamic value resolution at runtime.

## Benefits

Environment variables for site settings offer several benefits, including:

- Streamline ALM by avoiding hard-coded values in site settings.
- Simplify multi-environment deployments with environment-specific configurations.
- Enable dynamic updates to site behavior without redeploying solutions.
  
## How it works

This article describes how environment variables work with site settings. The following description is a high-level overview:

1. Makers define environment variables in the [Power Pages management app](portal-management-app.md) or in the solution designer.
1. Site settings reference these environment variables instead of static values.
1. When the site is accessed, the system resolves the referenced environment variable's value and applies it.
  
## Set up environment variables for site settings

### Prerequisites

To use environment variables with site settings, you must meet the following prerequisites:

- The site must be within an environment where the [enhanced data model](../admin/enhanced-data-model.md) is enabled.
- The following versions are required for environment variables to work in Power Pages:
  - Dataverse server version 9.2.25013.x
  - Power Pages package version 1.0.2501.x
  - Power Pages runtime version 9.7.1.x
  
### Use environment variables in site settings

To use environment variables in site settings:

1. Open the [Power Pages Management app](portal-management-app.md) and go to **Site Settings**.
1. Select the specific site setting you want to configure with an environment variable.
1. Select the source as **Environment Variable**.

    :::image type="content" source="media/environment-variables-for-site-settings/site-setting-source.png" alt-text="Screenshot showing a site setting with the source as environment variable.":::

1. If an environment variable definition is already created, select the **Environment Variable** lookup. A drop-down menu appears for selection.

    :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-selection.png" alt-text="Screenshot of the environment variable selection dropdown.":::

1. If an environment variable definition doesn't exist, select **New Environment Variable Definition** and fill in the required fields such as **Owner**, **Schema Name**, **Display Name**, and **Type**. Note the schema name value as that is what you need to use when you associate an environment variable with a site setting.

    :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-creation.png" alt-text="Screenshot of creating a new environment variable definition.":::

1. After you create the environment variable definition, it's available to select in the **Environment Variable** lookup control. Search for and select the schema name to relate it with the site setting.

> [!NOTE]
> - The data type set to "data source" isn't supported.
> - Environment variables with the data type set as "secret" can't be configured without providing key vault details.
> - For the `PWAFeature` site setting, use the value `{"status":"disable"}` for false and `{"status":"enable"}` for true.

## Update environment-specific values

To ensure that your site settings are correctly configured for each environment, follow these steps to update the environment-specific values in the Power Pages Management app or design studio.

> [!NOTE]
> Not all site settings have a corresponding configuration option in design studio.

# [Power Pages Management app](#tab/azure)

1. For each environment (for example, dev, QA, and production), go to the [Power Pages Management app](portal-management-app.md).
1. Locate the environment variable created earlier by opening the associated site setting.
1. Select the **Environment Variable**.
1. Within the **Values** section, select **New Environment Variable Value**.
1. Enter a **Value** and select **Save & Close**.

# [Design studio](#tab/keyvault)

1. For each environment (for example, dev, QA, and production), go to [design studio](../getting-started/use-design-studio.md).
1. Locate the configuration option that corresponds to the site setting.
1. Update the value.
1. Save the configuration.

    :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-PPMA.png" alt-text="Screenshot of updating the environment variable value in design studio.":::

> [!IMPORTANT]
> - When you're in design studio and view a site setting, a notification appears if it uses an environment variable. If you edit the value, it updates all referenced site settings across the environment.
> - If a site setting's data type is marked as secret, the field is disabled in the design studio, preventing makers from editing its values. Additionally, reading or writing Key Vault secrets within the design studio settings isn't supported.

---

After setting the environment variable, follow these additional steps:

1. Navigate to a solution and add your existing site, verifying that the relevant environment variables are also included.
1. Export the solution and then import it into the desired target environment.

During the import process into the target environment, assign a value to the environment variable. Changing the value updates the corresponding site settings in the target environment.

## Manage environment variables

You can manage site settings with environment variables whether you deploy [solutions](power-pages-solutions.md) manually or through [pipelines](power-pages-pipelines.md).

### Solutions

Set up your environment variables and sites across different environments by following these steps:
  
1. **Set up environment variables in the source environment**:
    1. Open the [Power Apps portal](https://make.powerapps.com/).
    1. Go to **Solutions** in the source environment.
    1. Within a solution, add a new environment variable by entering the required details and saving it.

        :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-solution-import.png" alt-text="Screenshot of the environment variable assignment during solution import.":::

    1. Incorporate the existing site into the solution.
  
1. **Configure site settings**:
    1. Open the **Power Pages Management app** and access **Site Settings**.
    1. Select the site setting to define for the environment.
    1. Use the dropdown menu to select or create an environment variable. Users can view and choose environment variables created through the solutions flow in this dropdown.

        :::image type="content" source="media/environment-variables-for-site-settings/new-environment-variable.png" alt-text="Screenshot of the pipeline configuration for environment variables.":::

> [!NOTE]
> In the site settings, the dropdown menu displays the names of environment variables created using the solutions flow, allowing users to easily select and associate them.
  
- During the import process into the target environment, you're prompted to assign a value to the environment variable.
- Any modifications made to the environment variable update the corresponding site settings with the new value in the target environment.

### Pipelines

If you use [pipelines](power-pages-pipelines.md) to deploy solutions, you specify the value of the environment variable for the target environment. If you update it, refresh the corresponding site settings to reflect the new value.
  
:::image type="content" source="media/environment-variables-for-site-settings/pipeline-deployment-setting.png" alt-text="Screenshot of the pipeline deployment settings for environment variables.":::

## Surfaces supporting environment variables for site settings

You can use environment variables for site settings in the following surfaces:

- **Power Pages Management app:** Create and manage environment variables.
- **Design studio:** View or edit the site settings with environment variables.
- **Solution designer:** Include environment variables in your ALM process.
- **Pipeline deployments:** Manage and validate environment-specific configurations during deployment.

## Clear cache after updates

 When changes are made to the environment variable value or default value, manually clear the cache using one of the following methods:

1. Select **Sync** in the [design studio](../getting-started/use-design-studio.md).

    :::image type="content" source="media/environment-variables-for-site-settings/sync-button.png" alt-text="Screenshot of the Sync button in the studio interface.":::

1. Clear the cache from the portal:
   - Sign in to the portal as an administrator and go to the website with '/_services/about' appended to the URL. For example: [https://contoso.powerappsportals.com/_services/about](https://contoso.powerappsportals.com/_services/about).

     :::image type="content" source="media/environment-variables-for-site-settings/clear-cache.png" alt-text="Screenshot of the portal details page showing the Clear cache button.":::

   - On the portal details page, select **Clear cache**.
  
1. Restart the portal from the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

## Troubleshooting

The following are some different reasons you might encounter errors when using environment variables with site settings:

- **Mismatch in environment variable value and expected type**

    For example, if a site setting like `Search/Enabled` expects a boolean value (true/false), but the environment variable contains an invalid value (such as 'abc') or is missing, it causes issues.

- **Unsupported environment variable source type**

    This issue occurs when the environment variable is configured in an unsupported way, such as setting the source type to "data storage".

- **Key Vault access issues**

    This type of issue can occur if the environment variable source is Key Vault, but the runtime is missing permissions or the secret is missing.

## Best practices

When working with environment variables for site settings, it's important to follow best practices to ensure efficient and effective management. Here are some key recommendations:

- **Usage**

    Use this feature only for ALM-related settings or secrets. Avoid using it for all site settings because it can lead to performance degradation.

- **Name variables consistently**

    Use consistent names for environment variables to make them easier to identify.

- **Document variables**

    Maintain a reference document listing all environment variables, their purposes, and their default values.

- **Test thoroughly**

    Validate changes in a nonproduction environment before applying them to production.

- **Use descriptions**

    Use the description field to explain the variable's purpose.

## Configure environment variables as secrets

To configure environment variables as secrets and use them in Power Pages, follow these steps:

1. Configure an environment variable as a secret. Learn more in [Use environment variables for Azure Key Vault secrets](/power-apps/maker/data-platform/environmentvariables-azure-key-vault-secrets).
  
2. Add permissions to access the secret from the portal.
    1. Within the Azure portal, get the name of your app in **App registrations** that corresponds to your Power Pages website.
    1. The app name is the same as your website name with a prefix of "Portals-". If your site name is *Woodgrove Bank Applications*, then the app name on the Azure portal is *Portals-Woodgrove Bank Applications*. Remember the app registration name for later use.
    1. Sign in to the [Azure portal](https://portal.azure.com/) and navigate to **Key Vaults**.
3. Create a new key vault or use an existing one.

    When creating a new key vault, choose a permission model. Select either [Azure role-based access control](/azure/role-based-access-control/overview) or [Key Vault access policy](/azure/key-vault/general/assign-access-policy-portal). To see the appropriate steps, select the following tab based on your choice of permission model:

# [Azure role-based access control](#tab/azure)

1. Go to your key vault in the [Azure portal](https://portal.azure.com/).
1. Select **Access control (IAM)** from the left menu.
1. Select **+ Add** at the top of the page, then select **Add role assignment**.
1. Under the **Job function roles** tab, search for **Key Vault Secrets User**, select it, then select **Next**.
1. For **Assign access to**, select **User, group, or service principal**.
1. Select **+ Select members** and search for your site's app registration name as described earlier.
1. Select the app for your site, then select **Next**.
1. Select **Review + assign**.

Your site now has permissions to read secrets from this key vault.

# [Key Vault access policy](#tab/keyvault)

1. Select **Access policies** on the left side menu.
1. Select **+ Create** at the top of the page.
1. Under **Secret permissions**, select **Get** > **Next**.
1. Search for your site's app registration name as described earlier.
1. Select the app for the site and then select **Next**.
1. Select **Create**.

Your site now has permissions to read secrets from this key vault.

---

4. Add your key as a secret to the key vault. Learn how to create a secret in Azure Key Vault in [Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/secrets/quick-create-portal).

## FAQ

1. **Can I use environment variables for any site settings?**  
    Yes, any site setting that supports dynamic values can use an environment variable.

1. **What happens if an environment-specific value is not defined?**  
    The default value is used as a fallback.

1. **Can I edit environment variable values directly in production?**  
Yes, but make sure changes are tested and documented to avoid unintended consequences.

## Conclusion

The environment variable for site settings feature simplifies ALM, enhances configurability, and reduces the risk of manual errors. Makers and administrators who adopt this feature ensure their sites stay flexible and align with organizational deployment strategies.

## Related information

- [Configure site settings for websites](configure-site-settings.md)
- [Environment variables overview](/power-apps/maker/data-platform/environmentvariables)
