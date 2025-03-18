---
title: Additional settings for OAuth 2.0 providers
description: Learn about other settings you can change when you add an OAuth 2.0 provider to sites you create with Microsoft Power Pages.
ms.date: 11/15/2024
ms.topic: how-to
author: DanaMartens
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Additional settings for OAuth 2.0 providers

[Add an OAuth 2.0 provider](oauth2-provider.md) to your Power Pages site to allow visitors to authenticate using a [Microsoft](oauth2-microsoft.md), [LinkedIn](oauth2-linkedin.md), [Facebook](oauth2-facebook.md), [Google](oauth2-google.md), or [Twitter](oauth2-twitter.md) account. After you enter the specific client ID and client secret for your identity provider, you may need to change other settings that apply to any OAuth 2.0 provider. These settings are optional and you should change them only if you know what you're doing.

To change the other settings for an OAuth 2.0 identity provider, [edit the provider settings](configure-site.md#edit-an-identity-provider) and expand the **Additional settings** section.

:::image type="content" source="../media/authentication/additional-settings.jpg" alt-text="Screenshot of optional additional settings for OAuth 2.0 providers.":::

| Setting | Description |
|---------|---------|
| Authentication type | The OWIN authentication middleware type |
| Authentication mode | The OWIN authentication middleware mode |
| Backchannel timeout | The timeout value in milliseconds for back-channel communications |
| Callback path | The request path in the application's base path where the user-agent is returned |
| Sign in As authentication type | The name of another authentication middleware that's responsible for issuing a user claims identity |
| Scope | A comma-separated list of permissions to request |
| Registration enabled | Turns on or off the provider's registration requirement. When this setting is off, users are denied registration with an error if no contact record exists for them. When this setting is on, users can register only if the site setting **Authentication/Registration/Enabled** is set to true. |
| Contact mapping with email | Specifies whether contacts are mapped to a corresponding email. When this setting is on, it associates a unique contact record with a matching email address, and then automatically assigns the external identity provider to the contact after the user successfully signs in. This setting isn't applicable for multitenant endpoints and the [Microsoft identity provider](oauth2-microsoft.md). Use [invitations](../invite-contacts.md) or open registration to allow users to authenticate to your website. |

## Additional information

[Set up an OAuth 2.0 identity provider](oauth2-provider.md)
