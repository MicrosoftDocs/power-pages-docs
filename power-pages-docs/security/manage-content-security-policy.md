---
title: Manage your site's Content Security Policy
description: Learn how to manage the Content Security Policy (CSP) for sites you create with Microsoft Power Pages.
ms.date: 03/17/2026
ms.topic: how-to
author: nabha
ms.author: nabha
ms.reviewer: danamartens
contributors:
    - nageshbhat-msft
ms.custom: bap-template
---

# Manage your site's Content Security Policy

[Content Security Policy (CSP)](https://content-security-policy.com/) is an extra layer of security that helps detect and mitigate some types of web attacks such as cross-site scripting, data injection attacks, site defacement, or the distribution of malware. CSP provides an extensive set of policy directives that help control the resources that a site page can load. Each directive defines the restrictions for a specific type of resource.

## Prerequisites

> [!IMPORTANT]
> Test CSP changes in a development environment first. Enabling or modifying CSP on existing sites might break functionality if the policy doesn't account for third-party scripts, custom code, or external resources. 

Use the following approach when making CSP changes: 

1. Start with report-only mode to identify violations without blocking resources. 
1. Review the browser console for CSP violation messages. 
1. Add required sources incrementally based on violations found. 
1. Switch to enforcement mode once no critical violations are reported. 

## Default CSP policy

> [!IMPORTANT]
> For sites created after November 10, 2025, CSP is enabled by default with the following policy: 

```
script-src 'self' content.powerapps.com content.powerapps.us content.appsplatform.us content.powerapps.cn 'nonce';
style-src 'unsafe-inline' https:;

```

This default policy: 

- Allows scripts from your site’s origin ('self') 
- Allows scripts from Power Pages content delivery domains 
- Uses nonce-based script validation for inline scripts 
- Allows inline styles and styles from HTTPS sources 

**For sites created before this change**: CSP might not be enabled. We recommend enabling it by configuring the HTTP/Content-Security-Policy site setting. See [Migration guide for existing sites>](#migration-guide-for-existing-sites) for step-by-step instructions. 

## Understanding the default policy directives

| **Directive**  | **Value**  | **Purpose**  |
|----|----|----|
| `script-src`  | `'self'`  | Allows scripts from your site’s origin  |
| `script-src`  | `content.powerapps.com, content.powerapps.us, content.appsplatform.us, content.powerapps.cn`  | Allows Power Pages platform scripts  |
| `script-src`  | `'nonce'`  | Enables nonce-based validation for inline scripts  |
| `style-src`  | `'unsafe-inline'`  | Allows inline styles (required for many site features)  |
| `style-src`  | `https:`  | Allows styles from any HTTPS source  |

## Customizing CSP

You can modify, extend, or disable the default CSP policy to meet your site's specific requirements.

### Modify or disable CSP

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.
1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**. 
1. Select **Site Settings** in the **Portal Management** app. 
1. Find or create the **HTTP/Content-Security-Policy** site setting. 
1. Modify the value as needed. To disable CSP, clear the site setting value (leave it empty) rather than deleting the setting.

### Adding external script sources

If your site uses external JavaScript libraries (for example, analytics, chat widgets), add their domains to the `script-src` directive: 

```
script-src 'self' content.powerapps.com content.powerapps.us
  content.appsplatform.us content.powerapps.cn 'nonce'
  https://cdn.example.com https://analytics.example.com;
style-src 'unsafe-inline' https:;
```

### Adding additional directives

You can add more CSP directives as needed. Common additions include: 

| **Directive**  | **Example**  | **Purpose**  |
|----|----|----|
| `img-src`  | `img-src 'self' https: data:;`  | Control image sources  |
| `font-src`  | `font-src 'self' https://fonts.gstatic.com;`  | Control font sources  |
| `connect-src`  | `connect-src 'self' https://api.example.com;`  | Control AJAX/fetch destinations  |
| `frame-src`  | `frame-src 'self' https://www.youtube.com;`  | Control `iframe` sources  |
| `frame-ancestors`  | `frame-ancestors 'self';`  | Control who can embed your site  |
| `media-src`  | `media-src 'self' https:;`  | Control audio/video sources  |
| `object-src`  | `object-src 'none';`  | Block plugins (Flash, Java applets)  |

## Nonce support

### What is a nonce?

A nonce (number used once) is a cryptographic random value generated for each page request. When you enable nonce, only inline scripts that include a matching nonce attribute run. 

### How nonce works in Power Pages?

When you include 'nonce' in your CSP policy: 

1. Power Pages generates a unique nonce value for each page request. 
1. Power Pages automatically adds the nonce to inline script tags from trusted sources. 
1. Power Pages blocks inline scripts without the matching nonce. 
1. This process prevents injected malicious scripts from running. 
1. Power Pages secures inline event handlers separately through automatic hash generation. 

### Nonce is enabled by default

The default CSP policy includes 'nonce' in the `script-src` directive, providing automatic protection for inline scripts from trusted sources. 

### How nonce works with custom scripts?

Power Pages handles nonce injection automatically in most scenarios: 

- **Liquid templates**: Power Pages automatically injects the nonce attribute into inline scripts rendered through Liquid templates after rendering. No action required from makers. 

- **Inline event handlers**: Power Pages automatically secures event handlers through hash generation. No manual action is needed. 

- **Dynamically created scripts**: Scripts created at runtime via JavaScript (for example, using `document.createElement`) can't receive the server-side nonce. Where possible, move such scripts to external files and add their source domains to the `script-src` directive. 

## Test with report-only mode

Before enforcing a CSP policy, use report-only mode to identify what the policy blocks without blocking it: 

1. In **Portal Management**, create a site setting named `HTTP/Content-Security-Policy-Report-Only`. 
1. Set its value to the CSP policy you want to test. 
1. Open your site in a browser and check the console for violation reports. 
1. Address all violations by adjusting the policy. 
1. Once satisfied, move the policy value to `HTTP/Content-Security-Policy` (enforcement mode). 
1. Delete the `HTTP/Content-Security-Policy-Report-Only` site setting. 

> [!NOTE]
> You can use both `HTTP/Content-Security-Policy` and `HTTP/Content-Security-Policy-Report-Only` simultaneously. Use report-only to test stricter policies while enforcing a baseline policy. 

## Migration guide for existing sites

For sites created before CSP was enabled by default, follow these steps to enable CSP: 

### Step 1: Check current CSP status

1. Open **Portal Management** > **Site Settings**. 
1. Search for `HTTP/Content-Security-Policy`. 
1. If the setting doesn't exist, CSP isn't enabled on your site. 

> [!NOTE]
> When you don't configure CSP, the site's health checker shows a warning: "HTTP/Content-Security-Policy site setting is missing or misconfigured." You can check this warning in your site's health diagnostics. 

### Step 2: Start with report-only mode

1. Create a site setting named `HTTP/Content-Security-Policy-Report-Only` with the default policy. 

   ```
   script-src 'self' content.powerapps.com content.powerapps.us content.appsplatform.us content.powerapps.cn 'nonce'; style-src 'unsafe-inline' https:;
   ```

1. Browse your site and check the browser console for violations. 
1. Add any required external domains to the policy. 

### Step 3: Enable enforcement

1. Create the `HTTP/Content-Security-Policy` site setting with your tested policy. 
1. Optionally remove the report-only setting. 
1. Monitor problems and adjust as needed. 

### Considerations

- Existing sites don't automatically migrate to CSP for enforcement. 

- Automatic nonce injection handles custom JavaScript added through the code editor for liquid-rendered content. 

- You must explicitly add domains for third-party scripts (analytics, chat widgets, and so on) to `script-src`. 

## Troubleshooting

### Scripts from external sources are blocked

**Symptom**: Browser console shows a CSP violation for a script source. 

**Solution**: First, verify that the external source is trusted and required for your site. Only add domains from sources you trust. Once validated, add the script's domain to your `script-src` directive: 

```
script-src 'self' content.powerapps.com content.powerapps.us
  content.appsplatform.us content.powerapps.cn 'nonce'
  https://blocked-domain.com;
style-src 'unsafe-inline' https:;
```

### Inline scripts don't run

**Symptom**: Custom inline scripts don't run; CSP nonce violation in console. 

**Solution**: For Liquid-rendered content, Power Pages automatically injects the nonce attribute. If your scripts are still blocked, ensure the script is within a Liquid template or server-rendered page where automatic nonce injection applies. For dynamically created scripts, consider moving them to external .js files and adding the source domain to your CSP policy. 

### Images or fonts don't load

**Symptom**: Images appear broken, or custom fonts don't render. Browser console shows CSP violations for `img-src` or `font-src`. 

**Solution**: Add the appropriate source directive to your CSP policy: 

```
img-src 'self' https: data:;
font-src 'self' https://fonts.gstatic.com
  https://fonts.googleapis.com;
```

### Iframes don't display

**Symptom**: Embedded content (YouTube, Maps, Power BI) doesn't load. Browser console shows CSP violations for `frame-src`. 

**Solution**: Add `frame-src` with the required domains: 

```
frame-src 'self' https://www.youtube.com
  https://app.powerbi.com;
```

### Third-party widgets not working

**Symptom**: Chat widgets, analytics scripts, or other third-party integrations don't load or function correctly. 

**Solution**: Third-party widgets often require multiple directives. Check the browser console for all violation types and add the required sources. Example for a chat widget: 

```
script-src 'self' content.powerapps.com 'nonce'
  https://widget.chatprovider.com;
style-src 'unsafe-inline' https:;
connect-src 'self' https://api.chatprovider.com;
frame-src 'self' https://widget.chatprovider.com;
img-src 'self' https: data:;
```

## Site settings reference

| **Site setting**  | **Purpose**  | **Default**  |
|----|----|----|
| HTTP/Content-Security-Policy  | The complete CSP policy (enforcement mode)  | See default policy above (new sites only)  |
| HTTP/Content-Security-Policy-Report-Only  | CSP policy in report-only mode (violations logged, not blocked)  | Not set  |

 

## Best practices

1. **Start with the default policy**: The default CSP provides strong protection while allowing Power Pages features to work correctly. 
1. **Test with report-only mode first**: Use HTTP/Content-Security-Policy-Report-Only to identify what would be blocked before enforcing. 
1. **Add sources incrementally**: When integrating external services, add only the specific domains required. Avoid broad wildcards like `https:` for `script-src`. 
1. **Avoid `unsafe-inline` for scripts**: The nonce-based approach is more secure than allowing all inline scripts. The default policy uses nonce instead of `unsafe-inline` for `script-src`. 
1. **Monitor browser console**: CSP violations are logged to the browser console, helping identify blocked resources. 
1. **Regularly review and tighten policies**: As you identify and remove dependencies on external resources, tighten your CSP policy accordingly. 
1. **Use specific domains, not wildcards**: Instead of `https:`, specify exact domains (for example, `https://cdn.example.com`) for better security. 

## Common scenarios

### Scenario: Add Google Analytics

```
script-src 'self' content.powerapps.com 'nonce'
  https://www.googletagmanager.com
  https://www.google-analytics.com;
style-src 'unsafe-inline' https:;
img-src 'self' https: data:;
connect-src 'self'
  https://www.google-analytics.com
  https://analytics.google.com;
```

### Scenario: Add a YouTube embed

```
script-src 'self' content.powerapps.com 'nonce';
style-src 'unsafe-inline' https:;
frame-src 'self' https://www.youtube.com
  https://www.youtube-nocookie.com;
```

### Scenario: Use Google Fonts

```
script-src 'self' content.powerapps.com 'nonce';
style-src 'unsafe-inline'
  https://fonts.googleapis.com;
font-src 'self' https://fonts.gstatic.com;
```

## Related resources

- [Content Security Policy Level 3 (W3C Specification)](https://www.w3.org/TR/CSP3/) 
- [MDN Web Docs: Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) 
- [Configure site settings for Power Pages](/power-pages/configure/configure-site-settings)
