---
title: Provide access to external audiences
description: Learn how to allow external audiences to use a local account to access sites you create with Microsoft Power Pages.
ms.date: 04/28/2026
ms.topic: how-to
author: dmartens
ms.author: dmartens
contributors:
ms.custom:
  - bap-template
  - sfi-image-nochange
---
# Provide access to external audiences

 Power Pages site user information is stored as contact records in Dataverse. Before users can authenticate to your site with a local account, a record must exist for them in your site's Contacts table. You can create the contact yourself, or the user can create a record by submitting a sign-up form if you [turn on user registration](authentication/set-authentication-identity.md#enable-or-disable-user-registration) on your site.

Contact records that you create don't have a username and password. You must [enter a username](#add-a-username-to-a-contact-record), and then use the [change password](#change-a-contacts-password) workflow to set an initial password. Use the [Portal Management app](../configure/portal-management-app.md) to create and edit your site's contact records.

You can also send a user an [invitation to register locally](invite-contacts.md). [Learn more about local authentication, registration, and other settings](authentication/set-authentication-identity.md).

> [!IMPORTANT]
> We recommend you use the [Microsoft Entra External ID identity provider](authentication/entra-external-id.md) for authentication and [deprecate the local identity provider](authentication/migrate-identity-providers.md).

## Choose the right authentication method

Before setting up external access, choose the authentication method that best fits your scenario:

| Method | Best for | Details |
| --- | --- | --- |
| **Microsoft Entra External ID** (recommended) | New sites, enterprise scenarios, B2C | Modern, secure, supports multi-factor authentication. See [Set up Microsoft Entra External ID](authentication/entra-external-id.md). |
| **SAML 2.0 / OpenID Connect** | Federated identity scenarios | Use when integrating with existing identity providers. See [Configure site authentication](authentication/configure-site.md). |
| **Local authentication** | Simple scenarios, legacy sites | Users sign in with username and password stored in Dataverse. Less secure than external identity providers. |

## Add a username to a contact record

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, scroll down to the **Security** section and select **Contacts**.

1. Create or select a contact.

1. Select the **Portal Contact (Enhanced)** form.

1. Select the **Web Authentication** tab.

1. Enter a **Username**.

    :::image type="content" source="media/user-management/config-contact-record.png" alt-text="Screenshot of a contact record in the Portal Management app, with the username box on the Web Authentication tab highlighted.":::

1. Select **Save**.

1. To set an initial password, [change the contact's password](#change-a-contacts-password).

## Change a contact's password

To change a contact's password, you need to have the System Administrator [security role](/power-platform/admin/database-security).

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, scroll down to the **Security** section and select **Contacts**.

1. Select a contact.

1. In the command bar, select **Change Password**. It may be hidden in the **More commands** (**&vellip;**) menu.

1. Enter a new password, and then select **Next**.

    To remove the password entirely, don't enter a new password. Leave the **New password** box empty and select **Next**. When you're asked whether you want to remove the password for the contact, select **Yes**, and then select **Next** again.

1. Select **Done**.

### Deprecation of business process flow

Earlier versions of the change password process used a task flow that's been deprecated. In Dataverse security roles, the **Change Password for Portals Contact** privilege under the **Business Process Flows** tab no longer requires any options to be selected.

## Troubleshoot external access issues

If users experience errors when trying to sign in or access your Power Pages site, use the following table to identify and resolve common issues.

| Symptom | Possible cause | Solution |
| --- | --- | --- |
| **HTTP 403 – Access Denied** | The user is authenticated but doesn't have the correct web role or table permissions to view the page. | Assign the user's contact record to the correct [web role](create-web-roles.md) and verify [table permissions](table-permissions.md) allow access to the requested page. |
| **Sign-in fails with "ExternalAuthenticationFailed"** | The external identity provider configuration is incorrect or the user's identity couldn't be mapped to a contact. | Review your identity provider settings in [Authentication settings](authentication/configure-site.md). Ensure the user has a contact record with a matching email or identity claim. |
| **HTTP 500 on external login callback** | The authentication response from the identity provider couldn't be processed by Power Pages. | Verify the redirect URI in the identity provider configuration matches your site URL. Check that the identity provider's signing certificate hasn't expired. |
| **User is redirected to registration even though a contact exists** | The contact record exists but isn't linked to the external identity provider. | The user must complete the registration flow once to link the external identity to their contact record. Enable **Contact mapping with email** in the [identity provider settings](authentication/configure-site.md) to automate this. |
| **"Registrations are disabled" error** | Open registration is turned off in the site's authentication settings. | Go to **Set up** > **Identity providers** in the design studio and enable the **Open registration** setting for the identity provider. Or, [invite the user](invite-contacts.md) to the site. |

> [!TIP]
> To debug authentication issues, enable [diagnostic logging](/power-apps/maker/portals/admin/view-portal-error-log) on your site and review the error codes in the logs. Error codes prefixed with `RTAUEX` indicate authentication-related errors.

### See also

[Invite contacts to your Power Pages site](invite-contacts.md)  
[Configure site authentication](authentication/configure-site.md)  
[Set up Microsoft Entra External ID](authentication/entra-external-id.md)  
[Troubleshoot authentication issues in Power Pages](/troubleshoot/power-platform/power-pages/security/authentication-issues)
