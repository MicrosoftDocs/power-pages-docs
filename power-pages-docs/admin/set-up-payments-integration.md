---
title: Set up Payments integration (preview)
description: Learn how to set up Payments integration with your website. 
author: sandhangitmsft
ms.topic: conceptual
ms.custom: 
ms.date: 11/09/2023
ms.subservice:
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - sandhangitmsft
    - ProfessorKendrick
---
# Set up Payments integration (preview) 

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Accept payments on your Power Pages websites from design studio's Set up workspace. With this integration, you can add a payment component to your multistep form, enabling your website to accept payments. 

:::image type="content" source="Media/set-up-payments-integration/preview-form-step.svg" alt-text="A screenshot of the payments integration inside a Power Pages site.":::

> [!IMPORTANT]
> - This is a preview feature.
> - This feature currently only works with the [enhanced data model](../admin/enhanced-data-model.md).
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

To accept payments on your Power Pages site, you must complete these steps: 

- [Step 1: Install the package](#step-1-install-the-package). In this step, the site admin installs the package consisting of required tables and other prerequisites for the environment to enable payments experience. 
- [Step 2: Configure Provider](#step-2-configure-provider). In this step, the site admin or maker configures keys specific to a payment provider. 
- [Step 3: Enable the Payments experience on your form](#step-3-enable-the-payments-experience-on-your-form). In this step, the maker includes the form and enables digital payments on the required step for the multistep form. 

## Prerequisites 

- Sign up for an account with Stripe as your payment provider and obtain test mode keys from the Developer dashboard. 
- Create or identify a Microsoft Dataverse table to use in a multistep form. This table must have a currency field type that is used to charge the amount that you wish to collect from the site user. More information: [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md)
-   Configure a [multistep form](../getting-started/multistep-forms.md) using a Dataverse table with a step to allow users to pay. This step displays the payments control once configured in a later step. 

## Step 1: Install the package 

1. In the design studio, choose **Set up**.
1. Select **Integrations**, then **External apps**. 
1. Choose the **Install** action for Stripe. 
1. Once the package installation is complete, restart the website from [Site Actions](admin-overview.md#site-actions) in the admin center.
The installation action might take a few minutes. The action changes to enable once the installation is complete. 

## Step 2: Configure provider

Once you install the package, you can begin to configure Stripe for your Power Pages site. 

1. In the design studio, choose **Set up**.
1. Select **Integrations**, then **External Apps**. 
1. In the Integrations table, select the **Enable** action for Stripe. 
1. Go to the Stripe developer dashboard.
    From the API Keys tab, obtain the **Publishable** and **Secret Keys** required to enable this integration. 
  
    > [!NOTE]
    > - For the secret key, we recommend using the **restricted API keys** that Stripe provides to limit access and permissions for different areas of your account data in Stripe. 
    > - In public preview you'll only be able to use **test mode** keys for this integration with Power Pages. To understand various types of keys, refer to [Stripe's documentation on API keys](https://stripe.com/docs/keys) 
1. In the design studio, enter the Publishable and Secret keys respectively in the **Enable integration panel**. 
        :::image type="content" source="Media/set-up-payments-integration/stripe-integration.svg" alt-text="A screenshot of the Enable integration panel inside the Set up workspace of Power Pages design studio.":::
1. Choose **Save** and close the panel. 
1. Select the **Sync** button. 

## Step 3: Enable the Payments experience on your form

To enable payments, complete the following steps: 

1. Create a multistep form step for the Dataverse table used in your multistep form process where you wish to accept payments. 
1. Add [table permissions](../security/table-permissions.md)  for the Dataverse tables used in the multistep form process (you need at least **Create** and **Write** permissions) and assign appropriate [web roles](../security/create-web-roles.md). 
1. Select the **Sync** button. 
1. In the design studio, choose **Pages** and navigate to the webpage where payment experience is intended. 
1. Add or edit the [multistep form](../getting-started/multistep-forms.md) , and create a step called *Pay* (or similar).
1. Proceed to **Step settings**. 
    :::image type="content" source="Media/set-up-payments-integration/form-step-settings.svg" alt-text="The Step settings options inside of the Pages workspace of Power Pages design studio.":::

    - Select **Integrations**. 
    - Switch the **Enable digital payments** toggle to the on position. 
    - Select the currency type field on the table used to charge the amount that you wish to collect from the site user.  
    
    > [!NOTE]
    > Configuration of payments methods and more settings can be directly done in Stripe. They might require acceptance of other terms and configuration.

The payment control is automatically added to the form step that shows a preview of payment methods enabled for accepting payments. 

### Preview and test your webpage 

On the Pay step, you should be able to perform a payment using test cards available on Stripe's website.

A successful payment shows the confirmation with the amount paid and a transaction ID returned from the Payment provider.

> [!NOTE]
> Please disable back-button from Step settings if you do not wish to allow users to go to the previous step from the payment step.

If this step is the last step of your multi-step form, a submit button is enabled that submits the form and completes your process.

## More details

- **Payment currencies and amounts** - Minimum and maximum payment amount values can vary by currencies. Review the [Stripe documentation on supported currencies](https://stripe.com/docs/currencies#minimum-and-maximum-charge-amounts) to ensure your form and tables are configured correctly to accept payments in that range 

- **PCI DSS Compliance** – This feature uses [Stripe Web Elements](https://stripe.com/docs/payments/elements) payment integration approach and card data is not stored in Power Pages or Dataverse. PCI compliance is a shared responsibility and applies to business as well.  Please see Stripe's documentation on [validating your PCI Compliance](https://stripe.com/docs/security/guide#validating-pci-compliance).

- **Payments table –** For storing transactions, there's a new Payments table installed with the solution. The table is automatically related to the table that you choose when you configure the form steps. You can use the table to view the details of transactions and status. This table is just a snapshot of information that is provided which you can use to create other experiences for your business users in Power Apps or Power Pages. For more details and troubleshooting payment related issues, you should rely on payment provider, such as Stripe's dashboard. 

- **Webhook –** The payments feature also configures a webhook on Stripe that is used to asynchronously update the status of payments that might take extra time for completion.    
    > [!NOTE]
    > When a website is in private mode, this webhook may not be able to communicate with the Power Pages and hence you may receive emails from Stripe. This is intermittent behavior and once your website is switched to public mode, the webhook should be able to communicate successfully. 
