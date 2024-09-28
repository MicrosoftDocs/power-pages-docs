---
title: Provide access to external audiences
description: Learn how to allow external audiences to use a local account to access sites you create with Microsoft Power Pages.
ms.date: 07/20/2023
ms.topic: conceptual
author: nickdoelman
ms.author: danamartens
contributors:
    - nickdoelman
ms.custom: bap-template
---
# Provide access to external audiences

 Power Pages site user information is stored as contact records in Dataverse. Before users can authenticate to your site with a local account, a record must exist for them in your site's Contacts table. You can create the contact yourself, or the user can create a record by submitting a sign-up form if you [turn on user registration](authentication/set-authentication-identity.md#enable-or-disable-user-registration) on your site.

Contact records that you create don't have a username and password. You must [enter a username](#add-a-username-to-a-contact-record), and then use the [change password](#change-a-contacts-password) workflow to set an initial password. Use the [Portal Management app](../configure/portal-management-app.md) to create and edit your site's contact records.

You can also send a user an [invitation to register locally](invite-contacts.md). [Learn more about local authentication, registration, and other settings](authentication/set-authentication-identity.md).

> [!IMPORTANT]
> We recommend you use the [Azure AD B2C identity provider](authentication/azure-ad-b2c-provider.md) for authentication and [deprecate the local identity provider](authentication/migrate-identity-providers.md).

## Add a username to a contact record

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, scroll down to the **Security** section and select **Contacts**.

1. Create or select a contact.

1. Select the **Contact - Portal Contact** form.

1. Select the **Web Authentication** tab.

1. Enter a **Username**.

    :::image type="content" source="media/user-management/config-contact-record.svg" alt-text="Screenshot of a contact record in the Portal Management app, with the username box on the Web Authentication tab highlighted.":::

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

### See also

[Invite contacts to your Power Pages site](invite-contacts.md)