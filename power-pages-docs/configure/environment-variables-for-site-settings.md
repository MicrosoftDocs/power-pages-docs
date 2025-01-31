---
title: Environment variables for site settings in Power Pages
description: Discover the benefits of using environment variables for site settings in Power Pages for dynamic configuration management.
author: DanaMartens
contributors: null
ms.topic: conceptual
ms.date: 01/30/2025
ms.author: pudupa
ms.reviewer: dmartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:01/30/2025
---

# Environment variables for site settings

Environment variables for site settings provide a flexible and scalable way to manage site configuration values dynamically across environments. This feature allows makers and administrators to define and use environment-specific values for site settings, enabling smoother application lifecycle management (ALM) and deployment processes.

## Solution for enhanced data model

With the enhanced data model, Power Pages introduces a solution to address the gap in defining different site settings values across environments. While the standard data model supports defining different site settings values across environments via deployment profiles, the enhanced data model now allows for dynamic configuration and environment-specific customization using environment variables.

## Key definitions

  1. **Environment variable:** A variable that holds configuration values specific to an environment, which the application or features can reference.
  
  1. **Site settings:** Configurable properties that influence the behavior of a site, such as identity provider site settings, progressive web applications, and advanced settings in the security workspace.
  
  1. **Environment variable reference:** A pointer to an environment variable within a site setting, enabling dynamic value resolution at runtime.

## Use cases

The following are some use cases for environment variables in site settings:

- Streamline ALM by avoiding hard-coded values in site settings.
- Simplify multi-environment deployments with environment-specific configurations.
- Enable dynamic updates to site behavior without redeploying solutions.
  
## How it works

The following text provides a high-level description of how environment variables work with site settings.

  1. Makers define environment variables in the Power Pages Management App (PPMA) or solution designer.
  1. Site settings can reference these environment variables instead of static values.
  1. When the site is accessed, the referenced environment variable’s value is resolved and used dynamically.
  
## Setting Up environment variables for site settings

### Prerequisite

- The user must have a site within an environment where the [enhanced data model ](../admin/enhanced-data-model.md)is enabled.
- The following versions are needed for environment variables to work in Power Pages:
  - Dataverse server version: 9.2.25013.x
  - Power Pages package version: 1.0.2501.x
  - Power Pages runtime version: 9.7.1.x
  
### Steps to follow

1. Open the [Power Pages Management Application](portal-management-app.md), then go to **Site Settings**.
1. Select the specific site setting you wish to configure with an environment variable.
1. Select the source as **Environment Variable**.

    :::image type="content" source="media/environment-variables-for-site-settings/site-setting-source.png" alt-text="Screenshot showing a site setting with the source as environment variable.":::

1. Select the **Environment Variable** lookup and select **New Environment Variable**.
1. If an environment variable definition is already created, select the environment variable option; a drop-down menu appears for selection.

    :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-selection.png" alt-text="Screenshot of the environment variable selection dropdown.":::

1. If an environment variable definition doesn't exist, select **create new environment variable definition**. Then, fill in the required fields, such as Owner, Schema Name, Display Name, and Type.

    :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-creation.png" alt-text="Screenshot of creating a new environment variable definition.":::

1. After you create the environment variable definition, the schema name is listed in the environment variable field's drop-down menu. Choose the schema name from the drop-down menu. Relationship with the site settings to be created via EnvironmentVariableSchemaName.

> [!NOTE]
> - Data type= “Data source” isn't supported.
> - Environment variables with the data type set as "Secret" can't be configured without providing Key Vault details.

## Update environment specific values

1. For each environment (for example, dev, QA, production), go to the [Power Pages Management App](portal-management-app.md) or [design studio](../getting-started/use-design-studio.md).
1. Locate the environment variable created earlier.
1. Update the environment-specific value in the **EnvironmentVariableValue** field.
1. Save the configuration.

    :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-PPMA.png" alt-text="Screenshot of updating the environment variable value in PPMA.":::

1. After setting the environment variable, follow these steps:
    1. Navigate to a solution and incorporate the previously created site, verifying that the relevant environment variables are included.
    1. Proceed to export the solution and then import it into the desired target environment.

During the import process into the target environment, the user is prompted to assign a value to the environment variable. Any modifications made result in the corresponding site settings being updated with this new value in the target environment.

> [!IMPORTANT]
> - Makers are notified if the value of a specific site setting is configured through an environment variable in design studio. If makers choose to edit this value, changing the environment variable impacts all instances referenced across the environment.
> - If a site setting's data type is marked as secret, the field is disabled in the design studio, preventing makers from editing its values. Additionally, reading or writing Key Vault secrets within the design studio settings isn't supported.

## Common flows

### Solution flow

To set up your environment variables and sites across different environments, follow these steps:
  
1. **Set up environment variables in the source environment:**
    1. Navigate to the **Solution** in the source environment.
    1. Add a new environment variable, input the necessary details, and save it.

        :::image type="content" source="media/environment-variables-for-site-settings/environment-variable-solution-import.png" alt-text="Screenshot of the environment variable assignment during solution import.":::

    1. Incorporate the existing site into the solution.
  
1. **Configure site settings:**
    1. Open the **Power Pages Management App** and access **Site Settings**.
    1. Select the specific site setting that needs to be defined for a particular environment.
    1. Use the dropdown menu to select or create an environment variable. Users can view and choose environment variables created through the solutions flow in this dropdown.

        :::image type="content" source="media/environment-variables-for-site-settings/new-environment-variable.png" alt-text="Screenshot of the pipeline configuration for environment variables.":::

> [!NOTE]
> In the site settings, the dropdown menu displays the names of environment variables created via the solutions flow, allowing users to easily select and associate them.
  
- During the import process into the target environment, the user is prompted to assign a value to the environment variable.
- Any modifications made to the environment variable update the corresponding site settings with the new value in the target environment.

### Pipeline

During the deployment of the solution, the user is expected to specify the value of the environment variable for the target environment. If there are any alterations, the corresponding site settings must be refreshed to reflect the updated value in the target environment.
  
:::image type="content" source="media/environment-variables-for-site-settings/pipeline-deployment-setting.png" alt-text="Screenshot of the pipeline deployment settings for environment variables.":::

## Surfaces supporting environment variables for site settings

- **Power Pages Management app:** To create and manage environment variables.
- **Design studio:** To view or edit the site settings with environment variables.
- **Solution designer:** To include environment variables in your ALM process.
- **Pipeline deployments:** To manage and validate environment-specific configurations during deployment.

> [!NOTE]
> - For PWAFeature site-setting, use value - `{"status":"disable"}` for false and `{"status":"enable"}` for true.
> - **Cache Clearing After Updates:** Whenever changes are made to the environment variable value or default value, you must manually clear the cache using one of the following methods:

- **Option 1:** Select **Sync** [design studio](../getting-started/use-design-studio.md).
  
    :::image type="content" source="media/environment-variables-for-site-settings/sync-button.png" alt-text="Screenshot of the Sync button in the studio interface.":::

- **Option 2:** Clear the cache from the portal:
  - **From portal**
    - Sign in to the portal as an administrator and navigate to the website with '/_services/about' appended to the URL. For example: [https://contoso.powerappsportals.com/_services/about](https://contoso.powerappsportals.com/_services/about)).
  
    :::image type="content" source="media/environment-variables-for-site-settings/clear-cache.png" alt-text="Screenshot of the portal details page showing the Clear Cache button.":::

  - On the portal details page, select **Clear Cache**.
  
  - **Option 3:** Restart the portal from the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

## Error handling scenarios

The following are some potential errors you might encounter:

- **Mismatch in environment variable value and expected type:**
  - Example: A site setting like Search/Enabled expects a boolean value (true/false), but the environment variable contains an invalid value (for example, abc) or is missing.
  
- **Unsupported environment variable source type:**
  - Example: The environment variable source type is set to "data storage," which isn't supported by this feature.
  
- **Key Vault access issues:**
  - Example: The environment variable source is Key Vault, but the runtime lacks access permissions, or the secret is missing.

## Best practices

- **Usage recommendation:** Use this feature exclusively for ALM-related settings or secrets. Avoid using it for all site settings, as doing so might lead to performance degradation.
- **Name consistently:** Use consistent naming conventions for environment variables to make them easily identifiable.
- **Document variables:** Maintain a reference document listing all environment variables, their purposes, and default values.
- **Test thoroughly:** Validate changes in a nonproduction environment before applying them to production.
- **Use descriptions:** Use the description field to explain the variable’s intent and usage.

## Configure environment variables as secrets and use them in portals

- Steps to configure any environment variable as secret: [Use environment variables for Azure Key Vault secrets](/power-apps/maker/data-platform/environmentvariables-azure-key-vault-secrets)
  
- Steps to add permissions to access secret from portal:
  - Within the Azure portal, obtain the name of your app in **App registrations** which corresponds to your Power Pages website.
  - The app name is the same as your website name with a prefix of "Portals-". If your site name is *Woodgrove Bank Applications*, then the app name on the Azure portal is *Portals-Woodgrove Bank Applications*. Note this app registration name for use in the following steps.
  - Sign in to the [Azure portal](https://portal.azure.com/) and navigate to **Key Vaults**.
  - Create a new key vault or use an existing one. While creating a new key vault, you have to choose a permission model. You can choose either [Azure role-based access control](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview) or a [Key Vault access policy](https://learn.microsoft.com/en-us/azure/key-vault/general/assign-access-policy-portal). To see the appropriate steps, select the following tab based on your choice of permission model.

### Azure role-based access control

  1. Navigate to your key vault in the [Azure portal](https://portal.azure.com/).
  1. Select **Access control (IAM)** on the left side menu.
  1. Select **+ Add** on the top of the page, and then select **Add role assignment**.
  1. Under the **Job function roles** tab, search for **Key Vault Secrets User**, select it, and then select **Next**.
  1. For **Assign access to**, select **User, group, or service principal**.
  1. Select **+ Select members** and search for your site's app registration name as described earlier.
  1. Select the app for your site and select **Next**.
  1. Select **Review + assign**.

### Key Vault access policy

  1. Select **Access policies** on the left side menu.
  1. Select **+ Create** on the top of the page.
  1. Under **Secret permissions**, select **Get** > **Next**.
  1. Search for your site's app registration name as described earlier.
  1. Select the app for the site and then select **Next**.
  1. Select **Create**.

Your site now has permissions to read secrets from this key vault.

- Add your key as a secret to the key vault. To learn how to create a secret in Azure Key Vault, go to [Set and retrieve a secret from Azure Key Vault using the Azure portal](https://learn.microsoft.com/en-us/azure/key-vault/secrets/quick-create-portal).
- To configure an Azure Key Vault and secret for studio

## FAQ

1. **Can I use environment variables for any site settings?**  
    Yes, any site setting that supports dynamic values can reference an environment variable.

1. **What happens if an environment-specific value is not defined?**  
    The default value is used as a fallback.

1. **Can I edit environment variable values directly in production?**  
    Yes, but ensure changes are tested and documented to avoid unintended impacts.

## Conclusion

The environment variable for site settings feature simplifies ALM, enhances configurability, and reduces the risk of manual errors. Makers and administrators who adopt this feature can ensure their sites remain flexible and aligned with organizational deployment strategies.

## Related information

- [Configure site settings for websites](configure-site-settings.md)
- [Environment variables overview](/power-apps/maker/data-platform/environmentvariables)
