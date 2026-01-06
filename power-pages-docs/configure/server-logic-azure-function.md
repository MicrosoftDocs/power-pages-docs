---
title: Connect Power Pages server logic to Azure Function
description: Learn how to integrate Azure Function HTTP triggers with Power Pages server sogic in this step-by-step guide. Build seamless server-side interactions effortlessly.
#customer intent: As a developer, I want to integrate Azure Function HTTP triggers with Power Pages Server Logic so that I can create dynamic web applications.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 01/06/2026
ms.topic: how-to
---

# How to: interact with Azure Function HTTP trigger using server logic 

This tutorial demonstrates how to integrate Azure Function HTTP trigger with Power Pages server logic. You use the official Azure Functions QuickStart Sample as the backend API and learn how to call it from server logic. 

For detailed Azure Function creation and HTTP trigger setup, see the official Azure Functions QuickStart: [Azure Functions JavaScript QuickStart Sample](/azure/azure-functions/functions-bindings-http-webhook-trigger?tabs=python-v2%2Cisolated-process%2Cnodejs-v4%2Cfunctionsv2&pivots=programming-language-javascript#example). 

## Step 1: Create Azure Function 

For this tutorial, use the official Azure Functions QuickStart sample. 

1. Go to the Azure portal and create a **Function App** with the Node.js runtime. 
1. Add a new **HTTP trigger function** named server-logic-api. 
1. Use the sample code provided in the Quickstart repository. 
1. Copy the **Function URL** including the function key. 

For the full step-by-step guide, see [Azure Functions JavaScript Quickstart Sample](/azure/azure-functions/functions-bindings-http-webhook-trigger?tabs=python-v2%2Cisolated-process%2Cnodejs-v4%2Cfunctionsv2&pivots=programming-language-javascript#example). 

**Example HTTP trigger code (JavaScript)** 

```javascript
const { app } = require('@azure/functions');

app.http('httpTrigger1', {
    methods: ['GET', 'POST'],
    authLevel: 'anonymous',
    handler: async (request, context) => {
        context.log(`Http function processed request for url "${request.url}"`);
        const name = request.query.get('name') || (await request.text()) || 'world';
        return { body: `Hello, ${name}!` };
    },
});
``` 

Test the function directly with a browser or Postman: 

`https://yourfuncapp.azurewebsites.net/api/ServerLogicApi?name=Alice&code=XXXX` 

Expected response: 

`https://yourfuncapp.azurewebsites.net/api/ServerLogicApi?name=Alice&code=XXXX`

`{"message": "Hello Alice! " }`

## Step 2: Create Power Pages server logic 

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).
1.Select the required site, and then select **+Edit**.
1. Go to the **Set up** workspace, and then select **Server logic (preview)**.
1. Select **+New server logic**.
1. Enter a name for the server logic. This name is used in the API as a resource identifier while you construct the server logic API. For example:
    | **Property**  | **Example Value**                      |
    |---------------|----------------------------------------|
    | Name          | Call-azure-function                    |
    | Display Name  | Call azure function from server logic  |
1. Select **+Add roles** to assign the appropriate web role. In this example, select **Authenticated User**, and then sign in to proceed.
1. Select **Add**. 
1. Select the server logic, and then select **Edit code**.
1. In the **Edit in Microsoft Visual Studio Code for the Web** dialog, select **Open Visual Studio Code** to author the custom logic. You'll find predefined methods and scripts in the file. Clear all existing code.
1. Replace the code with the following code to invoke the Azure function URL.
    ```javascript
    // Azure Function URL including function key
    const functionUrl = '<replace function url copied in previous step>'
    
    async function get() { 
      const name = Server.Context.QueryParameters["name"] || "World";
      
      const response = await Server.Connector.HttpClient.GetAsync(
        functionUrl
      );
      
      return JSON.parse(response).Body;
    }
    ``` 
1. Save the server logic.

Server logic endpoint URL format: 

`https://<your-power-page>/_api/serverlogics/cal-lazure-function` 

## Step 3: Call server logic from web page 

1. Launch the [Power Pages design studio](/power-pages/getting-started/use-design-studio). 
1. In the **Pages** workspace, select **+ Page**. 
1. In the **Add a page** dialog, enter **Server logic** in the **Name** box, and then select the **Start from blank** layout.
1. Select **Add**. 
1. In the upper-right corner, select **Edit Code**.
1. Select **Open Visual Studio Code**. 
1. Copy the following code snippet, and then paste it between the \<div\>\</div\> tags of the page section.

```html
<style>
.sl-card { max-width:360px; padding:16px; border:1px solid #e1e1e1; border-radius:6px; background:#fff; font-family:Segoe UI, Arial, sans-serif; }
.sl-card h3 { margin:0 0 10px; font-size:16px; color:#323130; }
.sl-row { display:flex; gap:8px; }
.sl-row input { flex:1; padding:6px 8px; border:1px solid #c8c6c4; border-radius:4px; font-size:14px; }
.sl-row button { padding:6px 12px; border:0; border-radius:4px; background:#0078d4; color:#fff; font-size:14px; cursor:pointer; }
.sl-row button:hover { background:#106ebe; }
.sl-result { margin-top:10px; font-size:14px; color:#323130; }
.sl-error { color:#a80000; }
</style>

<div class="sl-card">
<h3>Test Server Logic</h3>
<div class="sl-row">
<input id="nameInput" placeholder="Name" />
<button id="callBtn">Call</button>
</div>
<div id="result" class="sl-result"></div>
</div>

<script>
document.getElementById('callBtn').onclick = async () => {
const name = document.getElementById('nameInput').value || 'World';
const result = document.getElementById('result');
result.textContent = 'Loading...';

try {
const res = await fetch(`/_api/serverlogics/call-azure-function?name=${encodeURIComponent(name)}`);
const data = await res.json();
result.textContent = data?.data || 'No response';
} catch (e) {
result.textContent = 'Request failed';
result.className = 'sl-result sl-error';
}
};
</script>
``` 

To test the server logic functionality: 

1. Select **Preview** and then choose **Desktop**. 
1. Sign in to your site with the user account that has been assigned the **Server logic User** role you created earlier. 
1. Go to the **Server logic** webpage created earlier. 
1. Enter a name, and then verify the response.
