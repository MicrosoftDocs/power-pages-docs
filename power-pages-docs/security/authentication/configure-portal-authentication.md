---
title: Configure Power Pages site authentication
description: Learn how to configure your Power Pages site authentication using different identity providers.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: intro-internal
ms.date: 3/9/2022
ms.subservice:
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
---


# Configure Power Pages site authentication

Setting up authentication is a core customization in any Power Pages site. Simplified identity provider configuration in Power Pages provides in-app guidance for identity provider setup and abstracts setup complexities. Makers and administrators can easily configure the website for supported identity providers.

## Overview

You can enable, disable, and configure identity providers from [Power Pages](https://make.powerpages.microsoft.com/) by using simplified authentication configuration. After you select an identity provider, you can then follow prompts to easily enter the provider settings.

> [!NOTE]
> Changes to the authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the website. Restart the website by using [the admin center](../../admin/admin-overview.md) if you want the changes to be reflected immediately.

To configure an identity provider for your website:

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. Create a site or edit an existing site created in that environment.
1. Go to Set up in the left navigation menu.
1. Select Identity Providers under Authentication to see a complete list of identity providers.

## Configure general authentication settings

You can configure the following general authentication settings by selecting **Authentication Settings** on the **Identity providers** page.

- **External login**: External authentication is provided by the ASP.NET Identity API. Account credentials and password management are handled by third-party identity providers.
  - When set to **On**, users sign up for access by selecting an external identity to register with the website. After it's registered, an external identity has access to the same features as a local account. See [manage external accounts](set-authentication-identity.md#manage-external-accounts) for related site settings. 
  -  When set to **Off**, external account registration and sign-in are disabled and hidden.

- **Open registration**: Enables or disables the sign-up registration form for creating new local users.
  - When set to **On**, the sign-up form allows any anonymous user to visit the website and create a new user account.
  - When set to **Off**, new user account registration is disabled and hidden.

- **Require unique email**: Specifies whether a unique email address is needed for validating a new user during sign-up.
  -  When set to **On**, a sign-up attempt might fail if a user provides an email address that's already present in a contact record.
  -  When set to **Off**, a contact that uses a duplicate email address can be created.

You can also go to general authentication settings from the details page by selecting **Settings** in the upper-right corner of the **Identity providers** section.

## Configure a default identity provider

You can set any identity provider as the default. When an identity provider is set as the default, users signing in to the website aren't redirected to the sign-in page. Instead, the sign-in experience always defaults to signing in by using the selected provider.

> [!IMPORTANT]
> If you set an identity provider as the default, users won't have the option to choose any other identity provider.

After you set an identity provider as the default, you can select **Remove as default** to remove it. After you remove an identity provider from being the default, users will be redirected to the sign-in page and can choose from the identity providers you've enabled.

> [!NOTE]
> You can only set a configured identity provider as the default. The **Set as default** option becomes available after you configure an identity provider.

## Add, configure, or delete an identity provider

Several identity providers that you can configure are added by default. You can add additional Azure Active Directory (Azure AD) B2C providers, or configure the available OAuth 2.0 providers such as LinkedIn or Microsoft.

> [!NOTE]
> - You can't change the configuration of the **Local sign in** and **Azure Active Directory** providers when using this interface.
> - You can have only one instance of each identity provider type for OAuth 2.0, such as **Facebook**, **LinkedIn**, **Google**, **Twitter**, and **Microsoft**.
> - Updates to identity provider configuration might take a few minutes to be reflected on the website. To apply your changes immediately, you can [restart the website](../../admin/admin-overview.md).
> - If you [add a custom domain name](../../admin/add-custom-domain.md) or [change the base URL](../admin/change-base-url.md), you must re-create the provider configuration by using the correct URL.

### Add or configure a provider

To add an identity provider, select **Add provider** from **Authentication Settings**.

Select from the available list of providers, enter a name, and then select **Next** to configure the provider settings. The provider name you enter here is displayed on the sign-in page for users as the text on the button they use when selecting this provider.

To configure a provider, select **Configure** (or select **More Commands** (**...**), and then select **Configure**).

> [!NOTE]
> You can use **Add provider** or **Configure** to add or configure a provider for the first time. After you configure a provider, you can edit it. You can also select the provider name hyperlink to open the configuration options quickly.

The configuration steps after you select **Next** depend on the type of identity provider you select. More information: [Common identity providers](overview.md#common-identity-providers)

### Edit a provider

After you add and configure a provider, you can see the provider in the **Enabled** state on settings or details pages.

To edit a provider you've configured, select it, select **More Commands** (**...**), and then select **Edit configuration**.

Refer to the provider-specific articles to edit settings for the provider type you selected.

### Delete a provider

To delete an identity provider, select **More Commands** (**...**), and then select **Delete**.

Deleting a provider deletes your provider configuration for the selected provider type, and the provider becomes available again for configuration.

> [!NOTE]
> When you delete a provider, only the configuration for the provider is deleted. For example, if you delete the LinkedIn provider, your LinkedIn app and app configuration remain intact. Similarly, if you delete an Azure AD B2C provider, only the configuration is deleted; the Azure tenant configuration for this provider won't change.

### Error caused by deleting and re-creating a website

If you delete and re-create your Power Pages site, users might receive the following error when signing in. When this issue happens, update the website's identity provider configuration correctly.

`Sorry, but we're having trouble signing you in.`

`AADSTS700016: Application with identifier 'https://contoso.powerappsportals.com/' was not found in the directory 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'. This can happen if the application has not been installed by the administrator of the tenant or consented to by any user in the tenant. You may have sent your authentication request to the wrong tenant.`

### See also

- [Configure the Azure Active Directory B2C provider](azure-ad-b2c-provider.md)
- [Configure an OAuth 2.0 provider for Power Pages](oauth2-provider.md)- 
- [Configure an OpenID Connect provider for Power Pages](openid-provider.md)
- [Configure a SAML 2.0 provider for Power Pages](saml2-provider.md)
- [Configure a WS-Federation provider for Power Pages](ws-federation-provider.md)
