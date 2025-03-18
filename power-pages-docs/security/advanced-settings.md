---
title: Advanced Settings (preview)
description: Explore advanced security settings in Power Pages design studio to protect your site content and data from potential threats.
author: dmartens
ms.topic: conceptual
ms.date: 05/17/2024
ms.subservice:
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:05/17/2024
---

# Advanced settings (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Security workspace allows you to further protect your site content and data from security threats, directly from Power Pages design studio. Use Advanced settings to configure HTTP headers of your site quickly and efficiently, configure Content Security Policy (CSP), Cross Origin Resource Sharing (CORS), cookies, permissions, and more.

> [!IMPORTANT]
>
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

1. Sign into Power Pages, and open your site for editing.
1. Select **Security Workspace** from left navigation, and then, choose **Advanced settings (preview)**.

## Configure Content Security Policy (CSP)

Content Security Policy (CSP) is used by web servers to enforce a set of security rules for a web page. It helps protect sites from various types of security attacks like cross-site scripting (XSS), data injection, and other code injection attack.

### Directives

The following directives are supported.

| **Directive** | **Description** |
|-------------------------|-------------------------|
| Default source | Specifies the default source for content not explicitly defined by other directives. It acts as a fallback for other directives. |
| Image source | Specifies valid sources for images. Controls the domains from which images can be loaded. |
| Font source | Specifies valid sources for fonts. Used to control the domains from which web fonts can be loaded. |
| Script source | Specifies valid sources for JavaScript code. The script source can include specific domains, 'self' for the same origin, 'unsafe-inline' for inline scripts, and 'nonce-xyz' for scripts with a specific nonce. Choose to enable nonce or inject unsafe eval.<br />Learn more at [Manage your site's Content Security Policy: Turn on nonce](manage-content-security-policy.md#turn-on-nonce) |
| Style source | Specifies valid sources for stylesheets. Similar to script-src, it can include domains, 'self', 'unsafe-inline', and 'nonce-xyz'. |
| Connect source | Specifies valid sources for XMLHttpRequest, WebSocket, or EventSource. Controls the domains to which the page can make network requests. |
| Media source | Specifies valid sources for audio and video. Used to control the domains from which media resources can be loaded. |
| Frame source | Specifies valid sources for frames. Controls the domains from which the page can embed frames. |
| Frame Ancestors | Specifies valid sources that can embed the current page as a frame. Controls which domains are allowed to embed the page. |
| Form Action | Specifies valid sources for form submissions. Defines the domains to which form data can be sent. |
| Object source | Specifies valid sources for the object element's resources, such as Flash files or other embedded objects. It helps control from which origins these objects can be loaded. |
| Worker source | Specifies valid sources for web workers, including dedicated workers, shared workers, and service workers. It helps control from which origins these worker scripts can be loaded and executed. |
| Manifest source | Specifies valid sources for web workers, including dedicated workers, shared workers, and service workers. It helps control from which origins these worker scripts can be loaded and executed. |
| Child source | Specifies valid sources for web workers, including dedicated workers, shared workers, and service workers. It helps control from which origins these worker scripts can be loaded and executed. |

For each directive, you can either choose specific URL, all domains, or none.

For advanced configuration, go to [Manage your site's Content Security Policy: Set your site's CSP](manage-content-security-policy.md#set-your-sites-csp).

## Configure Cross-Origin Resource Sharing (CORS)

Cross-Origin Resource Sharing (CORS) is used by web browsers to allow or restrict web applications that run in one domain to request and access resources from another domain.

### Directives

The following directives are supported.

| **Directive** | **Description** | **Value(s)** |
|-------------------------|-------------------------|-------------------------|
| Allow accessing resources from the server | Also known as Access-Control-Allow-Origin, helps the server decide which origins are allowed to access its resources. Origins can be domains, protocols, and ports. | Choose domain URLs |
| Send headers during server requests | Also known as Access-Control-Allow-Headers, helps define the headers that can be sent in requests from a different origin to access resources on the server. | Choose specific headers with following permissions</br>Origin</br>Accept</br>Authorization</br>Content – type |
| Expose header values in client-side code | Also known as Access-Control-Expose-Headers, this directive instructs the browser on which response headers should be exposed and made accessible to the requesting client-side code in cross-origin requests. | Choose specific headers with following permissions</br>Origin</br>Accept</br>Authorization</br>Content – type |
| Define methods to access resources | Also known as Access-Control-Allow-Methods, helps define which HTTP methods are allowed when accessing resources on a server from a different origin. | GET - Requests data from a specified resource</br>POST - Submits data to be processed to a specified resource</br>PUT - Updates or replaces a resource at a specific URL</br>HEAD -Same as GET but retrieves only the headers and not the actual content</br>PATCH - Partially modifies a resource</br>OPTIONS - Requests information about the communication options available for a resource or server</br>DELETE - Deletes the specified resource |
| Specify duration for caching request results | Also known as Access-Control-Max-Age, helps define the duration for which a preflight request's results can be cached by the browser. | Specify duration in times (seconds) |
| Allow site to share credentials | Also known as Access-Control-Allow-Credentials, helps define if the site can share credentials like cookies, authorization headers, or client-side SSL certificates during cross-origin requests. | Yes/No |
| Display webpage as an iFrame from same origin | Also known as X-Frame-Options, allows the page to be displayed in an iframe only if the request comes from the same origin. | Yes/No |
| Block MIME sniffing | Also known as X-Content-Type-Options: no-sniff, this helps prevent web browsers from performing MIME type (content-type) sniffing or guessing the content type of a resource. | Yes/No |

## Configure cookies (CSP)

The Cookie header in an HTTP request contains information about cookies previously stored by a website in your browser. When you visit a website, your browser sends a Cookie header containing all relevant cookies associated with that site back to the server.

### Directives

The following directives are supported.

| **Directive**                       | **Description**                                                                                                                                                                          | **Header**                                                        |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| Transfer rules for all cookies      | Control how cookies are sent with cross-origin requests. It's a security feature aimed at mitigating certain types of cross-site request forgery (CSRF) and information leakage attacks. | This setting corresponds to the header SameSite/Default.          |
| Transfer rules for specific cookies | Control how cookies are sent with cross-origin requests. It's a security feature aimed at mitigating certain types of cross-site request forgery (CSRF) and information leakage attacks. | This setting corresponds to the header SameSite/Specific cookie. |

## Configure Permissions-Policy (CSP)

The Permissions-Policy header allows web developers to control which web platform features are allowed or denied on a web page.

### Directives 

The following directives are supported and control access to their respective APIs.

:::row:::
   :::column span="11":::
      - Accelerometer<br />
      - Ambient-Light-Sensor<br />
      - Autoplay<br />
      - Battery<br />
      - Camera<br />
      - Display<br />
      - Document-Domain<br />
      - Encrypted-Media<br />
      - Execution-While-Not-Rendered<br />
      - Execution-While-Out-Of-Viewport<br />
      - Fullscreen<br />
      Gamepad
   :::column-end:::
   :::column span="11":::
      - Geolocation<br />
      - Gyroscope<br />
      - Hid<br />
      - Identity-Credentials-Get<br />
      - Idle-Detection<br />
      - Local-Fonts<br />
      - Magnetometer<br />
      - Microphone<br />
      - Midi<br />
      - Otp-Credentials<br />
      - Payment
   :::column-end:::
   :::column span="11":::
      - Picture-In-Picture<br />
      - Publickey-Credentials-Create<br />
      - Publickey-Credentials-Get<br />
      - Screen-Wake-Lock<br />
      - Serial<br />
      - Speaker-Selection<br />
      - Storage-Access<br />
      - Usb<br />
      - Web-Share<br />
      - Window-Management<br />
      - Xr-Spatial-Tracking
   :::column-end:::
:::row-end:::

## Configure more HTTP Headers

### Allow secure connection over HTTPS

The setting corresponding to the HTTP Strict-Transport-Security header informs the browser that it should only connect to the website over HTTPS, even if the user enters "http://" in the address bar. It helps prevent man-in-the-middle attacks by ensuring that all communication with the server is encrypted and protect against certain types of attacks, such as protocol downgrade attacks and cookie hijacking.

> [!NOTE]
> For security reasons, this setting can't be modified.

### Include referrer information in HTTP headers

The Referrer-Policy HTTP header is used to control how much information about the origin of the request (referrer information) is disclosed in the HTTP headers when a user navigates from one page to another. This header helps control privacy and security aspects related to referrer information.

| **Value**                     | **Description**                                                                                                                                                  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| No referrer                   | No-referrer means that no referrer information is sent in the headers. This setting is the most privacy-conscious option.                                        |
| No Referrer When Downgrade    | It sends the full referrer information when navigating from an HTTPS to an HTTP site but only the origin (no path or query) when navigating between HTTPS sites. |
| Same Origin - Referrer-Policy | Same-origin sends the full referrer information only when the request is to the same origin. For cross-origin requests, only the origin is sent.                 |
| Origin                        | Origin sends the origin of the referrer, but no path or query information, both for same-origin and cross-origin requests.                                       |
| Strict Origin                 | Similar to origin, but only sends referrer information for same-origin requests.                                                                                 |
| Origin When Cross-Origin      | Similar to origin, but only sends referrer information for same-origin requests.                                                                                 |
