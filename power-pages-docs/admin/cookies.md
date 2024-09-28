---
title: Cookies in Power Pages
description: Learn about cookies used by Power Pages.
author: nageshbhat-msft

ms.topic: conceptual
ms.custom: 
ms.date: 07/11/2024
ms.subservice: 
ms.author: nabha
ms.reviewer: danamartens
contributors:
    - nageshbhat-msft
    - neerajnandwana-msft
    - nickdoelman
---
 
# Cookies in Power Pages

A cookie is a small file sent from the web site to visitor's device by the browser. A single web session can use multiple cookies.

Power Pages also use cookies to store information for various purposes. The following table describes the cookies that Power Pages uses, and their lifetime.

| Cookie name | Description | Lifetime |
| - | - | - |
| __RequestVerificationToken | Used by the [antiforgery](/dotnet/api/system.web.helpers.antiforgeryconfig.cookiename) system. | Session |
| .AspNet.ApplicationCookie | Used to identify user sessions. A user session starts when a user browses website for the first time. And ends when the session is closed. [Configure authentication](../security/authentication/configure-site.md) can be used to change session expiry time span. | Session |
| adxPreviewUnpublishedEntities | Stores preview **ON/OFF** mode used in classic CMS system for website administrators. | Session |
| adx-notification | Used in basic form actions to store alert message to be shown on redirection. | Session |
| ARRAffinity<br />ARRAffinitySameSite | Added automatically by Azure websites and ensures that requests are load balanced between different sites. Doesn't store any of user information. You see either the  ARRAffinity or ARRAffinitySameSite cookie depending on your browser.  | Session |
| ASP.NET_SessionId | Used to maintain the session of a logged in user to avoid repeated sign-in. | Session |
| ContextLanguageCode | Stores the default language of the user accessing website within a session and across webpages. The cookie is deleted after session closes. | Session |
| Dynamics365PortalAnalytics | Critical service cookie to analyze service usage anonymously and aggregated for statistical purpose. | 90 days |
| isDSTObserved | Stores a value to indicate if the current moment is in daylight saving time. | Session |
| isDSTSupport | Indicates whether a specified date and time falls in the range of daylight saving time. | Session |
| timeZoneCode | Stores the *timezonecode* field value of *CRM timezonedefinition* table for the current timezone. | Session |
| timezoneoffset | Stores the [timezone difference](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getTimezoneOffset) between UTC and Local browser time. | Session |
| PrivateModeLoginCookie | Used to identify internal maker sessions when site is in private mode. This cookie isn't dropped once site is made public. | Session |
| OpenIdConnect.nonce.xxxxxx | Used to associate a Client session with an ID Token, and to mitigate replay attacks. | Session |
| AspNet.ExternalCookie | Used to identify user sessions in external sign in scenarios. | Session|
| WebPageCaching | This cookie is dropped for sites where the [Content Delivery Network](../configure/configure-cdn.md) is enabled. This cookie helps the CDN to identify if a page needs to be served from CDN cache or from web server. | One day |

## Frequently asked questions

### Can I deactivate some or all cookies in my Power Pages site?

No. If necessary, consider adding a consent dialog for website users through external scripts.

### Why can't I use my Power Pages site without cookies?

Cookies are required to maintain a website functional, with the purpose as described in the table.

### What does the session lifetime mean?

Cookies with the "session" lifetime are only used while the browser is open, and removed after you close the browser.

### What is the data governance policy for cookies in Power Pages?

For information about data governance, data storage and access, read [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

### Do cookies in Power Pages store any personal data?

No.

### Do cookies in Power Pages store my IP address?

No. However, check the terms of your analytics provider if you configured traffic analysis on your website. Traffic analysis can be configured through [Portal Management app](../configure/portal-management-app.md) > **Administration** > **Enable Traffic Analysis**.

