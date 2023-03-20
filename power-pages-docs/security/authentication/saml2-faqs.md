---
title: FAQs for using SAML 2.0 in Power Pages
description: Learn about Frequently Asked Questions when using SAML 2.0 providers for authentication in Power Pages.
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
    - ProfessorKendrick
---

# FAQs for using SAML 2.0 in Power Pages

This article includes information about common Power Pages scenarios and frequently asked questions for using an authentication provider that conforms to the Security Assertion Markup Language (SAML) 2.0 standard.

## Does Power Pages support SAML 1.0&ndash;based providers?

No. Power Pages only supports SAML 2.0&ndash;based providers.

## Does Power Pages support Signed Assertion?

No. Power Pages doesn't support signed assertion requests. If you're using signed assertion, we suggest that you use OpenID Connect. If your identity provider doesn't support OpenID Connect, use an intermediary identity provider (preferably Azure AD B2C) that supports federation with SAML and can federate with Power Pages by using OpenID Connect.

## Does Power Pages support signed SAML responses?

Yes. Power Pages requires all SAML responses to be signed by the identity provider.

## Does Power Pages support encrypted assertion and response?

No. Power Pages doesn't support encrypted SAML assertion or response.

## What type of name identifiers are supported?

Power Pages requires *persistent* identifiers that ensure that the user can always be uniquely identified across sessions. Power Pages doesn't support *transient* identifiers.

## Does Power Pages require any specific AuthNContextClass in SAML assertion requests?

Yes. Power Pages will specify *PasswordProtectedTransport* in authentication requests, and requires that the identity provider support it.

## Does Power Pages support SAML logout request?

Yes.  Use the [Power Platform admin center](../../admin/admin-overview.md) to upload the custom certificate.  After uploading the custom certificate, copy the thumbprint of the uploaded custom certificate from the Manage custom certificate screen and paste it to site settings *Authentication/SAML2/[ProviderName]/ExternalLogoutCertThumbprint*.

### See also

[Configure a SAML 2.0 provider for Power Pages with Azure AD](saml2-settings-azure-ad.md)
[Configure a SAML 2.0 provider for Power Pages with AD FS](saml2-settings.md)
[Configure a SAML 2.0 provider for Power Pages](saml2-provider.md)

