---
title: FAQs about using OpenID Connect in Power Pages
description: Get answers to frequently asked questions about using OpenID Connect providers for authentication on sites you create with Microsoft Power Pages.
ms.date: 07/19/2023
ms.topic: conceptual
author: dileepsinghmicrosoft
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# FAQs about using OpenID Connect in Power Pages

This article provides information about common Power Pages scenarios and answers to frequently asked questions about using an authentication provider that conforms to the [OpenID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html).

## Do I need an OpenID Connect autodiscovery document to integrate with Power Pages?

An autodiscovery document, or OpenID Connect metadata document (also known as `/.well-known/openid-configuration`) is required to integrate with Power Pages. Power Pages uses the information in this document to create authorization requests and validate the authentication tokens.

If your identity provider doesn't provide an autodiscovery document, you can create one yourself and host it at any public location, including your website.

> [!NOTE]
> Similar to the discovery document, Power Pages also requires the identity provider to provide a public *JWKS URI* endpoint where the public keys are available to verify the signature of the ID token. This endpoint needs to be specified in the discovery document as the *jwks_uri* key.

## Does Power Pages support *acr_values* request parameters in the authentication requests?

Power Pages doesn't support *acr_values* request parameters in authorization requests. However, Power Pages authentication does support all the required and recommended request parameters defined in the [OpenID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html#AuthRequest). The following optional parameters are also supported:

- Response_mode
- Nonce
- UI_Locales

## Does Power Pages support custom scope parameters in authentication requests?

Custom scope parameters can be specified using the **Scope** setting in your provider configuration.

## Why is the username in a contact or external identity record in Dataverse different from what the user entered on the sign-in page?

The username field in a contact record and an external identity record shows the value that's sent in either the subclaim or object ID (OID) claim for Microsoft Entra&ndash;based providers. This is because the subclaim represents the user identifier and is guaranteed by the identity provider to be unique. An OID claim, where the object ID is a unique identifier for all users in a tenant, is supported when used with single-tenant Microsoft Entra&ndash;based providers.

## Does Power Pages support signing out from OpenID Connect&ndash;based providers?

Power Pages authentication supports the front-channel sign-out technique to sign out from both the application and the OpenID Connect&ndash;based provider.

## Does Power Pages support single sign-out?

Power Pages doesn't support the single sign-out technique for OpenID Connect&ndash;based providers.

## Does Power Pages require a specific claim in an ID token?

Power Pages requires a claim that represents the user's email address in the ID token. This claim must be named `email`, `emails`, or `upn`. These claims are processed in the following order to set as the *Primary Email Address* of the contact record in Dataverse:

1. email
1. emails
1. upn

When in use, "emailclaimsmapping" is also used to search for an existing contact (Primary Email Address field in Dataverse).

## Can I get access to tokens (ID or access) using JavaScript?

The ID token provided by the identity provider isn't available using JavaScript or any standard technique on the client side. It's used only for authentication. However, if you're using the implicit grant flow, you can use the methods provided by your identity provider to get access to ID or access tokens. For example, Microsoft Entra ID provides the [Microsoft Authentication Library](/azure/active-directory/develop/msal-overview) for this scenario.

## Can I use a custom OpenID Connect provider instead of Microsoft Entra ID?

Power Pages supports any identity provider that conforms to the standard [OpenID Connect specification](https://openid.net/specs/openid-connect-core-1_0.html).

### See also

[Set up an OpenID Connect provider](openid-provider.md)