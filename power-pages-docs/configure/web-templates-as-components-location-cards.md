---
title: Display locations as cards
description: Learn how to create a web templates components to display locations in Power Pages.
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

# Display locations as cards

This sample demonstrates how to use the manifest to extend a web template to display locations on a web page in a card format.

:::image type="content" source="media/web-template-components/loc-cards-in-studio.png" alt-text="Web template component as a location card.":::

## How to create a web template component to display locations

### Step 1: Preparation

1. Create a table in your environment with the matching columns (name, address, and link). 
1. Copy the table's logical name.
1. Create a few sample records on the new table.

### Step 2: Set up the web template

1. Copy the source code into a new web template in your environment. See [How to create a web template component](web-templates-as-components-how-to.md) for more details.

    ```html
    
    {% fetchxml locationsQuery %}
      <fetch mapping='logical' output-format='xml-platform'>
        <entity name='cr50f_place'>
          <attribute name='cr50f_name' />
          <attribute name='cr50f_address' />
          <attribute name='cr50f_link' />
        </entity>
      </fetch>
    {% endfetchxml %}
    
    <h2>{{ name | default: 'Cards' }}</h2>
    
    {% assign place_count = count | integer %}
    {% assign column_count = columns | integer %}
    
    <ul style="list-style:none" class="grid">
      {% for loc in locationsQuery.results.entities limit: place_count %}
        <li class="col-md-{{ 12 | divided_by: column_count }}">
          <div class="panel panel-default">
            <div class="panel-heading">
              <h3>{{ loc.cr50f_name }}</h3>
            </div>
            <div class="panel-body">
              <p>{{ loc.cr50f_address }}</p>
            </div>
            {% if footer == 'true' and loc.cr50f_link %}
              <div class="panel-footer">
                <a href="{{loc.cr50f_link}}">Learn more about {{ loc.cr50f_name }}</a>
              </div>
            {% endif %}
          </div>
        </li>
      {% endfor %}
    </ul>
    {% manifest %}
      {
      "type": "Functional",
                  "displayName": "Cards",
                  "description": "Custom card component using the table 'Place' as the data source",
                  "tables": [
                    "cr50f_place"
                  ],
                  "params": [
                    {
                      "id": "name",
                      "displayName": "Title",
                      "description": "Let's give it a title"
                    },
                    {
                      "id": "count",
                      "displayName": "Count",
                      "description": "No. of items"
                    },
                    {
                      "id": "columns",
                      "displayName": "# of Columns",
                      "description": "less than 12"
                    },
                    {
                      "id": "footer",
                      "displayName": "Footer",
                      "description": "Show the footer of the cards"
                    }
                  ]
              }
    {% endmanifest %}
    ```

1. Replace all instances of **cr50f** with the new table's schema name. This should take care of the fetchXML properties as well as throughout the HTML and `{% manifest %}`.
    
### Step 3: Use the web template

1. Add the new web template to the page copy of a page, for example, add `{% include 'Cards' %}` using the [Visual Studio Code for the Web](./visual-studio-code-editor.md).
1. Edit and configure the web template's properties in design studio.
1. Re-use the component across different web pages as needed and repeat the previous step to configure the display based on your requirements.
1. Select **edit data** to update records on the newly created table.

## See Also

- [How to create a web template component](web-templates-as-components-how-to.md)
- [Display records as a carousel](web-templates-as-components-carousel.md)
- [Display product reviews as cards](web-templates-as-components-product-reviews.md)
