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

When creating a site, you might have to create, update, or read business information. Consider a page that's used for collecting feedback, showing a list of available classes, or rescheduling an appointment. Typically this type of information is stored in a database. Microsoft Power Platform has a powerful cloud-based data service called [Dataverse](/power-apps/maker/data-platform/data-platform-intro). Dataverse not only stores information like a traditional database, but also provides features for security, analytics, automation, and more. 

You can build applications&mdash;including Power Pages sites&mdash;that are connected to Dataverse.

## Data workspace

Makers are able to create and modify Dataverse [tables](/power-apps/maker/data-platform/entity-overview) directly in the design studio by using the [Data workspace](use-data-workspace.md).

:::image type="content" source="media/data-workspace/table-designer.png" alt-text="Data workspace table designer.":::

A feature of Dataverse is the ability for makers to use Power Apps to create [model-driven apps](/power-apps/maker/model-driven-apps/) that allow users to work with data by using a [view](/power-apps/maker/model-driven-apps/create-edit-views) of data records in a grid or list, and a [form](/power-apps/maker/model-driven-apps/create-design-forms) to add, update, and view details of each record. 

Power Pages sites are unique, but they have components that use these model-driven app views and forms<!--note from editor: Is this what "components" means here?--> as a foundation to build interactive, data-driven webpages.

Using the Data workspace, a maker can use preexisting or new Dataverse model-driven app views to build [list](add-list.md) components, and preexisting or new Dataverse model-driven app forms to create [basic](add-form.md) or [advanced form](advanced-forms.md) components on pages.

### See also

[Create and modify tables](../configure/data-workspace-tables.md)<br>
[Create and modify views](../configure/data-workspace-views.md)<br>
[Create and modify forms](../configure/data-workspace-forms.md)