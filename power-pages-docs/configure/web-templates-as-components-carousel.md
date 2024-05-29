---
title: Display records as a carousel
description: Learn how to create a web templates component to display locations in Power Pages as a carousel.
author: ckwan-ms

ms.topic: how-to
ms.custom: 
ms.date: 07/25/2023
ms.subservice:
ms.author: ckwan
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - clromano

---

# Display records as a carousel

This sample demonstrates how to use the manifest to extend a web template to display locations on a web page in a rotating carousel format.

:::image type="content" source="media/web-template-components/loc-carousel-in-studio.png" alt-text="Web template component as a location carousel.":::

## How to create a web template component to display locations

### Step 1: Preparation

1. Create a table in your environment with the matching columns (name, address, and image). 
2. Copy the table's logical name.
1. Create a few sample records on the new table.

### Step 2: Set up the web template

1. Copy the source code into a new web template in your environment. See [How to create a web template component](web-templates-as-components-how-to.md) for more details.

    ```html
    
    {% fetchxml locationsQuery %}
        <fetch mapping='logical'>
        <entity name='cr50f_place'>
            <attribute name='cr50f_name' />
            <attribute name='cr50f_address' />
            <attribute name='cr50f_image' />
        </entity>
        </fetch>
    {% endfetchxml %}
    
    <h2>{{ title | default: "Locations" }}</h2>
    
    {% assign interval = interval | integer %}
    {% assign count = count | integer %}
    {% assign height = height | integer %}
    
    <span>Showing {{ count }} out of {{ locationsQuery.results.entities.size }}</span>
    {% if locationsQuery.results.entities.size > 0 %}
        <div id="carousel-example-generic"
        class="carousel slide"
        data-ride="carousel"
        data-interval="{{interval}}">
        <!-- Indicators -->
        <ol class="carousel-indicators">
            {% for location in locationsQuery.results.entities limit: count %}
            <li
                data-target="#carousel-example-generic"
                data-slide-to="{{forloop.index0}}"
                class="{% if forloop.first %}active{% endif %}"></li>
            {% endfor %}
        </ol>
        <!-- Wrapper for slides -->
        <div class="carousel-inner" role="listbox">
            {% for loc in locationsQuery.results.entities limit: count %}
            <div class="item {% if forloop.first %}active{% endif %}" style="background-image:url('{{loc.cr50f_image.Url}}&Full=true'); height: {{height | default:500}}px">
                <div class="carousel-caption" style="background:white">
                <h3>{{ loc.cr50f_name }}</h3>
                <p>{{ loc.cr50f_address }}</p>
                </div>
            </div>
            {% endfor %}
        </div>
        <!-- Controls -->
        <a
            class="left carousel-control"
            href="#carousel-example-generic"
            role="button"
            data-slide="prev">
            <span class="glyphicon glyphicon-chevron-left" aria-hidden="true"></span>
            <span class="sr-only">Previous</span>
        </a>
        <a
            class="right carousel-control"
            href="#carousel-example-generic"
            role="button"
            data-slide="next">
            <span class="glyphicon glyphicon-chevron-right" aria-hidden="true"></span>
            <span class="sr-only">Next</span>
        </a>
        </div>
    {% endif %}
    
    <style>
        .carousel .item {
        background-size: cover;
        background-repeat: no-repeat;
        }
    </style>
    
    {% manifest %}
        {
        "type": "Functional",
            "displayName": "Locations Slider",
            "description": "Locations slider using the table 'Place' as the data source",
            "tables": ["cr50f_place"],
            "params": [
                {
                "id": "title",
                "displayName": "Title",
                "description": ""
            },{
                "id": "interval",
                "displayName": "Interval",
                "description": "The amount of time to delay between automatically cycling an item. If false, carousel will not automatically cycle. Default: 5000ms"
            },{
                "id": "count",
                "displayName": "Count",
                "description": "The number of locations to display"
            },{
                "id": "height",
                "displayName": "Slide's height",
                "description": "In px, default: 500px"
            }
          ]
        }
    {% endmanifest %}
    
    ```

1. Replace all instances of 'cr50f' with the new table's schema name. This should take care of the fetchXML properties and throughout the HTML and `{% manifest %}`.

### Step 3: Use the web template

1. Add the new web template to the page copy of a page, for example, add `{% include 'locations-slider' title:'Locations' interval:'6500' count:'4' height:'500' %}` or `{% include 'locations-slider' title:'Locations' interval:'3500' count:'3' height:'750' %}`
1. Edit and configure the web template's properties in design studio.
1. Reuse the component across different web pages as needed and repeat the previous step to configure the display based on your requirements.
1. Select **edit data** to update records on the newly created table.

## See Also

- [How to create a web template component](web-templates-as-components-how-to.md)
- [Display locations as cards](web-templates-as-components-location-cards.md)
- [Display product reviews as cards](web-templates-as-components-product-reviews.md)