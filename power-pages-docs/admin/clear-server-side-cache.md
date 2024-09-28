---
title: How server-side caching works in Power Pages
description: Learn how server-side caching in works Power Pages
author: dileepsinghmicrosoft

ms.topic: conceptual
ms.custom: 
ms.date: 04/11/2023
ms.subservice: 
ms.author: dileeps
ms.reviewer: danamartens
contributors:
    - dileepsinghmicrosoft
    - nickdoelman
---

# How server-side caching works in Power Pages

In order to improve scalability and performance, Power Pages websites cache the data that is queried from Microsoft Dataverse. This caching is done on the application server for all business data and website metadata and is different from browser based or content delivery network caching of static resources.

Server side caching is done for two types of tables described below:

## Metadata/configuration tables

Metadata/configuration tables represent all the tables that store website configuration information like web pages, web templates, content snippets, and others.

The following tables are considered as **configuration** tables. This list is fixed and can't be modified through any configuration.

> [!NOTE]
> - The tables used for site configuration will depend if the site has been configured using the standard or enhanced data model. See [Enhanced data model](enhanced-data-model.md) for more information.
> - These tables cannot be modified.

| System table | Enhanced data model virtual table | Standard data model table |
| - | - | - |
|powerpagesite|mspp_website|adx_website|
|powerpagesitelanguage|mspp_websitelanguage|adx_websitelanguage|
| powerpagecomponent | mspp_columnpermission</br>mspp_columnpermissionprofile</br>mspp_contentsnippet</br>mspp_entityform</br>mspp_entityformmetadata</br>mspp_entitylist</br>mspp_entitypermission</br>mspp_pagetemplate</br>mspp_pollplacement</br>mspp_publishingstate</br>mspp_publishingstatetransitionrule</br>mspp_redirect</br>mspp_shortcut</br>mspp_sitemarker</br>mspp_sitesetting</br>mspp_webfile</br>mspp_webform</br>mspp_webformmetadata</br>mspp_webformstep</br>mspp_weblink</br>mspp_weblinkset</br>mspp_webpage</br>mspp_webpageaccesscontrolrule</br>mspp_webrole</br>mspp_websiteaccess</br>mspp_websitelanguage</br>mspp_webtemplate</br>|adx_columnpermission</br>adx_columnpermissionprofile</br>adx_contentsnippet</br>adx_entityform</br>adx_entityformmetadata</br>adx_entitylist</br>adx_entitypermission</br>adx_pagetemplate</br>adx_pollplacement</br>adx_publishingstate</br>adx_publishingstatetransitionrule</br>adx_redirect</br>adx_shortcut</br>adx_sitemarker</br>adx_sitesetting</br>adx_webfile</br>adx_webform</br>adx_webformmetadata</br>adx_webformstep</br>adx_weblink</br>adx_weblinkset</br>adx_webpage</br>adx_webpageaccesscontrolrule</br>adx_webrole</br>adx_websiteaccess</br>adx_websitelanguage</br>adx_webtemplate</br>|

All configuration table data is same for all users and is cached automatically. This configuration data cache for any table is updated automatically when any record is changed. Automatic cache update has a service level agreement of 15 minutes. Any change done for a configuration record would be automatically available on the website within 15 minutes.

However, in case the record changes are needed immediately, you can explicitly clear the cache using following options;

| Option | Details |
|---------|---------|
| Design studio     | Selecting the [Preview](../getting-started/first-page.md#preview-a-page) option on the design studio will clear the cache.        |
|`/_services/about` page on the website    |  Utilize the **clear config** or **clear cache** option by navigating to the website with '/_services/about' appended to the URL of the website. In order to view these options, user should have a webrole with all [website access permissions](../security/website-access-permission.md) assigned.       |

:::image type="content" source="media/clear-cache/clear-cache.png" alt-text="Clear cache.":::

> [!NOTE]
> Updates to the data in [configuration tables](#metadataconfiguration-tables) or invoking the clear cache or config actions should be performed during non-peak hours. Frequent or too many table changes may adversely affect website performance.

All configuration tables must be enabled for change notification in the organization. Change notification is set correctly by default and shouldn't be modified.

## Data tables

Data tables represent all the Dataverse tables that store business data displayed on the website. This data is typically cached per user except in certain cases like anonymous users or tables with [global permission](../security/table-permissions.md#available-access-types). Also only the data accessed by user on the website is cached and not the data for whole table.  

This cache is updated through several mechanisms described below:

- Any record for a table (or a related table) is created, updated, or deleted on the website by any website user. The action will instantaneously clear the cache for all the website users for that specific table.

- Cache is cleared automatically within 15 minutes even if no changes are made.

- Cache is cleared manually through following options:

    | Option| Details |
    |---------|---------|
    | Design studio     | Selecting the [Preview](../getting-started/first-page.md#preview-a-page) option on the design studio will clear the cache.        |
    |`/_services/about` page on the website    |  Utilize the **clear config** or **clear cache** option by navigating to the website with '/_services/about' appended to the URL of the website. In order to view these options, user should have a webrole with all [website access permissions](../security/website-access-permission.md) assigned.       |

> [!NOTE]
> The clear cache option should be seldom used as it clears cache for all data tables as well as [configuration tables](#metadataconfiguration-tables) and can cause temporary slowness. For live site with heavy usage, this can lead to users facing performance issues.

### FAQs

1. Can I change the cache refresh duration from 15 minutes to a lesser duration?

    No. SLA for cache refresh remains 15 minutes. Any changes from Dataverse will reflect on the website within 15 minutes for both data tables and configuration tables.

1. I'm using plugins or workflows to update data in other tables and need these data changes to reflect immediately on my website.  

    This design approach isn't recommended. Except the primary record where the create or update action is triggered, data reflection from Dataverse to websites is never guaranteed to be immediate.

1. Is there any difference in caching between capacity-based websites and add-on portals?

    No.

1. How long does it take for changes to reflect from a website to Dataverse?

    Immediately, as long as the update changes a primary record and isn't based on indirect changes to data using post operation plugins or workflows.

