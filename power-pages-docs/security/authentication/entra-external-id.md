---
title: Set up Microsoft Entra External ID with Power Pages (preview)
description: Learn how to set up Microsoft Entra External ID authentication for sites created with Power Pages.
ms.date: 11/14/2024
ms.topic: how-to
author: ankitavish
ms.author: avishwakarma
ms.reviewer: dmartens
contributors:
    - DanaMartens
ms.custom: bap-template
---

# Set up Microsoft Entra External ID with Power Pages (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Microsoft Entra External ID is a Customer Identity Access Management (CIAM) solution that personalizes and secures customers' and partners' access to websites and applications. It shares foundational technology with Azure B2C but operates as a distinct service, using the Microsoft Entra Admin Center instead of the Azure portal. Integrating External ID with Power Pages simplifies customer sign-ins and reduces development efforts. Learn more about Microsoft Entra External ID at [Introduction to Microsoft Entra External ID](/entra/external-id/external-identities-overview).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

> [!NOTE]
> Authentication setting changes may take a few minutes to reflect on your site. For immediate effect, restart the site in the [admin center](../../admin/admin-overview.md). Learn more about clearing the cache at [How server-side caching works in Power Pages](../../admin/clear-server-side-cache.md).

## Set up Microsoft Entra External ID in Power Pages

Follow these steps to set up Microsoft Entra External ID in Power Pages:

### Step 1: Add Microsoft Entra External ID as an identity provider

To configure Microsoft Entra as an identity provider:

1. Sign in to [Power Pages Studio](https://make.powerpages.microsoft.com).
1. Locate the site where you want to enable Microsoft Entra External ID.
1. Select **Edit**.
1. Select **Security > Identity providers**.
1. Locate **Microsoft Entra External ID (preview)** as the login provider and select **Configure**.
1. Enter a name for the provider, such as *Microsoft Entra External ID*. This name appears on the button users see when they select their identity provider on the sign-in page.
1. Select **Next**.

    > [!NOTE]
    > Keep your Power Pages browser tab open. You'll return to it soon.

### Step 2: Set up Microsoft Entra External ID in the admin center

To set up Microsoft Entra External ID in the admin center, follow these steps.

#### Create an external tenant

If you don't have an external tenant, create one in the [Microsoft Entra Admin Center](https://entra.microsoft.com/#home). Start with a [30-day free trial](/entra/external-id/customers/quickstart-trial-setup) or use an [Azure subscription](/entra/external-id/customers/quickstart-tenant-setup).

#### Register your application

1. Copy the **Reply URL** from your Power Pages site.
1. Sign in to the [Microsoft Entra Admin Center](https://entra.microsoft.com/#home) and create an app registration using this URL as the redirect URI.
1. Under **Applications**, select **App registrations**, then select **New registration**.
1. Name your application (for example, *power-pages-app*).
1. Under **Redirect URI**, select **Web** as the platform.
1. Enter the reply URL of your site.

    > [!NOTE]
    > If you're using your site's default URL, paste the reply URL you copied. If you're using a custom domain name, enter your custom URL. Use the same custom URL for the redirect URL in the settings for the identity provider on your site.

1. Select **Register**.
1. Under **Manage**, select the power-pages-app **Authentication** tab.
1. Select **Access tokens** and **ID tokens**, and then select **Save**.
1. On the **API permissions** tab, select **Grant admin consent**.

#### Create a user flow

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com/#home), select **External Identities** > **User flows**.
1. Select **New user flow**. If **New user flow** is disabled, learn how to enable it at [Enable self-service sign-up for your tenant](/entra/external-id/self-service-sign-up-user-flow#enable-self-service-sign-up-for-your-tenant).
1. Name the user flow (for example, *Power-pages-user-flow*) and select **Email with password** or **Email one-time passcode**.
1. Select **Create**.

#### Add your application to the user flow

1. On the user flow you created (power-pages-user-flow), select **Applications** > **Add application**.
1. Select your application (for example, power-pages-app) and choose **Select**.  

### Step 3: Configure site settings in Power Pages

1. Go to the Power Pages identity provider configuration page and enter the following values:

    | Field              | Value                                                                                                                      |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | Client ID      | Copy the **Application (client) ID** from **App registrations** > `<your app registration>` > **Overview** in the Microsoft Entra admin center. |
    | Authority     | Copy the **Authority URL** from **App registrations** > `<your app registration>` > **Endpoints** in the Microsoft Entra admin center.           |
    | Redirect URL   | If your site uses a custom domain name, enter the custom URL; otherwise, leave the default value. Make sure the value is exactly the same as the redirect URI of the application you created. |
    | Metadata address | Copy the **OpenID Connect metadata document** URL from **App registrations** > `<your app registration>` > **Endpoints** in the Microsoft Entra admin center. |

    Optionally, change the [additional settings](#additional-settings-in-power-pages) as needed.

1. Select **Confirm** when you're done.

## Additional settings in Power Pages

The following optional settings offer more control over authentication:

| Setting                  | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| External logout          | This setting controls external account sign-out. Turn it on to redirect users to the external sign-out experience when they sign out of your website. Turn it off to sign users out of your website only.                         |
| Claims mapping           | In user authentication, a *claim* is information that describes a user's identity, like an email address or date of birth. When you sign in to an application or a website, it creates a *token*. A token contains information about your identity, including any claims that are associated with it. Tokens are used to authenticate your identity when you access other parts of the application or site or other applications and sites that are connected to the same identity provider. Claims mapping is a way to change the information included in a token. It can be used to customize the information that's available to the application or site and to control access to features or data. Registration claims mapping modifies the claims that are emitted when you register for an application or a site. Login claims mapping modifies the claims that are emitted when you sign in to an application or a site. Learn more about claims mapping policies at [Claims customization using a policy](/entra/identity-platform/reference-claims-customization).       |
| Nonce lifetime           | Enter the lifetime of the nonce value, in minutes. The default value is 10 minutes.                        |
| Use token lifetime       | This setting controls whether the authentication session lifetime, such as cookies, should match that of the authentication token.            |
| Contact mapping with email | This setting determines whether contacts are mapped to a corresponding email address when they sign in. This setting isn't applicable for multitenant endpoints and the [Microsoft identity provider](oauth2-microsoft.md). Use [invitations](../invite-contacts.md) to allow users to authenticate to your website. </br></br>**On**: Associates a unique contact record with a matching email address and automatically assigns the external identity provider to the contact after the user successfully signs in. </br></br>**Off:** Contacts aren't mapped to an email address when they sign in. |
