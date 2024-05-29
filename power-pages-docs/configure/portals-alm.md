---
title: Overview of Power Pages ALM
description: Learn how to use ALM in Power Pages.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 03/02/2023
ms.author: nenandw
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Overview of Power Pages ALM

Makers and pro developers can use the Microsoft Power Platform CLI to download Power Pages site metadata, and use Azure Pipelines or GitHub Actions to commit the metadata to source control and deploy from development to other environments.

## Power Platform CLI

Microsoft Power Platform CLI is a simple command line interface (CLI) that empowers developers and ISVs to perform various operations in the Microsoft Power Platform.

Power Pages supports Microsoft Power Platform CLI to enable CI/CD (Continuous Integration/Continuous Deployment) of website configuration. You can now check in the website configuration to source control and move website configuration to any environment using Microsoft Power Platform CLI.
 
For detailed information on using the Microsoft Power Platform CLI for Power Pages website configuration, go to [Tutorial: Use Microsoft Power Platform CLI with Power Pages](power-platform-cli-tutorial.md).

The Microsoft Power Platform CLI also supports [deployment profiles](power-platform-cli-tutorial.md#upload-the-changes-using-deployment-profile) to allow unique attributes to be applied to specific target environments.

## Microsoft Power Platform Build Tools for Azure DevOps

Users can create an Azure DevOps pipeline and use the following Power Platform build tool tasks for Power Pages specific functions.
- Power Platform Download PAPortal
- Power Platform Upload PAPortal

:::image type="content" source="media/alm/power-pages-azure-tasks.png" alt-text="Microsoft Power Platform Azure DevOps tasks.":::

For detailed information on using Azure DevOps for application lifecycle management (ALM), go to [Microsoft Power Platform Build Tools for Azure DevOps](/power-platform/alm/devops-build-tools) in the Power Platform ALM documentation.

## GitHub Actions

Users can use GitHub Actions to upload website metadata to a target Dataverse environment.

For detailed information on using GitHub Actions for application lifecycle management (ALM), go to [GitHub Actions - portal tasks](/power-platform/alm/devops-github-available-actions#portal-tasks) in the Power Platform ALM documentation.

### See also

[Overview of application lifecycle management with Microsoft Power Platform](/power-platform/alm/overview-alm)
