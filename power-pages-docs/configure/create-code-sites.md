---
title: Create and deploy a single-page application in Power Pages
description: Discover how to upload, download, and activate Power Pages single-page application (SPA) sites with step-by-step guidance and examples.
author: neerajnandwana-msft
ms.topic: concept-article
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:05/20/2025
ms.date: 11/03/2025
ms.subservice:
ms.author: nenandw
ms.reviewer: dmartens
contributors:
  - neerajnandwana-msft
  - DanaMartens
---

# Create and deploy a single-page application in Power Pages

Power Pages supports integrating single-page application (SPA) code created with next-generation AI-assisted tools, like GitHub Copilot. This capability lets developers bring modern, component-based front-end experiences into Power Pages by using natural language as a coding interface.

By guiding, testing, and refining AI-generated code, makers can shift their focus from repetitive implementation tasks to higher-level orchestration. This empowers more intuitive, creative development while maintaining enterprise-grade quality and standards.

This article shows you how to:

- Create and set up an SPA project for Power Pages by using the [Power Platform CLI](/power-platform/developer/cli/introduction) (PAC CLI).
- Upload and download code assets to and from your Power Pages site.
- Set up a secure and maintainable project structure.
- Learn key differences between SPA-based and traditional Power Pages implementations.

> [!NOTE]
> - An SPA site is a Power Pages site that runs entirely in the user's browser (client-side rendering). Unlike traditional Power Pages sites, SPA sites are managed only through source code and command-line interface (CLI) tools.
> - [Power Platform Git integration](/power-platform/alm/git-integration/overview) isn't supported for Single-Page Application (SPA) websites in Power Pages.

## Prerequisites

Before you begin, make sure you have:

- A Power Pages environment with [admin privileges](../getting-started/create-manage.md#roles-and-permissions).
- [Power Platform CLI (PAC CLI)](/power-platform/developer/cli/introduction) version 1.44.x or later installed and authenticated.
- A Power Pages site on version 9.7.4.x or later.
- [Allow JavaScript file uploads](#)
- A local Git repository with your custom front-end project, such as React, Angular or Vue.

### Allow JavaScript file uploads**

By default, some Dataverse environments block the upload of JavaScript (`.js`) files. If you encounter the error **"Import failed: The attachment is either not a valid type or is too large. It cannot be uploaded or downloaded."** you must update your environment settings to allow this file type.

1. Sign in to the **[Power Platform admin center](https://admin.powerplatform.microsoft.com/)**.
2. Select your environment.
3. Select **Settings** > **Product** > **Privacy + Security**.
4. In the **Blocked attachments** section, remove `js` from the list of file extensions.
5. Select **Save**.

## Create and deploy an SPA site

Power Pages SPA sites are managed using the PAC CLI commands `upload-code-site` and `download-code-site`. After you upload a site, it appears in [Power Pages](https://make.powerpages.microsoft.com/) in the **Inactive sites** list. Activate the site to make it available to users.

### Upload an SPA site

Use the [pac pages upload-code-site](/power-platform/developer/cli/reference/pages#pac-pages-upload-code-site) command to upload your local source and compiled assets to your Power Pages environment.

#### Syntax

```powershell
pac pages upload-code-site `
  --rootPath <local-source-folder> `
  [--compiledPath <build-output-folder>] `
  [--siteName <site-display-name>]
```

#### Parameters

| Parameter        | Alias | Required  | Description                                                            |
| ---------------- | ----- | --------- | ---------------------------------------------------------------------- |
| `--rootPath`     | `-rp` | Yes       | Local folder that has your site’s source files                         |
| `--compiledPath` | `-cp` | No        | Path to compiled assets, like React `build`          |
| `--siteName`     | `-sn` | No        | Display name for your Power Pages site                                 |

#### Example

```powershell
pac pages upload-code-site `
  --rootPath "../your-project" `
  --compiledPath "./build" `
  --siteName "Contoso Code Site"
```

If you don't have an existing project, try the [sample implementations of SPA sites using React, Angular, and Vue](https://go.microsoft.com/fwlink/?linkid=2326698).

#### Defining upload parameters with `powerpages.config.json`

Customize the behavior of the `upload-code-site` command by including a `powerpages.config.json` file in your site. Place this configuration file in the site root folder. When you use config-based site uploads, run the `upload-code-site` command with just the `rootPath` parameter. The command automatically reads other values, like the compiled assets path and site display name, from the `powerpages.config.json` file. If you provide both command-line arguments and config values, the command-line arguments take precedence.

**Sample `powerpages.config.json`:**

```json
{
  "siteName": "Contoso Bank",
  "defaultLandingPage": "index.html",
  "compiledPath": "C:\\PowerPages\\your-project\\dist"
}
```

### Download an SPA site

Use the [pac pages download-code-site](/power-platform/developer/cli/reference/pages#pac-pages-download-code-site) command to download an existing site's code to a local directory for editing or backup purposes.

#### Syntax

```powershell
pac pages download-code-site `
  [--environment <env-url-or-guid>] `
  --path <local-target-folder> `
  --webSiteId <site-guid> `
  [--overwrite]
```

#### Parameters

| Parameter       | Alias  | Required  | Description                                                                    |
| --------------- | ------ | --------- | ------------------------------------------------------------------------------ |
| `--environment` | `-env` | No        | Dataverse environment (GUID or full URL). Defaults to your active auth profile |
| `--path`        | `-p`   | Yes       | Local directory to download the site code                                      |
| `--webSiteId`   | `-id`  | Yes       | Website record GUID of the Power Pages SPA site                                |
| `--overwrite`   | `-o`   | No        | Overwrite existing files in the target directory if they exist                 |

#### Example

```powershell
pac pages download-code-site `
  --environment "https://contoso.crm.dynamics.com" `
  --path "./downloaded-site" `
  --webSiteId "11112222-bbbb-3333-cccc-4444dddd5555" `
  --overwrite
```

### Activate and test your site

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select **Inactive sites**, find your site, and select **Reactivate**.
1. When the site is active, go to your site's URL to check deployment.

> [!TIP]
> Any later `upload-code-site` command automatically updates the active site.

## Project structure and configuration

A consistent project layout helps ensure correct upload behavior.

```
/your-project
│
├─ src/                       ← Your source code, like React components
├─ build/                     ← Compiled assets, output of the `npm run build` command
├─ powerpages.config.json     ← Optional CLI configuration file
└─ README.md
```

Use the optional `powerpages.config.json` file to customize how the `upload-code-site` command works.

## Authentication and authorization

Power Pages SPA sites use the same [security model](../security/power-pages-security.md) as traditional Power Pages sites.

### Configure identity providers

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. Find your site and select **Edit**.
1. Select **Security** > **Identity providers**.
1. Add or set up [identity providers](../security/authentication/index.md), like Microsoft Entra ID.
1. Each new site automatically has a default Microsoft Entra ID provider.

### Access user context in code

Get authentication metadata on the client:

- **Authority URL:**

    The authority or login URL for Microsoft Entra ID is:

    ```js
    https://login.windows.net/<tenantId>
    ```

- Find the **Authority URL** for other configured identity providers by going to [Power Pages](https://make.powerpages.microsoft.com) > `<your site>` > **Security** > **Identity providers** > configuration settings.

- **User details:**

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

## Use Power Pages Web APIs 

Developers can leverage [Power Pages Web APIs](web-api-overview.md) to load content into the UI or to create, update, and delete records. Before using these APIs, ensure that the required Web APIs are enabled and appropriate table permissions and web roles are properly configured.


```tsx

// Create query to get all cards from Dataverse
const fetchCards = async () => {
    const response = await fetch("/_api/cr7ae_creditcardses");
    const data = await response.json();
    const cards = data.value;
    const returnData = [];

    // Loop through the cards and get the name and id of each card
    for (let i = 0; i < cards.length; i++) {
        const card = cards[i];
        const cardName = card.cr7ae_name;
        const cardId = card.cr7ae_creditcardsid;
        const features = card.cr7ae_features
            ?.split(',')
            .map((feature: string) => feature.trim());
        const type = card.cr7ae_type;
        const image = card.cr7ae_image;
        const category = card.cr7ae_category
            ?.split(',')
            .map((cat: string) => cat.trim());
        
        // ...additional processing/pushing to returnData...
    }

    return returnData;
};

```

## Set up local development by enabling Web API calls from localhost using Microsoft Entra ID authentication

Developers need faster iteration cycles, local debugging, and hot reload capabilities when building applications. SPA supports these workflows by enabling secure Web API calls from `localhost` using Microsoft Entra ID (Azure AD) v1 authentication.

This setup lets you:
- Run your app locally with full authentication support.
- Use modern development tools like **Vite** for hot reload and rapid feedback.
- Avoid CORS issues when calling Power Pages Web APIs.
- Accelerate development without deploying changes to the portal.

This configuration enables a productive local development experience for SPA, allowing developers to build, test, and iterate quickly with full API access and authentication support.

> [!IMPORTANT]
> - Use only Microsoft Entra v1 endpoints for authentication.
> - Bearer authentication is supported only in portal versions 9.7.6.6 or later.
> - Apply these settings only in development environments.


### Configuration steps

1. **Enable SPA authentication**
   1. In https://portal.azure.com, open the Microsoft Entra app registered for your portal.
   2. Enable **Single Page Application (SPA)** authentication.
   3. Add `localhost` as a redirect URI using the **Single-page application** platform configuration. Refer to [How to add a redirect URI in your application](/entra/identity-platform/how-to-add-redirect-uri) for more details.
      - **Redirect URI**: `http://localhost:<port>/`.

2. **Add site settings**
   - Add these [site settings](configure-site-settings.md) in Power Pages:

   ```plaintext
   Authentication/BearerAuthentication/Enabled = true
   Authentication/BearerAuthentication/Protocol = OpenIdConnect
   Authentication/BearerAuthentication/Provider = AzureAD
   ```

3. **Use ADAL.js for login**
   - Implement client-side login using **ADAL.js**.

   > [!NOTE]
   > MSAL.js isn't compatible because Power Pages uses Microsoft Entra v1 endpoints, while MSAL uses v2. The issuer format differs between versions.

4. **Add authorization header**
   - Include this header in all Web API requests:

   ```http
   Authorization: Bearer <id_token>
   ```

5. **Set site visibility to Public**
   - This setting lets `localhost` access the site for development and testing purposes.

6. **Configure development proxy**
   - If you use **Vite**, add this to `vite.config.js` to avoid CORS issues:

   ```js
   export default defineConfig({
     plugins: [react()],
     server: {
       proxy: {
         '/_api': {
           target: 'https://site-foo.powerappsportals.com',
           changeOrigin: true,
           secure: true
         }
       }
     }
   });
   ```

## Differences from existing Power Pages sites

The following table summarizes key differences between SPA sites created with this feature and traditional Power Pages sites:

| Feature                 | SPA site behavior                                                            |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Server-side refresh** | Always returns the site’s root page, and the client-side router renders sub-routes.    |
| **Route conflicts**     | Client-side routes take precedence, and a hard refresh falls back to the root.           |
| **Page workspace**      | The [pages workspace](../getting-started/first-page.md) isn't supported. Use client routing and client site pages. For page-level security, check assigned web roles with the global user object, and conditionally render the UI. |
| **Style workspace**     | Styling with the [style workspace](../getting-started/style-site.md) isn't supported. Use your framework’s styling, such as CSS, CSS-in-JS, or utility classes. |
| **Localization**        | Single-language support. Implement client-side resource loading.          |
| **Liquid templating**   | [Liquid](liquid/liquid-overview.md) code and Liquid templates aren't supported. Access data by using your framework’s template engine and Web APIs. |

## FAQ

### What support is available for unit and integration testing?

Currently, there's no built-in support for unit and integration testing. Makers should write and execute these tests locally or within their CI/CD pipelines.

### Is there support for Power Fx integration using WebAssembly?

This capability isn't currently supported.

### Is source code available in Power Pages?

Currently, makers can build websites using TypeScript or GitHub Copilot Agent. The compiled JavaScript and CSS files are accessible and can be edited in Visual Studio Code. However, direct and extensive editing of HTML files isn't currently supported.

### Can I create a component externally using this feature and bring it to a Power Pages site?

No, you can't bring an externally generated component to an existing Power Pages site using this feature.

### Can I add out-of-the-box components like lists and forms?

Adding out-of-the-box components like lists and forms isn't currently supported. However, you can build custom forms and lists using the React framework and Web APIs.

### How does source control work?

Developers can use Power Platform Git integration for source control. However, only the compiled web files are added to the repository, not the full source code.

### Do these sites support SEO?

Because SPA sites are built with the React framework and use client-side rendering, SEO support is limited.

### What Power Pages security and governance support do SPA sites offer?

Power Pages enforces table permissions and security web roles on Web API calls, ensuring that data access aligns with user roles. Use the `window["Microsoft"].Dynamic365.Portal.User` object to retrieve basic user properties and tailor experiences based on user personas.

Additionally, SPA sites support:

- Public and private site configurations  
- Governance settings, including control over anonymous data access  
- Authentication provider configurations  

These features help ensure secure and compliant integration of custom components within Power Pages.

### Related information

- [Microsoft Power Platform CLI](/power-platform/developer/cli/introduction)
- [Tutorial: Use Microsoft Power Platform CLI with Power Pages](power-platform-cli-tutorial.md)
- [Use the Visual Studio Code extension](vs-code-extension.md)
