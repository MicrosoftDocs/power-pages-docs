---
title: Display product reviews as cards
description: Learn how to create and manage web templates as product review cards in Power Pages.
author: clromano

ms.topic: how-to
ms.custom: 
ms.date: 07/25/2023
ms.subservice:
ms.author: clromano
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - clromano
    - ProfessorKendrick

---

# Display product reviews as cards

This sample demonstrates how to use the manifest to extend a web template to display product reviews on a web page in a card format.

:::image type="content" source="media/web-template-components/prod-review-sample-studio-2.png" alt-text="Web template component as a product review.":::

## How to create a web template component to display product reviews

### Step 1: Preparation

1. Create a table in your environment with the matching columns (name, content, and rating) 
1. Copy the table's logical name.
1. Create a few sample records on the new table.
    
### Step 2: Set up the web template

1. Copy the source code into a new web template in your environment. See [How to create a web template component](web-templates-as-components-how-to.md) for more details.

    ```html
    {% fetchxml postsQuery %}
      <fetch mapping='logical'>
        <entity name='cr50f_review'>
          <attribute name='cr50f_name' />
          <attribute name='cr50f_content' />
          <attribute name='cr50f_rating' />
          <attribute name='createdon' />
          <order attribute='createdon' descending='false' />
        </entity>
      </fetch>
    {% endfetchxml %}
    
    {% assign posts_count = count | integer %}
    {% assign column_count = columns | integer %}
    {% assign cutoff = cutoff | integer %}
    
    <h2>{{ name | default: "Feedback entries (default)" }}
    </h2>
    
    <span>Showing {{ posts_count }} out of {{ postsQuery.results.entities.size }}</span>
    {% if postsQuery.results.entities.size > 0 %}
      <div class="col-sm-12">
        <ul style="list-style:none" class="grid">
          {% for post in postsQuery.results.entities limit: posts_count %}
            <li class="col-md-{{ 12 | divided_by: column_count }}">
              <div class="panel panel-{% if post.cr50f_rating < cutoff %}danger{%elsif post.cr50f_rating == cutoff%}warning{%elsif post.cr50f_rating == 10%}success{% else %}default{% endif %}">
                <div class="panel-heading">{{ post.cr50f_name }}
                  <span class="badge" style="float:right">{{ post.cr50f_rating }}</span>
                </div>
                <div class="panel-body" style="height:150px">
                  <p>{{ post.cr50f_content }}</p>
                </div>
                <div class="panel-footer" style="height:55px">
                  <span>{{ post.createdon }}</span>
                  {% if post.cr50f_rating < cutoff %}
                    <button
                      type="button"
                      class="btn btn-danger"
                      style="float:right"
                      onclick="alert('Flagging this review!')">
                      <span class="glyphicon glyphicon-flag" aria-hidden="true"></span>
                    </button>
                  {% endif %}
                </div>
              </div>
            </li>
          {% endfor %}
        </ul>
      </div>
      {% if postsQuery.results.entities.size > count %}
        <hr/>
        <button
          onclick="alert('Not yet implemented :)')"
          class="button1"
          style="margin: 0 auto; display:block">{{ load_more_label | default: "Load More" }}</button>
      {% endif %}
    {% endif %}
    
    {% manifest %}
      {
      "type": "Functional",
        "displayName": "Posts",
        "description": "Shows all posts",
        "tables": ["cr50f_review"],
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
            "id": "cutoff",
            "displayName": "Limit for review",
            "description": "Number between 1 and 10"
          },
          {
            "id": "load_more_label",
            "displayName": "Load more label",
            "description": ""
          }
        ]
      }
    {% endmanifest %}
    ```
    
1. Replace all instances of **cr50f** with the new table's schema name. This should take care of the fetchXML properties and throughout the HTML and `{% manifest %}`.

### Step 3: Use the web template

1. Add the new web template to the page copy of a page, for example, add `{% include 'product-reviews' name:'Product Review' count:'15' columns:'3' cutoff:'5' load_more_label:'Load more entries' %}` or `{% include 'product-reviews' name:'Product Review' count:'3' columns:'3' cutoff:'5' load_more_label:'Load more entries' %}` using the [Visual Studio Code for the Web](./visual-studio-code-editor.md).
1. Edit and configure the web template's properties in design studio.
1. Reuse the component across different web pages as needed and repeat the previous step to configure the display based on your requirements.
1. Select **edit data** to update records on the newly created table.

## See Also

- [How to create a web template component](web-templates-as-components-how-to.md)
- [Display records as a carousel](web-templates-as-components-carousel.md)
- [Display locations as cards](web-templates-as-components-location-cards.md)
