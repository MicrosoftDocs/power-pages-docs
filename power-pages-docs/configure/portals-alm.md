---
title: Overview of Power Pages ALM
description: Learn how to use ALM in Power Pages.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 10/19/2022
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Overview of Power Pages ALM

Makers and pro developers can use the Microsoft Power Platform CLI to download Power Pages site metadata, and use Azure DevOps pipelines or GitHub actions to commit the metadata to source control and deploy from development to other environments.

## Power Platform CLI

Microsoft Power Platform CLI is a simple, one-stop developer CLI that empowers developers and ISVs to perform various operations in Microsoft Power Platform related to environment lifecycle, authentication, and work with Microsoft Dataverse environments, solution packages, websites, and code components.

Power Pages supports Microsoft Power Platform CLI to enable CI/CD (Continuous Integration/Continuous Deployment) of website configuration. You can now check in the website configuration to source control and move website configuration to any environment using Microsoft Power Platform CLI.
 
For detailed information on using the Microsoft Power Platform CLI for Power Pages website configuration, go to [Tutorial: Use Microsoft Power Platform CLI with portals](/power-apps/maker/portals/power-apps-cli-tutorial) in the Power Apps documentation.

The Microsoft Power Platform CLI also supports [deployment profiles](/power-apps/maker/portals/power-apps-cli-tutorial#upload-the-changes-using-deployment-profile) to allow unique attributes to be applied to specific target environments.

## Microsoft Power Platform Build Tools for Azure DevOps

Users can create an Azure DevOps pipeline and use the following Power Platform build tool tasks for Power Pages specific functions.
- Power Platform Download PAPortal
- Power Platform Upload PAPortal

For detailed information on using Azure DevOps for application lifecycle management (ALM), go to [Microsoft Power Platform Build Tools for Azure DevOps](/power-platform/alm/devops-build-tools) in the Power Platform ALM documentation.

## GitHub actions

Users can use GitHub actions to upload website metadata to a target Dataverse environment.

For detailed information on using GitHub actions for application lifecycle management (ALM), go to [Github Actions - portal tasks](/power-platform/alm/devops-github-available-actions#portal-tasks) in the Power Platform ALM documentation.

### See also

[Overview of application lifecycle management with Microsoft Power Platform](/power-platform/alm/overview-alm)