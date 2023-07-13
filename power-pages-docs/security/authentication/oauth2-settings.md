---
title: Additional settings for OAuth 2.0 providers
description: Learn about the additional settings you need to change for specific OAuth 2.0 providers in Power Pages.
ms.date: 3/6/2023
ms.topic: how-to
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Additional settings for OAuth 2.0 providers

[Add an OAuth 2.0 provider](oauth2-provider.md) to your Power Pages site to allow visitors to authenticate using a Microsoft, LinkedIn, Facebook, Google, or Twitter account. 



 The additional authentication settings in this section apply to the [Microsoft](oauth2-microsoft.md), [LinkedIn](oauth2-linkedin.md), [Facebook](oauth2-facebook.md), [Google](/power-apps/maker/portals/configure/configure-oauth2-google), and [Twitter](oauth2-twitter.md) providers.

To configure the additional settings for any OAuth 2.0 identity provider, select **Configure** from the [provider settings](/power-apps/maker/portals/configure/use-simplified-authentication-configuration#add-configure-or-delete-an-identity-provider) page, and expand **Additional settings**.

:::image type="content" source="../media/authentication/additional-settings.jpg" alt-text="Optional additional settings for OAuth 2.0 providers.":::


|Setting |Description  |
|---------|---------|
|Authentication type    | The OWIN authentication middleware type. <br /> Example: `https://sts.windows.net/contoso.onmicrosoft.com/`|
|Authentication mode    | The OWIN authentication middleware mode.|
|Backchannel timeout     | Timeout value in milliseconds for back-channel communications: MicrosoftAccountAuthenticationOptions.BackchannelTimeout.|
|Callback path    | The request path within the application's base path where the user-agent will be returned: MicrosoftAccountAuthenticationOptions.CallbackPath.|
|Sign in As authentication type     |  The name of another authentication middleware that will be responsible for actually issuing a user claims identity: MicrosoftAccountAuthenticationOptions.SignInAsAuthenticationType.|
|Scope    | A comma-separated list of permissions to request: MicrosoftAccountAuthenticationOptions.Scope.|
|Registration Enabled    | Enables or disables the registration requirement for the existing identity provider. When this is disabled, the user is denied registration with an error if no contact record exists for the user. When this is enabled, user registration is allowed for a new user only if the site setting **Authentication/Registration/Enabled** is set to true.|
|Contact mapping with email| Specifies whether contacts are mapped to a corresponding email. When enabled, this setting associates a unique contact record with a matching email address, and then automatically assigns the external identity provider to the contact after the user successfully signs in.        |


### See also

[Configure an OAuth 2.0 provider for Power Pages](oauth2-provider.md)

