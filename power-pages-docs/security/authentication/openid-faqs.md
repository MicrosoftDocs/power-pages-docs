---
title: FAQs for using OpenID Connect in Power Pages
description: Learn about frequently asked questions when using OpenID Connect providers for authentication in Power Pages.
author: dileepsinghmicrosoft

ms.topic: conceptual
ms.custom: 
ms.date: 3/20/2023
ms.author: dileeps
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
---

# FAQs for using OpenID Connect in Power Pages

This article includes information about common Power Pages scenarios and frequently asked questions for using an authentication provider that conforms to the [OpenID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html).

## Do I require an OpenID Connect Auto-Discovery Document to integrate with Power Pages?

Yes. The Auto-Discovery Document (also known as `/.well-known/openid-configuration`) is required to integrate with Power Pages. Information present in this document is used by Power Pages to create authorization requests and validate the authentication tokens.

If your identity provider doesn't provide this document, you can create it manually and host it at any public location (including your website).

> [!NOTE]
> Similar to the discovery document, Power Pages also requires the identity provider to provide a public *JWKS URI* endpoint where the public keys are available to verify the signature of the ID token. This endpoint needs to be specified in the discovery document as the *jwks_uri* key.

## Does Power Pages support *acr_values* request parameters in the authentication requests?

No. Power Pages doesn't support *acr_values* request parameters in authorization requests. However, the Power Pages feature does support all the required&mdash;and recommended&mdash;request parameters defined in the [OpenID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html#AuthRequest).

The following optional parameters are supported:

- Response_mode
- Nonce
- UI_Locales

## Does Power Pages support custom scope parameters in authentication requests?

Yes. Custom scope parameters can be specified by using the scope option during configuration.

## Why does the username value in a contact, or an external identity record in Dataverse, show a different value compared to what the user entered on the sign-in page?

The username field on a contact record and an external identity record will show the value sent in either the sub-claim or object ID (OID) claim (for Azure AD&ndash;based providers). This is because the sub-claim represents the identifier for the end user and is guaranteed by the identity provider to be unique. An OID claim (where the object ID is a unique identifier for all users in a tenant) is supported when used with single-tenant Azure AD&ndash;based providers.

## Does Power Pages support sign-out from OpenID Connect&ndash;based providers?

Yes. The Power Pages feature supports the front-channel sign-out technique to sign out from both the application and the OpenID Connect&ndash;based providers.

## Does Power Pages support single sign-out?

No. Power Pages doesn't support the single sign-out technique for OpenID Connect&ndash;based providers.

## Does Power Pages require any specific claim in an ID token*?

In addition to all required claims, the Power Pages feature requires a claim representing the email address of users in the ID token. This claim must be named `email`, `emails`, or `upn`.

Apart from all the required claims, Power Pages requires a claim representing email address of the users in the *id_token*. This claim must be named as either “email”, “emails” or “upn”.

These claims are processed at in the following order of priority to set as the *Primary Email Address* of the contact record in Dataverse:

1. email
1. emails
1. upn

When in use, "emailclaimsmapping" is also used to search for an existing contact (Primary Email Address field in Dataverse).

## Can I get access to tokens (ID or access) by using JavaScript?

No. The ID token provided by the identity provider isn't made available through any standard technique on the client side, and is only used for the purpose of authentication. However, if you're using the Implicit Grant flow, you can use the methods provided by your identity provider to get access to ID or access tokens.

For example, Azure AD provides [Microsoft Authentication Library](/azure/active-directory/develop/msal-overview) to achieve this scenario in clients.

## Can I use a custom OpenID Connect provider instead of Azure AD?

Yes. Power Pages supports any OpenID Connect provider that supports the standard [OpenID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html).

### See also
 
[Configure an OpenID Connect provider for Power Pages](openid-provider.md)
