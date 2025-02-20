---
title: Local authentication, registration, and other settings
description: Learn about the settings you can use to control user authentication on sites you create with Microsoft Power Pages.
ms.date: 02/05/2025
ms.topic: conceptual
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
    - nageshbhat-msft
ms.custom: bap-template
---

# Local authentication, registration, and other settings

> [!IMPORTANT]
> We recommend you use the [Azure AD B2C identity provider](azure-ad-b2c-provider.md) for authentication on your Power Pages site and [deprecate the local identity provider](migrate-identity-providers.md).

Power Pages provides authentication functionality built on the [ASP.NET Identity](https://www.asp.net/identity) API. ASP.NET Identity is in turn built on the [OWIN](https://www.asp.net/aspnet/overview/owin-and-katana) framework, which is also an important component of the authentication system. Power Pages provides the following services:

- Local (username/password) authentication
- External (social provider) authentication through third-party identity providers
- Two-factor authentication with email
- Email address confirmation
- Password recovery
- Invitation code sign-up for registering prepopulated contact records

> [!NOTE]
> The `Mobile Phone Confirmed` column in the contact record isn't used except when upgrading from Adxstudio Portals.

## Requirements

Power Pages requires:

- Portals Base
- Microsoft Identity
- Microsoft Identity Workflows solution packages

## Authenticate and register

Returning site visitors can authenticate using local user credentials or external identity provider accounts. A new visitor can register for a user account either by providing a username and password or by signing in through an external provider. Visitors who receive an invitation code from the site administrator can redeem the code while signing up for a new user account.

Related site settings:

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

## Reset a password

Returning visitors who provided an email address when they registered can request a password reset token to be sent to their email account. A reset token allows its owner to choose a new password. The token can also be abandoned, leaving the user's original password unchanged.

Related site settings:

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

Related process: Send a password reset to a contact

1. The visitor provides an email address.
1. Submit the email address to start the process.
1. The visitor is prompted to check email.
1. The visitor receives the password reset email with instructions.
1. The visitor returns to the reset form and selects a new password.
1. The password reset is complete.

## Redeem an invitation

Redeeming an invitation code allows a registering visitor to be associated with an existing contact record that was prepared in advance specifically for that visitor. Typically, invitation codes are sent by email. You can use a general code submission form to send codes though other channels. After the visitor submits a valid invitation code, the normal user registration process sets up the new user account.

Related site setting: `Authentication/Registration/InvitationEnabled`

Related process: Send invitation

Customize the invitation email to include the URL to the redeem invitation page on your site.

1. Create an invitation for a new contact.
1. Customize and save the invitation.
1. Customize the invitation email.
1. Process the [send invitation](../invite-contacts.md) workflow.
1. The invitation email opens the redemption page.
1. The user submits the invitation code to sign up.

### Disabled registration

If registration is disabled for a user after the user redeemed an invitation, use the following content snippet to display a message: `Account/Register/RegistrationDisabledMessage`

## Manage user accounts through profile pages

Authenticated users manage their user accounts through the **Security** option on the profile page. Users aren't limited to the single local account or single external account they chose when they registered. Users who have an external account can choose to create a local account by providing a username and password. Users who started with a local account can choose to associate multiple external identities with that account. The profile page is also where users are reminded to confirm their email address by requesting a confirmation email to be sent to their email account.

Related site settings:

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## Set or change a password

A user who has a local account can select a new password by providing the original password. A user who doesn't have a local account can choose a username and password to set up a new local account. The username can't be changed after it's set.

Related site setting: `Authentication/Registration/LocalLoginEnabled`

Related processes:

- Create a username and password
- Change a password

These task flows work only when invoked using the Portal Management app. They aren't affected by the [upcoming deprecation of task flows](/power-platform/important-changes-coming#task-flows-are-deprecated).

## Confirm an email address

Changing an email address or setting one for the first time marks it as unconfirmed. The user can request a confirmation email to be sent to their new email address. The email includes instructions for completing the email confirmation process.

Related process: Send an email confirmation to a contact

1. The user submits a new, unconfirmed email address.
1. The user checks email for the confirmation message.
1. Process the send email confirmation to contact workflow.
1. The user selects the confirmation link to complete the confirmation process.

Make sure that the primary email address is specified for the contact. The confirmation email is sent only to the primary email address (emailaddress1), not to the secondary (emailaddress2) or alternate (emailaddress3) address of the contact record.

## Enable two-factor authentication

Two-factor authentication increases user account security by requiring proof of ownership of a confirmed email address in addition to the standard local or external account authentication. When a user tries to sign in to an account that has two-factor authentication enabled, a security code is sent to the confirmed email address associated with the account. The user must enter the security code to complete the sign-in process. A user can choose to have the site remember the browser that successfully passed the verification so that a security code isn't required the next time the user signs in using the same browser. Each user account enables this feature individually and requires a confirmed email address.

> [!WARNING]
> If you create and enable the `Authentication/Registration/MobilePhoneEnabled` site setting to enable the legacy functionality, an error occurs. This site setting isn't provided out of the box and isn't supported by Power Pages.

Related site settings:

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

Related process: Send email two-factor code to a contact

1. The visitor chooses to receive the security code by email.
1. The visitor waits for the email that contains the security code.
1. the visitor enters the security code.
1. Process the send email two-factor code to contact workflow.
1. The visitor can disable two-factor authentication.

## Manage external accounts

An authenticated user can connect, or register, multiple external identities to their user account, one from each configured identity provider. After the identities are connected, the user can choose to sign in using any of them. Identities can also be disconnected, as long as a single external or local identity remains.

Related site setting: `Authentication/Registration/ExternalLoginEnabled`

Related process: Connect an identity

1. The visitor selects a provider to connect to the user account.
1. The visitor signs in using a connected provider.

The provider can also be disconnected.

## Enable ASP.NET identity authentication

The following table describes the settings for enabling and disabling various authentication features and behaviors.

| Site setting name | Description |
| --- | --- |
| Authentication/Registration/LocalLoginEnabled | Enables or disables local account sign-in based on a username or email address and password. Default: True |
| Authentication/Registration/LocalLoginByEmail | Enables or disables local account sign-in using an email address instead of a username. Default: False |
| Authentication/Registration/ExternalLoginEnabled | Enables or disables external account sign-in and registration. Default: True |
| Authentication/Registration/RememberMeEnabled | Selects or clears a **Remember me?** check box on local sign-in to allow authenticated sessions to persist even when the web browser is closed. Default: True |
| Authentication/Registration/TwoFactorEnabled | Enables or disables two-factor authentication. Users with a confirmed email address can opt in to the added security of two-factor authentication. Default: False |
| Authentication/Registration/RememberBrowserEnabled | Selects or clears a **Remember browser?** check box on second-factor validation (email code) to persist the second-factor validation for the current browser. The user isn't required to pass the second-factor validation for subsequent sign-ins using the same browser. Default: True |
| Authentication/Registration/ResetPasswordEnabled | Enables or disables the password reset feature. Default: True |
| Authentication/Registration/ResetPasswordRequiresConfirmedEmail | Enables or disables password reset for confirmed email addresses only. If enabled, unconfirmed email addresses can't be used to send password reset instructions. Default: False |
| Authentication/Registration/TriggerLockoutOnFailedPassword | Enables or disables recording of failed password attempts. If disabled, user accounts aren't locked out. Default: True |
| Authentication/Registration/IsDemoMode | Enables or disables a demo mode flag for use in development or demonstration environments only. Don't enable this setting in production environments. Demo mode also requires the web browser to be running locally to the web application server. When demo mode is enabled, the password reset code and second-factor code are displayed to the user for quick access. Default: False |
| Authentication/Registration/LoginButtonAuthenticationType | If a site requires a single external identity provider to handle all authentication, this setting allows the **Sign In** button to link directly to the provider's sign-in page instead of the intermediate local sign-in form and identity provider selection page. Only one identity provider can be selected for this action. Specify the provider's *AuthenticationType*.<br/>- For a single sign-on configuration that uses OpenID Connect, such as Azure AD B2C, the user needs to provide the authority.<br/>- For OAuth 2.0&ndash;based providers, the accepted values are `Facebook`, `Google`, `Yahoo`, `Microsoft`, `LinkedIn`, or `Twitter`.<br/>- For WS-Federation&ndash;based providers, use the value specified for the `Authentication/WsFederation/ADFS/AuthenticationType` and `Authentication/WsFederation/Azure/\<provider\>/AuthenticationType` site settings. |

## Enable or disable user registration

The following table describes the settings for enabling and disabling user registration (sign-up) options.

| Site setting name | Description |
|-------------------|-------------|
| Authentication/Registration/Enabled | Enables or disables all forms of user registration. Registration must be enabled for the other settings in this section to take effect. Default: True |
| Authentication/Registration/OpenRegistrationEnabled | Enables or disables the sign-up registration form. The sign-up form allows any anonymous visitor to create a user account. Default: True |
| Authentication/Registration/InvitationEnabled | Enables or disables the invitation code redemption form for registering users who have an invitation code. Default: True |
|Authentication/Registration/CaptchaEnabled | Enables or disables captcha on the user registration page. Default: False<br/>This setting might not be available by default. To enable captcha, you must create the site setting and set its value to true. |

Make sure that the primary email address is specified for the user. Users can register only with the primary email address (emailaddress1), not the secondary (emailaddress2) or alternate (emailaddress3) address of the contact record.

## User credential validation

The following table describes the settings for adjusting username and password validation parameters. Validation occurs when users sign up for a new local account or change a password.

| Site setting name | Description |
|-------------------|-------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy | Determines whether the password must contain characters from three of the following categories:<br/><ul><li>Uppercase letters of European languages (A through Z, with diacritic marks and Greek and Cyrillic characters)</li><li>Lowercase letters of European languages (a through z, sharp-s, with diacritic marks and Greek and Cyrillic characters)</li><li>Base 10 digits (0 through 9)</li><li>Nonalphanumeric characters or special characters</li></ul>Default: True. [Learn more about password policy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh994562(v=ws.10)). |
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | Determines whether to allow only alphanumeric characters for the username. Default: False |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail | Determines whether a unique email address is needed to validate the user. Default: True |  
| Authentication/UserManager/PasswordValidator/RequiredLength | Sets the minimum required password length. Default: 8 |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit | Determines whether the password requires a special character. Default: False |  
| Authentication/UserManager/PasswordValidator/RequireDigit | Determines whether the password requires a number. Default: False |  
| Authentication/UserManager/PasswordValidator/RequireLowercase | Determines whether the password requires a lowercase letter. Default: False |  
| Authentication/UserManager/PasswordValidator/RequireUppercase | Determines whether the password requires an uppercase letter. Default: False |

## User account lockout settings

The following table describes the settings that define how and when an account becomes locked from authentication. When a certain number of failed password attempts are detected in a short timespan, the user account is locked for a time. The user can try again after the lockout period elapses.

| Site setting name | Description |
|-------------------|-------------|
| Authentication/UserManager/UserLockoutEnabledByDefault | Indicates whether the user lockout is enabled when users are created. Default: True |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan | Sets the default amount of time that a user is locked out after reaching the maximum number of failed attempts. Default: 24:00:00`(1 day) |
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | The maximum number of failed sign-in attempts allowed before a user is locked out if lockout is enabled. Default: 5 |

## Cookie authentication site settings

The following table describes settings for modifying default authentication cookie behavior, defined by the CookieAuthenticationOptions class.

| Site setting name | Description |
|-------------------|-------------|
| Authentication/ApplicationCookie/AuthenticationType | Sets the type of the application authentication cookie. Default: ApplicationCookie |
| Authentication/ApplicationCookie/CookieName | Determines the cookie name used to persist the identity. Default: .AspNet.Cookies |
| Authentication/ApplicationCookie/CookieDomain | Determines the domain used to create the cookie. |
| Authentication/ApplicationCookie/CookiePath | Determines the path used to create the cookie. Default: / |
| Authentication/ApplicationCookie/CookieHttpOnly | Determines whether the browser should allow the cookie to be accessed by client-side JavaScript. Default: True |
| Authentication/ApplicationCookie/CookieSecure | Determines whether the cookie should only be transmitted on HTTPS request. Default: SameAsRequest |
| Authentication/ApplicationCookie/ExpireTimeSpan | Controls how much time the application cookie remains valid from the moment it was created. Default: 24:00:00 (1 day) |
| Authentication/ApplicationCookie/SlidingExpiration | Instructs the middleware to reissue a new cookie with a new expiration time whenever it processes a request that's more than halfway through the expiration window. Default: True |
| Authentication/ApplicationCookie/LoginPath | Informs the middleware that it should change an outgoing 401 Unauthorized status code to a 302 redirection to the given sign-in path. Default: /signin |
| Authentication/ApplicationCookie/LogoutPath | If the sign-out path is provided by the middleware, a request to that path is redirected based on the ReturnUrlParameter. |
| Authentication/ApplicationCookie/ReturnUrlParameter | Determines the name of the query string parameter that's appended by the middleware when a 401 Unauthorized status code is changed to a 302 redirect to the sign-in path. |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | Sets the period of time between security stamp validations. Default: 30 minutes |
| Authentication/TwoFactorCookie/AuthenticationType | Sets the type of two-factor authentication cookie. Default: TwoFactorCookie |
| Authentication/TwoFactorCookie/ExpireTimeSpan | Controls how much time a two-factor cookie remains valid from the moment it was created. the value shouldn't exceed six minutes. Default: 5 minutes |

## Next steps

[Migrate identity providers to Azure AD B2C](migrate-identity-providers.md)

### See also

[Overview of authentication in Power Pages](index.md)  
[Set up an OAuth 2.0 provider](oauth2-provider.md)  
[Set up an OpenID Connect provider](openid-provider.md)  
[Set up a SAML 2.0 provider](saml2-provider.md)  
[Set up a WS-Federation provider](ws-federation-provider.md)