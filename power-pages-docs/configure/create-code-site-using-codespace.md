---
title: Build Single-Page Applications With GitHub Spark and Codespaces for Power Pages
description: Learn how to create, customize, and deploy single-page applications for Microsoft Power Pages using GitHub Spark and Codespaces.
author: neerajnandwana-msft
contributors:
ms.topic: concept-article
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:08/12/2025
ms.date: 08/12/2025
ms.author: nenandw
ms.reviewer: smurkute
contributors:
- neerajnandwana-msft
- shwetamurkute
---

# Create and deploy a single-page application using GitHub Spark and Codespaces (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

The new [single-page application](create-code-sites.md) support gives developers greater flexibility: you can create, customize, and manage Power Pages sites entirely in source code. With the recent release of the [GitHub Spark](https://github.com/features/spark), developers can now author a site, edit it directly in a GitHub Codespace, and deploy it to a Power Pages environment all without leaving their browser. This tutorial walks you through the complete workflow.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

[GitHub Spark](https://github.com/features/spark) is a new AI-powered natural‑language platform from GitHub Copilot. It is designed to help developers bootstrap modern web applications quickly. When combined with GitHub Codespaces for code editing, Spark provides:

- A ready-to-use template repository for your project.
- Pre-configured dev containers for consistent environments.
- AI-powered, natural‑language platform from GitHub Copilot.

For Power Pages developers, this means you can start with a ready-made site template, customize it, and deploy without the traditional local setup.

By the end of this article, you will know how to:

1. Create a prototype Power Pages site using the GitHub Spark.
2. Configure your Codespace for .NET and PAC CLI support.
3. Build and upload your single-page application to a Power Pages environment.
4. Reactivate and test your site directly from [Power Pages](https://make.powerpages.microsoft.com/).

## Prerequisites

Before you begin, make sure you have:

- A Power Pages environment with [admin privileges](../getting-started/create-manage.md#roles-and-permissions).
- [Power Platform CLI (PAC CLI)](/power-platform/developer/cli/introduction) version 1.44.x or later installed and authenticated.
- A Power Pages site on version 9.7.4.x or later.
- GitHub Spark with Codespaces for your custom frontend project.

## Step 1: Start with the GitHub Spark template

1. Go to the GitHub Spark tool and generate a new site using natural language.
1. Once created, click **Open in Codespaces**.

This gives you a cloud-based development environment where you can work on your Power Pages project without any local setup.

## Step 2: Update the development container configuration

Inside the repository, locate the file:

`.devcontainer/devcontainer.json`

Modify the features section to add support for .NET 9.0. Your configuration should look like this:

```json
"features": {
  "ghcr.io/devcontainers/features/sshd:1": {
    "version": "latest"
  },
  "ghcr.io/devcontainers/features/dotnet:2.3.0": {
    "version": "9.0"
  }
}
```

### Rebuild the Container

After saving your changes:

1. Press `Ctrl + Shift + P` (or `Command + Shift + P` on Mac) to open the command palette.
2. Type **Codespaces: Rebuild Container** and select it.
3. The container will restart. During this process, .NET 9 and all other dependencies will be installed.
4. Wait a few seconds for the installation to complete before continuing.

This step ensures your Codespace environment is refreshed with the new configuration. This ensures your Codespace includes the necessary runtime for Power Pages build tooling.

## Step 3: Install Power Platform tools

From your Codespaces terminal:

1. Install Power Platform tools (available as a VS Code extension).
2. This installation also brings in the PAC CLI, a command-line interface that enables you to authenticate, download, and upload sites.

## Step 4: Connect to your Power Platform environment

Use the PAC CLI to authenticate against your target environment:

```bash
pac auth create -u https://org12x34x45.crm.dynamics.com
```

Replace the URL with your actual Power Platform environment URL.

## Step 5: Build your site

Before deploying, build your site code:

```bash
npm run build
```

This command compiles your site and outputs the artifacts into a `dist` folder.

## Step 6: Upload your site

Deploy your site to the Power Pages environment using:

```bash
pac pages upload-code-site --rootPath "./spark-template" --compiledPath "./dist" --siteName "YourSiteName"
```

### Parameters

| Parameter        | Alias  | Description                       |
| ---------------- | ----- | ----------------------------------- |
| `--rootPath`     | `-rp` |  Local folder that has your site’s source files       |
| `--compiledPath` | `-cp` | Path to compiled assets, like React `build`   |
| `--siteName`     | `-sn` | Display name for your Power Pages site  |

## Step 7: Reactivate and test

1. After the upload, your site appears under **Inactive sites** in the [Power Pages](https://make.powerpages.microsoft.com).
2. Go to **Inactive sites**, find your site, and select **Reactivate**.
3. When the site becomes active, open its URL to confirm the deployment.

## Next Steps: Secure and Extend Your Site

Now that your site is deployed:

- Configure Authentication and Authorization to secure access.
- Use Power Pages Web APIs to dynamically load content, and perform create, update, and delete operations from your custom code.
- Explore the sample React site code and documentation to build single-page applications (SPA) with deeper customizations.
