---
title: Defense-in-Depth
description: Learn about Power Pages' enterprise grade, Defense-in-Depth security as a platform.
author: kkendrick
ms.topic: guidance
ms.custom: 
ms.date: 10/25/2022
ms.author: kkendrick
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Defense-in-Depth

Azure as a hosting platform enables Power Pages to use capabilities like elastic scaling, high availability, platform layer security, automatic infrastructure and operating systems security patching and upgrades, and advanced threat protections. Power Pages is available in many [datacenters](https://dynamics.microsoft.com/en-us/availability-reports/georeport/) around the world.

The objective of defense-in-depth is to protect information and prevent it from being accessed or stolen by those that aren't authorized to access it. A defense-in-depth strategy uses a series of mechanisms to slow the advance of an attack that aims to acquire unauthorized access to data.

Power Pages offers Defense-in-Depth by using the best of Microsoft's and Power Platform's security stack, which enables it to offer multi-layered protection from a wide variety of security threats. This multi-layered security stack improves overall security of Power Pages applications by reducing the probability of security breaches. The Power Pages platform provides makers and administrators the necessary controls to harden security and governance for their sites and data. This section describes the seven layers of protection that enable Power Pages to offer defense-in-depth as a platform.

## Physical security

Power Pages run on [Azure App service](/azure/app-service/overview), a cloud computing platform for hosting applications. Azure App service is a fully managed service with built-in infrastructure maintenance. It offers rigorous security and compliance standards. Microsoft operates the Azure data centers and manages physical security of hardware on which these applications run at locations worldwide. Only authorized personnel have access to parts of Azure data centers.

## Identity and access

Power Pages allows both anonymous and authenticated visitors to have authorized access to business data when they interact with the site. It offers a robust security model based on secure Authentication mechanisms and Authorization (via RBAC) that protect identities and access. The authentication framework is based on Microsoft Identity Platform, which offers identity-as-a-service and implements authentication and authorization with industry standard protocols OpenID Connect (OIDC), SAML 2.0, WS-Fed and OAuth 2.0. Using OAuth2.0, Power Pages enables multiple identity providers such as Microsoft, LinkedIn, Google, Facebook, Twitter, etc. Additionally, website makers can configure other enterprise Identity providers such as Azure AD, Azure AD B2C, Okta, Auth0, etc. using OpenID Connect, SAML 2.0 and WS-Fed. The [identity provider configuration](/power-apps/maker/portals/configure/use-simplified-authentication-configuration) is available for website makers to enable a wide variety of identities with Power Pages. Once authenticated, a users' access to website content and data is controlled via configurable Role-based access controls (RBAC).

Admins and makers can configure authorization for anonymous and authenticated users on Power Pages by configuring [web roles](/power-apps/maker/portals/configure/create-web-roles), [table permissions](/power-apps/maker/portals/configure/assign-entity-permissions) and [page permissions](/power-apps/maker/portals/configure/webpage-access-control). Authorization determines resources (Website Pages, Business data) that a website user (Anonymous, or Authenticated) has access to in Power Pages. Web Roles provides a way to group users, Table Permissions, and Page Permissions control and protect access to business data and website content. Makers can also [create web roles]([configure web roles](../../security/create-web-roles.md)) for custom use-cases and associate them to Table Permissions and Page Permissions for implementing granular access controls.

[Power Pages Architecture white paper](https://aka.ms/PowerPagesArchitecture) describes Authentication and Authorization in depth.

## Perimeter

Power Pages uses Azure's Distributed denial of service (DDoS) basic protection, which includes always-on traffic monitoring and real-time mitigation of common network-level attacks. Customers can also protect their Power Pages sites by purchasing and using the [standard tier](/azure/ddos-protection/types-of-attacks) of Azure DDoS protection that supplies extra capabilities to protect against volumetric attacks, protocol attacks, and application attacks.

## Network

Admins can [configure Web Application Firewall](/power-apps/maker/portals/azure-front-door) (WAF) with their Power Pages sites. WAF sits on the edge of the network and provides centralized protection of the site from common exploits and vulnerabilities, including protection from OWASP Top 10 security vulnerabilities. Power Pages can be integrated with several WAF providers. WAF integration with Power Pages enables administrators to control access to Power Pages sites from a geography, VPN, or a specific network. Power Pages also provides turn-key configurations to enable Azure WAF. With Azure WAF enabled, each Power Pages site is intelligently secured against known and new threats with security protection mechanisms that embrace a Zero Trust framework.

Site Admins can also use [IP (Internet Protocol) Address Restriction capability](/power-apps/maker/portals/admin/ip-address-restrict) in Power Pages to filter network traffic to their site, which enables admins to limit access to a list of IP addresses. When a request to the website is generated, the user's IP address is evaluated against the "allow" list. If the IP address isn't on the list, the website displays a webpage with an HTTP 403 status code. This capability can be used when website traffic originates from known networks. (for example, a corporate network)

## Compute

Power Pages run on Azure App service, which offers native protection for compute and infrastructure. The platform components of App Service, including Azure VMs (Virtual Machines), storage, network connections, web frameworks, management, and integration features, are actively secured and hardened. Microsoft Defender for Cloud is natively integrated with the Azure App service and monitors threats to underlying resources, including a complete list of MITRE ATT&CK (Adversarial Tactics, Techniques and Common Knowledge) tactics from pre-attack to command and control. It can also detect Dangling DNS. App Service goes through vigorous compliance checks on a continuous basis to make sure that:

- App resources are [secured](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox) from the other customers' Azure resources.

- Virtual Machine (VM) instances and runtime software are [regularly updated](/azure/app-service/overview-patch-os-runtime) to address newly discovered vulnerabilities.

- 24-hour threat management protects the infrastructure and platform against malware, distributed denial-of-service (DDoS), man-in-the-middle (MITM), and other threats.

## Application

Power Pages offers multiple controls and configurations that enable makers and admins to harden security at the Application layer.

### Authentication and authorization

Power Pages allows authorized users access to website content and business data. Makers can choose to configure a wide variety of [Authentication providers](/power-apps/maker/portals/configure/use-simplified-authentication-configuration) on Power Pages to allow users to sign in securely. Once a user is signed in, Power Pages checks Authorization for the user. Each anonymous or authenticated user can be granted Web roles, which can be linked with Page Permissions and Table permissions that specify what parts of the website the user can access, and what business data they interact with. can additionally be applied if granular control on Table columns is necessary. Using the authorization techniques available, a maker can choose to restrict access to certain parts of the website and data for authenticated users or groups of authenticated users than other parts of the site, which are open to the public anonymously. Power Pages offers tools like [Portal Checker](/power-apps/maker/portals/admin/portal-checker) which enables makers to uncover common configuration issues with their websites.

### HTTPS Only

Each Power Pages site comes with a digital certificate (SSL) that authenticates its identity and enables an encrypted connection between the browser and the Power Pages site. Internet traffic to Power Pages sites is encrypted and enforces HTTPS (Hyper Text Transport Protocol Secure). When branding their site with a [custom domain](/power-apps/maker/portals/admin/add-custom-domain), admins should use a secure SSL certificate and link it to their site.

### Managed application identity

Each Power Pages site uses a managed Azure Active Directory (AAD) identity, which allows it access to other Azure Active Directory-protected resources and integrations with other services like Power BI, SharePoint, Microsoft Dataverse, etc.

### HTTP security headers

[HTTP Security headers](https://owasp.org/www-project-secure-headers/#div-headers) are directives used by web applications to configure security defenses in web browsers. Power Pages offers advanced web security tightening capabilities for makers via configuration of [HTTP Security headers](/power-apps/maker/portals/configure/cors-support). The HTTP Security Headers that Power Pages honor are described below as Default and Configurable. The default headers are set by the platform for responses. Makers can configure more HTTP security headers for added security based on specific needs.

#### Default headers

|Header |Description  |
|---------|---------|
|HTTP Strict Transport Security (HSTS)     |HTTP Strict Transport Security is a web security policy mechanism that helps protect websites against protocol downgrade attacks and cookie hijacking. It allows web servers to declare that web browsers (or other complying user agents) should only interact with it using secure HTTPS connections. Power Pages use HSTS and HTTPS is enforced, which means that requests over HTTP get automatically redirected to HTTPS.         |
|Referrer-Policy    |The Referrer-Policy HTTP header governs which referrer information, sent in the Referrer header, should be included with requests made. Power Pages sets the Referrer-Policy response header for responses.         |
|Cache-Control     |This header holds directives (instructions) for caching in both requests and responses. Specifying the capability of a resource to be cached is important to prevent [exposure of information via the cache](https://cwe.mitre.org/data/definitions/525.html). Power Pages sets the Cache-control header for responses.         |
|X-Content-Type-Options    |Setting this header prevents the browser from interpreting files as a different MIME type to what is specified in the Content-Type HTTP header (for example, treating text/plain as text/CSS). Power Pages sets this header for responses.         |
|X-Frame-Options Header (XFO)   |The X-Frame-Options response header improves the protection of web applications against [clickjacking](https://portswigger.net/web-security/clickjacking). It instructs the browser whether the content can be displayed within frames. Power Pages sets this header for responses.         |

#### Configurable headers

|Header  |Description  |
|---------|---------|
|X-Frame-Options Header (XFO)     |         |
|X-Content-Type-Options    |         |
|Content Security policy (CSP)     |Content Security Policy is an extra layer of security that helps detect and mitigate certain types of web attacks such as data theft, XSS, site defacement, or the distribution of malware. CSP provides an extensive set of policy directives that help control the resources that a site page is allowed to load. Each directive defines the restrictions for a specific type of resource.<br />When CSP is turned on for a Power Pages website, it blocks connections, scripts, fonts, and other types of resources that originate from unknown or malicious sources. CSP is turned off by default in Power Pages; however, many websites might [require CSP](/power-apps/maker/portals/configure/manage-content-security-policy#configure-csp) to enhance security.         |
|Number Only Once (Nonce)    |[Enabling nonce ](/power-apps/maker/portals/configure/manage-content-security-policy#enable-nonce)(Number used once) in Power Pages blocks execution of all inline scripts except those specified within the inline script. A unique cryptographic nonce is generated and added to each script specified in the CSP header.         |
|Cross Origin Resource Sharing (CORS)     |This protocol consists of a set of headers that indicates whether a HTTP response can be shared with another domain. CORS is blocked by default on Power Pages for security. When a Power Pages site is embedded into another application, makers can [configure CORS](/power-apps/maker/portals/configure/cors-support).         |
|Cookie Security     |Power Pages use cookies to store information for various purposes. The details of various cookies used in Power Pages can be found [here](/power-apps/maker/portals/admin/portal-cookies). By default, sensitive cookies are created and set by the Power Pages server with attributes- Secure and HttpOnly. A cookie with the Secure attribute is sent to the server with an encrypted request over the HTTPS protocol, which prevents it from man-in-the-middle attacks. HttpOnly is an additional flag included in a Set-Cookie HTTP response header. Using the HttpOnly flag when generating a cookie helps mitigate the risk of client-side scripts accessing the protected cookie. With HttpOnly attribute set on cookies browsers won't reveal the cookie to a third party and thereby prevent against cookie [replay attacks](https://en.wikipedia.org/wiki/Replay_attack).<br />Makers have the flexibility to [configure SameSite Cookie](/power-apps/maker/portals/important-changes-deprecations#samesite-mode-changes) attribute as "Strict" on Power Pages to declare if cookies should be restricted to a [first-party](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies#third-party_cookies) or same-site context.         |
|Cross-Site Request Forgery (XSRF/CSRF) Protection    |Cross-site request forgery is an attack against web applications whereby a malicious web app can influence the interaction between a client browser and a web app that trusts that browser. These attacks are possible because web browsers send certain types of authentication tokens automatically with every request to a website. This form of exploit is also known as a one-click attack or session riding because the attack takes advantage of the user's previously authenticated session. Power Pages provides protection from XSRF/CSRF attacks by using anti-forgery tokens to protect writes. The anti-forgery token is a unique token that gets generated by the Power Pages backend server whenever the client requests a page and is validated by the server on every write to identify a genuine client.         |

## Data 

Protecting data is a multi-layered process and appropriate data management is a critical part of this process. Improper handling of data weakens security and creates security and privacy risks. Business data that Power Pages interact with is stored in Microsoft Dataverse, where it's [encrypted](/power-platform/admin/about-encryption) both at-rest and in transit.