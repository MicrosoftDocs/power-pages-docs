---
title: Power Platform CLI solution support for Power Pages
description: Learn how to work with Power Platform CLI solution commands for a Power Pages site.
author: gitanjalisingh33msft

ms.topic: concept-article
ms.custom: 
ms.date: 10/03/2024
ms.subservice: 
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - gitanjalisingh33msft
    - neerajnandwana-msft
---

# Power Platform CLI solution support for Power Pages (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Power Pages [enhanced data model](../admin/enhanced-data-model.md) supports the [solution awareness feature for Power Pages](power-pages-solutions.md). This feature helps you use Microsoft Power Platform solution capabilities to move a website configuration from one environment to another.

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

The Power Platform CLI provides solution-related commands that can also be applied to Power Pages.

## Create a new solution

Run the following command to create a new solution by using the PAC CLI:

`pac solution init --publisher-name '<<publisher name>>' --publisher-prefix '<<publisher prefix>>' --outputDirectory '<<directory>>'`

Example:

`pac solution init --publisher-name 'ppmaker' --publisher-prefix 'pp' --outputDirectory 'c:\dev\ppsolution'`

## Add an existing website to a solution

To add a website to a solution by using the PAC CLI, you must determine the **component type** and the **component ID**.

### Determine the component type

To get the specific Power Pages `componentType` names and values, send a **GET** request by using the Dataverse Web API OData call.

`{OrgURL}/api/data/v9.1/solutioncomponentdefinitions?$filter=startswith(name,'powerpage')&$select=name,solutioncomponenttype`

:::image type="content" source="media/cli-solutions/component_types.png" alt-text="Screenshot that shows a list of component types.":::

### Determine the component ID

To get the `componentId` value, send a **GET** request by using the Web API OData call.

You can use the following endpoints:

- `powerpagesite`
- `powerpagesitelanguage`
- `powerpagecomponent`

The following example uses the `powerpagesite` endpoint:

`{OrgURL}/api/data/v9.1/powerpagesites?$select=name`

:::image type="content" source="media/cli-solutions/component_ids.png" alt-text="Screenshot that shows a list of component IDs.":::

After you've determined the component type and component ID, run the following command to add an existing website to a solution by using the PAC CLI:

`pac solution add-solution-component`

Example:

`pac solution add-solution-component -sn SampleSolution -c c6f2aec0-ddd2-ed11-a7c6-6045bdf05d59 -ct 10463`

In this example:

- `SampleSolution` represents the solution's unique name.
- `c6f2aec0-ddd2-ed11-a7c6-6045bdf05d59` is the record ID of the Power Pages site.
- `10319` is the `CompomponentType` value of the Power Pages site solution from the earlier Web API response.

Run `pac solution sync` or `pac solution export` to export the solution by using the PAC CLI.

You can now move the Power Pages website configuration by using Microsoft Power Platform Application Lifecycle Management (ALM) processes.

## See also

- [Enhanced data model](../admin/enhanced-data-model.md)
- [Microsoft Power Platform CLI support for Power Pages](power-platform-cli.md)
- [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction)
- [Use the Visual Studio Code extension (preview)](vs-code-extension.md)
