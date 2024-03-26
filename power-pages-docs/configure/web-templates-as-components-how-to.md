---
title: "How to: Create a web template component"
description: Learn how to create a web templates component in Power Pages.
author: ckwan-ms

ms.topic: how-to
ms.custom: 
ms.date: 09/15/2023
ms.subservice:
ms.author: ckwan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - clromano
    - ProfessorKendrick
---

# How to: Create a web template component

Creating a web template component allows you to build a configurable, repeatable component that can be customized for each specific instance used.

In this how-to, you learn how to:

> [!div class="checklist"]
> * Define a manifest and specify the parameters to be passed to a web template component
> * Create a web template component
> * Add the web template component to a web page
> * Configure the parameters using the design studio

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](../getting-started/trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](../getting-started/create-manage.md).

## Create a web template component

In the steps below, we create a web template component that displays feedback records from a Microsoft Dataverse table in a card layout format, with a button to provide a review. You are able to define the number of cards can configuration.

### Create a Dataverse table to use in the web template component

In our example, we create a Dataverse table called *Review* for our process. For more information on how to create Dataverse tables, see [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md). You can modify these steps to reflect your own business processes.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select a site where you want to add the web template component and select **Edit**. 

1. In the design studio, select the **Data** workspace.

1. Create a Dataverse table called *Review* with the following properties:

    > [!TIP] 
    > - The following table is just an example, feel free to create tables to match your own business processes.

    | Column name | Column data type |
    | - | - |
    | Name | Text (existing *name* column) |
    | Content | Multiple lines of text |
    | Rating | Whole Number (minimum value: 1, maximum value: 5) |

    :::image type="content" source="media/web-template-components/example-table-data.png" alt-text="Create table to use in the how to.":::

1. Add some sample records to the table.

1. In the **Set up** workspace, add a [table permission](../security/table-permissions.md) to allow read access and assign to appropriate web roles.

### Create web template with manifest

1. In the [Portal Management app](portal-management-app.md), in the **Content** section, choose **Web Templates** and select **New** from the main menu to create a new web template.

1. Enter *reviews* for the **Name** (or other value that reflects your requirement).

1. Copy and paste the following code into the **Source** field of the web template record, replace values prefixed with `cr54f` with the prefix used in your own environment.

    ```html
    {% fetchxml postsQuery %}
    <fetch mapping='logical'>   
       <entity name='cr54f_review'>  
            <attribute name='cr54f_name'/>   
            <attribute name='cr54f_content'/>   
            <attribute name='cr54f_rating'/>   
            <attribute name='createdon'/>  
            <order attribute='createdon' descending='false'/>   
       </entity>   
    </fetch>
    {% endfetchxml %}
    {% assign posts_count = count | times: 1 %}
    {% assign col_div = columns | integer %}
    <h2>({{postsQuery.results.entities.size}}) {{name | default:"Feedback entries (default)"}} </h2>
    {% if postsQuery.results.entities.size > 0 %}
        <div class="col-sm-12">
          <ul style="list-style: none;">
              {% for post in postsQuery.results.entities limit:count %}
                  <li class="col-md-{{ 12 | divided_by: col_div }}">
                      <div class="panel panel-{% if post.cr54f_rating < cutoff %}danger{% else %}default{% endif %}">
                          <div class="panel-heading">{{post.cr54f_name}} <span class="badge" style="float:right">{{post.cr54f_rating}}</span></div>
                          <div class="panel-body">
                              <p>{{post.cr54f_content}}</p>
                          </div>
                          <div class="panel-footer">{{post.createdon}}</div>
                      </div>
                </li>
              {% endfor %}
          </ul>
        </div>
        {% if postsQuery.results.entities.size > count %}
          <hr/>
          <button onclick="alert('Not yet implemented :)')" class="button1" style="margin: 0 auto; display:block">{{load_more_label | default: "Load More"}}</button>
        {% endif %}
    {% endif %}
    
    {% manifest %} 
    {
      "type": "Functional",
      "displayName": "Posts",
      "description": "Shows all posts",
      "tables": ["cr54f_review"],
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
          "description": "Number between 1 and 5"
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

### Add web template component to web page

Once you have created the web template component, you can add it to a web page.

1. In the Power Pages [design studio](../getting-started/use-design-studio.md), select the page that you want to add the web template component to.

1. Select **Edit Code** which opens the [Visual Studio Code for the Web](visual-studio-code-editor.md) for the webpage.

1. Enter the following include statement that references the web template you created earlier, you can replace the name with the name of your own web template:

    `{% include "reviews" %}` 

1. Select **CTRL-S** to save the code. Return to design studio and select **Sync**. A preview of the component on your webpage will display. 

1. Select **Edit custom component** and you can configure the parameters that are defined in the manifest of the web template component you created above.

    :::image type="content" source="media/web-template-components/howto-configure-parameters.png" alt-text="How to add parameters to custom component.":::

1. Preview the site to view the layout, return to the design studio and experiment with different layout options.
