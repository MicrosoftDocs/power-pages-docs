---
title: Power Pages security best practices
description: Power Pages security uses a layered model covering identity, pages, data, APIs, code, and network controls. Learn the security best practices.
author: shwetamurkute
ms.author: bipuldeora
ms.reviewer: smurkute
ms.date: 09/04/2026
ms.topic: concept-article
---

# Apply security best practices to your Power Pages site

Power Pages provides a range of security capabilities that help protect sites, data, and users. However, the site's security also depends on how you configure and maintain these capabilities.
This guidance outlines recommended security practices for Power Pages makers and administrators. The recommendations are organized across key areas including identity and authentication, access to data and APIs, application security, site and network protection, and governance to help you build and maintain secure Power Pages sites.

> [!NOTE]
> Use this guidance alongside your organization's security policies and requirements. Review the recommendations based on your site's data, users, integrations, and security requirements.


## Identity and authentication

Authentication verifies the identity of a site user. A secure authentication design also controls registration, identity mapping, session duration, and sign-out behavior.

- **External identity providers**: Don't use Power Pages local authentication for production sites. Use a supported external identity provider for production authentication. Use local authentication for development, testing, or demonstration scenarios, as appropriate. 

- **Identity provider access policies**: Configure access policies in the identity provider. Use identity provider security features, such as multifactor authentication (MFA), risk-based access, location restrictions, or device compliance requirements. Test policies before enforcing them.

- **Registration control**: Disable open registration when you need to control access. Open registration is enabled by default and allows anonymous visitors to create an account without an invitation. For sites that require controlled access, disable open registration and require users to be explicitly invited or provisioned before they can access the site. 

- **Identity mapping**: Use stable identity mapping for external users. By default, Power Pages associates external users with contacts by using a stable identity identifier. Keep `AllowContactMappingWithEmail` disabled unless email-based mapping is required. Because email addresses can change or be reassigned, they shouldn't be used as a permanent identity identifier.

- **Token data minimization**: Use the UserInfo endpoint to retrieve additional user attributes. When the identity provider supports it, use the UserInfo endpoint to obtain user attributes instead of adding unnecessary claims to the ID token. Use validated ID token claims only for authentication and user identification.

- **Session timeout**: Configure session expiration based on the sensitivity of the site. Set an appropriate Power Pages session timeout and consider the identity provider's session and token lifetime separately. Ensure that authentication sessions don't remain valid longer than permitted by the organization's security requirements.

- **Sign-out**: Enable external logout when required by the site's security requirements. For sites using an external identity provider, configure logout so that signing out of Power Pages also terminates the relevant identity-provider session where supported. 

- **Provider governance**: Govern which external identity providers makers can configure. Where available, restrict sites to organization-approved identity providers and prevent makers from introducing unapproved authentication methods.

## Authorization for pages, data, and APIs

Power Pages authorization controls determine which pages users can view and which Dataverse records they can access or change. Web roles, page permissions, table permissions, column security, and API configuration are related parts of a single authorization model.

- **Effective web-role permissions**: Review and validate permissions assigned to default web roles. The **Authenticated Users** and **Anonymous Users** roles apply broadly to their respective user categories. Ensure these roles grant only the minimum access required and don't provide unintended access to pages, tables, or other resources. 

- **Page permissions**: Configure page permissions for every page that shouldn't be publicly accessible. Use page permissions to control who can view the page. Hiding a page from navigation doesn't secure it.

- **Relationship-based table permissions**: Use relationship-based table permissions for business data. Prefer Contact, Account, Self, Parent/child, or supported custom access patterns so that access to Dataverse records is enforced server-side.

- **Global access**: Avoid global table permissions for sensitive business data. Global access grants the associated web roles access to all records in the table. This risk is amplified when the table is exposed through the Web API. When users require filtered or business-specific access, use relationship-based table permissions or server-side logic that enforces the required authorization and filtering rather than exposing the table broadly through the Web API.

- **Anonymous table permissions**: Treat anonymous table permissions as public data access. Don't grant anonymous users create, read, update, or delete access unless the business requirement explicitly calls for public access.

- **Server-side enforcement**: Don't rely on client-side or presentation-layer filtering for authorization. User can bypass or modify JavaScript filters. Use table permissions or other server-side authorization controls to ensure that unauthorized Dataverse records aren't returned. Use client-side filtering only to control how data is displayed, not as a security boundary.

- **Web API exposure**: Enable the Power Pages Web API only for required tables and explicit columns. For each exposed table, enable the API only when required and specify an explicit allow list of columns.

- **Column-security model**: Apply the appropriate column security model. Use Power Pages column permissions for the Web API authorization model. When enhanced authorization is enabled, use Dataverse column security profiles instead.

- **Sensitive data exposure**: Review sensitive data exposure across search and other rendering paths. Don't assume that Web API column permissions protect data exposed through search, Liquid, FetchXML, forms, lists, or other server-side rendering paths. Avoid exposing sensitive columns through these paths unless explicitly required.

## Secure applications and custom code

Custom code and external integrations extend the site's capabilities, but they can also introduce browser-side and server-side security risks.

- **Secrets management**: Never expose secrets in browser-delivered content. Keep access tokens, connection strings, SAS tokens, credentials, and privileged API keys out of JavaScript, content snippets, web files, and any other content delivered to the browser.

- **CAPTCHA protection**: Enable CAPTCHA on forms that accept anonymous submissions. Use CAPTCHA to protect public registration, contact, feedback, application, and other anonymous forms from automated abuse. For higher-risk or high-volume scenarios, consider a custom CAPTCHA provider that meets the site's security, accessibility, and compliance requirements.

- **Built-in validation protections**: Don't disable Power Pages validation and sanitization protections. Keep request validation, web template validation, and Safe HTML validation enabled to help protect the site from malicious or unintended content.

- **Safe data rendering**: Treat all data that you render on a page as untrusted. Sanitize and safely encode data before rendering it through JavaScript or Liquid. Don't use unsafe rendering patterns such as `innerHTML` with untrusted data or the Liquid raw filter.

- **CSRF protection**: Always enforce CSRF protection for data-changing requests. Include the required Power Pages request-verification token with POST, PUT, PATCH, and DELETE requests. Use `shell.safeAjax` or another supported mechanism to include and validate the token correctly.

- **Server Logic authorization**: Secure Server Logic operations with server-side authorization. Assign each Server Logic operation only to the web roles that require it, validate inputs within the server-side code, and enforce appropriate table permissions or equivalent authorization before accessing, modifying, or returning Dataverse data.

- **File download security**: Protect and test file downloads. Use table permissions to ensure that only authorized users can retrieve files, and test direct download URLs with anonymous and unauthorized users. For sensitive files, use appropriate cache-control settings to prevent unintended caching.

- **Trusted script and style sources**: Load custom scripts and styles only from controlled, trusted sources. Prefer Power Pages web files or reviewed, fixed-version resources from trusted locations. Avoid unreviewed third-party scripts, libraries, and CDN resources.

- **Power Automate flow access**: Use the Power Pages trigger when invoking Power Automate flows from a Power Pages site. Avoid exposing Power Automate flows through generic HTTP request triggers when the flow is intended to be called from Power Pages. Configure the flow's web-role access to allow only the users who need to invoke it.

- **Least privilege**: Apply least privilege to Server Logic and Power Automate flows. Ensure that the identities and connections used by Server Logic and downstream Power Automate operations have only the permissions required to perform the operation.

## Protect the site and its traffic

Layered browser and network controls reduce exposure to common web attacks and prevent data leakage.

- **Web Application Firewall (WAF) protection**: Enable and maintain WAF protection for production sites where supported. Enable managed rules and appropriate bot-protection rules. Use custom WAF rules or rate-limiting controls for IP-, geography-, request-, or rate-based restrictions when required by the site's threat model or business requirements.

- **WAF rule management**: Review WAF logs before modifying managed rules. Investigate false positives and legitimate Power Pages behavior before disabling a rule. Document and periodically review any exceptions.

- **Content Security Policy (CSP)**: Enable and maintain an appropriate Content Security Policy (CSP). Use CSP to restrict scripts, styles, frames, images, and API connections to required sources. Test changes in development, review violations, and enforce the policy after validating required site functionality.

- **CSP minimization**: Minimize CSP allowances. Remove unnecessary wildcards and allow only the sources required by the site. Avoid unnecessary `unsafe-eval`. If it's currently required for site functionality, retain it only where necessary and review its use as platform support evolves.

- **HTTP security headers**: Set protective HTTP security headers. Use `X-Frame-Options` with a value of `SAMEORIGIN` or `DENY` unless an approved embedding scenario requires otherwise, and set `X-Content-Type-Options` to `nosniff`.

- **Authentication cookie settings**: Use an appropriate SameSite setting for authentication cookies. Use `Lax` when it's compatible with the site's authentication and integration requirements. Avoid `None` unless cross-site scenarios require it, and use `Strict` as appropriate for highly sensitive scenarios.

- **CORS restrictions**: Restrict CORS to approved origins. Allow only specific trusted origins for cross-origin access. Don't use wildcard origins for authenticated or sensitive scenarios, and don't combine credentialed requests with wildcard origins.

- **SSL/TLS certificates**: Use managed SSL/TLS certificates where supported. Prefer certificate management that automatically renews certificates where possible, and monitor certificates that require manual renewal to prevent expiration and site-availability issues.

- **Cached content protection**: Protect cached content from user-specific data leakage. Keep shared header and footer caching enabled as appropriate, but isolate dynamic user-specific Liquid in the supported substitution mechanism. Don't run user-specific Dataverse queries directly in shared cached content.

## Govern and maintain a secure environment

Maintain security through controlled development, deployment, administration, and retirement processes.

- **Non-production site privacy**: Keep development and test sites private. Don't make a site public until you review identity, page, data, API, form, and browser security configurations.

- **Production administration**: Restrict production security configuration to designated administrators. Limit who can change site visibility, identity providers, web roles, page permissions, table permissions, site settings, Server Logic, and production content.

- **Controlled Application lifecycle management (ALM)**: Use supported ALM processes for Power Pages configuration. Deploy configuration through supported solutions and controlled application lifecycle processes. Avoid unmanaged production changes that can't be reviewed or reproduced.

- **Environment separation**: Keep production data and secrets out of development and test environments. Don't copy production secrets or unnecessary personal or sensitive data into lower environments. Use appropriate test data and environment-specific secrets, and store secrets in environment variables.

- **Security recommendations**: Monitor and act on Microsoft security recommendations. Regularly review security recommendations and alerts surfaced through Microsoft administration and security experiences, and address applicable findings promptly.

- **Ongoing security reviews**: Repeat the security review after material configuration changes. Re-review authentication, registration, web roles, page permissions, table permissions, Web API fields, search, Server Logic, upload controls, and external integrations after changes that could alter the security boundary.

- **Obsolete configuration**: Remove obsolete configuration. Delete unused pages, forms, permissions, identity providers, APIs, credentials, server logic, and integrations when they're no longer required. Avoid leaving obsolete security configurations inactive where they could be reactivated.

- **Auditing**: Configure Dataverse auditing for sensitive data. Audit tables and columns that require traceability and regularly review audit data according to established retention and compliance requirements.

## Use security tools to continuously monitor and improve security

Security reviews aren't limited to the initial launch. Power Pages security and governance capabilities find configuration issues and track remediation.

- **Power Pages Security Scan**: Use Power Pages Security Scan to identify security vulnerabilities. Run Security Scan periodically and after significant security changes to identify common vulnerabilities and configuration issues. Review the scan results and address material findings by using the recommended remediation guidance.

- **Security Hub**: Use Security Hub in the Power Platform admin center to monitor security scan coverage and findings across sites. Review site-specific findings, identify sites that you didn't scan, initiate scans, and share remediation recommendations with site owners and makers.

- **Security agent**: Use Security Agent to review and remediate security issues. Use the AI-powered agent to review the site's security posture, analyze configuration and scan findings, explain prioritized risks, and provide guided remediation. Review and approve proposed configuration changes before they're applied.

- **End-to-end security review**: Use the Power Pages security skills to perform an end-to-end security review. Use the Power Pages security review skill to assess the site's security posture across authentication, permissions, browser security, firewall configuration, and other security controls, and consolidate findings into a single review with prioritized remediation guidance.

- **Governance and DLP controls**: Use Power Platform governance and DLP controls to prevent security and data-protection risks. Apply appropriate environment and DLP policies to control connectors, data movement, and other capabilities in accordance with organizational security requirements.

## Related content


- [Power Pages security](power-pages-security.md)
- [Power Pages security FAQ](faq.yml)
