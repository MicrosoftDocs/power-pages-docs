---
title: Configure a SAML 2.0 provider for Power Pages with Azure AD
description: Learn how to configure SAML 2.0 for Power Pages with Azure Active Directory.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 3/7/2023
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
---

# Configure a SAML 2.0 provider for Power Pages with Azure AD

In this article, you'll learn about configuring a SAML 2.0 provider for portals with Azure Active Directory (Azure AD).

> [!NOTE]
> - Portals can be configured with identity providers that conform to the Security Assertion Markup Language (SAML) 2.0 standard. In this article, you'll learn about using Azure AD as an example of identity providers that use SAML 2.0.
> Changes to the authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the portal. Restart the portal by using [portal actions](../admin/admin-overview.md) if you want the changes to be reflected immediately.

**To configure Azure AD as the SAML 2.0 provider**

1. Select [Add provider](/power-apps/maker/portals/configure/use-simplified-authentication-configuration#add-configure-or-delete-an-identity-provider) for your portal.

1. For **Login provider**, select **Other**.

1. For **Protocol**, select **SAML 2.0**.

1. Enter a provider name.

1. Select **Next**.

1. In this step, you create the application and configure the settings with your identity provider.

    > [!NOTE]
    > - The Reply URL is used by the app to redirect users to the portal after the authentication succeeds. If your portal uses a custom domain name, you might have a different URL than the one provided here.
    > - More details about creating the app registration on the Azure portal are available in [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).

    1. Sign in to the [Azure portal](https://portal.azure.com).

    1. Search for and select **Azure Active Directory**.

    1. Under **Manage**, select **App registrations**.

    1. Select **New registration**.

    1. Enter a name.

    1. If necessary, select a different **Supported account type**. More information: [Supported account types](/azure/active-directory/develop/quickstart-register-app)

    1. Under **Redirect URI**, select **Web** (if it isn't already selected).

    1. Enter the **Reply URL** for your portal in the **Redirect URI** text box. <br /> Example: `https://contoso-portal.powerappsportals.com/signin-saml_1`

        > [!NOTE]
        > If you're using the default portal URL, copy and paste the **Reply URL** as shown in the **Create and configure SAML 2.0 provider settings** section on the **Configure identity provider** screen (step 6 above). If you're using a custom domain name for the portal, enter the custom URL. Be sure to use this value when you configure the **Assertion consumer service URL** in your portal settings while configuring the SAML 2.0 provider. <br /> For example, if you enter the **Redirect URI** in Azure portal as `https://contoso-portal.powerappsportals.com/signin-saml_1`, you must use it as-is for the SAML 2.0 configuration in portals.

    1. Select **Register**.

    1. Select **Expose an API**.

    1. For **Application ID URI**, select **Set**.

    1. Enter the portal URL as the **App ID URI**.

        > [!NOTE]
        > The portal URL might be different if you're using a custom domain name.

    1. Select **Save**.

    1. Keep the Azure portal open, and switch to the SAML 2.0 configuration for Power Apps portals for the next steps.

1. In this step, enter the site settings for the portal configuration.

    > [!TIP]
    > If you closed the browser window after configuring the app registration in the earlier step, sign in to the Azure portal again and go to the app that you registered.

    1. **Metadata address**: To configure the metadata address, do the following:

        1. Select **Overview** in the Azure portal.

        1. Select **Endpoints**.

        1. Copy the URL for **Federation metadata document**.

        1. Paste the copied document URL as the **Metadata address** for portals.

    1. **Authentication type**: To configure the authentication type, do the following::

        1. Copy and paste the **Metadata address** configured earlier in a new browser window.

        1. Copy the value of the `entityID` tag from the URL document.

        1. Paste the copied value of `entityID` as the **Authentication type**. <br /> Example: `https://sts.windows.net/7e6ea6c7-a751-4b0d-bbb0-8cf17fe85dbb/`

    1. **Service provider realm**: Enter the portal URL as the service provider realm. <br /> Example: `https://contoso-portal.powerappsportals.com`
    
        > [!NOTE]
        > The portal URL might be different if you're using a custom domain name.
        
    1. **Assertion consumer service URL**: Enter the **Reply URL** for your portal in the **Assertion consumer service URL** text box. <br /> Example: `https://contoso-portal.powerappsportals.com/signin-saml_1`

        > [!NOTE]
        > If you're using the default portal URL, you can copy and paste the **Reply URL** as shown in the **Create and configure SAML 2.0 provider settings** step. If you're using a custom domain name, enter the URL manually. Be sure that the value you enter here is exactly the same as the value you entered as the **Redirect URI** in the Azure portal earlier.

1. Select **Confirm**.

1. Select **Close**.

### See also

[Configure a SAML 2.0 provider for portals with AD FS](saml2-settings.md)
[FAQs for using SAML 2.0 in portals](saml2-faqs.md)
[Configure a SAML 2.0 provider for Power Pages](saml2-provider.md)
