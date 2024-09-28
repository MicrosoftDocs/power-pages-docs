---
title: Set up an OpenID Connect provider with Azure AD B2C 
description: Learn how to set up an OpenID Connect identity provider with Azure Active Directory B2C for use with sites you create with Microsoft Power Pages.
ms.date: 09/10/2024
ms.topic: how-to
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Set up an OpenID Connect provider with Azure AD B2C

Azure Active Directory (Azure AD) B2C is one of the OpenID Connect identity providers you can use to [authenticate visitors](configure-site.md) to your Power Pages site. You can use any identity provider that conforms to the [Open ID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html).

This article describes the following steps:

- [Set up Azure AD B2C in Power Pages](#set-up-azure-ad-b2c-in-power-pages)
- [Create an app registration](#create-an-app-registration)
- [Create user flows](#create-user-flows)
- [Enter site and password settings in Power Pages](#enter-site-settings-and-password-reset-settings-in-power-pages)

> [!NOTE]
> Changes to your site's authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the site. To see the changes immediately, restart the site in the [admin center](../../admin/admin-overview.md).

## Set up Azure AD B2C in Power Pages

Set Azure AD B2C as an identity provider for your site.

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. To the right of **Azure Active Directory B2C**, select **More Commands** (**&hellip;**) > **Configure** or select the provider name.

1. Leave the provider name as it is or change it if you like.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

1. Select **Open Azure**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an app registration

Create a tenant for Azure AD B2C and [register an application](/azure/active-directory-b2c/tutorial-register-applications?tabs=applications#register-a-web-application) with your site's reply URL as the redirect URI.

1. [Create an Azure AD B2C tenant](/azure/active-directory-b2c/tutorial-create-tenant).

1. Search for and select **Azure AD B2C**.

1. Under **Manage**, select **App registrations**.

1. Select **New registration**.

1. Enter a name.

1. Select one of the [**Supported account types**](/azure/active-directory/develop/quickstart-register-app) that best reflects your organization requirements.

1. Under **Redirect URI**, select **Web** as the platform, and then enter the reply URL of your site.

    - If you're using your site's default URL, paste the reply URL [you copied](#set-up-azure-ad-b2c-in-power-pages).
    - If you're using a custom domain name, enter the custom URL. Be sure to use the same custom URL for the redirect URL in the settings for the identity provider on your site.

1. Select **Register**.

1. Copy the **Application (client) ID**.

1. In the left side panel, under **Manage**, select **Authentication**.

1. Under **Implicit grant**, select **Access tokens (used for implicit flows)**.

1. Select **Save**.

1. [Configure token compatibility](/azure/active-directory-b2c/configure-tokens#configure-token-compatibility) using an **Issuer (iss) claim** URL that includes **tfp**. [Learn more about token compatibility](/azure/active-directory-b2c/tokens-overview#compatibility).

### Create user flows

1. [Create a sign-up and sign-in user flow](/azure/active-directory-b2c/tutorial-create-user-flows#create-a-sign-up-and-sign-in-user-flow).

1. (Optional) [Create a password reset user flow](/azure/active-directory-b2c/tutorial-create-user-flows#create-a-password-reset-user-flow).

### Get the issuer URL from the user flows

1. Open the sign-up and sign-in user flow [you created](#create-user-flows).

1. Go to the Azure AD B2C tenant in the [Azure portal](https://portal.azure.com).

1. Select **Run user flow**.

1. Open the OpenID Connect configuration URL in a new browser tab.

    The URL refers to the OpenID Connect identity provider configuration document, also known as the *OpenID well-known configuration endpoint*.

1. Copy the **Issuer** URL in the address bar. Don't include the quotation marks. Do make sure that the **Issuer (iss) claim** URL includes **tfp**.

1. Open the password reset user flow, if you created one, and repeat steps 2&ndash;5.

## Enter site settings and password reset settings in Power Pages

1. Return to the Power Pages **Configure identity provider** page you left earlier.

1. Under **Configure site settings**, enter the following values:

    - **Authority**: Paste the issuer URL [you copied](#get-the-issuer-url-from-the-user-flows).​

    - **Client ID​**: Paste the **Application (client) ID** of the Azure AD B2C application [you created](#create-an-app-registration).

    - **Redirect URI**: If your site uses a custom domain name, enter the custom URL; otherwise, leave the default value, which should be your site's reply URL.

1. Under **Password reset settings**, enter the following values:

    - **Default policy ID**: Enter the name of the sign-up and sign-in user flow [you created](#create-user-flows). The name is prefixed with *B2C_1*.

    - **Password reset policy ID**: If [you created](#create-user-flows) a password reset user flow, enter its name. The name is prefixed with *B2C_1*.

    - **Valid issuers**: Enter a comma-delimited list of the [issuer URLs](#get-the-issuer-url-from-the-user-flows) for the sign-up, sign-in, and password reset user flows [you created](#create-user-flows).

1. (Optional) Expand [**Additional settings**](#additional-settings-in-power-pages) and change the settings as needed.

1. Select **Confirm**.

### Additional settings in Power Pages

The additional settings give you finer control over how users authenticate with the Azure AD B2C identity provider. You don't need to set any of these values. They're entirely optional.

- **Registration claims mapping​** and **Login claims mapping**: In user authentication, a *claim* is information that describes a user's identity, like an email address or date of birth. When you sign in to an application or a website, it creates a *token*. A token contains information about your identity, including any claims that are associated with it. Tokens are used to authenticate your identity when you access other parts of the application or site or other applications and sites that are connected to the same identity provider. *Claims mapping* is a way to change the information that's included in a token. It can be used to customize the information that's available to the application or site and to control access to features or data. *Registration claims mapping* modifies the claims that are emitted when you register for an application or a site. *Login claims mapping* modifies the claims that are emitted when you sign in to an application or a site. [Learn more about claims mapping policies](/azure/active-directory/develop/reference-claims-mapping-policy-type).

  - You don't need to enter values for these settings if you use the *email*, *first name*, or *last name* attributes. For other attributes, enter a list of logical name/value pairs. Enter them in the format `field_logical_name=jwt_attribute_name`, where `field_logical_name` is the logical name of the field in Power Pages and `jwt_attribute_name` is the attribute with the value returned from the identity provider. These pairs are used to map claim values (created during sign-up or sign-in and returned from Azure AD B2C) to attributes in the contact record.

    For example, you use **Job Title (jobTitle)** and **Postal Code (postalCode)** as **User Attributes** in your [user flow](#create-user-flows). You want to update the corresponding `Contact` table fields **Job Title (jobtitle)** and **Address 1: ZIP / Postal Code (address1_postalcode)**. In this case, enter the claims mapping as `jobtitle=jobTitle,address1_postalcode=postalCode`.

- **External logout**: This setting controls whether your site uses federated sign-out. With federated sign-out, when users sign out of an application or site, they're also signed out of all applications and sites that use the same identity provider. For example, if you sign in to a site using your Microsoft account, and then sign out of your Microsoft account, federated sign-out makes sure that you're signed out of the site, too.

  - **On**: Redirects users to the federated sign-out experience when they sign out of your website.
  - **Off**: Signs users out of your website only.

- **Contact mapping with email**: This setting determines whether contacts are mapped to a corresponding email address when they sign in.

  - **On**: Associates a unique contact record with a matching email address and automatically assigns the external identity provider to the contact after the user successfully signs in.
  - **Off**: Contact record is not matched with an identity provider. This is the default option for this setting.

- **Registration enabled**: This setting controls whether users can register on your site.

  - **On**: Displays a sign-up page where users can create an account on your site.
  - **Off**: Disables and hides the external account registration page.

### See also

[Set up site authentication](configure-site.md)  
[Migrate identity providers to Azure AD B2C](/power-apps/maker/portals/configure/migrate-identity-providers)