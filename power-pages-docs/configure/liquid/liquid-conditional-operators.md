---
title: Available Liquid conditional operators
description: Learn about the available Liquid conditional operators in a Power Pages.
author: gitanjalisingh33msft

ms.topic: concept-article
ms.custom: 
ms.date: 01/15/2025
ms.subservice:
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - GitanjaliSingh33msft
---

# Available Liquid conditional operators

When used in conditional statements (**if**, **unless**), some Liquid values are treated as true, and some are treated as false.

In Liquid, null and the Boolean value false are treated as false; everything else is treated as true. For example, empty strings and empty arrays are treated as true.

```
{% assign empty_string = "" %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```

Test for empty strings and arrays using the special value empty if necessary.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```

Test the size of [Liquid types](liquid-types.md) using the special size property.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## Summary

|   Operator                        | True | False |
|---------------------------|------|-------|
| True                      | ×    |       |
| False                     |      | ×     |
| Null                      |      | ×     |
| String                    | ×    |       |
| empty string              | ×    |       |
| 0                         | ×    |       |
| 1, 3.14                   | ×    |       |
| array or dictionary       | ×    |       |
| empty array or dictionary | ×    |       |
| Object                    | ×    |       |

### See also

- [Store source content by using web templates](../web-templates.md)  
- [Understand Liquid operators](liquid-operators.md)  
- [Liquid types](liquid-types.md)  
- [Liquid Objects](liquid-objects.md)  
- [Liquid Tags](liquid-tags.md)  
- [Liquid Filters](liquid-filters.md)  
