---
title: Known issues for Power Pages release
description: A list of known issues in Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 2/24/2023
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---
# Known issues

## Power Pages trial

- If your administrator disabled the self-service sign-up, you won't be able to sign up for a trial of Power Pages. 

- If your administrator disables site creation for non-administrator–type users in your company, you won't be able to create a website. You'll be redirected to the Power Pages home page in the default environment. You'll have to reach out to your administrator to provide you with an environment that has enough privileges for you to edit an existing site in the environment. 

- If your administrator disables the creation of a trial environment for non-administrator–type users in your company, you won't be able to create an environment. However, you can still create a site inside an existing environment in the tenant, where you have necessary minimum privileges. 

- When you create a site for the first time in a new environment, you won't be able to rename the environment; however, the ability to rename the environment when it's created will be available in a future update. 

## Pages workspace

- Buttons added in websites built with the starter template can't be resized.

### Modifying the header in Portal Management App

When customizing the header, if someone has modified the Liquid code, these changes must be synchronized. Changes won't reflect in studio until the attribute values in the underlying content snippets are updated to reflect these changes. To resolve this issue, open the Mobile Header content snippet in the [Portal Management app](configure/portal-management-app.md) and update the source code with the correct attribute values for each snippet as in the example below.

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

- The section padding/margin settings feature in the Style workspace won't work for sites built using the starter templates.

## Adjusting the background color for your Power Pages site

This known issue applies only to sites created using Power Pages prior to September 23, 2022.

Power Pages themes have been updated to meet the highest visual accessibility standards.  To ensure that your existing Power Pages sites created prior to September 23, 2022 adhere to these standards, you'll need to update your theme settings to adjust the background using one of the following options.

### Option 1: add a new color to the theme's palette

Add a new color to the theme's palette using the Color Palette in the **Style workspace**.

### Option 2: edit a background on a section of the page

Select the desired color while editing the background on a section in the **Pages workspace**.

### Option 3: modify your theme

Modify the theme in the **Style workspace** using the following steps:

1. Select a different theme.

2. Choose your original theme.

3. Select **Save**.

## Site visibility

A Power Pages website in private mode will not work when you disable Azure Active Directory authentication. Azure Active Directory authentication is enabled by default when the website is provisioned. Change the [site visibility](/security/site-visibility.md) state to **public** before disabling Azure Active Directory authentication.

## Dynamics 365 templates 

Editing capabilities in Power Pages design studio are not available for [Microsoft Dynamics 365 templates](templates/dynamics-365-templates.md).

You can preview the webpages using design studio, but you can't add or modify sections, components, or text. 

Instead, use tools such as [Portals Management app](configure/portal-management-app.md) or [Visual Studio Code](configure/cli-tutorial.md) to edit the underlying [web templates](configure/store-content-web-templates.md) and configure them for your unique needs.

## Images not displaying in design studio

If third party cookies are disabled in your browser, images will not display in Power Pages design studio. To correct this known issue, you need to enable cookies in your browser. 

Here's how to enable cookies if your browser is blocking them:

### Edge (Windows 10)

1. In the Edge window, select More (...) > Settings > View advanced settings.

1. Scroll down to Cookies, and select Don't block cookies

### Internet Explorer

1. In Internet Explorer, in the menu bar, selectTools Tools button in Internet Explorer, upper right corner > Internet options > Privacy > Advanced.

1. Select Accept or Prompt under First-party Cookies, and Accept or Prompt under Third-party Cookies.

1. Select OK.

### Chrome

1. In a Chrome window, do one of the following:

    - In the browser address box, enter chrome://settings/content.

        OR

    - On the Chrome menu, select Settings > Show advanced settings, and then under Privacy, select Content settings.

1. In the Content settings dialog box, under Cookies, make sure Allow local data to be set (recommended) is selected.

1. Select Done and refresh the browser.

### Mozilla Firefox

1. If you’re using Windows, in the Firefox window, select Open menu Firefox browser options menu > Options.

    > [!TIP]  
    > If you’re using a Mac, go to Firefox > Preferences.

1. Select the Privacy tab.

1. In the History section under Firefox will, select Use custom settings for history.

1. Make sure Accept cookies from sites is checked and Accept third party cookies is set to Always, and then select OK.

### Safari

1. On your Mac, go to Safari > Preferences > Privacy.

1. Under Cookies and website data, select Always allow.

1. Select Close and refresh the browser. 



## General issues

- You receive the following error message when configuring or using table fields:

    ***Field Name**: You have exceeded the maximum number of X characters in this field.*

    This can happen if the referenced field for the table exceeds characters limit mentioned in the error. To increase this limit, go to the Data workspace, select the table, select the field, choose **Edit column**. In the Advanced options, increase the **Maximum character count** field value to a higher value. Allowed values: 1 through 1,048,576. 

    Fields where limit may need to be increased:

    | Table | Field Display Name |
    | - | - |
    | Basic Form | Settings (adx_settings) |
    | List | View (adx_views) |
    | Basic Form Metadata | Subgrid Setting (adx_subgrid_settings) |
    | Web Page | Copy (adx_copy) |

- The **Modified Date** for the app might be incorrect because these apps are pre-provisioned apps and could have been provisioned earlier.

- When you create an environment along with the starter portal, the owner of the site isn't displayed correctly. It's displayed as System.

- If you're reusing the URL of a recently deleted site to create a new site, it will have some delay for runtime to setup. This experience happens because the purge of previous resources would still be in progress and may take from 30 minutes to 1 hour for the new site to setup on Azure. The site will also not be available for editing during this time and may show errors when launched in studio for editing.

- When switching an environment in Power Apps, the sites within an environment may not show up immediately in **Apps** or **Recent Apps** list. This experience happens particularly on environments that are created in a different region than their tenant. The workaround is to use browser refresh or wait for some time for the site to show up in the apps list. You will be able to view all sites in an environment from the [Power Pages home page](https://aka.ms/mpp).

- If you keep the portal settings pane open in Power Apps home page while resetting the site from the [Power Pages hub](admin/admin-overview.md) in the Power Platform admin center, a user will see the "Something went wrong" error message in the portal settings pane, as the site is no longer available.

- In certain cases, when you create a new site, the styles aren't applied properly to the site, and the website is displayed without the styles when opened through **Browse website**. This behavior rarely happens and styles can be recovered by restarting the site from the [Power Pages hub](admin/admin-overview.md) in the Power Platform admin center.

- When configuring a [basic form](/power-apps/maker/portals/configure/entity-forms) using the [Portals Management app](configure/portal-management-app.md), the incorrect model-driven form is displayed when rendered as a basic form on a page. This may happen when a model-driven form name is duplicated across different form types (**Main**, **Card**, and **QuickViewform**). Only one form name appears when configuring or creating a basic form for the portal. To resolve the issue, rename or create a copy (with a unique name) of the model-driven form to use when configuring the basic form. When creating a form in [Data workspace](getting-started/use-data-workspace.md), you will only be presented with the **Main** form.

- By default, Power Pages sites uses the **Azure Active Directory Graph API** for the portal's [Azure app registration](/power-apps/maker/portals/admin/connectivity) which is currently deprecated. Power Pages will use the [Microsoft Graph API](/graph/use-the-api/) in a future update, so no administrator intervention is required. If the existing Azure Active Directory Graph API permission is replaced manually using the Microsoft Graph API, it will revert back to the Azure Active Directory Graph API when you [Enable or Disable SharePoint integration](/power-apps/maker/portals/manage-sharepoint-documents#step-2-set-up-sharepoint-integration-from-power-apps-portals-admin-center) from the Power Pages hub in the Power Platform admin center.

    :::image type="content" source="media/known-issues/azure-ad-graph-api.png" alt-text="Azure AD Graph API configuration.":::

- When configuring the *Open in New Window* setting on the **Profile** [web link](/power-apps/maker/portals/configure/manage-web-links), the profile page will not open in a new window. To resolve this issue, update the **Header** [web template](/power-apps/maker/portals/liquid/store-content-web-templates) by updating the [Liquid](/power-apps/maker/portals/liquid/liquid-overview) code in the `{% if profile_nav %}` section.

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

## Power Apps portals Studio issues

> [!NOTE]
> You can edit and design Power Apps portals sites using the new Power Pages design studio. More information: [Power Pages design studio and Power Apps portals Studio](/power-pages/configure/editing-sites).

- If a site has page hierarchy of more than three levels, the pages from fourth level onwards aren't displayed in Power Apps portals Studio.

- The selected text font size will only be displayed if there's a font size defined specifically for that text. If it's part of the standard HTML tags such as p, H1, H2, H3, and so on, Power Apps portals Studio won't display the font size.

- Webpage using the **Page with side navigation** template displays only the link of the pages that existed during the webpage creation. You can update the links on the left side of the page by changing the page template to another template and then back to **Page with side navigation**.

- When you delete a webpage, canvas doesn't reflect the updated menu until the next refresh of canvas.

- Color picker and its related strings are supported only in English.

- A few template pages on the Employee Self Service portal aren't able to render correct breadcrumb.

- A few Power Apps portals templates, especially bound to customer engagement apps (such as Dynamics 365 Sales and Dynamics 365 Customer Service), don't have default menu items as per their hierarchy of pages. The reason is that there isn't page order available in all or few of the webpages. Any portal without the display order of webpages will have this issue.

- An error message is displayed when the page content (page copy) exceeds its limit of 65536 characters and page summary exceed its default limit of 2000 characters.

- Navigation menu is only visible on the canvas with a resolution of minimum width of 1600 px.

- An image uploaded on a page becomes the child of the page. If you delete the page, and use the image on another page, the image won't render on Power Apps portals Studio and website.

- Form rendering isn't currently supported in Power Apps portals Studio. When you add a form, you must select **Browse website** to open the website and verify the form.

- On a text or a section background, if you change the color to **No color**, Power Apps portals Studio doesn't remove the related attributes such as background color or font color, instead make the values null.

- In the following scenarios Power Apps portals Studio stops to load and shows the "Sorry, there's a disconnect" error:
    - If the Home page is deleted or disabled for a portal.
    - If a page template related to the Home page or any page is disabled or deleted.

- Power Apps portals Studio will be unable to load source code of those content snippets that don't have a language assigned in Dataverse.

- In some instances, the changes for header and footer, either through WYSIWYG experience of Power Apps portals Studio or through the code editor, won't be reflected immediately.

- If a webpage is assigned the Search template in Power Apps portals Studio, it will show a page with the loader. For this scenario to work, you'll have to create an appropriate site marker for that page.

- The Default studio template also shows up as an option in page template while creating a new page once it's used in Power Apps portals Studio. Also, this template is only inserted in English language and it doesn't support localization based on default Dataverse or portal language.

- A list rendered as a calendar control or map isn't configurable through Power Apps portals Studio.

- The Partial URL field in page properties doesn't accept special characters and it breaks the rendering in the canvas for some time.

- Upload CSS might fail in scenarios where CSS file name contains special characters or space in the file name.

- Unpublished webpages don't render in canvas of Power Apps portals Studio.

- While using Power Apps portals Studio, if your portal base language is different than the browser's language, the new webpages created using the Default studio template will have dummy content inserted in browser's language instead of portal language.

- Only CSS applied at the root page is displayed in the **Theme** pane. Although if you try uploading a CSS file with a same name as any other CSS file available in the portal, Power Apps portals Studio asks you to replace that file.

- Power Apps portals Studio is currently not supported on Safari in Mac operating system and has the following issues:
    - The selection of component isn't correct and hovering on a component provides incorrect target indication.
    - Two or three column sections don't render properly in Power Apps portals Studio but works fine on the website.

### See also

[Power App portal maintenance and troubleshooting](/training/modules/portals-maintenance-troubleshooting/)
A Power Pages website in private mode won't work when you disable Azure Active Directory authentication. Azure Active Directory authentication is enabled by default when the website is provisioned. Change the [site visibility](/security/site-visibility.md) state to **public** before disabling Azure Active Directory authentication.
