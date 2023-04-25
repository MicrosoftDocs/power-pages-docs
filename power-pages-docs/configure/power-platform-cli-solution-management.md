---
title: Power Platform CLI solution support for Power Pages
description: Learn how to work with Power Platform CLI solution commands for a Power Pages site.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 04/25/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - gitanjalisingh33msft
    - neerajnandwana-msft
    - nickdoelman
---

# Microsoft Power Platform CLI solution support for Power Pages

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Power Pages [enhanced data model](../admin/enhanced-data-model.md) supports [solution awareness feature for the Power Pages](power-pages-solutions.md). This will help you use Power Platform solution capabilities to move website configuration from one environment to another.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

The Power Platform CLI provides solution related commands that can also be applied to Power Pages.

## Create a new solution

Use the following command to create a new solution using the PAC CLI;

`pac solution init --publisher-name '<<publisher name>>' --publisher-prefix '<<publisher prefix>>' --outputDirectory '<<directory>>'`

Example:

`pac solution init --publisher-name 'ppmaker' --publisher-prefix 'pp' --outputDirectory 'c:\dev\ppsolution'`

## Add existing website to a solution

You will need to determine the **component type** and **component id** in order to add a website to a solution using the PAC CLI.

### Determining component types

You can get the `componentType` by sending a **GET** request using the Web API OData call.

`{OrgURL}/api/data/v9.1/solutioncomponentdefinitions?filter=startswith(name,'powerpage')&select=name,solutioncomponenttype`

:::image type="content" source="media/cli-solutions/component_types.png" alt-text="List of component types.":::

### Determining component id

You can get the `componentId` by sending a **GET** request using the Web API OData call.

You can use the following endpoints:
`powerpagesite`
`powerpagesitelanguage`
`powerpagecomponent`

The example shown below is using the `powerpagesite` endpoint.

`{OrgURL}/api/data/v9.1/powerpagesites?$select=name`

:::image type="content" source="media/cli-solutions/component_ids.png" alt-text="List of component ids.":::

Once you have determined the component type and id, use the following command to add an existing website to a solution using the PAC CLI;

`pac solution add-solution-component`

Example:

`pac solution add-solution-component -sn SampleSolution -c c6f2aec0-ddd2-ed11-a7c6-6045bdf05d59 -ct 10319`

In this example; 
- **SampleSolution** represents solution unique name.
- **c6f2aec0-ddd2-ed11-a7c6-6045bdf05d59** is Power Pages Site record ID.
- **10319** is Power Pages site solution `CompomponentType` from the above Web API response.

Use `pac solution sync` or `pac solution export` to export the solution using the PAC CLI.

Power Pages website configuration can then moved using Power Platform ALM processes.

### See also

- [Enhanced data model](../admin/enhanced-data-model.md)
- [Microsoft Power Platform CLI support for Power Pages](power-platform-cli.md)
- [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction)
- [Use the Visual Studio Code extension (preview)](vs-code-extension.md)

