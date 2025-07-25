---
title: Known issues for Power Pages
description: List of known issues in Power Pages
author: DanaMartens
ms.topic: troubleshooting-known-issue
ms.date: 02/05/2025
ms.subservice:
ms.author: bipuldeora 
ms.reviewer: dmartens
contributors:
ms.custom:
  - sfi-image-nochange
---
# Known issues

## Power Pages trial

- If your admin disabled the self-service sign-up, you can't sign up for a trial of Power Pages.

- If your admin disables site creation for non-admin users in your company, you can't create a website. You're redirected to the Power Pages home page in the default environment. Reach out to your admin to provide you with an environment that has enough privileges for you to edit an existing site in the environment.

- If your admin disables the creation of a trial environment for non-admin users in your company, you can't create an environment. However, you can still create a site inside an existing environment in the tenant, where you have the necessary minimum privileges.

- When you create a site for the first time in a new environment, you can't rename the environment; however, the ability to rename the environment when it's created is available in a future update.

## Pages workspace

- Buttons added to websites built with the starter template can't be resized.

### Modifying the header in Portal Management App

When customizing the header, if someone modified the Liquid code, these changes must be synchronized. Changes don't reflect in studio until the attribute values in the underlying content snippets are updated to reflect these changes. To resolve this issue, open the Mobile Header content snippet in the [Portal Management app](configure/portal-management-app.md) and update the source code with the correct attribute values for each snippet as in the example below.

```html
<a href="~/">
    {% if snippets['Logo URL'] %}
        <img src="{{ snippets['Logo URL'] }}" alt="{{ snippets['Logo alt text'] }}" style="width: auto; height: 32px; margin: 0 10px;">
    {% endif %} 
    {% if snippets['Site name'] %}
        <h1 class="siteTitle">{{ snippets['Site name'] }}</h1>
    {% endif %}
</a> 
```

## Styling workspace

- The section padding and margin settings feature in the style workspace doesn't work for sites built using the starter templates.

## Adjusting the background color for your Power Pages site

This known issue applies only to sites created using Power Pages prior to September 23, 2022.

Power Pages themes have been updated to meet the highest visual accessibility standards.  To ensure that your existing Power Pages sites created prior to September 23, 2022 adhere to these standards, you'll need to update your theme settings to adjust the background using one of the following options.

### Option 1: Add a new color to the theme's palette

Add a new color to the theme's palette using the **Color Palette** in the **Style workspace**.

### Option 2: Edit a background on a section of the page

Select the desired color while editing the background on a section in the **Pages workspace**.

### Option 3: modify your theme

Modify the theme in the **Style workspace** using the following steps:

1. Select a different theme.
1. Choose your original theme.
1. Select **Save**.

## Site visibility

A Power Pages website in private mode won't work when you disable Microsoft Entra authentication. Microsoft Entra authentication is enabled by default when the website is provisioned. Change the [site visibility](security/site-visibility.md) state to **public** before disabling Microsoft Entra authentication.

## Dynamics 365 templates

For limitations related to editing Dynamics 365 templates using Power Pages design studio, see [Limitations](templates/dynamics-365-apps/overview.md#limitations).

## Visual Studio Code extension for Power Pages

- You might get an error when updating the Power Platform Tools for Visual Studio Code with the error message `Cannot install Power Pages generator: spawnSync npm.cmd ENOENT`. To resolve the issue, install [node.js](https://nodejs.org/en/download) and restart Visual Studio Code.

- Two sets of the Power Pages create commands might appear in the menu and won't work if you have both the stable version of **Power Platform Tools** and the **Power Platform Tools [PREVIEW]** installed on Visual Studio Code.

    Uninstall the **Power Platform Tools [PREVIEW]** version to resolve the issue.

## Microsoft Power Platform CLI for Power Pages

The following known issue applies only to PAC CLI version 1.29.6.
- You might receive the following error message while running [Power Pages download or upload command](configure/power-platform-cli.md#microsoft-power-platform-cli-commands-for-portals).

```
Sorry, the app encountered a non recoverable error and will need to terminate. The exception details have been captured and will be forwarded to the development team, if telemetry has been enabled. Exception Id: <guid>,Exception Type: System.AggregareException  The diagnostics logs can be found at: <Pac installation location>\logs\pac-log.txt
```
You can open pac-log.txt file and check for **MSALCachePersistenceException** to see if you're facing this issue
```
Error: Persistence check failed. Data was written but it could not be read. Possible cause: on Linux, LibSecret is installed but D-Bus isn't running because it cannot be started over SSH. HelpLink Url: Not Provided Stack Trace: at Microsoft.ldentity.Client.Extensions.Msal.Storage.VerifyPersistence0 at bolt.authentication.store.MsalExtensionCache
```
- You might not see login window when you use [pac auth](/power-platform/developer/cli/reference/auth) command to connect to your environment 

**Mitigation**: This known issue applies only to PAC CLI version 1.29.6. To resolve the issue, revert to the previous Power Apps CLI version 1.28.3. To uninstall the latest version 1.29.6, see [Uninstall Power Platform CLI for Windows](/power-platform/developer/cli/introduction#uninstall-power-platform-cli-for-windows) and install the previous version 1.28.3 from [here](https://www.nuget.org/packages/Microsoft.PowerApps.CLI/1.28.3).

## General issues

- You receive the following error message when configuring or using table fields:

    ***Field Name**: You've exceeded the maximum number of X characters in this field.*

    This can happen if the referenced field for the table exceeds characters limit mentioned in the error. To increase this limit, go to the Data workspace, select the table, select the field, choose **Edit column**. In the Advanced options, increase the **Maximum character count** field value to a higher value. Allowed values: 1 through 1,048,576. 

    Fields where limit might need to be increased:

    | Table | Field Display Name |
    | - | - |
    | Basic Form | Settings (adx_settings) |
    | List | View (adx_views) |
    | Basic Form Metadata | Subgrid Setting (adx_subgrid_settings) |
    | Web Page | Copy (adx_copy) |

- The **Modified Date** for the app might be incorrect because these apps are pre-provisioned apps and could have been provisioned earlier.

- When you create an environment along with the starter portal, the owner of the site isn't displayed correctly. It's displayed as System.

- If you're reusing the URL of a recently deleted site to create a new site, it has some delay for runtime to set up. This experience happens because the purge of previous resources would still be in progress and might take from 30 minutes to 1 hour for the new site to set up on Azure. The site will also not be available for editing during this time and might show errors when launched in studio for editing.

- When you switch environments in Power Apps, the sites within an environment might not show up immediately in the **Apps** or **Recent Apps** list. This experience happens particularly in environments that are created in a different region than their tenant. The workaround is to refresh the browser or wait for some time for the site to show up in the apps list. You can view all sites in an environment from the [Power Pages home page](https://aka.ms/mpp).

- If you keep the portal settings pane open in Power Apps home page while resetting the site from the [Power Pages hub](admin/admin-overview.md) in the Power Platform admin center, a user sees the "Something went wrong" error message in the portal settings pane, as the site is no longer available.

- In certain cases, when you create a new site, the styles aren't applied properly to the site, and the website is displayed without the styles when opened through **Browse website**. This behavior rarely happens, and styles can be recovered by restarting the site from the [Power Pages hub](admin/admin-overview.md) in the Power Platform admin center.

- When you configure a [basic form](/power-apps/maker/portals/configure/entity-forms) using the [Portals Management app](configure/portal-management-app.md), the incorrect model-driven form is displayed when rendered as a basic form on a page. This might happen when a model-driven form name is duplicated across different form types (**Main**, **Card**, and **QuickViewform**). Only one form name appears when configuring or creating a basic form for the portal. To resolve the issue, rename or create a copy (with a unique name) of the model-driven form to use when configuring the basic form. When creating a form in the [Data workspace](getting-started/use-data-workspace.md), you're only presented with the **Main** form.

- By default, Power Pages sites use the **Azure Active Directory Graph API** for the portal's [Azure app registration](/power-apps/maker/portals/admin/connectivity) which is currently deprecated. Power Pages will use the [Microsoft Graph API](/graph/use-the-api/) in a future update, so no administrator intervention is required. If the existing Azure Active Directory Graph API permission is replaced manually using the Microsoft Graph API, it reverts back to the Azure Active Directory Graph API when you [Enable or Disable SharePoint integration](/power-apps/maker/portals/manage-sharepoint-documents#step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center) from the Power Pages hub in the Power Platform admin center.

    :::image type="content" source="media/known-issues/azure-ad-graph-api.png" alt-text="Azure AD Graph API configuration.":::

- When configuring the *Open in New Window* setting on the **Profile** [web link](/power-apps/maker/portals/configure/manage-web-links), the profile page doesn't open in a new window. To resolve this issue, update the **Header** [web template](/power-apps/maker/portals/liquid/store-content-web-templates) by updating the [Liquid](/power-apps/maker/portals/liquid/liquid-overview) code in the `{% if profile_nav %}` section.

    :::image type="content" source="media/known-issues/profile-weblink.png" alt-text="Showing line of code to update in the header web template.":::

    > [!NOTE]
    > Make a backup of the **Header** web template before performing these steps.

    Replace this line of code:

    ```html
    <a aria-label="{{ link.name | escape }}" href="{{ link.url | escape }}" title="{{ link.name | escape }}">{{ link.name | escape }}</a>
    ```
    with this line:
    ```html
    <a aria-label="{{ link.name | escape }}" {% if link.Open_In_New_Window %} target="_blank" {% endif %} href="{{ link.url | escape }}" title="{{ link.name | escape }}">{{ link.name | escape }}</a>
    ```

- Adding a cloud flow immediately after creating a site results in a failure. To prevent this, wait approximately 30 minutes to 1 hour after you create the site before adding a cloud flow.

## Power Pages design studio issues

### Code components in design studio

Power Pages design studio’s canvas might not render some 3rd party code components.  Execution of untrusted scripts in third party code components, page copy, web templates, and content snippets are blocked because they can potentially access sensitive user data when rendered in Power Pages design studio.

### Images don't display in Power Pages design studio

If third-party cookies are disabled in your browser, images won't display in Power Pages design studio. To correct this known issue, enable cookies in your browser.

Here's how to enable cookies if your browser is blocking them:

# [Microsoft Edge](#tab/Edge)

1. In the Microsoft Edge window, select **More (...)** > **Settings** > **View advanced settings**.

1. Scroll down to **Cookies**, and select **Don't block cookies**.

# [Google Chrome](#tab/Chrome)

1. In a Chrome window, do one of the following:

    - In the browser address box, enter chrome://settings/content.

        OR

    - On the Chrome menu, select Settings > Show advanced settings, and then under Privacy, select Content settings.

1. In the Content settings dialog box, under **Cookies**, make sure **Allow local data to be set (recommended)** is selected.

1. Select **Done** and refresh the browser.

---

>[!NOTE]
> If you don't want to enable all third-party cookies, you can also adjust your browser settings to allow cookies for only ``[*.]powerpages.microsoft.com`` instead.

### Rich text editor (RTE) control on Power Pages

Only .png, .jpg, and .gif file formats are supported for drag and drop.
