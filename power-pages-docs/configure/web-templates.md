---
title: Web templates
description: Learn how to create and manage web templates in Power Pages.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 05/23/2023
ms.subservice:
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - GitanjaliSingh33msft
---

# Web templates

A web template is a Power Pages site metadata record that is used to store template source content. A web template will generally contain Liquid for dynamic content rendering and is the central table used to integrate Liquid templates with the rest of Power Pages.

Web Templates can be included in other content or combined with other templates by using template tags, and are referenced in these tags by their **Name** attribute. They can also be used to create entire custom page layouts, or create custom headers and footers for your Power Pages website.

## Web template attributes

|  Attribute         |     Description                                                                                                                                                                                                                                                                            |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Name    |                                                                         The name of the template. Used to reference this template when it's included in other content or extended by other templates.                                                                         |
|  Source   |                                  The source content of the template. A source code editor with syntax highlighting and other code editing features is provided for this field in Power Apps.                                  |
| MIME Type | Optionally provides a MIME type for the content of the template. A type of text/html is assumed if none is provided. This value will only be used in cases where the template is associated with a Page Template and controls the rendering of all content for that template. |
|           |                                                                                                                                                                                                                                                                                 |

## Web templates as custom page layouts

Web templates can be used with page templates to create new custom page layouts for the Power Pages sites.

To create a new page template based on a web template select a **Type** of web template when creating a new [page template](/power-apps/maker/portals/configure/page-templates) record. Then select a **Web Template**.

Note the option **Use Website Header and Footer** (which is checked by default). If this is checked, your web template will control rendering of all page content between the global website header and footer. If this option is unchecked, your web template will be responsible for rendering the entire response in the case that you're rendering HTML, this means everything from the doctype to the root &lt;html&gt; tags, and everything in between.

While the most common use cases for web templates will be to render HTML, rendering the entire response (by deselecting **Use Website Header and Footer**) gives you the option of rendering any text-based format you choose. This is where the **MIME Type** attribute of web template becomes relevant. When a page template that doesn't use the website header and footer is rendered, the HTTP response Content-Type header will be set to the MIME Type of the associated web template (text/html will be used if no MIME Type is provided.), providing a wide variety of options for rendering non-HTML content by using Liquid. A common use case would be to render an [RSS](https://en.wikipedia.org/wiki/RSS) feed, by setting a MIME Type of application/rss+xml.  

## Web templates as website headers and footers

Web templates can also be used to override the global header and footer used by Power Pages. Set the **Header Template** or **Footer Template** field of your website to the web template of your choice. If you override **Website Header**, your selected template assumes responsibility for rendering the primary navigation, sign-in/sign-out links, search interface, and so on, for your site interface elements that are normally handled by the default header template.

## Built-in web templates

There's a set of pre-made Liquid templates available within Power Pages. To use them, you must include them by name, using the list below as a reference.

| Name                        | Description                                                                                                                                                                                                                             | Code                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| Ad                          | This template renders an ad by name, or a random ad from an ad placement.                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| Blogs                       | This template renders recent blog posts in a list group.                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| Breadcrumbs                 | This template renders links of ancestor pages back to the Home page from the current page.                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| Child Link List Group       | This template renders links to any child pages of the current page in a list group.                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| Events: Upcoming            | This template renders links to events that occur between now and 60 days from now.                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| Forums                      | This template renders a list of the website's forums with their respective number of threads and posts.                                                                                                                                 | `{% include 'forums' %}`                                       |
| Layout 1 Column             | This template renders a single column layout containing breadcrumbs, page title, and page copy content.                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| Layout 2 Column Wide Left   | This template renders a two column layout. The left column is wider than the right. It contains breadcrumbs, page title at the top of the page and the page copy content is located in the left column.                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| Layout 2 Column Wide Right  | This template renders a two column layout. The right column is wider than the left. It contains breadcrumbs, page title at the top of the page and the page copy content is located in the right column.                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| Layout 3 Column Wide Middle | This template renders a three column layout. The middle column is wider than the left and right. The layout contains breadcrumbs and the page title at the top of the page and the page copy content is located in the middle column.   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| Page Copy                   | This template renders the editable page copy content HTML with support for embedded Liquid.                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| Page Header                 | This template renders the page title.                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| Poll                        | This template renders a poll by name, or a random poll from a poll placement.                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| Search                      | This template renders a basic search form with a single text input and search button.                                                                                                                                                   | `{% include 'search' %}`                                                             |
| Side Navigation             | This template renders a vertical tree view style navigation. It has links to ancestor pages back to the first level (or specified depth offset), links to sibling pages of the current page, and links to children of the current page. | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| Snippet                     | This template renders an editable HTML content snippet by name.                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| Top Navigation              | This template renders an editable nav bar with drop-down menus for the Primary Navigation web link set.                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Weblink List Group          | This template renders a list group of links for a web link set.                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

## Web templates as components (preview)

Web templates can be created and used as components in web pages to allow makers to use these reusable components and provide parameters to meet requirements.

More information: [Web templates as components](web-templates-as-components.md)

### See also

- [Create a custom page layout](../getting-started/tutorial-add-custom-page-layout.md)
- [Understand Liquid operators](liquid/liquid-operators.md)  
- [Liquid types](liquid/liquid-types.md)  
- [Conditional](liquid/liquid-conditional-operators.md)  
- [Liquid Objects](liquid/liquid-objects.md)  
- [Liquid Tags](liquid/liquid-tags.md)  
- [Liquid Filters](liquid/liquid-filters.md)  

