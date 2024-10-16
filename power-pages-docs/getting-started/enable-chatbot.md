---
title: Add a copilot to your Power Pages site
description: Learn how to add copilot to your Power Pages site for quicker customer support and an improved user experience.
ms.topic: how-to
ms.date: 10/15/2024
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection: 
  - bap-ai-copilot
contributors:
  - nageshbhat-msft
  - DanaMartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:09/07/2023
  - bap-template
---

# Add a copilot to your Power Pages site

Enhance your Power Pages site with a copilot to deliver swift and effective customer support, elevating the user experience for your visitors. Power Pages simplifies the process, allowing you to integrate a Microsoft Copilot Studio copilot within minutes. This copilot leverages [generative answers](/microsoft-copilot-studio/nlu-boost-conversations) to provide natural language responses, addressing questions and offering solutions in a conversational manner.

Follow the steps in this article to create a preconfigured copilot. If you already have a copilot in Microsoft Copilot Studio, you can [update Power Pages to use that copilot](pva-bot-how-to.md). The default setup allows the copilot to answer questions based on your Power Pages website's information. You can also configure the copilot to [generate answers from publicly available data by using Bing search](force-bing-index.md). Configuring Bing search enables the generation of answers from external sources beyond the Power Pages site built on the Dataverse instance. If you use Dynamics 365 Customer Service, you can [configure Omnichannel with your Power Pages site copilot](../configure/omnichannel.md) to seamlessly transition customers to a live agent if the copilot cannot resolve their queries or if they need a response beyond the site's capabilities.

> [!IMPORTANT]
>
> If you configure copilot for generative answers from public data using Bing search, use of Bing Search is governed by the [Microsoft Services Agreement](https://go.microsoft.com/fwlink/?linkid=2178408) and [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Prerequisites

To use AI-powered Copilot features in Power Pages:

- Your tenant administrator must turn on the setting [Publish Copilots with AI features](/microsoft-copilot-studio/security-and-governance) in the Power Platform admin center.
- Copilot uses Microsoft Copilot Studio generative answers. Learn more about generative answers in Copilot Studio in [Knowledge sources overview](/microsoft-copilot-studio/nlu-boost-conversations#whats-supported).

## Add a copilot

Follow these steps to manually add a copilot:

> [!NOTE]
> If a site meets the conditions outlined in the prerequisite section, the copilot will be added to the site during site provisioning. If you prefer not to have the copilot created by default, the [service admins](/power-platform/admin/use-service-admin-role-manage-tenant) can disable this capability at the tenant level, as described in the section [turn off default copilot provision](/power-pages/getting-started/enable-chatbot#turn-off-default-copilot-provisioning).  

1. Go to the [Set up workspace](../configure/setup-workspace.md).
1. Under **Copilot,** select **Add copilot**

    :::image type="content" source="media/enable-chatbot/select-copilot.png" alt-text="Screenshot of the copilot page in Power Pages.":::

1. Turn on **Create copilot**.

    Power Pages creates a [copilot with generative answers conversation](/microsoft-copilot-studio/nlu-boost-conversations) for you in Copilot Studio.

1. To make the copilot available to visitors and users, turn on **Enable copilot on site**.

    If your tenant admin hasn't turned on publish copilot with AI features, the **Enable copilot on site** isn't available.

## Customize your copilot

When creating a copilot for a website, it utilizes the content from the hosting site to generate responses. The Dataverse service facilitates the indexing of site content and configured tables, which are then summarized by Copilot Studio to generate responses.

Authenticated site users receive tailored, summarized answers that align with their web roles. To further improve the content model for authenticated site users, refine the data by following these steps within the **Add copilot** section:

1. Under **Refine your data**, choose the **Make changes** button.
1. Select **Choose tables lookup control** to select or deselect the tables.
    - You can select multiple tables in this section. Make sure any table you select here is used on the site.
    - On subsequent pages, you must specify the page where the table is used for generating the citation URL.
1. Select **Next**.
1. Under **Choose tables**, select the table that contains the columns and page link you wish to select. The table won't appear unless it has at least one multi-line column.
    - You can select one table at a time.
1. Under **Add page link**, select the page where table is used.  

    > [!NOTE]
    >
    > - Make sure you select the correct page where the table is used. Choosing the wrong table will result in the bot providing an incorrect citation URL for the answers.
    > - The page must use 'id' as the query string parameter. The citation URL will not function correctly if any other parameter name is used.

1. Under **Choose columns**, select the list of columns that are used in the page.

    > [!NOTE]
    > Only a column with multiline text is available to choose.  

1. Select **Next** and review the selection.
1. Choose **Save** to submit the changes.

## Customize copilot appearances

You can customize the copilot's style by overriding the default Cascade Style Sheet (CSS) classes. To do so, add a style tag to the header template and follow these steps to override the values.

1. Go to the site's [code editor](../configure/visual-studio-code-editor.md).
1. From **Explorer navigation**, expand the **web-templates** folder.
1. Open **Header.html**.
1. Add your style tag.
    :::image type="content" source="media/enable-chatbot/code-editor.png" alt-text="A screenshot of Visual Studio with a folder, file, and CSS selector emphasized.":::
1. Override the respective styles.

### Copilot widget

:::image type="content" source="media/enable-chatbot/open-chat-window-css.svg" alt-text="A screenshot of the chatbot widget.":::

Copilot collapsed icon:

```css
.pva-embedded-web-chat-widget {
    	background-color: #484644;
	border: 1px solid #FFFFFF;
}
```

Tooltip:

```css
.pva-embedded-web-chat-widget .pva-embedded-web-chat-widget-tooltip-text {
	background: white;
	color: #323130;
}
```

### Copilot elements

Reference the CSS samples provided for examples of how to customize your chatbot's elements.

:::image type="content" source="media/enable-chatbot/chatbot-css.svg" alt-text="A screenshot of a chatbot with individual elements annotated.":::

#### 1. Header

```css
.pages-chatbot-header 
{ 
	background: #77a145;  
	color: #ffffff; 
}
```

#### 2. Height and Width

```css
.pva-embedded-web-chat[data-minimized='false'] {
 	height: 80%;
	width: 25%;
	max-width: 400px;
	max-height: 740px;
}
```

#### 3. Copilot window

```css
.pva-embedded-web-chat-window { 
  background: white;  
} 
```

#### 4. Bubble from copilot

Background color:

```css
.webchat__bubble:not(.webchat__bubble--from-user) .webchat__bubble__content { 
  background-color: #77a145 !important;  
  border-radius: 5px !important; 
} 
```

Text color:

```css
.webchat__bubble:not(.webchat__bubble--from-user) p {  
color: #ffffff; 
} 
```

#### 5. Bubble from user

Background color:

```css
.webchat__bubble.webchat__bubble--from-user .webchat__bubble__content { 
  background-color: #797d81 !important;  
  border-radius: 5px !important; 
} 
```

Text color:

```css
.webchat__bubble.webchat__bubble--from-user p {  
  color: #ffffff; 
} 
```

#### 6. Reference links

```css
.webchat__link-definitions__badge {  
  color: blue !important; 
} 

.webchat__link-definitions__list-item-text {  
  color: blue !important;  
} 

.webchat__render-markdown__pure-identifier {  
  color: blue !important; 
} 
```

#### 7. Privacy message

Background color:

```css
.pva-privacy-message {  
  background: #797d81;  
} 
```

Text color:

```css
.pva-privacy-message p {  
  color: #ffffff;  
  font-size: 12px;  
  font-weight: 400; 
} 
```

## Turn off default copilot provisioning

[Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) who are members of any of the following Microsoft Entra roles can use a PowerShell script to change the tenant-level setting `enableChatbotOnWebsiteCreation`:

- [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
- [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

The default value of the tenant-level setting is ‘null’ which will behave as if the setting is set to ‘true’ and creates the bot during site creation. The admin can set its value to ‘true’ or ‘false’.

To get the current value of the tenant-level setting, use the [Get-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings) command. For example:
>

```powershell
$myTenantSettings = Get-TenantSettings
$myTenantSettings.powerPlatform.powerPages
```

> [!NOTE]
> The Get-TenantSettings command doesn't list tenant settings whose value is null. The default value of the tenant-level setting `enableChatbotOnWebsiteCreation` is null, so it doesn't appear the first time you run the script. After you set its value to `true` or `false`, the setting appears in the list.

To set a value for `enableChatbotOnWebsiteCreation`, use the [Set-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/set-tenantsettings) command. The following example sets the value to `false`:

```powershell
$requestBody = @{
    powerPlatform = @{
        powerPages = @{
            enableChatbotOnWebsiteCreation = $false
        }
    }
}
Set-TenantSettings -RequestBody $requestBody
```

## Known issues

- To change your site's custom domain after adding a copilot, first turn off the copilot, update the custom domain, and then turn the copilot back on.
- If you turn off the copilot feature, allow a few minutes for background operations to complete before you turn it on again.

### See also

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Force Bing webmaster to index your site (preview)](../getting-started/force-bing-index.md)
- [Responsible AI - FAQ for site copilot](../faqs-chatbot.md).
