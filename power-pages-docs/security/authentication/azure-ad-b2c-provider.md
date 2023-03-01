---
title: Configure the Azure Active Directory B2C provider
description: Learn how to configure the Azure Active Directory B2C identity provider for Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 2/15/2023
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
---

# Configure the Azure Active Directory B2C provider in Power Pages

Azure Active Directory (Azure AD) powers Microsoft 365 and Dynamics 365 services for employee or internal authentication. Azure Active Directory B2C (Azure AD B2C) is an extension to this authentication model that enables external customers to sign in through local credentials and federation with various common social identity providers.

A site owner can configure Azure AD B2C as an identity provider. Azure AD B2C supports Open ID Connect for federation.

> [!IMPORTANT]
> This article describes how to configure Azure AD B2C as the identity provider automatically. Using these steps, you can create a new Azure AD B2C tenant, register applications, and configure user flows from within Power Pages. If you want to configure the Azure AD B2C provider manually using the generally available interface, go to [Configure the Azure AD B2C provider manually](/power-apps/maker/portals/configure/configure-azure-ad-b2c-provider-manual).

> [!NOTE]
> Changes to the authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache) to be reflected on the website. If you want the changes to be reflected immediately, restart the webpage by using [portal actions](/power-apps/maker/portals/admin/admin-overview).

Follow these steps to configure Azure AD B2C as the OpenID Connect provider.

## Step 1. Select the provider

1. Go to [Power Apps preview](https://make.preview.powerapps.com).

1. On the left pane, select **Apps**.

1. Select your site from the list of available apps.

1. On the command bar, select **Settings**.<br />or<br />Select **More Commands** (**...**), and then select **Settings**.

1. In **Portal settings** on the right side of your workspace, select **Authentication Settings**.

1. For **Azure Active Directory B2C**, select **Configure**.

1. If necessary, update the **Provider name**.

1. Select **Next**.

## Step 2. Select a tenant

In this step, you select an existing Azure AD B2C tenant or create a new one.

### Option 1. Existing Azure AD B2C tenant

Select this option if you already have an existing Azure AD B2C tenant. Other details such as the initial domain name, country/region, and location will be automatically updated.

> [!NOTE]
> Ensure that the account you use to sign in to Power Apps has access to the Azure AD tenant that you want to use for configuring Azure AD B2C authentication. For information about adding different types of user accounts to an Azure AD B2C tenant, go to [Overview of user accounts in Azure Active DIrectory B2C](/azure/active-directory-b2c/user-overview).

Select **Next** to continue.

### Option 2. New Azure AD B2C tenant

Select this option to create a new Azure AD B2C tenant.

> [!NOTE]
> - Ensure that the account you use to sign in to Power Apps has been assigned at least the link [Contributor role](/azure/role-based-access-control/built-in-roles) for the subscription or for a resource group within the subscription.
> - Ensure the Azure subscription has the **Microsoft.AzureActiveDirectory** resource provider registered. Otherwise, creating the new Azure AD B2C tenant will fail with this error:
> <br /> `Error occurred while creating Azure AD B2C tenant. The subscription is not registered to use namespace 'Microsoft.AzureActiveDirectory'. See https://aka.ms/rps-not-found for how to register subscriptions.` More information: [Resolve errors for resource provider registration in Azure](/azure/azure-resource-manager/templates/error-register-resource-provider) 

To create a new Azure AD B2C tenant:

1. Select the Azure AD tenant or directory.

1. Select a subscription for the tenant, or&mdash;if you want to create a new subscription from the Azure website&mdash;select **Add subscription**.

1. Select the resource group for the Azure AD B2C tenant.

1. Enter the initial domain name.

1. Select **Country/Region** for the tenant.

    > [!NOTE]
    > - You can't change the country/region after you create your directory.
    > - It's important that you select the correct country/region, because your choice determines the **Datacenter location** for your directory.
    > - Microsoft doesn't control the location from which you or your users can access or move directory data through apps or services. To see Microsoft's data location commitments for its services, see the [Online Service Terms](https://go.microsoft.com/fwlink?linkid=2009014).

1. Select **Next**.

## Step 3. Register the application

In this step, you register your website as an application with Azure AD. You can create a new application or select an existing application from Azure AD.

> [!NOTE]
> If you're using a custom domain name for the website, enter the custom URL as the **Reply URL**.

### Option 1. Create a new application

1. Enter the application name.

1. Enter a **Reply URL**.

1. Select **Next**.

### Option 2. Select an existing application

1. Select an existing application from the list.

1. Select the **Reply URL**.<br />or<br />Select **Create new** to create a new **Reply URL**.

1. Select **Next**.

## Step 4. Configure user flows

In this step, you configure the **Sign up and sign in** and **Password reset** user flows. The **Sign up and sign in** user flow enables a user to create an account or sign in to their account. The **Password reset** flow enables a user to choose a new password after email verification. More information: [User flow and policy in Azure AD B2C](/azure/active-directory-b2c/user-flow-overview#user-flow-versions) 

- **New policy**: Select this option if you want to create a new policy. You can also change the default name of the policy. This option creates the flow by using the *local account* identity provider with the email address.
- **Existing policy**: Select this option if you want to select an existing policy from the Azure AD B2C tenant.

> [!NOTE]
> - Only the email claim is configured in these user flows. You can enable more claims&mdash;like *first name* and *last name*&mdash;in the flow's **User attributes** and **Application claims** configuration by using the Azure website. 
> - If you enable more claims in addition to *first name* and *last name*, ensure that you [edit the authentication provider](#edit-the-configuration) and add them to the *Registration claims mapping* and *Login claims mapping* in **Additional settings** (this isn't required for *first name* and *last name*). More information: [Configure the Azure Active Directory B2C provider manually](/power-apps/maker/portals/configure/configure-azure-ad-b2c-provider-manual)

Select **Create** to create the identity provider configuration.

## Step 5. Summary

The Azure AD B2C provider configuration is complete. You can view the summary of the configuration, and then select **Close** to exit.

## Edit the configuration

To edit the configuration, select **Edit configuration** for the **Azure Active Directory B2C** identity provider from the providers list. More information: [Edit a provider](/power-apps/maker/portals/configure/use-simplified-authentication-configuration)

## Delete configuration

To delete the configuration, select **Delete** for the **Azure Active Directory B2C** identity provider from the providers list. More information: [Delete a provider](/power-apps/maker/portals/configure/use-simplified-authentication-configuration)

### See also

[Migrate identify providers to Azure AD B2C](/power-apps/maker/portals/configure/migrate-identity-providers)
