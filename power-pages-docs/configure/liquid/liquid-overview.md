---
title: Liquid overview
description: Learn how to use Liquid, an open-source template language, in Power Pages.
author: nageshbhat-msft

ms.topic: overview
ms.custom: 
ms.date: 01/05/2026
ms.subservice:
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - GitanjaliSingh33msft
---

# Liquid overview

Liquid is an open-source template language integrated into Power Pages. It can be used to add dynamic content to webpages, and to create a wide variety of custom web templates. Liquid is processed on the server side, so the output is rendered as plain HTML to the end user.

Using Liquid, you can:

- Add dynamic content directly to the **Copy** field of a webpage or the content of a [content snippet](/power-apps/maker/portals/configure/customize-content-snippets).  

- Build custom [web templates](../web-templates.md), for use throughout the Power Pages content management system.  

- [Render a website header and primary navigation bar](render-site-header-primary-navigation.md), entirely through configuration within Power Apps.  

## Common use cases

Liquid is used extensively in Power Pages for scenarios like:

- **Displaying Dataverse data**: Use the `entityview` and `entitylist` tags or the `entities` object to query and display business data.
- **Conditional content**: Show or hide content based on user roles, site settings, or request parameters using `{% if %}` and `{% unless %}` tags.
- **Page layouts**: Create reusable web templates that define the layout structure and include dynamic sections with `{% include %}` and `{% block %}` tags.
- **Localization**: Use content snippets with Liquid to provide multi-language support across your site.

## Example: Display a list of records

The following example shows how to display data from a Dataverse table using a Liquid entity view:

```html
{% entityview logical_name:'contact', name:'Active Contacts' %}
  <ul>
    {% for item in entityview.records %}
      <li>{{ item.fullname }}</li>
    {% endfor %}
  </ul>
{% endentityview %}
```

## Example: Conditional content based on web role

```html
{% if user.roles contains 'Administrators' %}
  <p>Welcome, administrator!</p>
{% else %}
  <p>Welcome to our site.</p>
{% endif %}
```

> [!TIP]
> Use the [Power Pages Liquid reference documentation](liquid-objects.md) to explore all available Liquid objects, tags, and filters. When debugging Liquid templates, check for precompile errors in the [Portal Checker](../admin/portal-checker-analysis.md) and verify syntax against the [Liquid types](liquid-types.md) reference.

## Related information

- [Web templates](../web-templates.md)  
- [Understand Liquid operators](liquid-operators.md)  
- [Liquid types](liquid-types.md)  
- [Liquid conditional operators](liquid-conditional-operators.md)  
- [Liquid Objects](liquid-objects.md)  
- [Liquid Tags](liquid-tags.md)  
- [Liquid Filters](liquid-filters.md)
- [Create advanced Power Pages sites with Liquid templates (training module)](/training/modules/extend-power-app-portals/)
