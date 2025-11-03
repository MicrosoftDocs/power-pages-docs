---
title: Cookies in Power Pages
description: Learn about cookies used by Power Pages.
author: nageshbhat-msft

ms.topic: concept-article
ms.custom: 
ms.date: 07/11/2024
ms.subservice: 
ms.author: nabha
ms.reviewer: danamartens
contributors:
    - nageshbhat-msft
    - neerajnandwana-msft
---
 
# Cookies in Power Pages

A cookie is a small file sent from the web site to visitor's device by the browser. A single web session can use multiple cookies.

Power Pages use cookies that are required for the website to function properly. These essential cookies store information necessary to support core site operations and ensure a seamless user experience. The following table describes the cookies that Power Pages uses, and their lifetime.

| Cookie name | Description | Lifetime |
| - | - | - |
| __RequestVerificationToken | Security cookie used by the [ASP.NET anti-forgery](/dotnet/api/system.web.helpers.antiforgeryconfig.cookiename) system to validate that requests are genuine and not forged. Protects against Cross-Site Request Forgery (CSRF) attacks. | Session |
| .AspNet.ApplicationCookie | Authentication cookie that maintains the user’s login session across pages. Ensures users remain signed in during navigation. [Configure authentication](../security/authentication/configure-site.md) can be used to change session expiry time span. | Session |
| adx-notification | Temporarily stores short success or alert messages (e.g., “Form submitted successfully”) after user actions such as form submission. Ensures feedback messages are displayed correctly after redirects. | Session |
| ARRAffinity<br />ARRAffinitySameSite | Azure Infrastructure cookie to route a user’s session consistently to the same server. Prevents session interruptions and ensures reliability. You see either the  ARRAffinity or ARRAffinitySameSite cookie depending on your browser. | Session |
| ContextLanguageCode | Stores the user’s language preference for browsing the site. Users can change their preference through the language selector (dropdown) in the website header. Ensures consistent display of pages in the selected language. | Session |
| Dynamics365PortalAnalytics | Used to uniquely distinguish one site visitor from another without storing any personal data or user identity. This cookie is essential for delivering reliable, secure, and maintainable service functionality across multiple Power Pages features. | 90 days |
| isDSTObserved | Stores a value indicating whether Daylight Saving Time (DST) is currently in effect for a user’s location. Ensures that displayed date/time values correctly reflect seasonal adjustments. | Session |
| isDSTSupport | Indicates whether a specific date and time falls within Daylight Saving Time. Ensures the system can correctly calculate and display dates that occur during DST periods. | Session |
| timeZoneCode | Stores the user’s current time zone code, mapped to *timezonecode* field value of *Dataverse timezonedefinition* table. Allows the site to display and process dates/times in the user’s local time zone. | Session |
| timezoneoffset | Stores the [timezone difference](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getTimezoneOffset) between Coordinated Universal Time (UTC) and the user’s local device time. Used to align displayed times with the user’s actual local offset. | Session |
| PrivateModeLoginCookie | Identifies internal website maker sessions when the site is in private mode (development). This cookie isn't dropped once site is made public. | Session |
| OpenIdConnect.nonce.xxxxxx | Security cookie linking client session to ID token. Prevents replay attacks during authentication. | Session |
| AspNet.ExternalCookie | Used to identify user sessions in external sign in scenarios. Ensures secure session continuity. | Session|
| WebPageCaching | This cookie is dropped for sites where the site administrator enables the Microsoft First Party [Content Delivery Network](../configure/configure-cdn.md) feature in Power Pages. This cookie helps the CDN to identify if a page needs to be served from CDN cache or from web server. | One day |

## Frequently asked questions

### Can I deactivate some or all cookies in my Power Pages site?

No. If necessary, consider adding a consent dialog for website users through external scripts.

### Why can't I use my Power Pages site without cookies?

Essential cookies are required for your Power Pages site to function properly. These cookies enable core features and maintain the website’s basic operations, as described in the table. Without them, the site cannot work as intended.

### What does the session lifetime mean?

Cookies with the "session" lifetime are only used while the browser is open, and removed after you close the browser.

### What is the data governance policy for cookies in Power Pages?

For information about data governance, data storage and access, read [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

### Do cookies in Power Pages store any personal data?

No.

### Do cookies in Power Pages store my IP address?

No. However, check the terms of your analytics provider if you configured traffic analysis on your website. Traffic analysis can be configured through [Portal Management app](../configure/portal-management-app.md) > **Administration** > **Enable Traffic Analysis**.

