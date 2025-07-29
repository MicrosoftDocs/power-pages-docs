---
title: Set up payments integration
description: Learn how to set up payments integration with your website. 
author: PramithaU
ms.topic: how-to
ms.date: 11/01/2024
ms.subservice:
ms.author: pudupa
ms.reviewer: dmartens
contributors:
    - sandhangitms
    - DanaMartens
ms.custom:
  - sfi-image-nochange
---

# Set up payments integration

Enable your Power Pages site to accept payments by using design studio's Set up workspace. With this no-code integration, you can add a payment component to your multistep form, enabling your website to integrate with a payment provider.

:::image type="content" source="media/set-up-payments-integration/preview-form-step.svg" alt-text="A screenshot of the payments integration inside a Power Pages site.":::

To accept payments on your Power Pages site, you must complete these steps:

[Step 1: Install the package](#step-1-install-the-package). In this step, the site admin installs the package consisting of required tables and other prerequisites for the environment to enable payments experience.

[Step 2: Configure provider](#step-2-configure-the-provider). In this step, the site admin or maker configures keys specific to a payment provider.

[Step 3: Enable the payments experience on your form](#step-3-enable-the-payments-experience-on-your-form). In this step, the maker includes the form and enables digital payments on the required step for the multistep form.

> [!IMPORTANT]
> - This feature only works with the [enhanced data model](../admin/enhanced-data-model.md).
> - This feature requires [Power Pages website build version 9.5.10.x](/power-platform/released-versions/portals/pagesversion9510x) for the payments control to show on the site.

## Prerequisites

- Sign up for an account with Stripe as your payment provider and obtain test mode or the live keys from the payments app installed from Stripe Marketplace.
- Create or identify a Microsoft Dataverse table you want to use in a multistep form. This table must have a currency field type that is used to charge the amount that you wish to collect from the site user. For more information, see [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md).
- Configure a [multistep form](../getting-started/multistep-forms.md) using a Dataverse table with a step to allow users to pay. This step displays the payments control once configured in a later step.

## Step 1: Install the package

1. In the design studio, select **Set up**.
1. Under **Integrations**, select **External apps**.
1. Select the **Install** action for Stripe.
1. Once the package installation is complete, restart the website from [Site Actions](admin-overview.md#site-actions) in the admin center.

The installation action might take a few minutes. The action changes to manage once the installation is complete.

## Step 2: Configure the provider

Once you install the package, you can begin to configure Stripe for your Power Pages site.

### Step 2a: Obtain your Stripe keys

1. In the design studio, choose **Set up**.
1. Under **Integrations**, select **External apps**.
1. In the Integrations table, select the **Manage** action for Stripe.
1. Go to the [Stripe Marketplace](https://go.microsoft.com/fwlink/?linkid=2268776) and install the Microsoft Power Pages Payments app.
1. After the app is installed, obtain the **Publishable** and **Restricted** keys required to enable this integration. These values are needed in later steps.
  
    > [!NOTE]
    > - For the secret key, we recommend using the **restricted API keys** that Stripe provides to limit access and permissions for different areas of your account data in Stripe.
    > - Release 9.6.3.x. added support for live mode keys in addition to test mode keys. To understand various types of keys, refer to [Stripe's documentation on API keys](https://stripe.com/docs/keys).

### Step 2b: Choose your storage type

You can use Dataverse (only supports test mode) or Azure Key Vault (supports both test mode and live mode) to store the Stripe API keys.

:::image type="content" source="media/set-up-payments-integration/stripe-integration.svg" alt-text="Screenshot of the Enable integration panel inside the Set up workspace of Power Pages design studio.":::

If you choose Dataverse, continue to step 2d ([Add your keys to your configuration](#step-2d-add-your-keys-to-your-configuration)).

If you use Azure Key Vault, add the Stripe Restricted key as a secret in a key vault and assign permissions to your site by following step 2c ([Configure Azure Key Vault (optional)](#step-2c-configure-azure-key-vault-optional)).

### Step 2c: Configure Azure Key Vault (optional)

If you choose Azure Key Vault as your storage type, complete the following steps.

1. Within the Azure portal, obtain the name of your app in **App registrations** which corresponds to your Power Pages website.

    The app name is the same as your website name with a prefix of "Portals-". If your site name is *"Woodgrove Bank Applications"*, then the app name on the Azure portal is *"Portals-Woodgrove Bank Applications"*. Note this app registration name for use in the following steps.

    :::image type="content" source="media/set-up-payments-integration/azure-app-registration.svg" alt-text="Screenshot of the app registration in Azure for a Power Pages site.":::

1. Sign in to the [Azure portal](https://portal.azure.com) and navigate to **Key Vaults**.
1. Create a new key vault or use an existing one. While creating a new key vault, you have to choose a permission model. You can choose either [Azure role-based access control](/azure/role-based-access-control/overview) or a [Key Vault access policy](/azure/key-vault/general/assign-access-policy-portal). To see the appropriate steps, select the below tab based on your choice of permission model.

    # [Azure role-based access control](#tab/azurerbac)

    1. Navigate to your key vault in the Azure portal.
    1. Select **Access control (IAM)** on the left side menu.
    1. Select **+ Add** on the top of the page, and then select **Add role assignment**.
    1. Under the **Job function roles** tab, search for **Key Vault Secrets User** role name, select it, and then select **Next**.
    1. For **Assign access to**, select **User, group, or service principal**.
    1. Select **+ Select members** and search for your site's app registration name as described at the beginning of step 2c.
    1. Select the app for your site and select **Next**.
    1. Select **Review + assign**.

    # [Key Vault access policy](#tab/kvaccesspolicy)

    1. Select **Access policies** on the left side menu.
    1. Select **+ Create** on the top of the page.
    1. Under **Secret permissions**, select **Get** > **Next**.
    1. Search for your site's app registration name as described at the beginning of step 2c.
    1. Select the app for the site and then select **Next**.
    1. Select **Create**.

    ---

    Your site now has permissions to read secrets from this key vault.

1. Add your Stripe restricted key as a secret to the key vault. To learn how to create a secret in Azure Key Vault, go to [Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/secrets/quick-create-portal).

### Step 2d: Add your keys to your configuration

1. In the design studio, enter the settings in the **Enable integration** panel.

    If you're using the Dataverse storage option, enter the Publishable and Secret keys.

    If you're using the Key Vault storage option, enter the Publishable key, Azure Key vault name, and Secret name.

1. Select **Save** and close the panel. If you encounter an error while saving, refer to the error message and resolve the key vault setup related issues.
1. Select **Sync**.

## Step 3: Enable the payments experience on your form

To enable payments, complete the following steps:

1. Create a multistep form step for the Dataverse table used in your multistep form process where you want to accept payments.
1. Add [table permissions](../security/table-permissions.md) for the Dataverse tables used in the multistep form process (you need at least **Create** and **Write** permissions) and assign appropriate [web roles](../security/create-web-roles.md).
1. Select **Sync**.
1. In the design studio, select **Pages** and navigate to the webpage where the payment experience is intended.
1. Add or edit the [multistep form](../getting-started/multistep-forms.md), and create a step called *Pay* (or similar).
1. Proceed to **Step settings**.

   :::image type="content" source="media/set-up-payments-integration/form-step-settings.svg" alt-text="Screenshot of the Step settings options inside of the Pages workspace of Power Pages design studio.":::

    - Select **App Integrations**.
    - Toggle **Enable digital payments** to on.
    - In **Choose amount field** select the currency type field on the table used to charge the amount that you want to collect from the site user.  

    > [!NOTE]
    > Configuration of payment methods and more settings can be done directly in Stripe. They might require acceptance of other terms and configuration.

The payment control is automatically added to the form step that shows a preview of payment methods enabled for accepting payments.

### Preview and test your webpage

On the Pay step, you should be able to perform a payment using test cards available on Stripe's website.

A successful payment shows the confirmation with the amount paid and a transaction ID returned from the payment provider.

> [!NOTE]
> You should disable the back-button from the Step settings if you don't want to allow users to go to the previous step from the payment step.

If this step is the last step of your multistep form, a submit button is enabled that submits the form and completes your process.

## Control payments feature in a tenant

An administrator can disable payments in a tenant by setting the disablePaymentIntegrationForPages tenant level setting through PowerShell.

To run PowerShell cmdlets, you must first [install the required modules](/power-platform/admin/powerapps-powershell#module-installation).

### Disable payments

After installing the modules, run the following command in a PowerShell window as an administrator:

```powershell
$requestBody = @{
     powerPlatform = @{
         powerPages = @{
             disablePaymentIntegrationForPages = "All"
         }
     }
 }
 Set-TenantSettings -RequestBody $requestBody
```

Administrators are the users having one of the following Azure roles:

- [Dynamics 365 administrator](admin-roles.md#dynamics-365-administrator)
- [Power Platform administrator](admin-roles.md#power-platform-administrator)

When the payments feature is disabled in a tenant:

- Makers have the following experience in the **External apps** area.

    :::image type="content" source="media/set-up-payments-integration/stripe-integration-blocked.svg" alt-text="Screenshot of the Enable integration panel with Stripe payments integration shown as blocked.":::

- Makers have the following experience in the **App integrations** tab of a multi-step form configuration.

    :::image type="content" source="media/set-up-payments-integration/form-step-settings-blocked.svg" alt-text="Screenshot of the App integrations tab of a multi-step form.":::

Each experience includes the following message:

*"This application has been disabled by your organization. Contact your administrator to enable."*

> [!NOTE]
> Once this tenant setting is set to All, it prevents the setup of payments capability going forward for additional sites. It does not impact any configuration and payment setup on forms that may have already been completed by makers in their environments.

### Enable payments

To enable the payments feature in a tenant, run the following command in a PowerShell window as an administrator:

```powershell
$requestBody = @{
     powerPlatform = @{
         powerPages = @{
             disablePaymentIntegrationForPages = "None"
         }
     }
 }
 Set-TenantSettings -RequestBody $requestBody
```

## Considerations

- **Payment currencies and amounts**. Minimum and maximum payment amount values can vary by currencies. Review the [Stripe documentation on supported currencies](https://stripe.com/docs/currencies#minimum-and-maximum-charge-amounts) to ensure your form and tables are configured correctly to accept payments in that range.

- **Payment Card Industry Data Security Standard (PCI DSS) Compliance**. This feature uses the [Stripe Web Elements](https://stripe.com/docs/payments/elements) payment integration approach and card data isn't stored in Power Pages or Dataverse. PCI compliance is a shared responsibility and applies to business as well. See Stripe's documentation on [validating your PCI Compliance](https://stripe.com/docs/security/guide#validating-pci-compliance).

- **Payments table**. For storing transactions, there's a new payments table installed with the solution. The table is automatically related to the table that you choose when you configure the form steps. You can use the table to view the details of transactions and status. This table is just a snapshot of information that is provided, which you can use to create other experiences for your business users in Power Apps or Power Pages. For more details and troubleshooting payment-related issues, you should rely on the payment provider, such as Stripe's dashboard.

- **Webhook**. The payments feature also configures a webhook on Stripe that is used to asynchronously update the status of payments that might take extra time for completion.

    > [!NOTE]
    > When a website is in private mode, this webhook may not be able to communicate with the Power Pages and hence you may receive emails from Stripe. This is intermittent behavior and once your website is switched to public mode, the webhook should be able to communicate successfully.
