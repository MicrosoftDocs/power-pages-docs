# Create and Deploy a Power Pages Code Site

This article describes how to create, configure, and deploy a Power Pages Code Site using the Power Platform CLI (PAC CLI). You’ll learn how to upload and download code, configure your project structure, secure your site, and understand key differences from traditional Power Pages sites.

> **Note:** A Code Site is a fully client-rendered Power Pages site that you manage entirely through source code and CLI commands.


## Prerequisites

Before you begin, ensure that you have:

* A Power Pages environment with **Administrator** privileges
* The [Power Platform CLI (PAC CLI)](https://learn.microsoft.com/power-platform/developer/cli/introduction) installed and authenticated
* A local Git repository containing your custom frontend project (for example, React, Angular, or Vue)


## Create and Deploy a Code Site

Power Pages Code Sites are managed via the PAC CLI commands `upload-code-site` and `download-code-site`. After uploading, a site appears in the **Inactive sites** list in the Power Pages admin workspace. You must then activate it to make it available to end users.

### 1. Upload a Code Site

Upload your local source and compiled assets to the Power Pages environment.

#### Syntax

```bash
pac pages upload-code-site \
  --rootPath <local-source-folder> \
  [--compiledPath <build-output-folder>] \
  [--siteName <site-display-name>]
```

#### Parameters

| Parameter        | Alias | Description                                                            |
| ---------------- | ----- | ---------------------------------------------------------------------- |
| `--rootPath`     | `-rp` | **(Required)** Local folder containing your site’s source files        |
| `--compiledPath` | `-cp` | Path to compiled assets (for example, React `build` or Angular `dist`) |
| `--siteName`     | `-sn` | Display name for the Power Pages site                                  |

#### Example

```bash
pac pages upload-code-site \
  --rootPath "../your-project" \
  --compiledPath "./build" \
  --siteName "Contoso Code Site"
```

---

### 2. Download a Code Site

Retrieve an existing site’s code to a local directory for modification or backup.

#### Syntax

```bash
pac pages download-code-site \
  [--environment <env-url-or-guid>] \
  --path <local-target-folder> \
  --webSiteId <site-guid> \
  [--overwrite]
```

#### Parameters

| Parameter       | Alias  | Description                                                                    |
| --------------- | ------ | ------------------------------------------------------------------------------ |
| `--environment` | `-env` | Dataverse environment (GUID or full URL); defaults to your active auth profile |
| `--path`        | `-p`   | **(Required)** Local directory to download the site code                       |
| `--webSiteId`   | `-id`  | **(Required)** GUID of the Power Pages Code Site                               |
| `--overwrite`   | `-o`   | Overwrites existing files in the target directory if they already exist        |

#### Example

```bash
pac pages download-code-site \
  --environment "https://contoso.crm.dynamics.com" \
  --path "./downloaded-site" \
  --webSiteId "5a4f1363-8d97-40db-9407-dca5afbf5db8" \
  --overwrite
```


### 3. Activate and Test Your Site

1. Sign in to the [Power Pages admin center](https://make.powerpages.microsoft.com/) and navigate to **Sites**.
2. Locate your Code Site under **Inactive sites**, then select **Activate**.
3. Once active, browse to your site’s URL to verify deployment.

> **Tip:** Any subsequent `upload-code-site` commands will automatically update the active site.


## Project Structure and Configuration

A consistent project layout ensures correct upload behavior:

```
/your-project
│
├─ src/               ← Your source code (e.g. React components)
├─ build/             ← Compiled assets (output of `npm run build`)
├─ powerpages.config.json  ← Optional CLI configuration file
└─ README.md
```

* **powerpages.config.json**
  Customize CLI behavior (for example, exclude files or map routes).
* To specify a custom config location, add `--configPath <file-path>` to the upload command.


## Authentication and Authorization

Power Pages Code Sites leverage the same security model as traditional pages.

### Configure Identity Providers

1. In the Power Pages admin center, select **Security > Identity providers**.
2. Add or configure providers (for example, Microsoft Entra ID).
3. A default Entra ID provider is created automatically for each new site.

### Access User Context in Code

Authentication metadata is exposed on the client:

* **Authority URL:**

  ```js
  window["Microsoft"].Dynamic365.Portal.Authentication.authority
  ```
* **User details:**

  ```js
  window["Microsoft"].Dynamic365.Portal.User
  ```

### Sample React Flow

```tsx
import React from 'react';
import { shell } from '@microsoft/powerpages';

export function App() {
  const [token, setToken] = React.useState<string | null>(null);

  React.useEffect(() => {
    (async () => {
      try {
        const csrfToken = await shell.getTokenDeferred();
        setToken(csrfToken);
      } catch (err) {
        console.error('Failed to fetch CSRF token', err);
      }
    })();
  }, []);

  return (
    <form
      action="/Account/Login/ExternalLogin"
      method="post"
    >
      <input
        name="__RequestVerificationToken"
        type="hidden"
        value={token ?? ''}
      />
      <button
        name="provider"
        type="submit"
        value={window["Microsoft"].Dynamic365.Portal.Authentication.authority}
      >
        Sign In
      </button>
    </form>
  );
}
```

## Differences from existing Power Pages Sites

| Feature                 | Code Site Behavior                                                            |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Server-side refresh** | Always returns the site’s root page; client-side router renders sub-routes    |
| **Route conflicts**     | Client-side routes take precedence; hard refresh falls back to root           |
| **Page workspace**      | Page workspace feature is **not** supported—use client routing and client site pages. For page-level security, use the global user object to read assigned web roles and conditionally render UI. |
| **Style workspace**     | Styling via the style workspace is **not** supported—use your framework’s styling (CSS, CSS-in-JS, or utility classes) |
| **Localization**        | Single-language support; must implement client-side resource loading          |
| **Liquid Templating**   | Liquid code and Liquid templates are **not** supported—use your framework’s templating engine |


