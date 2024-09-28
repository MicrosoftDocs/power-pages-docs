---
title: Set up an OAuth 2.0 provider
description: Learn how to set up OAuth 2.0 identity providers such as Microsoft, LinkedIn, Facebook, Google, and Twitter for use with sites you create with Microsoft Power Pages.
ms.date: 07/19/2023
ms.topic: overview
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Set up an OAuth 2.0 provider

To allow users to authenticate on your Power Pages site with their Microsoft, LinkedIn, Facebook, Google, or Twitter account, add an OAuth 2.0 identity provider. Power Pages doesn't support the use of other OAuth providers. Use [OpenID Connect](openid-provider.md) instead.

OAuth 2.0&ndash;based external identity providers require that you register an application with a third-party service to get a *client ID* and *client secret* pair. You may also need to specify a redirect or reply URL to allow the identity provider to send users back to your website, called the *replying party*, after it authenticates them. The client ID and client secret establish a secure connection between the replying party and the identity provider. These values are site settings that are based on the properties of the [MicrosoftAccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [TwitterAuthenticationOptions](/previous-versions/aspnet/dn450335(v=vs.113)), [FacebookAuthenticationOptions](/previous-versions/aspnet/dn253793(v=vs.113)), and [GoogleOAuth2AuthenticationOptions](/previous-versions/aspnet/dn800251(v=vs.113)) classes.

## Provider settings

For the settings you need to change for specific OAuth 2.0 providers, select the name of the provider:

- [Microsoft](oauth2-microsoft.md)
- [LinkedIn](oauth2-linkedin.md)
- [Facebook](oauth2-facebook.md)
- [Google](/power-apps/maker/portals/configure/configure-oauth2-google)
- [Twitter](oauth2-twitter.md)

Then if needed, change [optional additional settings that apply to all OAuth 2.0 providers](oauth2-settings.md).

> [!NOTE]
> Changes to your site's authentication settings [might take a few minutes](/power-apps/maker/portals/admin/clear-server-side-cache#caching-changes-for-portals-with-version-926x-or-later) to be reflected on the site. To see the changes immediately, restart the site in the [admin center](../../admin/admin-overview.md).
