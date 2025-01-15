---
title: Overview of the Power Pages portals Web API
description: Learn how to use the portals Web API to create, read, update, and delete Microsoft Dataverse tables from your Power Pages sites.
author: neerajnandwana-msft

ms.topic: overview
ms.custom: 
ms.date: 01/15/2025
ms.subservice: 
ms.author: nenandw
ms.reviewer: dmartens
contributors:
    - neerajnandwana-msft
---

# Portals Web API overview

The portals Web API enables a richer user experience inside Power Pages sites. You can use the Web API to perform create, read, update, and delete operations across all Microsoft Dataverse tables from your webpages. For example, you can create a new account, update a contact, without using a [form](../getting-started/add-form.md) or [multistep form](../getting-started/multistep-forms.md) by using the portals Web API.

> [!IMPORTANT]
> - **Your Power Pages site version must be 9.3.3.x or later for this feature to work**.
> - The portals Web API is built for creating a rich user experience inside portal pages. It isn't optimized for third-party services or application integration. Using the portals Web API to integrate with other Power Pages sites is also not supported.
> - Portals Web API operations are limited to tables related to data&mdash;for example, accounts, contacts, or your custom tables. Configuring table metadata or portal configuration table data&mdash;for example, configuring portals tables such as adx_contentsnippet, adx_entityform, or adx_entitylist&mdash;isn't supported with the portals Web API. For a complete list, go to [unsupported configuration tables](#unsupported-configuration-tables) later in this article.
> - The portals Web API benefits from [server-side caching](/power-apps/maker/portals/admin/clear-server-side-cache), so subsequent calls to the Web API are faster than the initial calls. Clearing the portal server-side cache causes temporary performance degradation.
> - Portals Web API operations require a Power Pages license. For example, Web API calls made by anonymous users are counted towards the anonymous user capacity. Web API calls made by authenticated users (internal or external) aren't counted towards page views, but require applicable authenticated user capacity licenses. More information: [Power Pages licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq#power-pages)

## Web API operations

The portals Web API offers a subset of capabilities for Dataverse operations that you can do by using the Dataverse API. We kept the API format as similar as possible to reduce the learning curve.

> [!NOTE]
> Web API operations are case-sensitive.

### Web API operations available in Power Pages

- [Read records from a table](read-operations.md)
- [Create a record in a table](write-update-delete-operations.md#create-a-record-in-a-table)
- [Update and delete records in a table](write-update-delete-operations.md#update-and-delete-records-by-using-the-web-api) 
- [Associate and disassociate tables](write-update-delete-operations.md#associate-and-disassociate-tables-by-using-the-web-api)

> [!NOTE]
> Calling [actions](/power-apps/developer/data-platform/webapi/use-web-api-actions) and [functions](/power-apps/developer/data-platform/webapi/use-web-api-functions) using the portals Web API isn't supported.

## Site settings for the Web API

You must enable the site setting to enable the portals Web API for your portal. You can also configure the field-level Web API that determines the table fields that can or can't be modified with the portals Web API.

> [!NOTE]
> Use the table [logical name](/power-apps/developer/data-platform/entity-metadata) for these settings (for example **account**).

| Site setting name | Description|
| - |- |
| *Webapi/\<table name\>/enabled* | Enables or disables the Web API for \<table name\>. <br> **Default:** `False` <br> **Valid values:** `True`, `False` |
| *Webapi/\<table name\>/fields*  | Defines the comma-separated list of attributes that can be modified with the Web API. <br>  **Possible values:**  <br> - *All attributes:* `*` <br> - *Specific attributes:* `attr1,attr2,attr3` <br> **Note**:  The value must be either an asterisk (**\***) or a comma-separated list of field names. <br> **Important**: This setting is a mandatory site setting. When this setting is missing, you see the error "No fields defined for this entity." |
| *Webapi/error/innererror* | Enables or disables InnerError. <br> **Default:** `False` <br> **Valid values:** `True`, `False` |
| *Webapi/\<table name\>/disableodatafilter* | Enables or disables the OData filter. <br> **Default:** `False` <br> **Valid values:** `True`, `False` See [known issues](#known-issues) for more information. The site setting is available in portal version [9.4.10.74](/power-platform/released-versions/portals) or later. |


> [!NOTE]
> Site settings must be set to **Active** for changes to take effect.

For example, to expose the Web API for the Case table where authenticated
users are allowed to perform create, update, and delete operations on this entity, the site settings are shown in the following table.

| Site setting name | Site setting value|
| - |- |
| *Webapi/incident/enabled* | true |
| *Webapi/incident/fields* | attr1, attr2, attr3 |

## Security with the portals Web API

You can configure record-based security to individual records in portals by using [table permissions](../security/assign-table-permissions.md). The portals Web API accesses table (entity) records and follows the table permissions given to users through the associated [web role](../security/create-web-roles.md).

You can configure [column permissions](/power-apps/maker/portals/configure/column-permissions) to further define privileges to individual columns within a table while using the portals Web API. 

## Authenticating portals Web API requests

You don't need to include an authentication code because the application session manages authentication and authorization. All Web API calls must include a Cross-Site Request Forgery (CSRF) token.

## Using EntitySetName

When referring to Dataverse tables using the portals Web API in your code, you need to use the [EntitySetName](/power-apps/developer/data-platform/entity-metadata#table-names), for example, to access the **account** table, the code syntax uses the EntitySetName of **accounts**; `/_api/accounts()`.

> [!NOTE]
> Use the table logical name for [site settings](#site-settings-for-the-web-api) (for example, **account**).

You can determine the **EntitySetName** of specific tables by following these steps: 

1. Go to https://make.powerapps.com

1. Select the **Dataverse** tab from the side panel and select the table.

1. Select the **...** (Commands option) and then choose **Advanced**, **Tools**, and **Copy set name** to copy the **EntitySetName** of the table to your clipboard.

    :::image type="content" source="media/web-api/entitysetname.png" alt-text="How to locate EntitySetName of a Dataverse table.":::

## Privacy laws and regulations

All request headers use a contact ID passed for auditing purposes. For an anonymous user, this value is passed as `null`.

If audit logging is enabled, a user can see all the audit events in the [Office 365 audit log](https://protection.office.com/unifiedauditlog).

:::image type="content" source="media/web-api/office365-security-compliance-audit-log.png" alt-text="Screenshot of the Office 365 audit log.":::

More information:<br />[Enable and use activity logging](/power-platform/admin/enable-use-comprehensive-auditing)<br />[Export, configure, and view audit log records](/microsoft-365/compliance/export-view-audit-log-records)

## Unsupported configuration tables

Portals Web API can't be used for the following configuration tables:


:::row:::
:::column:::
	adx_contentaccesslevel
:::column-end:::
:::column:::
	adx_contentsnippet
:::column-end:::
:::column:::
	adx_entityform
:::row-end:::
:::row:::
:::column:::
	adx_entityformmetadata
:::column-end:::
:::column:::
	adx_entitylist
:::column-end:::
:::column:::
	adx_entitypermission
:::row-end:::
:::row:::
:::column:::
	adx_entitypermission_webrole
:::column-end:::
:::column:::
	adx_externalidentity
:::column-end:::
:::column:::
	adx_pagealert
:::row-end:::
:::row:::
:::column:::
	adx_pagenotification
:::column-end:::
:::column:::
	adx_pagetag
:::column-end:::
:::column:::
	adx_pagetag_webpage
:::row-end:::
:::row:::
:::column:::
	adx_pagetemplate
:::column-end:::
:::column:::
	adx_portallanguage
:::column-end:::
:::column:::
	adx_publishingstate
:::row-end:::
:::row:::
:::column:::
	adx_publishingstatetransitionrule
:::column-end:::
:::column:::
	adx_publishingstatetransitionrule_webrole
:::column-end:::
:::column:::
	adx_redirect
:::row-end:::
:::row:::
:::column:::
	adx_setting
:::column-end:::
:::column:::
	adx_shortcut
:::column-end:::
:::column:::
	adx_sitemarker
:::row-end:::
:::row:::
:::column:::
	adx_sitesetting
:::column-end:::
:::column:::
	adx_urlhistory
:::column-end:::
:::column:::
	adx_webfile
:::row-end:::
:::row:::
:::column:::
	adx_webfilelog
:::column-end:::
:::column:::
	adx_webform
:::column-end:::
:::column:::
	adx_webformmetadata
:::row-end:::
:::row:::
:::column:::
	adx_webformsession
:::column-end:::
:::column:::
	adx_webformstep
:::column-end:::
:::column:::
	adx_weblink
:::row-end:::
:::row:::
:::column:::
	adx_weblinkset
:::column-end:::
:::column:::
	adx_webnotificationentity
:::column-end:::
:::column:::
	adx_webnotificationurl
:::row-end:::
:::row:::
:::column:::
	adx_webpage
:::column-end:::
:::column:::
	adx_webpage_tag
:::column-end:::
:::column:::
	adx_webpageaccesscontrolrule
:::row-end:::
:::row:::
:::column:::
	adx_webpageaccesscontrolrule_webrole
:::column-end:::
:::column:::
	adx_webpagehistory
:::column-end:::
:::column:::
	adx_webpagelog
:::row-end:::
:::row:::
:::column:::
	adx_webrole_systemuser
:::column-end:::
:::column:::
	adx_website
:::column-end:::
:::column:::
	adx_website_list
:::row-end:::
:::row:::
:::column:::
	adx_website_sponsor
:::column-end:::
:::column:::
	adx_websiteaccess
:::column-end:::
:::column:::
	adx_websiteaccess_webrole
:::row-end:::
:::row:::
:::column:::
	adx_websitebinding
:::column-end:::
:::column:::
	adx_websitelanguage
:::column-end:::
:::column:::
	adx_webtemplate
:::row-end:::

## Known issues

Users get a CDS error if they invoke a `GET` Web API request for tables that have multiple levels of *1 to many* or *many to many* [table permissions](../security/table-permissions.md)  when **Parental**, **Contact, or **Account** scopes add more conditions to the query.

To resolve this issue, the recommended solution is to use [FetchXML](/power-apps/developer/data-platform/use-fetchxml-construct-query) in the OData query.

Alternatively, set the site setting *Webapi/\<table name\>/disableodatafilter* to `True`. 

> [!IMPORTANT]
> Changing the site setting *Webapi/\<table name\>/disableodatafilter* to `True` might result in slower performance for Web API `GET` calls.

The site setting is available in portal version [9.4.10.74](/power-platform/released-versions/portals) or later.

## Next step

[Query data using portals Web API](read-operations.md)

### See also

- [Compose HTTP requests and handle errors](web-api-http-requests-handle-errors.md)
- [Write, update, and delete operations using the Web API](write-update-delete-operations.md)
- [How to: Use portal Web API](webapi-how-to.md)

