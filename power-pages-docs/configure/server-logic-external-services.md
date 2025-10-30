---
title: Interact with external services using server logic
description: Learn how to interact with external services using server logic. Follow this step-by-step guide to create, read, update, and delete records using Power Pages.
#customer intent: As a developer, I want to create server logic in Power Pages so that I can interact with external services using CRUD operations.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 10/30/2025
ms.topic: concept-article
---

# How to: interact with external services using server logic 

In this guide, you'll set up a webpage that will use the server logic to read, write, update, and delete records from the external services httpclient server object. 

> [!NOTE]
> This example uses [https://services.odata.org/TripPinRESTierService](https://services.odata.org/TripPinRESTierService) , but you could use other publicly available free testing tools. 

## Step 1: Create a server logic 

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/). 
1. Select site **+ Edit**. 
1. Navigate to the **Set up** workspace, then select **Server logics (preview)** 
1. Select **+New server logic** 
1. Enter name for the server logic. This name is used in API as resource identifier while constructing the server logic API.  
    Example:  
    Name - services.odata.org 
    Display Name – Performing CRUD operations using OData service 
1. Click **+Add roles** to assign appropriate web role. 
1. Select 3 dots (**…**) next to name and select **Edit code.** 
1. Select **Open Visual Studio Code** to author the custom logic. 
    You will find pre-defined methods and scripts in the file 
1. Define server logic method to read, edit, create, delete operations using external service.  
Add below constant before the get() method 
`const baseUrl  = "https://services.odata.org/TripPinRESTierService";`

### Read: Add below script inside get method 

```javascript


if (!Server.Context.QueryParameters["username"]) {
    const response = await Server.Connector.HttpClient.GetAsync(
        `${baseUrl}/People?$select=UserName,FirstName,LastName,MiddleName,Age`, 
        {'content-type':'application/json'});
    return response;
}
else {            
    const id = Server.Context.QueryParameters["username"]; // Context reference
    const response = await Server.Connector.HttpClient.GetAsync(
        `${baseUrl}(${id})/People?$select=UserName,FirstName,LastName,MiddleName,Age`, 
        {'content-type':'application/json'});
    return response;
}
 ```

### Create: Add below script in post method

```javascript
const data = JSON.parse(Server.Context.Body);           
const url = `${baseUrl}/${data.serviceSession}/People`;
const { serviceSession, ...body } = data; 
const response = await Server.Connector.HttpClient.PostAsync(
       url, 
       JSON.stringify(body),
      {'content-type':'application/json'});
return response;
```

### Update : Add below script in put 

```javascript
const data = JSON.parse(Server.Context.Body);        
const url = `${baseUrl}/${data.serviceSession}/People('${data.UserName}')`;
const { UserName, ...body1 } = data;
const { serviceSession, ...body } = body1;
const response = await Server.Connector.HttpClient.PatchAsync(
   url, 
   JSON.stringify(body),
  {'content-type':'application/json'});
return response;
```

### Delete: Add inside del method 

```javascript
const username = Server.Context.QueryParameters["username"];
const serviceSession = Server.Context.QueryParameters["serviceSession"];
const url = `${baseUrl}/${serviceSession}/People('${username}')`;
const response = await Server.Connector.HttpClient.DeleteAsync(
        url, 
    {'content-type':'application/json'});
return response;
```

1. Save the file 

Here is the complete code:

```javascript
const baseUrl = "https://services.odata.org/TripPinRESTierService"; 

async function get() { 
    try { 
        Server.Logger.Log("GET called"); // Logger reference 
        if (!Server.Context.QueryParameters["username"]) { 
            const response = await Server.Connector.HttpClient.GetAsync( 
                `${baseUrl}/People?$select=UserName,FirstName,LastName,MiddleName,Age`, 
                {'content-type':'application/json'}); 
            return response; 
        } 
        else {             
            const id = Server.Context.QueryParameters["username"]; // Context reference 
            const response = await Server.Connector.HttpClient.GetAsync( 
                `${baseUrl}(${id})/People?$select=UserName,FirstName,LastName,MiddleName,Age`, 
                {'content-type':'application/json'}); 
            return response; 
        }         
    } catch (err) { 
        Server.Logger.Error("GET failed: " + err.message); 
        return JSON.stringify({ status: "error", method: "GET", message: err.message }); 
    } 
} 

async function post() { 
    try { 
        Server.Logger.Log("POST called"); 
        const data = JSON.parse(Server.Context.Body);            
        const url = `${baseUrl}/${data.serviceSession}/People`; 
        const { serviceSession, ...body } = data;  
        const response = await Server.Connector.HttpClient.PostAsync( 
            url,  
            JSON.stringify(body), 
            {'content-type':'application/json'}); 
        return response; 
    } catch (err) { 
        Server.Logger.Error("POST failed: " + err.message); 
        return JSON.stringify({ status: "error", method: "POST", message: err.message }); 
    } 
}  

async function put() { 
    try { 
        Server.Logger.Log("PUT called"); 
        const data = JSON.parse(Server.Context.Body);         
        const url = `${baseUrl}/${data.serviceSession}/People('${data.UserName}')`; 
        const { UserName, ...body1 } = data; 
        const { serviceSession, ...body } = body1; 
        const response = await Server.Connector.HttpClient.PatchAsync( 
            url,  
            JSON.stringify(body), 
            {'content-type':'application/json'}); 
        return response; 
    } catch (err) { 
        Server.Logger.Error("PUT failed: " + err.message); 
        return JSON.stringify({ status: "error", method: "PUT", message: err.message }); 
    } 
}    

async function del() { 
    try { 
        // "delete" keyword should not be used in script file. 
        Server.Logger.Log("DEL called"); 
        const username = Server.Context.QueryParameters["username"]; 
        const serviceSession = Server.Context.QueryParameters["serviceSession"]; 
        const url = `${baseUrl}/${serviceSession}/People('${username}')`; 
        const response = await Server.Connector.HttpClient.DeleteAsync( 
            url,  
            {'content-type':'application/json'}); 
        return response; 
    } catch (err) { 
        Server.Logger.Error("Deletion failed: " + err.message); 
        return JSON.stringify({ status: "error", method: "DEL", message: err.message }); 
    } 
} 
```

## Step 2: Create Webpage 

1. Launch the [Power Pages design studio](/power-pages/getting-started/use-design-studio). 
1. In the **Pages** workspace, select **+ Page**. 
1. In the **Add a page** dialog, enter details.
1. In the **Name** box, enter **Server logic** and select **Start from blank** layout. 
1. Select **Add**. 
1. Select the **Edit Code** option in the upper right hand corner. 
1. Select **Open Visual Studio Code**. 
1. Copy the following sample code snippet and paste it in between the \<div\>\</div\> tags of the page section. 

```html
<!-- Sample code for Web API demonstration -->
<style>
#processingMsg {
    padding: 6px 12px; background: #eee; border-radius: 4px;
    position: fixed; top: 10px; left: 50%; transform: translateX(-50%);
    display: none; z-index: 9999; text-align: center; font-weight: bold;
}
table { border-collapse: collapse; width: 100%; margin-top: 10px; font-family: Arial, sans-serif; }
th, td { border: 1px solid #ccc; padding: 6px; text-align: left; }
button { cursor: pointer; border: 1px solid #aaa; padding: 4px 8px; border-radius: 4px; background: #fff; font-size: 14px; margin-right: 2px; }
button.add { color: green; }
button.save { color: green; }
button.cancel { color: orange; }
button.delete { color: red; }
input { width: 95%; box-sizing: border-box; }
td.actions { white-space: nowrap; }
td[data-attribute="UserName"] { background: #f9f9f9; cursor: default; }
</style>

<div id="processingMsg">Processing...</div>
<div id="dataTable"></div>

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script>
$(function() {

    // Safe WebAPI wrapper for Power Pages
    (function(webapi, $) {
        function safeAjax(opts) {
            var d = $.Deferred();
            shell.getTokenDeferred().done(function(token) {
                opts.headers = opts.headers || {};
                opts.headers["__RequestVerificationToken"] = token;
                $.ajax(opts)
                    .done((data, ts, jq) => validateLoginSession(data, ts, jq, d.resolve))
                    .fail(d.reject);
            }).fail(() => d.rejectWith(this, arguments));
            return d.promise();
        }
        webapi.safeAjax = safeAjax;
    })(window.webapi = window.webapi || {}, jQuery);

    // Notification overlay
    const notify = (() => {
        const $m = $('#processingMsg'); let s = 0, t;
        return {
            show: (msg='Processing...') => { $m.text(msg); if(!s) $m.show(); s++; },
            hide: () => { s = Math.max(0, s-1); if(!s) t=setTimeout(()=>$m.hide(),200); }
        };
    })();

    function ajaxCall(msg, opts) {
        notify.show(msg);
        return webapi.safeAjax(opts)
            .fail(r => alert(r.responseJSON?.error?.message || 'Server error'))
            .always(notify.hide);
    }

    // Table columns
    const cols = [
        { name: 'UserName', label: 'User Name', editable: false },
        { name: 'FirstName', label: 'First Name' },
        { name: 'LastName', label: 'Last Name' },
        { name: 'MiddleName', label: 'Middle Name' },
        { name: 'Age', label: 'Age' }
    ];

    let data = [];
    let serviceSession = '';
    function render() {
        const html = `<table>
            <thead>
                <tr>
                    ${cols.map(c => `<th>${c.label}</th>`).join('')}
                    <th>Actions <button class="add">➕</button></th>
                </tr>
            </thead>
            <tbody>
                ${data.map(r=>`<tr data-UserName="${r.UserName}">
                    ${cols.map(c=>`<td data-attribute="${c.name}" data-value="${r[c.name]||''}">
                        ${r[c.name]||''}
                    </td>`).join('')}
                    <td class="actions">
                        <button class="delete">🗑️</button>
                    </td>
                </tr>`).join('')}
            </tbody>
        </table>`;
        $('#dataTable').html(html);
    }

    // Double click row to edit except username
    $('#dataTable').on('dblclick','tr',function() {
        const $tr=$(this);
        if($tr.hasClass('editing')) return;
        $tr.addClass('editing');
        $tr.find('td[data-attribute]').each(function(){
            const $td=$(this);
            if($td.data('attribute')==='UserName') return; 
            const old=$td.text().trim();
            $td.html(`<input type="text" value="${old}" data-attr="${$td.data('attribute')}"/>`);
        });
        $tr.find('.actions').append('<button class="save">✅</button><button class="cancel">❌</button>');
    });

    $('#dataTable').on('click','.save',function(){
        const $tr=$(this).closest('tr');
        const username=$tr.data('username');
        const updates={};
       $tr.find('input').each(function () {
          const attr = $(this).data('attr');
          let value = $(this).val().trim();

          if (attr === 'Age') {
              value = Number(value);
              if (isNaN(value)) value = null; // safety fallback
          }

          updates[attr] = value;
      });

        ajaxCall('Updating...', {
            type:'PUT',
            url:`/_api/serverlogics/services.odata.org`,
            contentType:'application/json',
            data:JSON.stringify(Object.assign({ UserName: username, serviceSession: `${serviceSession}` }, updates)),
            success:()=>{ Object.assign(data.find(x=>x.UserName===username),updates); render(); }
        });
    });

    $('#dataTable').on('click','.cancel',()=>render());

    $('#dataTable').on('click','.delete',function(){
        const username=$(this).closest('tr').data('username');
        if(!confirm('Delete '+username+'?')) return;
        ajaxCall('Deleting...', {
            type:'DELETE',
            url:`/_api/serverlogics/services.odata.org?username=${username}&serviceSession=${serviceSession}`,
            success:()=>{ data=data.filter(x=>x.UserName!==username); render(); }
        });
    });

    $('#dataTable').on('click','.add',function(){
        const r={
            serviceSession:`${serviceSession}`,
            UserName:'user'+Math.floor(Math.random()*9000+1000),
            FirstName:'New',
            LastName:'Person',
            MiddleName:'',
            Age:25
        };
        ajaxCall('Adding...', {
            type:'POST',
            url:`/_api/serverlogics/services.odata.org`,
            contentType:'application/json',
            data:JSON.stringify(r),
            success:()=>{ data.unshift(r); render(); }
        });
    });

    // Initial load
    ajaxCall('Loading...', {
        type:'GET',
        url:`/_api/serverlogics/services.odata.org`,
        contentType:'application/json'
    }).done(resp=>{
        const parsed=JSON.parse(resp.data);
        const body=JSON.parse(parsed.Body);
        
        const ctx = body['@odata.context'];
        const match = ctx.match(/\\S\\[^)]*\\/);
        serviceSession = match ? match[0] : '';

        data=(body.value||[]).map(r=>({
            UserName:r.UserName,
            FirstName:r.FirstName,
            LastName:r.LastName,
            MiddleName:r.MiddleName,
            Age:r.Age
        }));
        render();
    });

});
</script>
```

## Step 3: Use the Server logic to read, view, edit, create, and delete

To test the server logic functionality:

1. Select **Preview**, and then choose **Desktop**.
1. Sign in to your site with the user account that's been assigned the **Server logic User** role you created earlier.
1. Go to the **Server logic** webpage created earlier.
1. Verify the operations.
