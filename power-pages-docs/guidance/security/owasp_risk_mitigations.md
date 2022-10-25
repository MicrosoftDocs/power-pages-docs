---
title: Mitigations for OWASP's top 10 risks
description: Learn how Power Pages mitigates OWASP's top 10 risks.
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

# Mitigations for the Open Web Application Security Project's top 10 risks in Power Pages

This article describes how Power Pages helps mitigate OWASP Top 10 security risks by providing core security capabilities and controls by default and the configurations and tools that are available to administrators and makers to tighten and harden security for their Power Pages sites.

## The Open Web Application Security Project (OWASP)

The [Open Web Application Security Project (OWASP)](https://owasp.org/) is a nonprofit foundation that works to improve software security. Through community-led open-source software projects, hundreds of chapters worldwide, tens of thousands of members, and leading educational and training conferences, the OWASP Foundation is the source for developers and technologists to secure the web.

## Web Application Firewall (WAF)

Each Power Pages site can be [configured with a Web Application Firewall](/power-apps/maker/portals/azure-front-door) that monitors, filters, and blocks malicious requests to the website. Web application firewall (WAF) strengthens security as it applies a set of security rules to HTTP traffic to and from an application thereby protecting applications from OWASP Top 10 security risks and common attacks, such as [SQL injection](https://en.wikipedia.org/wiki/SQL_injection), [cross-site scripting](https://en.wikipedia.org/wiki/Cross-site_scripting) (XSS), file inclusion, and improper system configuration.

Makers can integrate [Web Application Firewall (WAF)](/power-apps/maker/portals/azure-front-door) with Power Pages that monitors, filters, and blocks malicious requests to the website. Web application firewall (WAF) strengthens security as it applies a set of security rules to HTTP traffic to and from an application thereby protecting applications from OWASP Top 10 risks. Power Pages offers out of the box integration with Azure Web Application Firewall via simple configuration.

## The OWASP top 10

The [OWASP top 10](https://owasp.org/www-project-top-ten/) is a standard awareness document for developers and others who are interested in web application security. It represents a broad consensus about the most critical security risks to web applications. 

### A01:2021 Broken Access Control

Broken Access Control in any web application leaves the application susceptible to attackers who can access, modify, or delete unauthorized content or data. The attackers may also take over a web application's administration with a broken access control. Power Pages offers protection from Broken Access Control threats through five different layers of application security and control mechanisms.

#### Least Privileged Access (LPA)

Power Pages security model is built on Least Privileged Access (LPA). LPA enables customers to build applications with more granular access control where Power Pages makers can choose to specify levels of access for end users accessing the website. Makers must ensure that the principle of LPA is honored when assigning Web Roles, Table Permissions and Page Permissions to website users. The Power Pages [out of the box Administrative and Maker roles](/power-apps/maker/portals/admin/portal-admin-roles) honor LPA. Makers and admins must follow the principles of least privileged access when extending maker or administrative privileges to other users.

#### Governance Controls on Site Administration and Customization

Only entrusted makers in an organization have access to creating and authoring Power Pages Sites. Site administration and authoring aren't enabled for external users and are enforced via Microsoft Azure Active Directory Identity protection and specific security roles. Power Pages offers the following governance controls to admins:

##### Website Visibility

New Power Pages sites are Private by Default on creation to prevent unintended broader exposure of business data. When a site's visibility is set as "Private" only entrusted makers can browse the site. When a site is Private, a maker can share the site with organizational users or other makers for preview via an explicit share action. After a maker has carefully reviewed and validated business data and content on the site, they can choose to make the website visibility "Public", which makes the site available for authorized website visitors. Admins can exercise governance controls to control makers who can make sites "Public". Portal Checker detects common security misconfiguration on sites, which can be run to find and fix issues before launching a website for broader external access.

##### Website Creation

Website creation requires makers to have certain privileges and roles as documented [here](/power-apps/maker/portals/admin/portal-admin-roles). Admins can exercise [additional governance controls](/power-apps/maker/portals/control-portal-creation) if they wish to disable portal creation in a tenant by non-administrators.

#### Secure By Default

New Power Pages site's visibility is Private by Default upon creation, providing makers with flexibility and control to publish the site only when they have completed website building and fully validated website configurations. The platform also offers tools like [maintenance mode](/power-apps/maker/portals/admin/enable-maintenance-mode) to take down the site for deployments or internal maintenance operations. Out of the Box website templates, maker and admin experiences offer Secure Default configurations for features to prevent unauthorized access of any website data or configuration. Makers must confirm and test the website's configuration and review data visibility in their dev and test environments for all business use cases before they change Website Visibility as "Public". Portal Checker can be run to detect common security misconfiguration on sites. Makers can use cookie security and HTTP Security headers capabilities to prevent against common security threats like XSS, clickjacking and session thefts.

#### Secure access via authentication

Authentication Provider configuration complexity increases the probability of Authentication issues, which result in vulnerability in applications from threats due to Broken Access control. Power Pages offers an intuitive Low Code [Authentication Provider configuration](../../security/configure-portal-authentication.md) experience for Makers to securely configure a wide variety of authentication providers. Power Pages provides Out of the box integration [with Azure Active Directory (Azure AD)](/azure/active-directory/develop/v2-overview) for authentication and can be easily integrated with [other industry standard Identity providers](/power-apps/maker/portals/configure/configure-portal-authentication). 

> [!IMPORTANT]
> - While configuring Authentication providers on Power Pages makers must review their organizational security policies (Requiring Multi-Factor Auth, Session Logout, Single Log Out, etc.) and validate authentication provider configurations through testing.
> - Makers should not use deprecated functionalities like "Local Authentication" and instead use the more secure Azure AD B2C identity provider on Power Pages for external identities.

Power Pages also allows makers to make client-side calls to external APIs securely using [OAuth implicit grant flow](/power-apps/maker/portals/oauth-implicit-grant-flow).

#### Authorization via access controls

There are three major types of access control mechanisms that Power Pages offers. For each control type there are default security capabilities that are offered by Power Pages and controls for makers and admins to enable stricter security for their applications to protect sensitive data and assets.

##### Vertical access controls

Vertical access control mechanisms restrict access to sensitive application functions based on user type. Power Pages implements Vertical Access controls to offer protection against Elevation of Privilege threats. With vertical access controls, distinct types of users have access to different application functions. For example, a Power Pages website administrator can add custom branding to their Power Pages site and manage the site's lifecycle, while an ordinary user doesn't have access to perform such administrative actions. Likewise, a website maker has control to author the site and change site configurations, but these privileges aren't available to a website visitor. Website visitors, makers or admins can't elevate their privileges to undertake unauthorized actions. Makers and admins must ensure that the principle of Least privilege access is followed, and only entrusted makers or admins have access to privileged operations. Makers and admins must set well-defined limits on access that is provided to authorized users and groups. Access to unauthorized users and groups must be explicitly denied. It isn't recommended to share administrative passwords or accounts with multiple users.

##### Horizontal access controls and role based access control

Horizontal Access Control mechanisms restrict access to application resources to users who are allowed to access them. Authentication for Power Pages admin and maker experiences applies Azure Active Directory for security and protection of identities. Power Pages offer a robust security model, which is based on industry standard authentication and a role-based access control mechanism for Authorization. Requests to Power Pages sites go through the Access control layer and are denied when not authorized. Makers can utilize Web Roles, Page Permissions and Table Permissions to configure access for the website and business data for external users.

Power Pages makers must review that the site's access is enabled only for authorized users by reviewing and validating website users' [Web Role association, Table permissions, and Page permissions](../../security/power-pages-security.md). [Portal Checker](/power-apps/maker/portals/admin/portal-checker-analysis) detects common security misconfiguration on sites, which can be run before launching a website for external access.

##### Context dependent access control

Context dependent access control mechanisms restrict access to functionality and resources based on the state of the application or the user's interaction with it. They prevent a user from performing actions in the wrong order. As an example, consider a Power Pages site that allows users to provide personal information and then submit a Visa application. A maker defines this Visa application form as an [advanced form](/power-apps/maker/portals/configure/web-form-steps) on Power Pages with each step being mandatory. When a website user interacts with this multi-step form, they can't skip steps without filling in the necessary intermediate steps. Additionally, website users can't modify the data submitted on the form after submission. This is an example of context dependent access control. The extensibility of the Power Pages platform allows low code and pro-developer makers to implement context dependent access controls via custom controls, business rules, Web APIs and plugins, which can prevent website users from performing any business actions exposed on the website, in the wrong order. Out of the box solution templates and workflows honor context dependent access controls.

### A02:2021 Cryptographic Failures

Cryptographic failures risk exposure of critical or sensitive business data, which could make applications vulnerable to data leak related security threats. Power Pages allow internal or external users of organizations or governments to interact with business data. When it comes to Enterprise Security- protecting data is at the core. Data is an organization's most valuable and irreplaceable asset, and encryption serves as the last and strongest line of defense in a multi-layered data security strategy. Microsoft business cloud services and products use encryption to safeguard customer data. Power Pages and Microsoft Dataverse ensure that customer data either in transit or at rest is [encrypted](/power-platform/admin/about-encryption) using highest industry standard encryption methodologies.

#### Data in transit

Each Power Pages site is secured via HTTPS, which enables secure and encrypted communication between the users' browser, over the network, and the backend servers powering the site. Power Pages uses Transport Layer Security (TLS) to encrypt HTTP-based network traffic. HTTP requests are redirected and use of HTTPS Only is enforced. The SSL certificate that Power Pages sites use is periodically renewed and updated to conform to the highest standards of security. Admins can also configure a [custom domain](/power-apps/maker/portals/admin/add-custom-domain) for branding their sites by uploading secure SSL certificate and linking websites with custom domain.

Power Pages employs a hardened TLS configuration by using TLS 1.2 or above that enables HTTP Strict Transport Security (HSTS). It uses Strong cipher suites (ECDHE-based and NIST curves) to encrypt data and stronger ciphers are higher in the order of cipher suites presented by the platform over weak ciphers. The platform uses strong keys for encryption in transit.

#### Data at rest

The customer data that Power Pages interacts with- business data and the sites' configuration data is stored in Microsoft Dataverse- a secure business data store. Dataverse databases use SQL Server TDE (Transparent Data Encryption), compliant with FIPS (Federal Information Processing Standards) 140-2 to provide real-time I/O encryption and decryption of the data and log files for data encryption at-rest. [Azure Storage Encryption](/azure/storage/common/storage-service-encryption) is used for data at rest stored in the Azure Blob Storage. These are encrypted and decrypted transparently using 256-bit AES (Advanced Encryption Standard) encryption compliant with FIPS 140-2. 

The data stored in Dataverse is distributed across different storage types:

- Azure SQL Database for relational data

- Azure Blob storage for binary data, such as images and documents

- Azure Search for search indexing

- Microsoft 365 Activity Log and Azure Cosmos DB for audit data

By default, Microsoft stores and manages the database encryption key for Power Platform environments.

Microsoft provides an extra ability to [encrypt data](/power-platform/admin/data-encryption) in Dataverse with customer provided encryption key. As of now, given the heterogenous storage, the customer managed key feature is available only for the Azure SQL database that stores transactional data.

### A03:2021 Injection

[Injection](https://owasp.org/Top10/A03_2021-Injection/) is an attacker's attempt to send data to an application in a way that changes the meaning of commands being sent to an interpreter. For example, the most common example is SQL injection, a SQL injection attack consists of insertion or "injection" of a SQL query via the input data from the client to the application.

Power Pages uses industry-standard best practices to prevent injection attacks. Power Pages product development follows [Microsoft's standard](https://www.microsoft.com/en-us/securityengineering/sdl/practices) SDLC patterns, which involve a full Software Development Cycle review every six months spanning the entire product.

In addition, the following security strategies enable Power Pages to mitigate risks from Injection flaws:

- Server-side sanitization and validation of input data and user data, the output data is also sanitized with server-side validations before it's rendered

- HTML input and output data are HTML encoded

- Power Pages uses safe APIs with parameterized interfaces

- Static and dynamic analysis tools are used during build time to detect security bugs at source

- Periodic assessment of Threat Model on new capability releases or every six months, whichever falls earlier

The following tools are available to makers to protect against injection flaws:

- Enable Azure Web Application Firewall with Power Pages.

- Makers must ensure that html encoding is applied for custom components. When working with [Liquid](/power-apps/maker/portals/liquid/liquid-overview) objects to read untrusted data, use of [escape filter](/power-apps/maker/portals/liquid/liquid-filters#escape) is recommended.

- When reading URL parameters using JavaScript, makers should apply html encoding to prevent Cross-site scripting.

- When working with Web APIs on Power Pages, makers must apply html encoding on the API response before using the data returned.

- Enable Content Security Policy and Nonce for extra security.

### A04:2021 Insecure Design

[Insecure design](https://owasp.org/Top10/A04_2021-Insecure_Design/) is a broad category representing different weaknesses, expressed as "missing or ineffective control design." There's a difference between insecure design and insecure implementation. A secure design can still have implementation defects leading to vulnerabilities that may be exploited. An insecure design can't be fixed by a perfect implementation as by definition, needed security controls were never created to defend against specific attacks.

Power Pages is built on the culture and methodology of secure design. Both culture and methodology are constantly reinforced through Microsoft's industry-leading [Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl/practices) (SDL) and [Threat Modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) practices, which constantly evaluate threats and ensures that code is robustly designed and tested to prevent known attack methods. New features and services on Power Pages periodically go through Threat modeling. The Threat Modeling review process ensures that threats that are identified during the design phase are mitigated and validated periodically.

Threat Modeling also accounts for changes to services that are already live through continuous regular reviews. Relying on the [STRIDE](/azure/security/develop/threat-modeling-tool-threats#stride-model) model helps Microsoft address the most common issues with insecure design.

Microsoft performs periodic security and penetration testing to detect vulnerabilities in services and applications. The penetration testing reports can be [downloaded](https://servicetrust.microsoft.com/viewpage/PenTest) from Microsoft Trust center.

### A05:2021 Security Misconfiguration

Attackers often try to exploit unpatched flaws or access default accounts, unused pages, unprotected files, and directories, etc. to gain unauthorized access or knowledge of the system.

Power Pages offers protection against [security misconfigurations](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/) using the following methods:

- Most new capabilities and configurations are set to "off" by default to uphold a "Default Deny" Design principle. Customers need to review and opt for new features and configurations.

- The Power Pages "Secure by Default" approach ensures that any new capability doesn't compromise application security once deployed or enabled.

- Backend servers where Power Pages are deployed worldwide are periodically patched and updated to prevent any security vulnerabilities.

- Since Power Pages follows Microsoft SDLC, open source, or third-party software and components used are periodically reviewed and updated to harden the application's security against flaws.

- Power Pages runs on Azure Platform as a Service (PaaS). Microsoft Defender protects the hosting infrastructure and monitors applications for a wide variety of threats like MITRE Att&CK (Adversarial Tactics, Techniques and Common Knowledge) tactics and Dangling DNS detection.

- Files and directories hosted on backend servers and the infrastructure hosting the servers themselves are locked to prevent unauthorized or unintended access.

Additionally, makers can use [Portal Checker](/power-apps/maker/portals/admin/portal-checker) to identify and address common configuration errors leading to insecure configurations. Before Power Pages Go-live, Authentication Provider and Authorization configuration on Power Pages sites can be reviewed to ensure that website content and data can be accessed only via authorized users.

### A06:2021 Vulnerable and Outdated Components

Power Pages follows [Microsoft's SDL practices](https://www.microsoft.com/en-us/securityengineering/sdl/practices) to manage[open-source and third-party components](https://www.microsoft.com/securityengineering/opensource) and libraries, preventing [vulnerable and outdated components](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/) by maintaining complete inventory, performing security analyses, keeping the components and libraries up to date, and aligning the components with a tried and tested security incident response process. Azure, the hosting platform for Power Pages, provides periodic and automatic operating System patching and keeps the underlying infrastructure protected.

Customers who utilize external open source or third-party libraries and components with Power Pages should perform similar periodic assessments and update vulnerable or outdated components and libraries.

### A07:2021 Identification and Authentication Failures

Power Pages prevents [identification and authentication failures](https://owasp.org/Top10/A07_2021-Identification_and_Authentication_Failures/) by allowing both anonymous and authenticated website users to interact with business data and processes securely. When it comes to securing identities, confirmation of the user's identity, authentication, and session management are critical to protect against authentication-related attacks.

Power Pages is built on Microsoft's Identity Platform and provides out of the box integration with Azure Active Directory (AD) for identification and authentication. Azure AD and Azure AD B2C helps Power Pages to enable [security features](https://azure.microsoft.com/services/active-directory/#features) for authenticated users. These features include single sign-on, single sign out, multi-factor authentication, session management, session timeouts and a single platform to engage with internal and external users more securely.

Power Pages can also be configured with other industry standard Identity and Authentication providers. When using providers other than the Out of Box providers, makers must ensure that the Identity Provider configuration meets the security policies of their organizations.

### A08:2021 Software and Data Integrity Failures

[Software and data integrity failures](https://owasp.org/Top10/A08_2021-Software_and_Data_Integrity_Failures/) relate to code and infrastructure that doesn't protect against integrity violations. An example of this is where an application relies upon plugins, libraries, or modules from untrusted sources, repositories, and content delivery networks (CDNs).

- Microsoft employs a Component Governance process for Microsoft managed repositories that enforce secure configuration of package source files to maintain software integrity.

- The process ensures that only internally sourced packages are served to address [substitution attack](https://azure.microsoft.com/resources/3-ways-to-mitigate-risk-using-private-package-feeds/). Substitution attack, also known as dependency confusion, is a technique that can be used to poison the app-building process inside secure enterprise environments.

- Encrypted data has integrity protection applied before it's transmitted. Integrity protection metadata present for incoming encrypted data is validated.

Makers building Power Pages sites must ensure that they use trusted sources for utilizing open-source or third-party libraries, components, and APIs on their site. Customers can protect their internal application repositories by restricting corporate access and running static and dynamic security analysis tools. Out of the box templates, data and integrations in Power Pages are [penetration tested](https://en.wikipedia.org/wiki/Penetration_test) periodically. It's recommended that customers [perform penetration testing](/azure/security/fundamentals/pen-testing) on their Power Pages sites especially when their implementation involves use of third party libraries or external APIs.

### A09:2021 Security Logging and Monitoring Failures

Logging and monitoring are critical ways to detect, escalate, and respond to active security breaches. Customers can prevent risks from Security logging failures on Power Pages by using [audit logging capabilities](/power-platform-release-plan/2022wave1/power-apps-portals/portals-audit-logging-365-compliance-center) that the platform offers. With Audit logging, Power Pages logs failed sign-in transactions and server-side input validation failures to identify suspicious or malicious attempts. Makers or admins can configure audit logging and can download detailed activity logs for Power Pages website from Microsoft 365 Compliance center.

Microsoft implements a Standardized Security Incident Response Process (SSIRP) which is [Microsoft's incident response process](https://msrc-blog.microsoft.com/2019/06/27/inside-the-msrc-anatomy-of-a-ssirp-incident/#:~:text=SSIRP%20is%20our%20incident%20response,that%20could%20be%20used%20to) for responding to major threats to our customers, including exploits in the wild that are being used to attack customers, threats to the security of Microsoft's services like Azure, Dynamics, Power Platform and O365, and the public disclosure of unpatched vulnerabilities that could be used to attack customers. Microsoft's SSIRP enables Microsoft to respond to active security breaches.

[Application insights](/azure/azure-monitor/app/app-insights-overview) is widely used within the enterprise landscape for monitoring and diagnostics. Makers can [integrate](/azure/azure-monitor/app/javascript?tabs=snippet#snippet-based-setup) Power Pages sites with Azure Application Insights for advanced monitoring, diagnostics, and performance insights.

### A10:2021 Server Side Request Forgery (SSRF)

[Server Side Request Forgery (SSRF) failures](https://owasp.org/Top10/A08_2021-Software_and_Data_Integrity_Failures/) occur whenever a web application is fetching a remote resource without validating the user-supplied URL. It allows an attacker to coerce the application to send a crafted request to an unexpected destination, even when protected by a firewall, VPN, or another type of network access control list (ACL). Power Pages offers protection from SSRF attacks by:

- Enforcing URL schemas

- Validating and sanitizing user inputs and liquid request objects (user and request)

- Avoiding sending a raw response body from Server to client

Makers implementing Power Pages sites must ensure that they follow the principles above when creating advanced custom implementations and controls on Power Pages.