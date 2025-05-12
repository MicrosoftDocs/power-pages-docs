---
title: Manage websites
description: Learn how to manage websites in Power Pages.
author: DanaMartens

ms.topic: how-to
ms.custom: 
ms.date: 04/13/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Manage websites

A website is the core table of a Power Pages application. A website application selects a single website record, and this determines what website metadata such as [web pages](web-page.md), [web files](web-files.md), [web roles](../security/create-web-roles.md), and [content snippets](customize-content-snippets.md) are applicable to this application.

With a website providing an application scope, multiple distinct website applications can be connected to a single organization.

> [!NOTE]
> Determination of which website record a given website application is bound to is usually by the website's name, specified in the configuration of the website deployment.
However, it is also possible to control this by domain name or website bindings.

## Manage websites

The websites record is created when you create a new Power Pages website. Advanced website management can be performed from the Portal Management app. 

> [!WARNING]
> When you delete a website record, data related to the website record in website metadata, such as webpages and web links, is also deleted. This is generally the desired behavior, as it means an entire website and all its related data can be removed from an organization in a single operation.

1. Open the [Portal Management app](portal-management-app.md).

2. Go to **Website** > **Websites**.

3. To edit an existing website, select the website name.

4. Enter or edit appropriate values in the fields.

5. Select **Save & Close**.

### Website attributes

|Name|Description|
|-|-|
|Name|The descriptive name of the website. This field is required.|
| Default Language | Default language for the selected website. Before you change the default language, you must: <br> - [Add the language in Microsoft Dataverse environment](/power-platform/admin/enable-languages). <br> - [Add the language in Supported Languages](enable-multiple-language-support.md) section for Websites record.
| Owner | The owner contact record for the selected Websites record.
|Primary Domain Name|The primary domain name of the website to which this website record will be added.|
|Parent Website\*|The parent website of the website. This field can generally be ignored, except in certain advanced website configurations in which a single website application is bound to one master website at the application root path, with one or more child websites available at specific sub-paths. <br>\* Only for backward compatibility, not to be used for new or existing websites. |
| Header and Footer Templates | The [Web templates for headers and footers](web-templates.md#web-templates-as-custom-page-layouts) overriding global headers and footers.
| Supported Languages | The [supported languages](enable-multiple-language-support.md) for the selected websites record.

### See also

[Website bindings](website-bindings.md)

