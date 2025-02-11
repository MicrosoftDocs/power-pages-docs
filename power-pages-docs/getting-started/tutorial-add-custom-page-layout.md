---
title: "Tutorial: Add custom page layout to your site"
description: Learn how to add a custom page layout to your Power Pages sites.
author: gitanjalisingh33msft
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 02/10/2025
ms.subservice:
ms.author: gisingh
ms.reviewer: danamartens 
contributors:
    - gitanjalisingh33msft
---
# Tutorial: Add custom page layout to your site

When you create new webpages using the Pages workspace, you have a choice of provided page layouts. In some cases, you might want to create a custom page layout to display information in a certain format or to provide a specialized user interface.

In this tutorial, you learn how to create a custom page layout using [Liquid](../configure/liquid-overview.md).

Our example scenario is to build a two-column template with the main site menu as left-side navigation and the page content to the right.

Here are the following steps and assets that are created to provide a custom page layout:

> [!div class="checklist"]
> * We'll create a common base web template with custom code to establish the basic page layout.
> * We'll create a second web template with additional code to demonstrate the modular features of web templates.
> * We'll also create a page template record referencing the web template that configures how the page layout is rendered on the site.
> * Finally, we'll create a web page using the custom page layout.

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md)
- A Power Pages site created. [Create a Power Pages site](create-manage.md)
- Basic knowledge of HTML and [Liquid](../configure/liquid-overview.md)

## Step 1: Create a web template and write the Liquid template code

First, create your web template and write the Liquid template code. You're likely to reuse some common elements of this template in future templates. So, create a common base template that you extend with your specific template. Your base template provides breadcrumb links, your page title/header, and defines your two-column layout.

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In the **design studio**, choose **...** and then select **Portal Management**. Use the Portal Management app to create a web template record and enter your custom code.

    :::image type="content" source="media/tutorial-custom-layouts/portal-management-app.png" alt-text="Selecting the ellipse directs you to a menu where you can choose the portal management app.":::

1. In the **Portal Management app**, scroll to the **Content** section and select **Web Templates**.

1. From the **Active Web Templates** screen, select **New**.

1. Name the web template **Two Column Layout**.

    :::image type="content" source="media/tutorial-custom-layouts/two-column-layout.png" alt-text="Custom web template for the two column layout.":::

1. Paste the following code into the **Source** field:

    ```html
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          {% for crumb in page.breadcrumbs -%}
            <li>
              <a href={{ crumb.url }}>{{ crumb.title }}</a>
            </li>
          {% endfor -%}
          <li class=active>{{ page.title }}</li>
        </ul>
        <div class=page-header>
          <h1>{{ page.title }}</h1>
        </div>
      </div>
      <div class=row>
        <div class=col-sm-4 col-lg-3>
          {% block sidebar %}{% endblock %}
        </div>
        <div class=col-sm-8 col-lg-9>
          {% block content %}{% endblock %}
        </div>
      </div>
    </div>
    ```

1. Select **Save**.

## Step 2: Create a new web template that extends our base layout template

We're creating a web template that reads the navigation record from the associated web page (see below). We also extend the base template we created in the previous step. Web templates can be used as reusable components when creating advanced sites.

1. In the **Portal Management app**, scroll to the **Content** section and select **Web Templates**.

1. From the **Active Web Templates** screen, select **New**.

1. Name the web template **Weblinks Left Navigation**.

:::image type="content" source="media/tutorial-custom-layouts/web-links-left-navigation.png" alt-text="Screenshot of a custom web template with navigation and content.":::

    ### Weblinks Left Navigation (Web Template)

    Note how the code uses the Liquid `extends` keyword to incorporate the base layout template.

    ```html
    {% extends 'Two Column Layout' %}
    
    {% block sidebar %}
      {% assign weblinkset_id = page.adx_navigation.id %}
      {% if weblinkset_id %}
        {% assign nav = weblinks[page.adx_navigation.id] %}
        {% if nav %}
          <div class=list-group>
            {% for link in nav.weblinks %}
              <a class=list-group-item href={{ link.url }}>
                {{ link.name }}
              </a>
            {% endfor %}
          </div>
        {% endif %}
      {% endif %}
    {% endblock %}
    
    {% block content %}
      <div id="mainContent" class = "wrapper-body" role="main">
        {% include 'Page Copy' %}
      </div>
    {% endblock %}
    ```

## Step 3: Create a new page template based on the web template

In this step, create a new page template based on the web template created in the previous step. The page template is required for the custom page layout to be an option you can select when creating a new web page.

1. In the **Portal Management app**, scroll to the **Website** section and select **Page Templates**.

1. From the **Active Page Templates** screen, select **New**.

1. Fill in the fields:

    |Field  |Value  |
    |---------|---------|
    | Name | Type in a name. |
| Website | Select the website to which the theme is applied. To display a list of available options, put your cursor in the field and hit enter on your keyboard. |
    | Type | Choose **Web Template** |
    | Web Template | Select **Web Links Left Navigation** (or whatever you named your web template). |
    | Use Website Header and Footer | Checked. |
    | Is Default | Unchecked. |
    | Table Name | None selected. |
    | Description | A description of your page template. |

    :::image type="content" source="media/tutorial-custom-layouts/page-template.png" alt-text="Page template weblinks left navigation layout." border="true":::

1. Select **Save**.

## Step 4: Create a web page to display content

1. In the **design studio**, select **Sync**. This action brings updates made in the Portal Management app to the design studio.

1. In the **Pages** workspace, select **+ Page**.

1. In the **Add a page** dialog:
    1. Enter **Page name**.
    1. From the **Custom layouts**, select your custom page layout.
    1. Select **Add**.

    :::image type="content" source="media/tutorial-custom-layouts/select-custom-layout.png" alt-text="Select custom page layout when creating a new web page.":::

1. Add any more content to the editable sections of the page.

### Additional page configuration

In this example, link the navigation record to the content page for the custom code to render the menu on the left navigation.

1. In the **design studio**, choose **...** and then select **Portal Management**. Use the Portal Management app to add more configurations to your page.

1. In the **Portal Management** app, scroll to the **Content** section and select **Web Pages**.

1. Locate and open the page you created previously in the **Pages** workspace. This opens the root webpage. Make changes in the related localized content page.

1. Within the **Localized Content** section, select the localized content web page.

    :::image type="content" source="media/tutorial-custom-layouts/web-page.png" alt-text="Screenshot showing selection of the localized content page.":::

    > [!NOTE]
    > If you have multiple languages provisioned, update each localized page.

1. Go to the **Miscellaneous** section and select the web link set to display in the **Navigation** field.

    :::image type="content" source="media/tutorial-custom-layouts/navigation-link.png" alt-text="Screenshot of the navigation lookup." border="true":::

1. Save your changes and return to the **design studio**.

1. Select **Preview** and then **Desktop** to view your custom page with the side navigation.

    :::image type="content" source="media/tutorial-custom-layouts/custom-page.png" alt-text="Web page using custom layout." border="true":::

### See also

- [Create a custom page layout](../configure/custom-page-layouts.md)
- [Liquid overview](../configure/liquid-overview.md)
