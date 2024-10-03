---
title: Create a custom page template to render an RSS feed
description: Learn how to create a custom page template and use it to render an RSS feed.
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

# Create a custom page template to render an RSS feed

In this example, we'll create a custom page template to render an [RSS feed](https://en.wikipedia.org/wiki/RSS) of news articles, using Liquid in a custom page layout. More information: [Web templates](../web-templates.md)  

## Step 1: Create a new view

First, we'll create a new [view](../data-workspace-views.md) that we'll use to load the data for our feed. In this example, we'll make it a view on Web Pages, and use this table to store our articles. We can use this view to configure the sorting and filtering of results, and include as columns the table attributes that we want available in our Liquid template.

:::image type="content" source="media/render-rss/create-view.png" alt-text="Create a view.":::

## Step 2: Create a web template for RSS feed

In this step, we'll create a web template for our RSS feed. This template will be applied to a particular webpage in our website, so we'll use the title and summary of that page as the title and description of the feed. The we'll use the entityview tag to load our newly-created News Articles view. More information: [Dataverse entity tags](dataverse-liquid-tags.md). Note that we also set the **MIME Type** field of the Web Template to application/rss+xml. This indicates what the response content type could be when our template is rendered.  

:::image type="content" source="media/render-rss/web-template-rss-feed.png" alt-text="Configure a web template for an RSS feed.":::

### RSS Feed (Web Template)

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## Step 3: Create a page template to assign RSS feed template

Now, we'll create a new page template, allowing us to assign our RSS feed template to any webpage in our website. Note that we deselect **Use Website Header and Footer**, as we want to take over rendering of the entire page response for our feed.

:::image type="content" source="media/render-rss/page-template-rss-feed.png" alt-text="Configure a page template for an RSS feed.":::

## Step 4: Create a web page to host RSS feed

Now all that's left is to [create a new web page](../../getting-started/first-page.md) using the **RSS Feed** page layout to host our feed. When we request this new web page, we'll receive our RSS feed XML:

:::image type="content" source="media/render-rss/rss-feed-example.png" alt-text="Example of an RSS feed.":::

In this example, we've seen how we can combine Liquid, web templates, Dataverse views, and site content management features to create a custom RSS feed. The combination of these features adds powerful customization capabilities to any Power Pages application.

### See also

[Create a custom page template by using Liquid and a web template page template](../../getting-started/tutorial-add-custom-page-layout.md)  
[Render the list associated with the current page](render-list-current-page.md)  
[Render a website header and primary navigation bar](render-site-header-primary-navigation.md)  
[Render up to three levels of page hierarchy by using hybrid navigation](hybrid-navigation-render-page-hierarchy.md)  

