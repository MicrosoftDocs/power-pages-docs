---
title: Provide access to external audiences
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

# Provide access to external audiences

User information in Power Pages is stored as contact records in Dataverse. To configure contacts and invite them as users to your site, use the [Portal Management app](../configure/portal-management-app.md).

## Configure contacts as site users

Fill out the basic information for a contact (or having a user fill out the sign-up form in a website), then go to the web authentication tab on the contact form to configure a contact by using local authentication. For more information about federated authentication options, see [Local authentication, registration, and other settings](authentication/set-authentication-identity.md). 

To configure a contact for Power Pages using local authentication, follow these instructions:  

> [!IMPORTANT]
> We recommend that you use the [Configure the Azure Active Directory B2C provider](authentication/azure-ad-b2c-provider.md) identity provider for authentication and deprecate the local identity provider for your website. 
> More information:[Migrate identity providers to Azure AD B2C](authentication/migrate-identity-providers.md)

Complete the change password workflow, and the necessary fields will be automatically configured. When you've taken these steps, your contact will be configured for your website.

1. In the **Security** section, select **Contacts**.

1. Create a new contact or select an existing contact.

1. Choose the **Contact - Portal Contact** form.

1. Select the **Web Authentication** tab.

1. Enter a **Username**.

1. Select **Save**.

1. On the command bar, choose **Change Password**.

1. Complete the [change password steps](#change-password-for-a-contact-from-the-portal-management-app), and the necessary fields will be automatically configured. The contact will then be configured to access the website.

A user can also [register directly](authentication/set-authentication-identity.md#sign-in-by-using-a-local-identity-or-external-identity) on the website, or be sent an [invitation](invite-contacts.md) to register. 

For more information about federated authentication options, see [Local authentication, registration, and other settings](authentication/set-authentication-identity.md). 

## Change password for a contact from the Portal Management app

In order to perform the following steps, you'll need to be assigned the **System Administrator** [security role](/power-platform/admin/database-security). 

1. Open the [Portal Management app](../configure/portal-management-app.md).

1. Go to **Portals** > **Contacts**, and open the contact for which you want to change the password.

1. Select **Change Password** from the command bar the contact form.

1. In the **New password** field, enter a new password, and then select **Next**.

    If you don't enter a password and select **Next**, you'll be asked whether you want to remove password for the selected contact.

1. After making the changes, select **Done**.

### Deprecation of business process flow

Earlier versions of the change password process utilized a task flow, which has been deprecated. In Dataverse security roles, the **Change Password for Portals Contact** privilege under the **Business Process Flows** tab no longer requires any options selected.

### See also
[Invite contacts to your Power Pages site](invite-contacts.md)
