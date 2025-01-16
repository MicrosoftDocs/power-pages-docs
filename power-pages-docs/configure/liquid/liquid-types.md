---
title: Available Liquid types
description: Learn about the available liquid types in a Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 01/15/2025
ms.subservice:
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - GitanjaliSingh33msft
---

# Available Liquid types

Liquid objects can return one of seven basic types: **String**, **Number**, **Boolean**, **Array**, **Dictionary**, **DateTime**, or **Null**. Use the **assign** or **capture** tags to initialize Liquid variables.

## String

Wrap text in single or double quotes to declare a String.

```
{% assign string_a = "Hello World!" %}

{% assign string_b = 'Single quotes work too.' %}
```

Get the number of characters in a string with the size property.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## Number

Numbers can be integers or floats.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## Boolean

A Boolean is either true or false.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This snippet is rendered because x is true.

{% endif %}
```

## Array

An array holds a list of values of any type. You can access a given item by (zero-based) index using \[ \], iterate over them using the **for tag**, and get the number of items in the array using the size property.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This list has {{ entitylist.views.size }} views.

{% endif %}
```

## Dictionary

Dictionaries hold a collection of values that can be accessed by a string key. You can access a given item by string key using \[ \], iterate over them using the **for tag**, and get the number of items in the dictionary using the size property.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## DateTime

A DateTime object represents a specific date and time.

```
{{ page.modifiedon | date: 'f' }}
```

## Null

Null represents an empty or nonexistent value. Any outputs that attempt to return a null value render nothing. It's treated as false in conditions.

```
{% if request.params[ID] %}

This snippet renders if the ID request parameter isn't null.

{% endif %}
```

### See also

- [Web templates](../web-templates.md)  
- [Understand Liquid operators](liquid-operators.md)  
- [Conditional](liquid-conditional-operators.md)  
- [Liquid Objects](liquid-objects.md)  
- [Liquid Tags](liquid-tags.md)  
- [Liquid Filters](liquid-filters.md)  
