---
title: Set up site authentication
description: Learn how to set up user authentication for your Microsoft Power Pages site and add, set up, and remove identity providers.
ms.date: 09/20/2024
ms.topic: how-to
ms.collection: get-started
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Set up site authentication

Deciding how and whether users must authenticate when they visit is a core customization in any Power Pages site. If you enforce authentication, users authenticate through an identity provider.

Power Pages includes several built-in OAuth 2.0 identity providers, so users can authenticate on your site with a Microsoft, LinkedIn, Facebook, Google, or Twitter account. Your website can have only one instance of an OAuth 2.0 identity provider at a time.

You can add SAML 2.0, OpenID Connect, and WS Federation identity providers if you need them.

Power Pages makes it easy for makers and admins to set up user authentication. After you select an identity provider, prompts in the app guide you through the remaining settings.

To set up user authentication for your site:

1. [Select general authentication settings](#select-general-authentication-settings).
1. [Enter the settings for a specific identity provider](#set-up-specific-identity-providers).

> [!NOTE]
> Changes to your site's authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the site. To see the changes immediately, restart the site in the [admin center](../../admin/admin-overview.md).

## Select general authentication settings

Some authentication settings don't depend on the identity provider you choose. They apply to your website's authentication method generally.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).

1. [Create a site](../../getting-started/create-manage.md) or edit an existing site.

1. In the left side panel, select **Security**.

1. Under **Manage**, select **Identity providers**.

1. Select **Authentication settings**.

1. [Select the general authentication settings you need](#general-settings), and then select **Save**.

Next, [enter the specific settings for your identity provider](#set-up-specific-identity-providers).

### General settings

Select the following general authentication settings:

- **External login**: External authentication is provided by the ASP.NET Identity API.  Third-party identity providers handle account credentials and password management.

  - **On**: To sign up for access, users select an external identity to register with the website. After it's registered, an external identity has access to the same features as a local account. [Learn how to manage external accounts](set-authentication-identity.md#manage-external-accounts).
  - **Off**: Users can't register or sign in with an external account.

- **Open registration**: Controls the sign-up, or new user account registration, form for creating a local user.

  - **On**: The sign-up form allows any anonymous user to visit the website and create a user account.
  - **Off**: The sign-up form is disabled and hidden.

- **Require unique email**: Specifies whether users need to provide a unique email address when they sign up.

  - **On**: A sign-up attempt might fail if a user provides an email address that already exists in a contact record.
  - **Off**: A new user can sign up with a duplicated email address.

## Set up specific identity providers

The specific identity provider you plan to use has its own settings that you need to enter.

> [!NOTE]
> If you [use or add a custom domain name](../../admin/add-custom-domain.md) or [change your site's base URL](/power-apps/maker/portals/admin/change-base-url), you must set up your identity provider to use the correct reply URL.

1. In your Power Pages site, select **Security** > **Identity providers**.

    The list shows all the identity providers that are available to use.

    :::image type="content" source="../media/authentication/authentication-id-providers.png" alt-text="Screenshot of the identity providers list in a Power Pages site.":::

1. To set up an identity provider that appears in the list, select **Configure**.

    If the provider you want to use isn't listed, [add it](#add-an-identity-provider).

1. Leave the provider name as it is or change it if you like.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. For the remaining steps, find the provider in the [common identity providers](index.md#common-identity-providers) table, and then select the documentation link.

## Add an identity provider

If the identity provider you want to use doesn't appear in the list, you can add it.

1. In your Power Pages site, select **Security** > **Identity providers**.

1. Select **+ New provider**.

1. In the **Select login provider** list, select **Other**.

1. In the **Protocol** list, select the authentication protocol the provider uses.

1. Enter the provider name as it should appear on your site's sign-in page.

1. Select **Next**.

1. For the remaining steps, select **Learn more** on the configuration page to open the appropriate documentation link:

    - [Configure an OpenID Connect provider](openid-provider.md)
    - [Configure a SAML 2.0 provider](saml2-provider.md)
    - [Configure a WS-Federation provider](ws-federation-provider.md)

1. Select **Confirm**.

## Edit an identity provider

1. In your Power Pages site, select **Security** > **Identity providers**.

1. To the right of the identity provider name, select **More Commands** (**&hellip;**) > **Edit configuration**.

1. Change the settings in accordance with the documentation for the provider:

    - [Set up an OAuth 2.0 provider](oauth2-provider.md)
    - [Set up an OpenID Connect provider](openid-provider.md)
    - [Set up a SAML 2.0 provider](saml2-provider.md)
    - [Set up a WS-Federation provider](ws-federation-provider.md)

1. Select **Save**.

> [!NOTE]
> You can't change the configuration of the **Local sign in** and **Microsoft Entra** providers here. Use the [site settings](../../configure/configure-site-settings.md#site-settings) instead.

## Delete an identity provider

When you delete an identity provider, only its configuration is deleted. The provider is still available for use in the future with a new configuration. For example, if you delete the LinkedIn identity provider, your LinkedIn app and app configuration remain intact. Similarly, if you delete an Azure AD B2C provider, only the configuration is deleted; the Azure tenant configuration for this provider doesn't change.

1. In your Power Pages site, select **Security** > **Identity providers**.

1. To the right of the identity provider name, select **More Commands** (**&hellip;**) > **Delete**.

## Set a default identity provider

You can set any configured identity provider as the default. When an identity provider is set as the default, users who sign in to the website aren't redirected to the sign-in page. Instead, they sign in using the selected provider.

You can only set a configured identity provider as the default.

> [!IMPORTANT]
> If you set an identity provider as the default, users can't choose any other identity provider.

1. In your Power Pages site, select **Security** > **Identity providers**.

1. To the right of the identity provider name, select **More Commands** (**&hellip;**) > **Set as default**.

To remove the default and allow users to select a configured identity provider when they sign in, select **Remove as default**.

## Prevent the "Trouble signing you in" error if you recreate your site

If you delete and recreate your Power Pages site, users might receive the following error when they try to sign in:

`Sorry, but we're having trouble signing you in.`
`AADSTS700016: Application with identifier '<your site URL>' was not found in the directory 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'. This can happen if the application has not been installed by the administrator of the tenant or consented to by any user in the tenant. You may have sent your authentication request to the wrong tenant.`

Make sure you configure the identity provider correctly after recreating your site.
