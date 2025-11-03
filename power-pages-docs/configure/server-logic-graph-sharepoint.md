---
title: Integrate Microsoft Graph and SharePoint with server logic
description: Learn how to integrate Power Pages with Microsoft Graph and SharePoint Online using server logic. Follow this step-by-step guide to set up and test the sample.
#customer intent: As a developer, I want to set up and test the Server Logic sample so that I can integrate Power Pages with Microsoft Graph and SharePoint Online.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 10/31/2025
ms.topic: concept-article
---

# How to: interact with Microsoft Graph and SharePoint using server logic 

This guide walks you through setting up and testing the server logic sample that integrates Power Pages with Microsoft Graph and SharePoint online. 

## Step 1: Download the sample package 

1. Go to the GitHub repository [https://github.com/microsoft/power-pages-samples](https://github.com/microsoft/power-pages-samples). 
1. Select **Code > Download ZIP**.
1. After downloading, extract the ZIP file to a local folder, for example:
    `C:\PowerPages\ServerLogic`
1. Navigate to the extracted path:
   `samples/server-logic/sharepoint-integration`
This folder contains the `event-registration.zip` solution package, which includes the Power Pages site resources you will import in later steps.

Alternatively, use git clone if you prefer.

```bash
git clone https://github.com/microsoft/power-pages-samples.git
cd power-pages-samples/samples/server-logic/sharepoint-integration
```

## Step 2: Prerequisites 

Before you start, make sure you have: 

- Access to **Microsoft Entra ID (Azure AD)** with permission to register apps. 
- Access to a **SharePoint Online site** (for example, [https://contoso.sharepoint.com/sites/EventSite](https://contoso.sharepoint.com/sites/EventSite)). 

## Step 3: Create and configure the Entra ID application 

You need an app registration to allow your server logic code to authenticate against Microsoft Graph. 

### Create the app registration 

1. Go to the [**Azure Portal**](https://portal.azure.com/), and select **App registrations**. 
1. Select **+ New registration**. 
1. Provide a name (for example, PowerPages-Graph-Integration). 
1. Choose **Accounts in this organizational directory only**. 
    > [NOTE!]
    > You don't need to provide a redirect URI for this sample. 
1. Select **Register**. 

### Configure API permissions 

1. In the new app, go to **API Permissions** > **Add a permission**. 
1. Select **Microsoft Graph** > **Application permissions**. 
1. Add the following permissions: 
    - Sites.ReadWrite.All (for SharePoint file operations) 
    - Mail.Send *(optional – only needed if you plan to enable the email section)* 
1. Select **Grant admin consent** for your tenant. 

### Create a client secret 

1. Go to **Certificates & secrets** > **Client secrets**. 
1. Select **+ New client secret**. 
1. Enter a description and choose an expiry period (for example, six months). 
1. Select **Add**, and **copy the generated value** immediately—this is your **CLIENT_SECRET**. 

### Collect required values 

From your Azure app: 

- **Client ID** → CLIENT_ID 
- **Tenant ID** → TENANT_ID 
- **Client Secret** → CLIENT_SECRET 

## Step 4: Identify your SharePoint site and folder 

The script uploads generated event tickets to a SharePoint site. 

1. Identify your **SharePoint hostname** and **site path**: 
    For example: HOSTNAME = `contoso.sharepoint.com` 
    SITE_PATH = `/sites/EventSite` 
1. Ensure a document library called **Documents** exists (default). 

## Step 5: Deploy the package 

1. Create a new site by importing the recently downloaded site from GitHub. To learn how to import the site, see [power-pages-solutions](/power-pages/configure/power-pages-solutions)  
1. During the site upgrade, update the values for environment variables. Update the following values that you captured in previous steps: 

    - **Client ID**  
    - **Tenant ID** 
    - **Client Secret** (Keep this value in a key vault and use it in the environment variable. For testing, you can keep it directly in the environment variable.) 
    - **HOSTNAME**  
    - **SITE_PATH**  

### Script highlight: Configuration section

```javascript
const CLIENT_ID = Server.SiteSetting.Get("CLIENT_ID");
const CLIENT_SECRET = Server.SiteSetting.Get("CLIENT_SECRET");;
const TENANT_ID = Server.SiteSetting.Get("TENANT_ID");

const HOSTNAME = Server.SiteSetting.Get("HOSTNAME"); 
const SITE_PATH = Server.SiteSetting.Get("SITE_PATH"); 
```
These are securely loaded from Power Pages site settings (environment variables).

## Step 6: Test the SharePoint integration 

The script processes **event registration form submissions**, acquires a Microsoft Graph access token, generates an **HTML ticket**, uploads it to SharePoint, and creates a record in Dataverse. 

### Script highlight: Calling Microsoft Graph for access token

```javascript
async function getAccessToken() {
   const body = {
      "client_id": CLIENT_ID,
      "client_secret": CLIENT_SECRET,
      "scope": "https://graph.microsoft.com/.default",
      "grant_type": "client_credentials"
   };
   const tokenResp = await Server.Connector.HttpClient.PostAsync(
      `https://login.microsoftonline.com/${TENANT_ID}/oauth2/v2.0/token`,
      JSON.stringify(body),
      { "Content-Type": "application/x-www-form-urlencoded" },
      "application/x-www-form-urlencoded"
   );
   const tokenJson = JSON.parse(JSON.parse(tokenResp).Body);
   return tokenJson.access_token;
}
```

### Script highlight: Uploading ticket to SharePoint

```javascript
const siteResp = await Server.Connector.HttpClient.GetAsync(
  `https://graph.microsoft.com/v1.0/sites/${HOSTNAME}:${SITE_PATH}`,
  { Authorization: `Bearer ${accessToken}` }
);
const siteId = JSON.parse(JSON.parse(siteResp).Body).id;

const driveResp = await Server.Connector.HttpClient.GetAsync(
  `https://graph.microsoft.com/v1.0/sites/${siteId}/drive`,
  { Authorization: `Bearer ${accessToken}` }
);
const driveId = JSON.parse(JSON.parse(driveResp).Body).id;

const uploadUrl = `https://graph.microsoft.com/v1.0/drives/${driveId}/root:/Tickets/${fileName}:/content`;

await Server.Connector.HttpClient.PutAsync(
  uploadUrl,
  htmlTicket,
  { Authorization: `Bearer ${accessToken}`, "Content-Type": "text/html" },
  "text/html"
);
```

After a successful run: 

1. A new record appears in **Dataverse** under **crd69_eventregistrations**. 
1. An HTML ticket file is uploaded to your **SharePoint Documents > Tickets** folder. 
1. The *crd69_ticketurl* field contains the link to the uploaded ticket file. 

## (Optional) Step 7: Enable email notification 

To send a confirmation email to the attendee: 

1. Uncomment the **"Send confirmation email"** section in the script. 
1. Replace {senderUserId} with a valid **mailbox-enabled user ID** (for example, a service account). 
1. Ensure Mail.Send permission is added and admin-consented.

### Related information

[Server logic overview](server-logic-overview.md)  
[Author server logic](author-server-logic.md)  
[Server objects](server-objects.md)   
[How to interact with Dataverse tables using Server logic](server-logic-operations.md)  
