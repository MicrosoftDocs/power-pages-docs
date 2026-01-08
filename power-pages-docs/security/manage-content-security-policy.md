---
title: Manage your site's Content Security Policy
description: Learn how to manage the Content Security Policy (CSP) for sites you create with Microsoft Power Pages.
ms.date: 01/05/2026
ms.topic: how-to
author: nabha
ms.author: nabha
ms.reviewer: danamartens
contributors:
    - nageshbhat-msft
ms.custom: bap-template
---

# Manage your site's Content Security Policy

[Content Security Policy (CSP)](https://content-security-policy.com/) is an extra layer of security that helps detect and mitigate some types of web attacks such as data theft, site defacement, or the distribution of malware. CSP provides an extensive set of policy directives that help control the resources that a site page is allowed to load. Each directive defines the restrictions for a specific type of resource.

When CSP is turned on for a Power Pages site, it helps to make the site more secure by blocking connections, scripts, fonts, and other types of resources that originate from unknown or malicious sources.

CSP is turned off by default. However, websites might require CSP to enhance other security.

Use the [Portal Management app](../configure/portal-management-app.md) to manage CSP.

## Set your site's CSP

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, select **Site Settings**.

1. Create or edit the **HTTP/Content-Security-Policy** site setting.

1. Set the values you need from the [CSP reference](https://content-security-policy.com/), separated by semicolons; for example, `script-src 'self' https://js.example.com;style-src 'self' https://css.example.com`

## Turn on nonce

A *nonce* represents a code, usually numeric, that's meant to be used only once ("number once"). When you use a nonce with your site's CSP, a unique cryptographic code is generated and added to each script that's specified in the CSP header. Only inline scripts that have a nonce attribute that matches the one in the CSP are allowed to run. Scripts that an attacker may have injected into the page are blocked because they don't include the nonce attribute. [Learn more about using a nonce with CSP](https://content-security-policy.com/nonce/).

In Power Pages sites, nonce supports inline scripts and inline event handlers only.

To turn on nonce for your site, add the **script-src 'nonce';** value to the **HTTP/Content-Security-Policy** site setting. A few examples follow.

- If you want a strict policy that doesn't allow scripts to load from sources outside of a Power Pages site, add the following value to the **HTTP/Content-Security-Policy** site setting: `script-src 'self' content.powerapps.com 'nonce'`

- If you want to load scripts from any secure source, add the following value: `script-src https: 'nonce'`

When nonce is turned on, **unsafe-eval** is injected to support the automatic evaluation of unsafe code. To turn off the automatic injection of **unsafe-eval**, change the site setting **HTTP/Content-Security-Policy/Inject-unsafe-eval** to **False**. Keep in mind that if **unsafe-eval** injection is turned off, the validation of automatically generated fields on [basic](../getting-started/add-form.md)  or [multistep](../getting-started/multistep-forms.md) forms might no longer work correctly.
