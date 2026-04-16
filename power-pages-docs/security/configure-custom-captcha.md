---
title: Custom CAPTCHA provider setup in Power Pages
description: Custom CAPTCHA in Power Pages lets you replace the built-in CAPTCHA with Google reCAPTCHA, hCaptcha, or Cloudflare Turnstile using site settings alone. Learn how to configure it.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 04/16/2026
ms.topic: concept-article
---

# Configure a custom CAPTCHA provider in Power Pages

CAPTCHA is a security challenge that protects web forms from automated bots, spam submissions, and credential stuffing attacks. Power Pages includes a built-in CAPTCHA control by default and supports replacing it with any third-party CAPTCHA service. 

The custom CAPTCHA applies to all Power Pages form surfaces that support CAPTCHA. 

Custom CAPTCHA providers let you replace Power Pages' default image-based challenge with modern, accessible solutions from leading vendors. This enables consistent branding, compliance with regional requirements, invisible user experiences, and alignment with your organization's security standards.

## Prerequisites

Before configuring a custom CAPTCHA provider, ensure you have the following items:

- **An account with a third-party CAPTCHA provider.** Supported providers include any service that:
  - Provides a client-side JavaScript widget that injects a hidden form field with a response token.
  - Provides a server-side HTTPS verification endpoint that accepts a `POST` request with `secret`, `response`, and optionally `remoteip` parameters, and returns a JSON response with a `"success"` boolean field.
- **A site key and a secret key** from your chosen CAPTCHA provider.
- **Content Security Policy (CSP) review.** If your portal has CSP headers configured, you must whitelist the CAPTCHA provider's domain in the relevant directives before completing setup.
- The Power Pages server must be able to reach the provider's HTTPS verification endpoint. 

## Site settings reference

Configure all settings through Dataverse site settings. To open site settings, go to **Portal Management** > **Site Settings** in your Power Platform environment.

### Provider selection

| Site Setting | Type | Required | Description |
|---|---|---|---|
| `Captcha/Provider` | String | No | Set to `custom` to enable a third-party CAPTCHA provider. The comparison is case-insensitive (`Custom`, `CUSTOM`, and `custom` all work). Any other value, or leaving this setting absent, uses the default built-in CAPTCHA. |

> [!NOTE]
> To revert to the built-in CAPTCHA, delete the `Captcha/Provider` site setting or set it to any value other than `custom`, then clear the portal cache. The portal automatically returns to using the default built-in CAPTCHA. Existing `Captcha/Custom/*` settings are ignored and can remain in place.

### Custom provider settings

The portal reads these settings only when you set `Captcha/Provider` to `custom`.

| Site Setting | Type | Required | Description |
|---|---|---|---|
| `Captcha/Custom/WidgetHtml` | HTML | **Yes** | The HTML snippet that renders the CAPTCHA widget on the form. Must include the provider's required attributes such as `data-sitekey`. If this setting is empty or missing, no CAPTCHA widget is rendered and a warning is logged. |
| `Captcha/Custom/ClientScriptUrl` | URL | Recommended | The HTTPS URL of the third-party CAPTCHA SDK script to load on the page. **Must use HTTPS.** HTTP and malformed URLs are rejected and a warning is logged. If omitted, no external script is registered. |
| `Captcha/Custom/ValidationEndpoint` | URL | **Yes** | The HTTPS verification endpoint URL. The portal POSTs the response token to this URL for server-side validation. **Must use HTTPS.** |
| `Captcha/Custom/ValidationSecretKey` | String | **Yes** | Your secret key from the CAPTCHA provider, used for server-to-server verification. This value is never sent to the browser. |
| `Captcha/Custom/ResponseFieldName` | String | **Yes** | The name of the hidden form field that the CAPTCHA widget automatically injects with the response token after a visitor completes the challenge. |
| `Captcha/Custom/ErrorMessage` | String | No | The error message displayed when CAPTCHA validation fails. If empty or missing, the portal uses its default CAPTCHA error message. |

> [!IMPORTANT]
> The portal renders the `Captcha/Custom/WidgetHtml` and `Captcha/Custom/ClientScriptUrl` values directly on the page. Only portal administrators with Dataverse write access can modify site settings. Don't enter user-supplied or untrusted values in these fields.

## Configure a custom CAPTCHA provider

### Step 1: Obtain keys from your CAPTCHA provider

Register with your chosen CAPTCHA provider and get a **site key** (used in the widget HTML) and a **secret key** (used for server-side verification). Most providers have a developer console where you can register your portal domain and download these keys.

For testing during setup, check whether your provider offers test keys that always pass or always fail, so you can verify the configuration without needing real user interaction.

### Step 2: Configure site settings

1. In your Power Platform environment, open **Portal Management**.
1. Under **Website**, select **Site Settings**.
1. Create or update the following site settings. Use the exact setting names shown.

Set `Captcha/Provider` to `custom`.

Then configure the following settings by using the values from your provider:

| Site Setting | What to enter |
|---|---|
| `Captcha/Custom/ClientScriptUrl` | The HTTPS URL of the provider's JavaScript SDK |
| `Captcha/Custom/WidgetHtml` | The HTML div element for the widget, including the `data-sitekey` attribute with your site key |
| `Captcha/Custom/ValidationEndpoint` | The provider's HTTPS server-side verification URL |
| `Captcha/Custom/ValidationSecretKey` | Your secret key from the provider |
| `Captcha/Custom/ResponseFieldName` | The hidden form field name that the widget uses to inject the response token |

Optionally, set `Captcha/Custom/ErrorMessage` to a custom validation failure message.

### Step 3: Update Content Security Policy (if applicable)

If your portal has a Content Security Policy configured, add the CAPTCHA provider's domain to the relevant directives:

- Add the provider's script domain to `script-src`.
- Add the provider's domain to `frame-src` if the widget loads in an iframe.
- Add image and style domains to `img-src` and `style-src` as needed.

Without these entries, the browser blocks the CAPTCHA script and widget from loading.

## Troubleshooting

### CAPTCHA widget doesn't appear

- Confirm `Captcha/Provider` is set to `custom` (exact spelling, case-insensitive).
- Confirm `Captcha/Custom/WidgetHtml` is set and contains valid HTML with a `data-sitekey` attribute.
- Confirm the form or form step has **Captcha Required** enabled.
- Check the portal diagnostic logs for the warning: *"Custom captcha is enabled but Captcha/Custom/WidgetHtml site setting is not configured."*
- If you're using CSP, confirm the provider's domain is whitelisted in `script-src`.

### CAPTCHA script doesn't load

- Confirm `Captcha/Custom/ClientScriptUrl` is set and uses **HTTPS**. HTTP URLs are rejected.
- Check the portal diagnostic logs for: *"Custom captcha client script URL is invalid or not HTTPS."*
- Check the browser console for CSP violations blocking the script URL.

### Form always fails validation even after completing CAPTCHA

- Confirm `Captcha/Custom/ValidationEndpoint` is set and uses HTTPS.
- Confirm `Captcha/Custom/ValidationSecretKey` is set and matches the secret key from your provider.
- Confirm `Captcha/Custom/ResponseFieldName` exactly matches the hidden field name the widget injects (for example, `g-recaptcha-response` for Google reCAPTCHA v2).
- Check the portal diagnostic logs for verification failure details, including any error codes returned by the provider endpoint.
- Verify the portal server can reach the verification endpoint. Network or firewall restrictions might block outbound HTTPS requests. Verification requests time out after 10 seconds.

### Diagnostic log messages

The following log messages can help diagnose configuration problems:

| Message | Cause |
|---|---|
| "Custom captcha is enabled but Captcha/Custom/WidgetHtml site setting is not configured." | `WidgetHtml` is empty or missing |
| "Custom captcha client script URL is invalid or not HTTPS: {url}" | `ClientScriptUrl` uses HTTP or is malformed |
| "Custom captcha validation endpoint or response field name is not configured." | `ValidationEndpoint` or `ResponseFieldName` is empty or missing |
| "Custom captcha response token is empty or missing from form data." | Visitor submitted the form without completing the CAPTCHA |
| "Custom captcha verification failed. Response: {json}" | The provider's endpoint returned `"success": false` |
| "Custom captcha verification response is missing a boolean 'success' field." | The provider's endpoint returned a response without a `"success"` boolean field |
| "Custom captcha verification request failed (possible timeout or network issue)." | The portal couldn't reach the verification endpoint within 10 seconds |

## Related articles

- [Manage your site's Content Security Policy](/power-pages/security/manage-content-security-policy)
