---
title: Understand Liquid operators
description: Learn about the available liquid operators in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 01/09/2023
ms.subservice:
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - GitanjaliSingh33msft
---

# Understand Liquid operators

Liquid has access to all common logical and comparison operators. These operators can be used in tags such as **if** and **unless**.

## Basic operators

| ==    | Equals                          |
|-------|---------------------------------|
| !=    | Doesn't equal                  |
| &gt;  | Greater than                    |
| &lt;  | Less than                       |
| &gt;= | Greater than or equal to        |
| &lt;= | Less than or equal to           |
| or    | Condition A **or** condition B  |
| and   | Condition A **and** condition B |

## contains

contains tests for the presence of a substring within a string.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains can also test for the presence of a string within an array of strings.

## startswith

startswith tests whether a string starts with a given substring.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## endswith

endswith tests whether a string ends with a given substring.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### See also

- [Web templates](../web-templates.md)  
- [Liquid types](liquid-types.md)  
- [Conditional](liquid-conditional-operators.md)  
- [Liquid Objects](liquid-objects.md)  
- [Liquid Tags](liquid-tags.md)  
- [Liquid Filters](liquid-filters.md) 

