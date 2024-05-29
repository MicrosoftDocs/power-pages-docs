---
title: Embed a Power Pages site in another website by using an iframe
description: Learn about how to embed a Power Pages site in another website.
author: dileepsinghmicrosoft

ms.topic: conceptual
ms.collection: get-started
ms.date: 03/28/2023

ms.author: dileeps
ms.reviewer: dmartens
contributors:
    - dileepsinghmicrosoft
    - nickdoelman
    - sandhangitmsft
---

# Embed a Power Pages site in another website by using an iframe

One of the most common ways of using web based applications is to embed web application functionality inside another website. Usually the other website already exists, but you want to enhance its abilities and add new functions that work with your data surfaced through the Power Pages application.

In this scenario, it's easier to embed your Power Pages site functionality rather than build it from scratch. This article explains the steps to embed a Power Pages application in a different website by using an iframe.

## Step 1. Enable the site for iframe

Iframes are disabled on new Power Pages sites by default, to ensure that no one can embed your website externally to attempt ["clickjacking" attacks](https://owasp.org/www-community/attacks/Clickjacking). 

1. Set up the HTTP response header. You can choose either the [Content-Security-Policy (CSP) frame-ancestors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) directive (recommended) or [X-Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options).

    >[!NOTE]
    > Content-Security-Policy frame-ancestors has superseded X-Frame-Options, and is the method described in this article.

    1. Set the site setting to enable the HTTP header **HTTP/Content-Security-Policy**. More information: [Set up HTTP headers in portals](/power-apps/maker/portals/configure/cors-support)

    1. Follow the syntax described in [CSP: frame-ancestors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) to set the value.

        For example, to enable a Power Pages site that can be embedded by using an iframe in the website `www.contoso.com`, the setting will look like the following:

        `Content-Security-Policy: frame-ancestors 'self' <https://www.contoso.com>;`

        > [!NOTE]
        > The `'self'` string is important; without it, the Power Pages site won't be able to embed its own pages, which is commonly required in scenarios such as modal pop-up menus for basic forms.
        >
        > It's important to limit the ability to embed a Power Pages site in an iframe to specific sites, rather than use the wildcard character (\*).  
        >
        > CSP consists of numerous directives whose values depends on various factors (like from where the scripts are loaded). This article doesn't cover that information because it's implementation-specific. However, we recommend that you first test this setup on a nonproduction site, look at the browser console errors to identify issues you need to fix, and adjust the setting.

1. Set the **SameSite** default to **None** for Power Pages site cookies.

    The [SameSite attribute](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie/SameSite) for cookies is useful for securing the site against cross-site request forgery (CSRF) attacks. However, this also means that the site can't be embedded in an iframe in scenarios like when the site requires user authentication or contains dynamic components like forms or lists.

    Therefore, to embed the Power Pages site in an iframe, you must change the SameSite cookie attribute for your Power Pages site to **None** by default. More information: [SameSite mode changes](/power-apps/maker/portals/important-changes-deprecations#samesite-mode-changes)

    > [!NOTE]
    > Marking SameSite cookies as **None** doesn't make your Power Pages site vulnerable to CSRF attacks, because the Power Pages uses anti-CSRF tokens to prevent these attacks.

## Step 2. Embed your Power Pages site

After you complete the previous step, all you need to do to embed the Power Pages site experience into your website is to use the [HTML iframe tag](https://www.w3schools.com/html/html_iframe.asp) to embed the whole site or specific pages, as required.
  
We recommend that the Power Pages domain name be a sibling or a child of the domain name of the site where you're embedding the  site in an iframe. For example, if your root website is `www.contoso.com`, the Power Pages site domain name should be `portal.contoso.com`. This is important to ensure that the cookies used by the Power Pages site won't be classified as [third-party cookies and be blocked by the browser (blog)](https://blog.chromium.org/2020/01/building-more-private-web-path-towards.html). Otherwise, functionality such as Captcha and basic/multistep form redirection might not work properly. To set up a custom domain name on your Power Pages site, go to [Add a custom domain name](/power-apps/maker/portals/admin/add-custom-domain).

## Step 3. Handle headers and footers

You can modify how headers and footers appear&mdash;or whether they appear at all&mdash;on embedded Power Pages site pages.

### Keep the embedded site headers and footers from showing

It's common for the parent site where you want to embed a Power Pages site to already have headers and footers. In such situations, you might not want to show the embedded site's header and footer. Consider the following scenarios:

- **When an entire Power Pages site is embedded in an iframe**  
    Remove the content of your header and footer by updating the respective header and footer web templates.

- **When a specific Power Pages site page is embedded in an iframe**  
    Typically, you don't want to show the site header or footer when you embed a specific page in a website. However, you still want the header and footer to be available when the user goes to the site directly. You can achieve this by modifying headers and footers to render dynamically based on page content.

### Add conditional code in header and footers

Header and footer web templates support full liquid customizations, so you can add conditional code to render certain properties.

For example, the following code displays a search bar in the header if the page is anything other than the search page.

> [!IMPORTANT]
> Because the header is an element common to all pages, `page.id` will get cached by default for the first page that's opened by a user. Hence, this code uses the [substitution tag](liquid/template-tags.md#substitution) to ensure that these elements won't be cached and will always be evaluated based on the current page.

```
{% substitution %}
{% assign current_page = page.id %}
{% assign sr_page = sitemarkers[Search].id %}
{% if current_page == sr_page %}
{% assign section_class = section-landing-search %}
<section class=page_section section-landing-{{ current_page }} {{ section_class | h }} color-inverse\>
    <div class=container\>
        <div class=row \>
            <div class=col-md-12 text-center\>
                {% if current_page == sr_page %}
                    <h1 class=section-landing-heading\>{% editable snippets 'Search/Title' default:resx["Discover_Contoso"] %}\</h1\>
                {% include 'Search' %}
                {% endif %}
            </div\>
        </div\>
    </div\>
</section\>
{% endif %}
{% endsubstitution %}
```

As an alternative to adding conditional code in header and footers, you can also consider the following methods. However, we don't recommend either approach; they both have limitations, and neither supports full functionality.

- For read-only scenarios that don't include any lists or forms, disable header and footer from your template.
- Use a special rewrite template (`~/Areas/Portal/Pages/Form.aspx`).

### See also

- [Configure site settings for portals](/power-apps/maker/portals/configure/configure-site-settings) 
- [Substitution template tag](liquid/template-tags.md#substitution) 
- [Enable header and footer output caching on a portal](/power-apps/maker/portals/configure/enable-header-footer-output-caching) 
- [SameSite mode](/power-apps/maker/portals/important-changes-deprecations#samesite-mode-changes)
- [Set up HTTP headers in portals](/power-apps/maker/portals/configure/cors-support)
