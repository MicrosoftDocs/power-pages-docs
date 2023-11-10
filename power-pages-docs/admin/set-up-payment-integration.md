---
title: Set up Payments integration (preview)
description: Learn how to set up Payments integration with your website. 
author: 
ms.topic: conceptual
ms.custom: 
ms.date: 11/09/2023
ms.subservice:
ms.author: 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---
# Set up Payments integration (preview) 

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Accept payments on your Power Pages websites with no-code configuration within the Studio experience. The configuration starts with **Integrations** &gt; **External Apps** tab in the Set up workspace that allows you to enable the payments provider. With this integration, you can add a Stripe payment component to your multistep form, enabling a streamlined process for accepting payments. 
> [!IMPORTANT]
> - This is a preview feature.
> - This feature currently only works with the **enhanced data model**. More information: [Enhanced data model](../admin/enhanced-data-model.md)
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

Enabling payments into your application requires three steps: 

- [Step 1: Install package](#step-1-install-package)In this step, the site admin installs the package consisting of required tables and other pre-requisites for the environment to enable payments experience. 
- [Step 2: Configure Stripe](#step-2-configure-stripe). In this step, the site admin or maker configures keys specific to a payment provider. 
- [Step 3: Enable payments experience on your form control](#step-3-enable-payments-experience-on-your-form). In this step, the maker includes the form and enables digital payments on the required step for the multistep form. 

## Prerequisites 

- Sign up for an account with Stripe as your payment provider and obtain test mode keys from the Developer dashboard. 
- Create or identify a Microsoft Dataverse table that will be used in a multistep form. This table must have a currency field type that will be used to charge the amount that you wish to collect from the site user. More information: [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md)

-   Configure a [multistep form](../getting-started/multistep-forms.md) using the Dataverse table that has a step to allow users to pay. This step will display the payments control once configured in a later step. 

## Step 1: Install package 

1. In the design studio, choose **Set up** > **Integrations** > **External apps**. 
1. Select the **Install** action for Stripe. 

The installation action may take a few minutes. The action changes to enable once the installation is complete. 

## Step 2: Configure Stripe

Once you've installed the package, you can begin to configure Stripe for your Power Pages site. 

1. In the design studio, choose **Set up** > **Integrations** > **External Apps**. 
1. In the Integrations table, select the **Enable** action for Stripe. 
1. Go to the Stripe developer dashboard.
1. From the **API Keys** tab obtain the **Publishable** and **Secret Keys** that you'll require to enable this integration.   
    > [!NOTE]
    > - For the secret key, we recommend using the **Restricted API Keys** that Stripe provides to limit access and permissions for different areas of your account data in Stripe. 
    > - In public preview this you'll only be able to use **test mode** keys for this integration with Power Pages. To understand various types of keys, refer to Stripe's documentation [API keys | Stripe documentation](https://stripe.com/docs/keys) 
1. Enter Publishable and Secret keys respectively in the Enable Stripe panel. 
1. Choose **Save** and close the panel. 
1. Select the **Sync** button. 

## Step 3: Enable payments experience on your form

To enable payments, complete the following steps: 

1. Create a multistep form step for the Dataverse table used in your multistep form process where you wish to accept payments. 
1. Add table permissions for the Dataverse tables used in the multistep form process (you'll need at least **Create** and **Write** permissions) and assign appropriate [web roles](../security/create-web-roles.md). <br /> More information: [Configure table permissions](../security/table-permissions.md) 
1. Select the **Sync** button. 
1. In the design Studio choose **Pages** and navigate to the webpage where payment experience is intended. Add or edit the multistep form, and create a step entitled *Pay* (or similar). <br />More information: [Add a multistep form](../getting-started/multistep-forms.md) 
1. Proceed to **Step settings**. 
1. Select **App** **Integrations**. 
    - Choose the correct template to associate with the form. 
    - Enable the form toggle for digital payments. And select the currency type field on the table that will be used to charge the amount that you wish to collect from the site user.  
    Configuration of payments methods and additional settings can be directly done in Stripe. They may require acceptance of additional terms as well as configuration.
1. Payment control will be automatically added to the form step that will show a preview of payment methods enabled for accepting payments. 
1. Preview and test your webpage.  

On the Pay step, you should be able to perform a payment using test cards available on Stripe's website.

A successful payment shows the confirmation with the amount paid and a transaction ID returned from the Payment provider.

> [!NOTE]
> Please disable back-button from Step settings if you do not wish to allow users to go to the previous step from the payment step.

If this is the last step of your multi-step form, then a submit button is enabled that will submit the form and complete your process.

## Additional details

- **Payment currencies and amounts** - Minimum and maximum payment amount values can vary by currencies so please review [Supported currencies | Stripe Documentation](https://stripe.com/docs/currencies#minimum-and-maximum-charge-amounts) to ensure your Form and tables are configured correctly to accept payments in that range 

- **PCI DSS Compliance** – \[TBD\] 

- **Payments table –** For storing transactions, there is a new Payments table that is installed with the solution. This table is automatically related to the table that you choose at the time of configuring form steps. You can choose this table to view the details of transactions and status. This is just a snapshot of information that is provided that you may use to create additional experiences for your business users in Power Apps or Power Pages. Dor mor details and troubleshooting payment related issues, you should rely on the payment provider e.g. Stripe's dashboard. 

- **Webhook –** The payments feature also configures a webhook on Stripe that is used to asynchronously update the status of payments that may take additional time for completion.    
    > Note: When a website is in private mode, this webhook may not be able to communicate with the Power Pages and hence you may receive emails from Stripe. This is an intermittent behavior and once you website in switched to public mode, the webhook should be able to communicate successfully. 
