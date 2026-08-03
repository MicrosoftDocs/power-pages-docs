---
title: Use WAF JavaScript challenge and CAPTCHA
description: WAF JavaScript challenge and CAPTCHA in Power Pages help block bots on public sites. Learn when to use each and how to scope rules safely.
author: RitGan
ms.author: ritwikganni
ms.reviewer: smurkute
ms.date: 07/22/2026
ms.topic: concept-article
---

# Use WAF JavaScript challenge and CAPTCHA to reduce bot abuse

Web Application Firewall (WAF) challenge actions in Power Pages are bot-mitigation controls that verify traffic before it reaches your site. Backed by Azure Front Door, WAF supports two challenge types - **JavaScript challenge** (`JSChallenge`) and **CAPTCHA** - that help reduce credential stuffing, fake sign-ups, scraping, and form abuse on public web apps.

This article explains what these challenge types are, when to use each, and how they fit into the Power Pages WAF model so you can reduce bot abuse without disrupting legitimate user journeys.

## Intended audience

- Power Pages makers and site owners who manage public site traffic.
- Security or platform admins tuning abuse protection without breaking user journeys.
- Teams that already have WAF enabled and want to add targeted challenge controls.

## Challenge types

Power Pages WAF supports two distinct challenge actions, each suited to different risk levels and user-experience tradeoffs.

**JavaScript challenge (`JSChallenge`)** is the lower-friction first line of defense. It validates browser behavior transparently and is a good fit for routes with noisy automation but high legitimate user traffic.

**CAPTCHA** is a stronger step-up control. It adds explicit human verification and is better suited to high-risk actions where the cost of abuse is higher.

By default, the challenge cookie lifetime is 30 minutes for both JavaScript challenge and CAPTCHA, and you can tune it at the policy level based on risk tolerance.

## Choosing between challenge types

A practical decision pattern helps balance protection with user experience:

- Start with **JavaScript challenge** on targeted non-auth content and form pages.
- Move to **CAPTCHA** on routes where abuse still persists or where false negatives are expensive.
- Keep CAPTCHA scope narrow to avoid unnecessary user friction.
- Tune challenge cookie lifetime based on your risk tolerance.

## Power Pages WAF context

Power Pages WAF is backed by Azure Front Door. In supported Power Pages environments, you can:

1. Enable WAF for a site.
1. Add custom WAF rules.
1. Read back the applied rules.

The existing `createWafRules` payload is used to configure Azure WAF challenge actions (`JSChallenge`, `CAPTCHA`). The rule payload shape stays the same across challenge types—the key behavior switch is the `action` field.

## Scoping guard rails

To avoid regressions in user flows, challenge actions should be scoped only to interactive, non-auth HTML entry routes. The following route categories should be excluded from challenge rules:

- Auth callback and sign-in return routes (OIDC/SAML/WS-Fed reply paths, return-url chains).
- API and async routes (`/_api`, JSON/XHR endpoints).
- Internal Power Pages routes (`/_services`, `/_portal`, `/_resources`).
- Static assets (`.css`, `.js`, images, fonts).

## Example: targeted rules

Consider a support site where bots scrape knowledge articles and spam the contact form. You can apply a JavaScript challenge to the knowledge base (high traffic, lower risk) and reserve CAPTCHA for the contact form (lower traffic, higher risk).

If WAF isn't enabled yet, you can optionally add a prerequisite call:

```http
POST https://api.powerplatform.com/powerpages/environments/{environmentId}/websites/{id}/enableWaf?api-version=2024-10-01
Authorization: Bearer <token>
```

Create the challenge rules:

```http
PUT https://api.powerplatform.com/powerpages/environments/{environmentId}/websites/{id}/createWafRules?api-version=2024-10-01
Authorization: Bearer <token>
Content-Type: application/json
```

```json
{
  "customRules": [
    {
      "name": "ProtectKnowledgeBaseWithJsChallenge",
      "priority": 100,
      "enabledState": "Enabled",
      "ruleType": "MatchRule",
      "action": "JSChallenge",
      "matchConditions": [
        {
          "matchVariable": "RequestUri",
          "operator": "StartsWith",
          "matchValue": ["/knowledge-base/"],
          "negateCondition": false
        }
      ]
    },
    {
      "name": "ProtectContactFormWithCaptcha",
      "priority": 110,
      "enabledState": "Enabled",
      "ruleType": "MatchRule",
      "action": "CAPTCHA",
      "matchConditions": [
        {
          "matchVariable": "RequestUri",
          "operator": "StartsWith",
          "matchValue": ["/contact-us/"],
          "negateCondition": false
        }
      ]
    }
  ],
  "managedRules": []
}
```

A successful submission returns `202 Accepted` with an `Operation-Location: <status-url>` header.

Verify the applied configuration:

```http
GET https://api.powerplatform.com/powerpages/environments/{environmentId}/websites/{id}/getWafRules?api-version=2024-10-01
Authorization: Bearer <token>
```

## Validation and telemetry

After you apply rules, validate behavior on the scoped routes:

- Allow time for propagation after rule updates (typically 15–20 minutes).
- Test once with a fresh session on the targeted route, then test again as a returning user.
- Use the browser **Network** trace to confirm challenge flow on the first request.
- Review [Power Pages WAF logs](web-application-firewall-logs.md) from the Security workspace to validate request-level outcomes.
- JavaScript challenge should show events like issued, pass, and valid for legitimate traffic.
- CAPTCHA should trigger only on the high-risk paths you scoped.

## Staged rollout

A staged rollout keeps risk low and avoids broad catch-all targeting in the first iteration:

1. Start with one or two high-risk paths.
1. Observe traffic impact and false positives.
1. Tune rule scope and priority.
1. Expand coverage gradually.

## Related documentation

For the latest supported actions, limits, and policy settings, check the current Power Pages and Azure WAF documentation:

- [Power Pages WAF overview](web-application-firewall.md)
- [Configure WAF for Power Pages](configure-web-application-firewall.md)
- [Access Power Pages WAF logs](web-application-firewall-logs.md)
- [Create WAF rules API](/rest/api/power-platform/powerpages/websites/create-waf-rules)
- [Get WAF rules API](/rest/api/power-platform/powerpages/websites/get-waf-rules)
- [Azure WAF JavaScript challenge](/azure/web-application-firewall/waf-javascript-challenge)
- [Azure Front Door WAF CAPTCHA](/azure/web-application-firewall/afds/captcha-challenge)
- [Azure Front Door WAF custom rules](/azure/web-application-firewall/afds/waf-front-door-custom-rules)