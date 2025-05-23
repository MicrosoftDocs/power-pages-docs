---
title: Create and Deploy a Single Page Application in Power Pages
description: Discover how to upload, download, and activate Power Pages code sites with step-by-step guidance and examples.
author: neerajnandwana-msft
ms.topic: concept-article
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:05/20/2025
ms.date: 05/20/2025
ms.subservice:
ms.author: nenandw
ms.reviewer: dmartens
contributors:
  - neerajnandwana-msft
  - DanaMartens
---

# Create and deploy a Single Page Application in Power Pages (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to create, configure, and deploy a Single Page Application in Power Pages using the [Power Platform CLI](/power-platform/developer/cli/introduction) (PAC CLI). You learn how to upload and download code, set up your project structure, secure your site, and understand key differences from traditional Power Pages sites.

> [!NOTE]
> A code site is a Power Pages site that runs entirely in the user's browser (client-side rendering). Unlike traditional Power Pages sites, code sites are managed only through source code and command-line interface (CLI) tools.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Prerequisites

Before you begin, make sure you have:

* A Power Pages environment with [admin privileges](../getting-started/create-manage.md#roles-and-permissions)
* [Power Platform CLI (PAC CLI)](/power-platform/developer/cli/introduction) version 1.43.x or later installed and authenticated
* A local Git repository with your custom frontend project (like React)

## Create and deploy a Single Page Site

Power Pages code sites are managed using the PAC CLI commands `upload-code-site` and `download-code-site`. After you upload a site, it appears in [Power Pages](https://make.powerpages.microsoft.com/) in the **Inactive sites** list. Activate the site to make it available to users.

### Upload a Single Page Site

Use the [pac pages upload-code-site](/power-platform/developer/cli/reference/pages#pac-pages-upload-code-site) command to upload your local source and compiled assets to your Power Pages environment. 

#### Syntax

```bash
pac pages upload-code-site \
  --rootPath <local-source-folder> \
  [--compiledPath <build-output-folder>] \
  [--siteName <site-display-name>]
```

#### Parameters

| Parameter        | Alias | Required  | Description                                                            |
| ---------------- | ----- | --------- | ---------------------------------------------------------------------- |
| `--rootPath`     | `-rp` | Yes       | Local folder that has your site’s source files                         |
| `--compiledPath` | `-cp` | No        | Path to compiled assets, like React `build`          |
| `--siteName`     | `-sn` | No        | Display name for your Power Pages site                                 |

#### Example

```bash
pac pages upload-code-site \
  --rootPath "../your-project" \
  --compiledPath "./build" \
  --siteName "Contoso Code Site"
```

If you don't have an existing project, you can start with the [sample React code site](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/bring-your-own-code-samples/react-sample).

---

### Download a code site

Use the [pac pages download-code-site](/power-platform/developer/cli/reference/pages#pac-pages-download-code-site) command to download an existing site’s code to a local directory so you can modify or back it up.

#### Syntax

```bash
pac pages download-code-site \
  [--environment <env-url-or-guid>] \
  --path <local-target-folder> \
  --webSiteId <site-guid> \
  [--overwrite]
```

#### Parameters

| Parameter       | Alias  | Required  | Description                                                                    |
| --------------- | ------ | --------- | ------------------------------------------------------------------------------ |
| `--environment` | `-env` | No        | Dataverse environment (GUID or full URL). Defaults to your active auth profile |
| `--path`        | `-p`   | Yes       | Local directory to download the site code                                      |
| `--webSiteId`   | `-id`  | Yes       | GUID of the Power Pages code site                                              |
| `--overwrite`   | `-o`   | No        | Overwrite existing files in the target directory if they exist                 |

#### Example

```bash
pac pages download-code-site \
  --environment "https://contoso.crm.dynamics.com" \
  --path "./downloaded-site" \
  --webSiteId "11112222-bbbb-3333-cccc-4444dddd5555" \
  --overwrite
```

### Activate and test your site

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select **Inactive sites**, find your site, and select **Reactivate**.
1. When the site is active, go to your site’s URL to check deployment.

> [!TIP]
> Any later `upload-code-site` command automatically updates the active site.

## Project structure and configuration

A consistent project layout helps ensure correct upload behavior:

```
/your-project
│
├─ src/                       ← Your source code (like React components)
├─ build/                     ← Compiled assets (output of the `npm run build` command)
├─ powerpages.config.json     ← Optional CLI configuration file
└─ README.md
```

* Use the optional `powerpages.config.json` file to customize CLI behavior, like excluding files or mapping routes.

## Authentication and authorization

Power Pages code sites use the same [security model](../security/power-pages-security.md) as traditional Power Pages sites.

### Configure identity providers

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. Find your site and select **Edit**.
1. Select **Security > Identity providers**.
1. Add or set up [identity providers](../security/authentication/index.md), like Microsoft Entra ID.
1. Each new site automatically has a default Microsoft Entra ID provider.

### Access user context in code

You can get authentication metadata on the client:

* **Authority URL:**
Authority URL / Login URL for Microsoft Entra Id is 
  ```js
  https://login.windows.net/<tenantId>
  ```

* **User details:**

  ```js
  window["Microsoft"].Dynamic365.Portal.User
  ```

### Sample React flow

```tsx
import { IconButton, Tooltip } from '@mui/material';
import {
    Login,
    Logout
} from '@mui/icons-material';
import React from 'react';

export const AuthButton = () => {
    const username = (window as any)["Microsoft"]?.Dynamic365?.Portal?.User?.userName ?? "";
    const firstName = (window as any)["Microsoft"]?.Dynamic365?.Portal?.User?.firstName ?? "";
    const lastName = (window as any)["Microsoft"]?.Dynamic365?.Portal?.User?.lastName ?? "";
    const isAuthenticated = username !== "";
    const [token, setToken] = React.useState<string>("");
    
    // @ts-ignore
    const tenantId = import.meta.env.VITE_TENANT_ID;

    React.useEffect(() => {
        const getToken = async () => {
            try {
                const token = await (window as any).shell.getTokenDeferred();
                setToken(token);
            } catch (error) {
                console.error('Error fetching token:', error);
            }
        };
        getToken();
    }, []);

    return (
        <div className="flex items-center gap-4">
            {isAuthenticated ? (
                <>
                    <span className="text-sm">Welcome {firstName + " " + lastName}</span>
                    <Tooltip title="Logout">
                        <IconButton color="primary" onClick={() => window.location.href = "/Account/Login/LogOff?returnUrl=%2F"}>
                            <Logout />
                        </IconButton>
                    </Tooltip>
                </>
            ) : (
                <form action="/Account/Login/ExternalLogin" method="post">
                    <input name="__RequestVerificationToken" type="hidden" value={token} />
                    <Tooltip title="Login">
                        <IconButton name="provider" type="submit" color="primary" value={`https://login.windows.net/${tenantId}/`}>
                            <Login />
                        </IconButton>
                    </Tooltip>
                </form>
            )}
        </div>
    );
};
```

## Differences from existing Power Pages sites

| Feature                 | Single Page Site behavior                                                            |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Server-side refresh** | Always returns the site’s root page. The client-side router renders sub-routes.    |
| **Route conflicts**     | Client-side routes take precedence. A hard refresh falls back to the root.           |
| **Page workspace**      | The [pages workspace](../getting-started/first-page.md) isn't supported. Use client routing and client site pages. For page-level security, use the global user object to check assigned web roles and conditionally render the UI. |
| **Style workspace**     | Styling via the [style workspace](../getting-started/style-site.md) isn't supported. Use your framework’s styling, like CSS, CSS-in-JS, or utility classes. |
| **Localization**        | Single-language support. You need to implement client-side resource loading.          |
| **Liquid templating**   | [Liquid](liquid/liquid-overview.md) code and Liquid templates aren't supported. Use your framework’s template engine and Web APIs to access data |

### Related information

- [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction)
- [Tutorial: Use Microsoft Power Platform CLI with Power Pages](power-platform-cli-tutorial.md)
- [Use the Visual Studio Code extension (preview)](vs-code-extension.md)
