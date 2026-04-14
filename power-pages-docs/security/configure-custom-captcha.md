---
title: Custom CAPTCHA provider setup in Power Pages
description: Custom CAPTCHA in Power Pages lets you replace the built-in CAPTCHA with Google reCAPTCHA, hCaptcha, or Cloudflare Turnstile using site settings alone. Learn how to configure it.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 04/14/2026
ms.topic: concept-article
---

# Configure a custom CAPTCHA provider in Power Pages

Power Pages supports replacing the built-in CAPTCHA with any third-party CAPTCHA solution, such as Google reCAPTCHA, hCaptcha, or Cloudflare Turnstile. You can make this change by using only site settings, without any code changes or deployments. This feature is sometimes referred to as **Bring Your Own Captcha (BYOC)**.

## Why configure a custom CAPTCHA provider

The default CAPTCHA in Power Pages is a built-in image-based challenge. While functional, it might not meet all accessibility requirements or align with your organization's security and branding standards. A custom CAPTCHA provider lets you:

- Use modern, accessible CAPTCHA solutions such as invisible challenges or image-based human verification from leading providers.
- Apply consistent CAPTCHA branding across your organization's web properties.
- Comply with regional or regulatory requirements that mandate specific CAPTCHA vendors.
- Enable invisible CAPTCHA experiences that don't require user interaction.

## Prerequisites

Before configuring a custom CAPTCHA provider, ensure you have the following items:

- **Portal administrator access** with write permissions to Dataverse site settings.
- **An account with a third-party CAPTCHA provider.** Supported providers include any service that:
  - Provides a client-side JavaScript widget that injects a hidden form field with a response token.
  - Provides a server-side HTTPS verification endpoint that accepts a `POST` request with `secret`, `response`, and optionally `remoteip` parameters, and returns a JSON response with a `"success"` boolean field.
- **A site key and a secret key** from your chosen CAPTCHA provider.
- **CAPTCHA enabled on at least one form.** The custom provider setting takes effect only on forms where CAPTCHA is configured as required (EntityForms, WebForms, or the registration page).
- **Content Security Policy (CSP) review.** If your portal has CSP headers configured, you must whitelist the CAPTCHA provider's domain in the relevant directives before completing setup. See [Content Security Policy considerations](#content-security-policy-csp-considerations).

## How custom CAPTCHA works

When a visitor loads a portal page that contains a CAPTCHA-enabled form, Power Pages reads the `Captcha/Provider` site setting to determine which provider to use. When you set this value to `custom`, the portal:

1. Injects the HTML widget snippet you configured directly into the form.
1. Loads the provider's JavaScript SDK from the URL you configured.
1. When the form is submitted, reads the response token that the widget injected into the form as a hidden field.
1. Posts the response token, your secret key, and the visitor's IP address to the provider's server-side verification endpoint.
1. Reads the `"success"` field from the JSON response. If `true`, form submission proceeds. If `false`, the visitor sees a validation error and must try again.

Your secret key is **never exposed client-side**. The verification POST sends it only server-to-server.

## Site settings reference

Configure all settings through Dataverse site settings. To open site settings, go to **Portal Management** > **Site Settings** in your Power Platform environment.

### Provider selection

| Site Setting | Type | Required | Description |
|---|---|---|---|
| `Captcha/Provider` | String | No | Set to `custom` to enable a third-party CAPTCHA provider. The comparison is case-insensitive (`Custom`, `CUSTOM`, and `custom` all work). Any other value, or leaving this setting absent, uses the default built-in CAPTCHA. |

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

### Step 4: Clear the portal cache

After saving site settings, clear the portal cache so the new configuration takes effect:

- **Local development:** Restart IIS Express or recycle the application pool.
- **Power Pages online:** In the Power Pages admin center, restart the portal or go to `/_services/about`.

### Step 5: Verify the widget renders

1. Go to a page that contains a form with **Captcha Required** enabled.
1. Confirm the third-party CAPTCHA widget appears in the form.
1. Open browser developer tools and inspect the page elements to confirm:
   - The provider's script tag is present.
   - The widget `div` element is present.
   - No errors appear in the browser console related to blocked scripts or CSP violations.
1. Confirm the default built-in CAPTCHA is no longer shown.

### Step 6: Test validation

**Test successful validation:**
1. Fill in all required form fields.
1. Complete the CAPTCHA challenge.
1. Submit the form and confirm it submits successfully.

**Test failed validation:**
1. Fill in all required form fields.
1. Don't complete the CAPTCHA.
1. Submit the form and confirm the validation error message appears and the form doesn't submit.

## Configuration examples

The following examples show the exact site setting values for three commonly used providers.

### Google reCAPTCHA v2

| Site Setting | Value |
|---|---|
| `Captcha/Provider` | `custom` |
| `Captcha/Custom/ClientScriptUrl` | `https://www.google.com/recaptcha/api.js` |
| `Captcha/Custom/WidgetHtml` | `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>` |
| `Captcha/Custom/ValidationEndpoint` | `https://www.google.com/recaptcha/api/siteverify` |
| `Captcha/Custom/ValidationSecretKey` | `YOUR_SECRET_KEY` |
| `Captcha/Custom/ResponseFieldName` | `g-recaptcha-response` |

Register and obtain keys at the [Google reCAPTCHA admin console](https://www.google.com/recaptcha/admin). Choose **reCAPTCHA v2 – "I'm not a robot" Checkbox** and add your portal domain.

**CSP additions:** Add `https://www.google.com` and `https://www.gstatic.com` to `script-src`, `frame-src`, `style-src`, and `img-src`.

### hCaptcha

| Site Setting | Value |
|---|---|
| `Captcha/Provider` | `custom` |
| `Captcha/Custom/ClientScriptUrl` | `https://js.hcaptcha.com/1/api.js` |
| `Captcha/Custom/WidgetHtml` | `<div class="h-captcha" data-sitekey="YOUR_SITE_KEY"></div>` |
| `Captcha/Custom/ValidationEndpoint` | `https://api.hcaptcha.com/siteverify` |
| `Captcha/Custom/ValidationSecretKey` | `YOUR_SECRET_KEY` |
| `Captcha/Custom/ResponseFieldName` | `h-captcha-response` |

Register and get keys at the [hCaptcha dashboard](https://dashboard.hcaptcha.com). Test keys are available in the [hCaptcha documentation](https://docs.hcaptcha.com/#integration-testing-test-keys) for always-pass, always-challenge, and always-fail behaviors.

**CSP additions:** Add `https://hcaptcha.com` and `https://*.hcaptcha.com` to `script-src`, `frame-src`, `style-src`, and `img-src`.

### Cloudflare Turnstile

| Site Setting | Value |
|---|---|
| `Captcha/Provider` | `custom` |
| `Captcha/Custom/ClientScriptUrl` | `https://challenges.cloudflare.com/turnstile/v0/api.js` |
| `Captcha/Custom/WidgetHtml` | `<div class="cf-turnstile" data-sitekey="YOUR_SITE_KEY"></div>` |
| `Captcha/Custom/ValidationEndpoint` | `https://challenges.cloudflare.com/turnstile/v0/siteverify` |
| `Captcha/Custom/ValidationSecretKey` | `YOUR_SECRET_KEY` |
| `Captcha/Custom/ResponseFieldName` | `cf-turnstile-response` |

Register and get keys at the [Cloudflare dashboard](https://dash.cloudflare.com) under **Turnstile > Add site**. Test keys for always-pass, always-block, and interactive-challenge modes are available in the [Cloudflare Turnstile testing documentation](https://developers.cloudflare.com/turnstile/troubleshooting/testing/).

**CSP additions:** Add `https://challenges.cloudflare.com` to `script-src` and `frame-src`.

## Supported form types

The custom CAPTCHA provider supports all form surfaces where you can enable CAPTCHA:

| Form type | CAPTCHA support |
|---|---|
| Basic form (EntityForm) - Insert mode | Yes |
| Basic form (EntityForm) - Edit mode | Yes |
| Basic form with file attachment | Yes |
| Multistep form (WebForm) - all steps | Yes |
| Registration page | Yes |

To enable CAPTCHA on a basic form or multistep form, open the form configuration in the Portal Management app and set **Captcha Required** to **Yes** on the form or form step.

To enable CAPTCHA on the registration page, set the site setting `Authentication/Registration/CaptchaEnabled` to `true`.

## Content Security Policy considerations

If your portal uses a Content Security Policy, the browser enforces it strictly and blocks external CAPTCHA scripts and widget iframes unless you explicitly allow the provider's domains. Update your CSP configuration before testing:

- `script-src` - allow the provider's JavaScript SDK domain.
- `frame-src` - allow the provider's domain if the widget loads inside an iframe.
- `style-src` - allow the provider's domain if it loads stylesheets.
- `img-src` - allow the provider's domain if the widget loads images.

If you don't update CSP, the CAPTCHA widget doesn't render and console errors appear in the browser.

## Revert to the default CAPTCHA

To revert to the built-in default CAPTCHA:

1. In **Site Settings**, delete the `Captcha/Provider` site setting, or change its value to anything other than `custom`.
1. Clear the portal cache.

The portal automatically returns to the default built-in CAPTCHA. No other changes are required. You can keep existing `Captcha/Custom/*` settings in place. The portal ignores these settings when the custom provider isn't active.

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

- [Add a CAPTCHA to a basic form](https://learn.microsoft.com/en-us/power-pages/configure/add-captcha)
- [Site settings for Power Pages](https://learn.microsoft.com/en-us/power-pages/configure/configure-site-settings)
- [Content security policy in Power Pages](https://learn.microsoft.com/en-us/power-pages/security/content-security-policy)
- [Multistep form properties](https://learn.microsoft.com/en-us/power-pages/configure/multistep-form-properties)