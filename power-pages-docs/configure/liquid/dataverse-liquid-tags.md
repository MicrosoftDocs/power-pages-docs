---
title: Dataverse Liquid tags
description: Learn about Power Pages Dataverse Liquid tags available when building sites.
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

# Dataverse Liquid tags

Microsoft Dataverse Liquid tags are used to load and display Dataverse data, or use other Power Pages framework services. These tags are Dataverse-specific extensions to the Liquid language.

## chart

Adds a Power Apps model-driven app chart to a web page. The chart tag can be added in the **Copy** field on a web page or in the **Source** field on a web template. For steps to add a Power Apps model-driven app chart to a web page, see [Add a chart to a web page in Power Pages](/power-apps/maker/portals/configure/add-chart).

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### Parameters

There are two parameters to be provided with the chart tag: chart id and viewid.

**chart id**

Visualization ID of the chart. You can get the id by exporting the chart.

**viewid**

ID of the table when opened in view editor. 

## powerbi

Adds the Power BI dashboards and reports within pages. The tag can be added in the **Copy** field on a web page or in the **Source** field on a web template. For steps to add a Power BI report or dashboard to a webpage in Power Pages, see [Add a Power BI report or dashboard to a webpage in Power Pages](../../getting-started/add-power-bi.md).

> [!NOTE]
> For the tag to work, you must [enable Power BI integration](../../admin/set-up-power-bi-integration.md) from Power Pages hub in the Power Platform admin center. If the Power BI integration isn't turned on, dashboard or report aren't displayed.

### Parameters

The powerbi tag accepts the following parameters:

**path**

Path of the Power BI report or dashboard. If the Power BI report or dashboard is secure, you must provide the authentication type.

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Type of authentication required for the Power BI report or dashboard. Valid values for this parameter are:

- **Anonymous**: Allows you to embed publish to web Power BI reports. The default authentication type is Anonymous. When using the authentication type as Anonymous, you must get the Power BI report URL as described at: [Publish to web from Power BI](/power-bi/service-publish-to-web)

- **AAD**: Allows you to share secure Power BI reports or dashboards to Power BI Microsoft Entra ID authenticated users.

- **powerbiembedded**: Allows you to share the secure Power BI reports or dashboards to external users who don't have Power BI license or Microsoft Entra authentication setup. For information on Power BI Embedded service setup, see [Enable Power BI Embedded service](../../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service).

When you add a secure Power BI report or dashboard, make sure it's shared with the Power Pages Microsoft Entra or Power BI Embedded services.

> [!NOTE]
> The values for the `authentication_type` parameter are case insensitive.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

You can also filter the report on one or more values. The syntax to filter a report is:

URL?filter=**Table**/**Field** eq '**value**'

For example, say you want to filter the report to see data for a contact named Bert Hair. You must append the URL with the following data:

`?filter=Executives/Executive eq 'Bert Hair'`

The complete code is:

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

More information on filtering a report: [Filter a report using query string parameters in the URL](/power-bi/service-url-filters)

> [!NOTE]
> Anonymous report doesn't support filtering. 

You can also create a dynamic path by using the `capture ` Liquid variable:

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

More information on Liquid variable: [Variable tags](variable-tags.md)

**tileid**

Displays the specified tile of the dashboard. You must provide the ID of the tile.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**roles**

Roles assigned to the Power BI report. This parameter works only when the **authentication_type** parameter is set to **powerbiembedded**.

If you defined roles in Power BI and assigned them to reports, you must specify the appropriate roles in the **powerbi** Liquid tag. Roles allow you to filter the data to be displayed in a report. You can specify multiple roles separated by a comma. For more information on defining roles in Power BI, see [Row-level security (RLS) with Power BI](/power-bi/service-admin-rls).

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

If you assigned a role to a Power BI report, and didn't specify the **roles** parameter in the Liquid tag or didn't specify a role in the parameter, an error is displayed.

> [!TIP]
> If you want to use the web roles defined in your site as the Power BI roles, you can define a variable and assign web roles to it. You can then use the defined variable in the Liquid tag.
>
> Let's say you defined two web roles as Region_East and Region_West in your site. You can join them by using the code: `{% assign webroles = user.roles | join: ", " %}`
>
> In the code snippet, `webroles` is a variable that stores the Region_East and Region_West web roles.
>
> Use the `webroles` variable as follows in the Liquid tag:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## editable

Renders a given Power Pages CMS object as editable on the site, for users with content editing permission for that object. Editable objects include [page](liquid-objects.md#page), [snippets](liquid-objects.md#snippets), and [weblinks](liquid-objects.md#weblinks).  

```
{% editable page 'adx_copy' type: 'html', title: 'Page Copy', escape: false, liquid: true %}

{% editable snippets Header type: 'html' %}

<!--

An editable web link set required a specific DOM structure, with

certain classes on the containing element, as demonstrated here.

-->

{% assign primary_nav = weblinks[Primary Navigation] %}

{% if primary_nav %}

<div {% if primary_nav.editable %}class=xrm-entity xrm-editable-adx_weblinkset{% endif %}>

<ul>

<!-- Render weblinks... -->

</ul>

{% editable primary_nav %}

</div>

{% endif %}
```

### Parameters

The first parameter provided to editable is the editable object, such as a web link set, snippets, or the current page. The optional second parameter is to specify an attribute name or key within that object that is to be rendered and edited. This value might be the name of a table attribute, or a snippet name, for example.

After these initial parameters, the tag supports many optional named parameters.

**class**

Specifies a class attribute value for the root element rendered by this tag.

**default**

A default value rendered in the case that the editable item has no value.

**escape**

A Boolean value indicating whether a value rendered by this tag is HTML-encoded. This value is false by default.

**liquid**

A Boolean value indicating whether any Liquid template code found within the text value rendered by this tag should be processed. This value is true by default.

**tag**

The name of the container HTML tags rendered by this tag. This tag renders div elements by default. It's recommended that you choose between div or span as a value for this parameter.

The name of the container HTML tags rendered by this tag. This tag renders `div` elements by default. It's recommended to choose between `div` or `span` for this parameter.

**title**

Specifies a label for this editable item within the content editing interface. If none is provided, a friendly label is generated automatically.

**type**

A string value indicating the type of editing interface to be presented, for editable text values. Valid values for this parameter are html or text. html is the default.

## entitylist

Loads a given list, by name or ID. The properties of the list can then be accessed using an [entitylist object](liquid-objects.md#entitylist) available within the tag block. To render the actual result records of the list, use the [entityview](#entityview) tag within the block.  

If the list is loaded successfully, the content within the block is rendered. If the list isn't found, the block content isn't rendered.

```
{% entitylist name:My List %}

Loaded list {{ entitylist.adx_name }}.

{% endentitylist %}
```
By default, the entitylist object is given the variable name entitylist. Optionally, a different variable name can be provided.

```
{% entitylist my_list = name:My List %}

Loaded list {{ my_list.adx_name }}.

{% endentitylist %}
```

### Parameters

Provide **only one** of id, name, or key to select the List to load.

**id**

Loads a list by [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) ID. id must be a string that can be parsed as a GUID.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded list {{ entitylist.adx_name }}.

{% endentitylist %}
```

Generally, literal GUID strings aren't used. Instead, id is specified using a GUID property of another variable.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**name**

Loads a list by name.

```
{% entitylist name:My List %}

Loaded list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**key**

Loads a list by ID **or** name. If the provided key value can be parsed as a [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier), the list is loaded by ID. Otherwise, it's loaded by name.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**language\_code**

A Dataverse integer language code to select the list localized labels to be loaded. If no language\_code is provided, the default language of the site application Dataverse connection is used.

```
{% entitylist name:"My List", language_code:1033 %}

Loaded list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## entityview

Loads a given Dataverse view, by name or ID. The properties of the view ߝ view column metadata, paginated result records, etc. can then be accessed using an [entityview object](liquid-objects.md#entityview) that is available within the tag block.  

If the view is loaded successfully, the content within the block is rendered. If the view isn't found, the block content isn't rendered.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

By default, the entityview object is given the variable name entityview. Optionally, a different variable name can be provided.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

If entityview is nested within an entitylist block, it inherits its default configuration (result page size, filter options, etc.) from the list. If no view id or name parameters are provided to entityview, it loads the default view from the enclosing entitylist.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### Parameters

Provide **either** id **or** logical\_name with name to select the Dataverse view to load. If neither is provided, and the entityview tag is nested within an entitylist tag, the default view of the enclosing entitylist is loaded.

**id**

id must be a string that can be parsed as a GUID.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

Generally, literal GUID strings aren't used. Instead, id is specified using a GUID property of another variable.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logical\_name**

The Dataverse entity logical name of the view to be loaded. Must be used in combination with name.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**name**

The Dataverse name of the view to be loaded. Must be used in combination with logical\_name.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**filter**

Specifies whether to filter the view results by user or account. Must have a string value of user or account.

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

A common use case is to set this parameter based on a [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

Specifies the List metadata filter expression by which to filter view results. This parameter is only valid when entityview is used in combination with entitylist. In most cases, this parameter is set based on a [request](liquid-objects.md#request).  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**order**

Specifies a sort expression for ordering view results. A sort expression can contain one or more entity attribute logical names, followed by a sort direction of either ASC or DESC.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

A common use case is to set this parameter based on a [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page**

Specifies the view result page to load. If this parameter isn't specified, the first page of results are loaded.

This parameter must be passed either an integer value, or a string that can be parsed as an integer. If a value is provided for this parameter, but the value is null or otherwise can't be parsed as an integer, the first page of results is loaded.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

A common use case is to set this parameter based on a [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page\_size**

Specifies the number of results to load for the current result page. If no value is provided for this parameter, and entityview is used within an [entitylist](#entitylist) block, the list page size is used. If not within an entitylist block, a default value of 10 is used.

This parameter must be passed either an integer value, or a string that can be parsed as an integer. If a value is provided for this parameter, but the value is null or otherwise can't be parsed as an integer, the default page size is used.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

A common use case is to set this parameter based on a [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**search**

Specifies a search expression by which to filter view results. Simple keyword search expressions filters by whether attributes begin with the keyword. Wildcards \* can also be included in the expression.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

A common use case is to set this parameter based on a [request](liquid-objects.md#request), so that the search filter can be set based on user input.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**language\_code**

A Dataverse integer language code to select the entity view localized labels (column header labels, etc.) to be loaded. If no language\_code is provided, the default language of the website application Dataverse connection is used.

If entityview is used within an entitylist block, entityview inherits its language code configuration from entitylist.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## searchindex

Performs a query against the website search index. The matching results can then be accessed using a [searchindex](liquid-objects.md#searchindex) that is available within the tag block.  

```
{% searchindex query: 'support', page: params.page, page_size: 10 %}

{% if searchindex.results.size > 0 %}

<p>Found about {{ searchindex.approximate_total_hits }} matches:</p>

<ul>

{% for result in searchindex.results %}

<li>

<h3><a href={{ result.url | escape }}>{{ result.title | escape }}</a></h3>

<p>{{ result.fragment }}</p>

</li>

{% endfor %}

</ul>

{% else %}

<p>Your query returned no results.</p>

{% endif %}

{% endsearchindex %}

<style>

    .highlight {background-color: #FFFCAC;}

</style>

```

By default, the search index object is given the variable name searchindex. Optionally, a different variable name can be provided.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### Parameters

The searchindex tag accepts the following parameters.

**query**

The query used to match results. This parameter is intended to accept the user-specified part of the index query (if any).

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

A common use case is to set this parameter based on a [request](liquid-objects.md#request).  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

This parameter supports [the Lucene Query Parser syntax](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

**filter**

Another query used to match results. This parameter is intended to accept a developer-specified filter for results, if desired.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

This parameter supports [the Lucene Query Parser syntax](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).  

> [!Note]     
> The difference between filter and query is that while both will accept the Lucene Query Parser syntax, query is intended to be more forgiving about how this syntax is parsed ߝ as it's expected that most end users will not be aware of this syntax. So, in the case that parsing query according to this syntax fails, the entire query will be escaped and submitted as the query text. filter, on the other hand, will be parsed strictly and return an error if the case of invalid syntax.

**logical\_names**

The Dataverse entity logical names to which matching results are restricted, as a comma-delimited string. If not provided, all matching entities are returned.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**page**

The search result page to be returned. If not provided, the first page (1) is returned.

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

A common use case is to set this parameter based on a [request](liquid-objects.md#request).  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**page\_size**

The size of the result page to be returned. If not provided, a default size of 10 is used.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## entityform

Fully renders a [form](../../getting-started/add-form.md), by name or ID.  

> [!Note]
> The entityform tag is only available for use in content rendered inside a <em>[web template](../web-templates.md)–</em>based page template. Attempting to use the tag inside a Rewrite-based Page Template will not render anything. You may only render a single entityform or webform tag per page. entityform or webform tags after the first will not be rendered.       

`{% entityform name: 'My Basic Form' %}`

### Parameters

**name**

The name of the Basic Form you wish to load.

`{% entityform name:My Basic Form %}`

## webform

Fully renders a [multistep form](../../getting-started/multistep-forms.md), by name or ID. The webform tag is only available for use in content rendered inside a [web template](../web-templates.md) based page template. Attempting to use the tag inside a Rewrite-based Page Template doesn't render anything. You can only render a single entityform or webform tag per page. Entityform or webform tags after the first aren't rendered.

`{% webform name: 'My Multistep Form' %}`

### Parameters

**name**

The name of the Multistep Form you wish to load.

`{% webform name:My Multistep Form %}`

## codecomponent

Allows you to embed code components using a Liquid tag. For example, adding a map display custom control to a web page.

### Parameters

**name**

The ID or name of the code component.

**property**

The values of the properties that the code component expects needs to be passed in as a key/value pair separated by colon (:), where key is the property name and the value is the JSON string value.

`{% codecomponent name:abc\_SampleNamespace.MapControl controlValue:'Space Needle' controlApiKey:<API Key Value> %}`

> [!NOTE]
> The properties required might be different depending on the component you choose.

See [Use code components Liquid template tag](component-framework-liquid.md).

### See also

- [Control flow tags](control-flow-tags.md)
- [Iteration tags](iteration-tags.md)
- [Variable tags](variable-tags.md)
- [Template tags](template-tags.md)
