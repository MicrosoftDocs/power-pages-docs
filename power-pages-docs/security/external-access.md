---
title: Configure contacts for Power Pages
description: Learn how to provide access to external audiences.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/24/2022
ms.subservice:
ms.author: kkendrick
ms.reviewer:
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Configure contacts for Power Pages

User information in Power Pages is stored as contact records in Dataverse. To configure contacts and invite them as users to your site, use the [Portal Management app](../configure/portal-management-app.md).

Fill out the basic information for a contact (or having a user fill out the sign-up form in a website), then go to the web authentication tab on the contact form to configure a contact by using local authentication. 

For more information about federated authentication options, see [Local authentication, registration, and other settings](authentication/set-authentication-identity.md).

To configure a contact using local authentication, follow these instructions:  

> [!IMPORTANT]
> - We recommend that you use the [Azure Active Directory B2C (Azure AD B2C)](configure-azure-ad-b2c-provider.md) identity provider for authentication and deprecate the local identity provider for your portal. More information: [Migrate identity providers to Azure AD B2C](migrate-identity-providers.md)

Complete the change password workflow, and the necessary fields will be automatically configured. When you've taken these steps, your contact will be configured for your website.

1. In the **Security** section, select **Contacts**.

1. Create a new contact or select an existing contact.

1. Choose the **Contact - Portal Contact** form.

1. Select the **Web Authentication** tab.

1. Enter a **Username**.

1. Select **Save**.

1. On the command bar, choose **Change Password**.

1. Complete the [change password steps](#change-password-for-a-contact-from-the-portal-management-app), and the necessary fields will be automatically configured. The contact will then be configured to access the portal.

A portal user can also [register directly](set-authentication-identity.md#sign-up-by-using-a-local-identity-or-external-identity) on the portal, or be sent an [invitation](invite-contacts.md) to register. 

For more information about federated authentication options, see [set authentication identity for a portal](set-authentication-identity.md). 

## Change password for a contact from the Portal Management app

In order to perform the following steps, you'll need to be assigned the **System Administrator** [security role](/power-platform/admin/database-security). 

1. In the design studio, select the ellipsis (**...**) from the tool belt, and then select **Portal Management**.

    :::image type="content" source="../configure/media/portals-management-app/launch-portals-management-app.png" alt-text="Open the Portal Management app.":::

1. Go to **Portals** > **Contacts**, and open the contact for which you want to change the password.
    Alternately, you can also open the **Contacts** page from the [Share](../manage-existing-portals.md#share) pane. 

1. Select **Change Password** from the command bar the contact form.

1. In the **New password** field, enter a new password, and then select **Next**.

    >[!NOTE]
    > If you don't enter a password and select **Next**, you'll be asked whether you want to remove password for the selected contact.

1. After making the changes, select **Done**.

### Deprecation of business process flow

Earlier versions of the change password process utilized a task flow, which has been deprecated. In Dataverse security roles, the **Change Password for Contact** privilege under the **Business Process Flows** tab no longer requires any options selected.

## See also

- [Invite contacts to your Power Pages site](invite-contacts.md)

