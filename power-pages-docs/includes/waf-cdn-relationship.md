WAF and CDN are complementary features that can be enabled independently. WAF provides security by filtering malicious requests, while CDN improves performance by caching static content closer to users. If your site already has CDN enabled, WAF reuses the same Front Door profile. Enabling either feature for the first time triggers domain validation for custom domains.

Both features use Azure Front Door infrastructure, so:

- Enabling either feature may require domain validation for custom domains.
- You can add CDN caching to a WAF-protected site at any time.
- You can add WAF protection to a CDN-enabled site at any time.