---
title: Overview of the Power Pages portals Web API
description: Learn how to use the portals Web API to create, read, update, and delete Microsoft Dataverse tables from your Power Pages sites.
author: neerajnandwana-msft
ms.topic: overview
ms.date: 08/27/2026
ms.subservice: 
ms.author: nenandw
ms.reviewer: smurkute
contributors:
 - neerajnandwana-msft
 - nageshbhat-msft
ms.custom:
  - sfi-image-nochange
ms.collection:
  - ai-assisted
---

# Portals Web API overview

The portals Web API enables a richer user experience inside Power Pages sites. You can use the Web API to perform create, read, update, and delete operations across all Microsoft Dataverse tables from your webpages. For example, you can create a new account or update a contact without using a [form](../getting-started/add-form.md) or [multistep form](../getting-started/multistep-forms.md) by using the portals Web API.

The Web API uses the `/_api` route (for example, `https://yoursite.powerappsportals.com/_api/accounts`) and follows a RESTful pattern similar to the Dataverse Web API.

> [!IMPORTANT]
> - The portals Web API is built for creating a rich user experience inside portal pages. It isn't optimized for third-party services or application integration. Using the portals Web API to integrate with other Power Pages sites isn't supported.
> - Portals Web API operations are limited to tables related to data&mdash;for example, accounts, contacts, or your custom tables. Configuring table metadata or portal configuration table data&mdash;for example, configuring portals tables such as adx_contentsnippet, adx_entityform, or adx_entitylist&mdash;isn't supported by using the portals Web API. For a complete list, see [unsupported configuration tables](#unsupported-configuration-tables) later in this article.
> - The portals Web API benefits from [server-side caching](/power-apps/maker/portals/admin/clear-server-side-cache), so subsequent calls to the Web API are faster than the initial calls. Clearing the portal server-side cache causes temporary performance degradation.
> - Portals Web API operations require a Power Pages license. For example, Web API calls made by anonymous users count towards the anonymous user capacity. Web API calls made by authenticated users (internal or external) don't count towards page views, but require applicable authenticated user capacity licenses. For more information, see [Power Pages licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq#power-pages).
> - Calling [actions](/power-apps/developer/data-platform/webapi/use-web-api-actions) and [functions](/power-apps/developer/data-platform/webapi/use-web-api-functions) by using the portals Web API isn't supported.

## Web API operations

The portals Web API offers a subset of capabilities for Dataverse operations that you can do by using the Dataverse API. The API format is as similar as possible to reduce the learning curve.

> [!NOTE]
> Web API operations are case-sensitive.

### Web API operations available in Power Pages

- [Read records from a table](read-operations.md)
- [Create a record in a table](write-update-delete-operations.md#create-a-record-in-a-table)
- [Update and delete records in a table](write-update-delete-operations.md#update-and-delete-records-by-using-the-web-api) 
- [Associate and disassociate tables](write-update-delete-operations.md#associate-and-disassociate-tables-by-using-the-web-api)

## Site settings for the Web API

> [!IMPORTANT]
> Support for the wildcard value (`*`) in the
> `Webapi/<table-name>/fields` site setting is deprecated.
>
> Replace `*` with a comma-separated list of the columns required by your
> site. Power Pages Web API requests for tables
> configured with `*` fail until you configure explicit column names.

To enable the portals Web API for your site, configure the site settings for each table that you want to expose. You can define the columns available to the Web API by listing them in a site setting, by using a Dataverse system view, or by combining both methods.

> [!NOTE]
> Use the table [logical name](/power-apps/developer/data-platform/entity-metadata) for these settings (for example, **account**).

| Site setting name | Description|
| - |- |
| `Webapi/<table-name>/enabled` | Enables or disables the Web API for \<table name\>. <br> **Default:** `False` <br> **Valid values:** `True`, `False` |
| `Webapi/<table-name>/fields`  | Defines a comma-separated list of column logical names available through the Web API. For example, `name,accountnumber,telephone1`. This setting is required unless `Webapi/<table-name>/UseFieldsFromView` is set to `True` and the configured system view contains at least one eligible column. The wildcard value (`*`) is deprecated. |
| `Webapi/<table-name>/UseFieldsFromView` | When set to `True`, makes columns from a Dataverse system view named **Power Pages Web API Columns** available through the Web API. **Default:** `False`. **Valid values:** `True`, `False`. If `Webapi/<table-name>/fields` is also configured, columns from both sources are combined. |
| `Webapi/error/innererror` | Enables or disables InnerError. <br> **Default:** `False` <br> **Valid values:** `True`, `False` |

For example, to expose the Web API for the Case table where authenticated
users can create, update, and delete records for this entity, use the site settings shown in the following table.

| Site setting name | Site setting value|
| - |- |
| *Webapi/incident/enabled* | true |
| *Webapi/incident/fields* | attr1, attr2, attr3 |

### Configure Web API columns by using a system view

By using a system view, makers can manage the columns available through the portal's Web API without maintaining a comma-separated list in a site setting.

1. In Power Pages design studio, open the [Data workspace](../getting-started/use-data-workspace.md).
1. Select the table, select the **Views** tab, and then create or edit a public system view.
1. Name the view **Power Pages Web API Columns**.
1. Add the columns that your site needs to the view, and then save and publish the view.
1. In the Portal Management app, create the `Webapi/<table-name>/UseFieldsFromView` site setting for the website and set its value to `True`.
1. Confirm that `Webapi/<table-name>/enabled` is set to `True`.


> [!NOTE]
> - Only columns from the primary table that are displayed in the view are included. Columns from related tables aren't included. Columns used only for filtering or sorting aren't included unless they're also displayed in the view.
> - For lookup columns, use the corresponding OData lookup property in Web API requests. The property name uses the format `_<column-logical-name>_value`. For example, the `primarycontactid` lookup column is returned as `_primarycontactid_value`.
> - Changes to the system view can take up to five minutes to become available to the Web API.

If both `Webapi/<table-name>/fields` and `Webapi/<table-name>/UseFieldsFromView` are configured, the Web API combines the columns listed in `Webapi/<table-name>/fields` with eligible columns from the **Power Pages Web API Columns** system view for that table.


> [!IMPORTANT]
> - The `Webapi/<table-name>/UseFieldsFromView` site setting is available in Power Pages site version 9.8.8.x and later.
> - Support for the wildcard value (`*`) in `Webapi/<table-name>/fields` is deprecated. Use explicit column names, the **Power Pages Web API Columns** system view, or both.


## Security with the portal Web API

You can configure record-based security for individual records in portals by using [table permissions](../security/assign-table-permissions.md). The portal Web API accesses table (entity) records and follows the table permissions given to users through the associated [web role](../security/create-web-roles.md).

You can configure [column permissions](/power-apps/maker/portals/configure/column-permissions) to further define privileges to individual columns within a table while using the portal Web API. 

## Authenticating portal Web API requests

You don't need to include an authentication code because the application session manages authentication and authorization. All Web API calls must include a Cross-Site Request Forgery (CSRF) token.

## Using EntitySetName

When referring to Dataverse tables by using the portal Web API in your code, use the [EntitySetName](/power-apps/developer/data-platform/entity-metadata#table-names). To access the **account** table, for example, the code syntax uses the EntitySetName of **accounts**; `/_api/accounts()`.

> [!NOTE]
> Use the table logical name for [site settings](#site-settings-for-the-web-api) (for example, **account**).

To determine the **EntitySetName** of specific tables, follow these steps: 

1. Go to https://make.powerapps.com

1. Select the **Dataverse** tab from the side panel and select the table.

1. Select the **...** (Commands option), and then choose **Advanced**, **Tools**, and **Copy set name** to copy the **EntitySetName** of the table to your clipboard.

    :::image type="content" source="media/web-api/entitysetname.png" alt-text="How to locate EntitySetName of a Dataverse table.":::

## Privacy laws and regulations

All request headers use a contact ID for auditing purposes. For an anonymous user, the value is `null`.

If audit logging is enabled, a user can see all the audit events in the [Office 365 audit log](https://protection.office.com/unifiedauditlog).

:::image type="content" source="media/web-api/office365-security-compliance-audit-log.png" alt-text="Screenshot of the Office 365 audit log.":::

More information:<br />[Enable and use activity logging](/power-platform/admin/enable-use-comprehensive-auditing)<br />[Export, configure, and view audit log records](/microsoft-365/compliance/export-view-audit-log-records)

## Unsupported configuration tables

You can't use Portal Web API for the following configuration tables:


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

Users get a CDS error if they invoke a `GET` Web API request for tables that have multiple levels of *one-to-many* or *many-to-many* [table permissions](../security/table-permissions.md) when **Parental**, **Contact**, or **Account** scopes add more conditions to the query.

To resolve this issue, use [FetchXML](/power-apps/developer/data-platform/use-fetchxml-construct-query) in the OData query.

## Next step

[Query data using portals Web API](read-operations.md)

### Related information

- [Compose HTTP requests and handle errors](web-api-http-requests-handle-errors.md)
- [Write, update, and delete operations using the Web API](write-update-delete-operations.md)
- [How to: Use portal Web API](webapi-how-to.md)
