---
title: Dataverse and Power Pages
description: Learn about Dataverse in context of Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/27/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer:
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Dataverse and Power Pages

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

When creating a site you may have a requirement to create, update, or read business information. 

Consider a page that can collect feedback, seeing a list of available classes, or re-scheduling an appointment. Typically this type of information is stored in a database. The Power Platform has a powerful cloud-based data service called [Dataverse](/power-apps/maker/data-platform/data-platform-intro). Dataverse can not only store information like a traditional database but also provides features for security, analytics, automation and more. 

Applications can be built that are connected to Dataverse, including Power Pages sites.

## Data workspace

Makers are able to create and modify Dataverse [tables](/power-apps/maker/data-platform/entity-overview) directly in the design studio using the [Data workspace](use-data-workspace.md).

:::image type="content" source="media/data-workspace/table-designer.png" alt-text="Data workspace table designer.":::

A feature of Dataverse is the ability to create [model-driven apps](/power-apps/maker/model-driven-apps/) using Power Apps that allow users to work with data using a [view](/power-apps/maker/model-driven-apps/create-edit-views) of data records in a grid/list type view and a [form](/power-apps/maker/model-driven-apps/create-design-forms) to be able to add, update and view details of each record. 

Power Pages applications are unique but have components that utilize these model-driven app components as a foundation to build interactive data-driven web pages.

Using the Data workspace, a maker can use pre-existing or new Dataverse model-driven views to build [list](add-list.md) components and pre-existing or new Dataverse model-driven app forms to create [basic](add-form.md) or [advanced form](advanced-forms.md) components on pages.

## See also

[Create and modify tables](../configure/data-workspace-tables.md)<br>
[Create and modify views](../configure/data-workspace-views.md)<br>
[Create and modify forms](../configure/data-workspace-forms.md)
