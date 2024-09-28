---
title: Migrate identity providers to Azure AD B2C
description: Learn how to migrate your Power Pages site's identity providers to Azure AD B2C.
ms.date: 07/19/2023
ms.topic: how-to
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Migrate identity providers to Azure AD B2C

Power Pages supports multiple authentication systems. Users can authenticate to your site with local credentials or using federated external identity providers that comply with standard protocols such as OIDC, SAML 2.0, and WS-Federation. We recommend you use the Azure Active Directory (Azure AD) B2C identity provider for authentication and deprecate other identity providers.

> [!IMPORTANT]
>
> - We recommend you migrate from [local authentication](set-authentication-identity.md) to Azure AD B2C.
> - To set up local authentication, you must use the [Portal Management app](../../configure/portal-management-app.md) to manually change required site settings.

## Deprecate an identity provider

To mark other identity providers as deprecated and allow users to migrate to an Azure AD B2C identity provider, change the following site settings:

- **Authentication/Registration/LocalLoginDeprecated**: Set this to true.
- **Authentication/*\<protocol\>*/*\<provider\>*/Deprecated**: Set this to true.

You can change the text that appears on the sign-in page of a legacy authentication provider using the following content snippet: **Account/Signin/SignInExternalDeprecatedFormHeading**

Deprecated identity providers aren't shown when a user registers on or redeems an invitation to register on a website.

## Migrate a deprecated identity provider to a new identity provider

If a user signs in using a deprecated identity provider, the account migration page displays a message to sign in using a different identity provider. When the user signs in using the new provider, the user's account is associated with that provider.

The following table describes the content snippets you can use to change the message that appears on the account migration page.

| Name | Type | Default value |
|------|------|-------|
| **Account/Conversion/PageTitle** | Text | Account Migration |
| **Account/Conversion/PageCopy** | HTML | You've signed in with an account that is no longer supported. To continue using this site, you must migrate to a different account. Select the button to sign in with a new or existing supported account. |
| **Account/Conversion/SignInExternalFormHeading** | Text | Sign in with a supported account. |

A Power Pages site allows multiple identities to be associated with a single contact record. When multiple providers are deprecated, a user must consent to the terms and conditions multiple times. Whenever a user signs in with a deprecated identity provider, the account migration process is started for each deprecated provider and the contact record is associated with the nondeprecated provider after account migration.

For example, your website supports Microsoft, Google, and Facebook as identity providers for authentication. You mark Google and Facebook as deprecated providers. If a user only has Google and Facebook as identity providers for authentication, the site displays the account migration message when the user tries to sign in using either of these accounts. When the user signs in using a Microsoft account, the Microsoft account is added to the user's contact record. The user now has only Microsoft as the supported authentication identity provider.

When a user selects a new identity provider and the identity is already associated with a different contact record, an error message appears. The following table describes the content snippets you can use to change the error message.

| Name | Type | Default value |
|------|------|-------|
| **Account/Signin/AccountConversionIdentityUsedErrorHeading** | Text | Account Conversion Error |
| **Account/Signin/AccountConversionIdentityUsedErrorText** | HTML | This account already exists. Close your browser, restart the process, and select a different account on the Account Migration page. |

## Turn off local authentication

To turn off local authentication on your site, set the `Authentication/Registration/LocalLoginDeprecated` site setting to true. If a user tries to sign in using local credentials, the account migration page appears along with the instruction to sign in using a nondeprecated identity provider. When the account is migrated, the user's local credentials are disabled. The `Local Login Disabled` column in the site's contact record changes to **Yes** to indicate the contact can no longer sign in using the local account. By default, this column is set to **No**.

If you deprecate local authentication, users can't register for a new account on your site.

### See also

[Set up the Azure AD B2C provider](azure-ad-b2c-provider.md)