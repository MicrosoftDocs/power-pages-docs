---
title: FAQs about using SAML 2.0 in Power Pages
description: Get answers to frequently asked questions about using SAML 2.0 providers for authentication on sites you create with Microsoft Power Pages.
ms.date: 07/19/2023
ms.topic: how-to
author: DanaMartens
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# FAQs about using SAML 2.0 in Power Pages

This article provides information about common Power Pages scenarios and answers to frequently asked questions about using an authentication provider that conforms to the Security Assertion Markup Language [(SAML) 2.0 specification](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html).

## Does Power Pages support SAML 1.0&ndash;based providers?

Power Pages supports SAML 2.0&ndash;based providers only.

## Does Power Pages support signed assertion?

Power Pages doesn't support signed assertion requests. If you're using signed assertion, we suggest you use OpenID Connect. If your identity provider doesn't support OpenID Connect, use an intermediary identity provider (preferably Azure AD B2C) that supports federation with SAML and can federate with Power Pages using OpenID Connect.

## Does Power Pages support signed SAML responses?

Power Pages requires all SAML responses to be signed by the identity provider.

## Does Power Pages support encrypted assertion and response?

Power Pages doesn't support encrypted SAML assertion or response.

## What type of name identifiers are supported?

Power Pages requires *persistent* identifiers that ensure that the user can always be uniquely identified across sessions. Power Pages doesn't support *transient* identifiers.

## Does Power Pages require any specific AuthNContextClass in SAML assertion requests?

Power Pages specifies *PasswordProtectedTransport* in authentication requests, and requires that the identity provider support it.

## Does Power Pages support SAML logout requests?

Power Pages supports SAML logout requests. Use the [Power Platform admin center](../../admin/admin-overview.md) to upload the custom certificate. Then copy the thumbprint of the uploaded custom certificate on the **Manage custom certificate** screen and paste it in the site setting **Authentication/SAML2/*ProviderName*/ExternalLogoutCertThumbprint**.

### See also

[Set up a SAML 2.0 provider with Microsoft Entra ID](saml2-settings-azure-ad.md)  
[Set up a SAML 2.0 provider with AD FS](saml2-settings.md)  
[Set up a SAML 2.0 provider](saml2-provider.md)