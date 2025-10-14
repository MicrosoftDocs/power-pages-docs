---
title: How to interact with Dataverse tables using server logic
description: Learn how to interact with Dataverse tables using server logic to read, write, update, and delete records. Follow this step-by-step guide to get started.
#customer intent: As a developer, I want to configure a webpage in Power Pages so that I can interact with Dataverse tables using server logic.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 09/30/2025
ms.topic: concept-article
---

# How to interact with Dataverse tables using Server logic 

In this guide, you'll set up a webpage and custom web template that will use the server logic to read, write, update, and delete records from the contact table.

## Step 1: Create a server logic

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).
1. Select site **+ Edit**.
1. Navigate to the **Set up** workspace, then select **Server logic (preview)**.
1. Select **+New server logic**.
1. Enter name for the server logic. This name is used in API as resource identifier while constructing the server logic API.
   > Example: dataverse-crud-operations
1. Select **+Add roles** to assign appropriate web role.
1. Select 3 dots (**…**) next to name and select **Edit code.**
1. Select **Open Visual Studio Code** to author the custom logic.
    You'll find pre-defined methods and scripts in the file.
1. Define server logic method to read, edit, create, delete the contact records.

   ### Read: Add below script inside get method

   ```javascript
   const entitySetName = Server.Context.QueryParameters["entitySetName"];
   if (!Server.Context.QueryParameters["id"]) {
       return Server.Connector.Dataverse.RetrieveMultipleRecords(entitySetName);
   } else {
       const id = Server.Context.QueryParameters["id"]; // Context reference
       return Server.Connector.Dataverse.RetrieveRecord(entitySetName, id);
   }
   ```

   ### Create: Add below script in post method

   ```javascript
   const data = Server.Context.Body;
   const entitySetName = Server.Context.QueryParameters["entitySetName"];
   return Server.Connector.Dataverse.CreateRecord(entitySetName, data);
   ```

   ### Update: Add below script in put method

   ```javascript
   const id = Server.Context.QueryParameters["id"];
   const data = Server.Context.Body;
   return Server.Connector.Dataverse.UpdateRecord("accounts", id, data);
   ```

   ### Delete: Add inside del method

   ```javascript
   const id = Server.Context.QueryParameters["id"];
   const entitySetName = Server.Context.QueryParameters["entitySetName"];
   Server.Logger.Log("Entity Set name:" + entitySetName);
   return Server.Connector.Dataverse.DeleteRecord(entitySetName, id);
   ```

10. Save the file.
11. Here's the complete server logic code that can be pasted

   ```javascript
   function get() {
    try {
        Server.Logger.Log("GET called"); // Logger reference
        const entitySetName = Server.Context.QueryParameters["entitySetName"];
        const additionParameters = Server.Context.QueryParameters['additionalParameters'];
        if (!Server.Context.QueryParameters["id"]) {
            const response = Server.Connector.Dataverse.RetrieveMultipleRecords(entitySetName,additionParameters);
            return response;
        }
        else{            
            const id = Server.Context.QueryParameters["id"]; // Context reference
            const response = Server.Connector.Dataverse.RetrieveRecord(entitySetName, id,additionParameters);
            return response;
        }        
    } catch (err) {
        Server.Logger.Error("GET failed: " + err.message);
        return JSON.stringify({ status: "error", method: "GET", message: err.message });
    }
    }
    function post() {
    try {
        Server.Logger.Log("POST called");
        const data = Server.Context.Body;
        const entitySetName = Server.Context.QueryParameters["entitySetName"];
         return Server.Connector.Dataverse.CreateRecord(entitySetName, data);
     } catch (err) {
        Server.Logger.Error("POST failed: " + err.message);
        return JSON.stringify({ status: "error", method: "POST", message: err.message });
    }
    } 
    function put() {
    try {
        Server.Logger.Log("PUT called");
        const id = Server.Context.QueryParameters["id"];
        const data = Server.Context.Body;
        const entitySetName = Server.Context.QueryParameters["entitySetName"];
        return Server.Connector.Dataverse.UpdateRecord(entitySetName, id, data);
     } catch (err) {
        Server.Logger.Error("PUT failed: " + err.message);
        return JSON.stringify({ status: "error", method: "PUT", message: err.message });
    }
    }   
    function del() {
    try {
        // "delete" keyword should not be used in script file.
        Server.Logger.Log("DEL called");
        const id = Server.Context.QueryParameters["id"];
          const entitySetName = Server.Context.QueryParameters["entitySetName"];
        return Server.Connector.Dataverse.DeleteRecord(entitySetName, id);
     } catch (err) {
        Server.Logger.Error("Deletion failed: " + err.message);
        return JSON.stringify({ status: "error", method: "DEL", message: err.message });
    }
    }
   ```
    

## Step 2: Create Webpage

1. Launch the [Power Pages design studio](/power-pages/getting-started/use-design-studio).
1. In the **Pages** workspace, select **+ Page**.
1. In the **Add a page** dialog, enter **Server logic** in the **Name** box and select **Start from blank** layout.
1. Select **Add**.
1. Select the **Edit Code** option in the upper right-hand corner.
1. Select **Open Visual Studio Code**.
1. Copy the following sample code snippet and paste it in between the `<div></div>` tags of the page section.

   ```html
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
   </style>

   <div id="processingMsg">Processing...</div>
   <div id="dataTable"></div>

   <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
   <script>
   $(function() {
       // --- safeAjax wrapper ---
       (function(webapi, $) {
           function safeAjax(ajaxOptions) {
               var dfd = $.Deferred();
               shell.getTokenDeferred().done(function(token) {
                   ajaxOptions.headers = ajaxOptions.headers || {};
                   ajaxOptions.headers["__RequestVerificationToken"] = token;
                   $.ajax(ajaxOptions)
                       .done((data, ts, jq) => validateLoginSession(data, ts, jq, dfd.resolve))
                       .fail(dfd.reject);
               }).fail(() => dfd.rejectWith(this, arguments));
               return dfd.promise();
           }
           webapi.safeAjax = safeAjax;
       })(window.webapi = window.webapi || {}, jQuery);

       // --- notification banner ---
       const notify = (function() {
           const $m = $('#processingMsg'); let s = 0, t;
           return {
               show: (msg = 'Processing...') => { $m.text(msg); if (!s) clearTimeout(t), $m.show(); s++; },
               hide: () => { s = Math.max(0, s - 1); if (!s) clearTimeout(t), t = setTimeout(() => $m.hide(), 300); }
           };
       })();

       function ajaxCall(msg, opts) {
           notify.show(msg);
           return webapi.safeAjax(opts)
               .fail(r => alert(r.responseJSON?.error?.message || 'Server logic not available'))
               .always(notify.hide);
       }

       // --- Table config ---
       const cols = [
           { name: 'firstname', label: 'First Name' },
           { name: 'lastname', label: 'Last Name' },
           { name: 'emailaddress1', label: 'Email' },
           { name: 'telephone1', label: 'Telephone' }
       ];
       let data = [];

       function render() {
           const html = `<table>
               <thead>
                   <tr>
                       ${cols.map(c => `<th>${c.label}</th>`).join('')}
                       <th>Actions <button class="add">➕</button></th>
                   </tr>
               </thead>
               <tbody>
                   ${data.map(r => `<tr data-id="${r.id}" data-name="${r.fullname}">
                       ${cols.map(c => `<td data-attribute="${c.name}" data-value="${r[c.name] || ''}">${r[c.name] || ''}</td>`).join('')}
                       <td class="actions">
                           <button class="delete">🗑️</button>
                       </td>
                   </tr>`).join('')}
               </tbody>
           </table>`;
           $('#dataTable').html(html);
       }

       function addRecord(r) { data.unshift(r); render(); }
       function removeRecord(id) { data = data.filter(r => r.id !== id); render(); }
       function updateRecord(id, attr, val) { const r = data.find(r => r.id === id); if (r) { r[attr] = val; render(); } }

       // --- Events ---
       $('#dataTable').on('dblclick', 'tr', function() {
           const $tr = $(this);
           if ($tr.hasClass('editing')) return; // prevent double edit
           $tr.addClass('editing');
           $tr.data('original', $tr.find('td[data-attribute]').map(function() { return $(this).text(); }).get());
           $tr.find('td[data-attribute]').each(function() {
               const $td = $(this);
               const oldVal = $td.text();
               $td.html(`<input type="text" value="${oldVal}" data-attr="${$td.data('attribute')}" />`);
           });
           const $actions = $tr.find('td.actions');
           $actions.append('<button class="save">✅</button><button class="cancel">❌</button>');
       });

       $('#dataTable').on('click', '.save', function() {
           const $tr = $(this).closest('tr');
           const id = $tr.data('id');
           const updates = {};
           $tr.find('input').each(function() {
               updates[$(this).data('attr')] = $(this).val();
           });
           ajaxCall('Updating...', {
               type: 'PUT',
               url: `/_api/serverlogics/dataverse-crud-operations?entitySetName=contacts&id=${id}`,
               contentType: 'application/json',
               data: JSON.stringify(updates),
               success: () => { Object.assign(data.find(r => r.id === id), updates); render(); }
           });
       });

       $('#dataTable').on('click', '.cancel', function() {
           const $tr = $(this).closest('tr');
           const original = $tr.data('original');
           $tr.find('td[data-attribute]').each(function(i) {
               $(this).text(original[i]);
           });
           $tr.removeClass('editing');
           $tr.find('button.save, button.cancel').remove();
       });

       $('#dataTable').on('click', '.delete', function() {
           const $tr = $(this).closest('tr');
           if (confirm('Delete "' + $tr.data('name') + '"?')) {
               ajaxCall('Deleting...', {
                   type: 'DELETE',
                   url: `/_api/serverlogics/dataverse-crud-operations?entitySetName=contacts&id=${$tr.data('id')}`,
                   contentType: 'application/json',
                   success: () => removeRecord($tr.data('id'))
               });
           }
       });

       $('#dataTable').on('click', '.add', function() {
           const r = { firstname: 'Willie', lastname: 'Huff' + Math.floor(Math.random() * 900 + 100), emailaddress1: 'Willie.Huff@contoso.com', telephone1: '555-123-4567' };
           ajaxCall('Adding...', {
               type: 'POST',
               url: '/_api/serverlogics/dataverse-crud-operations?entitySetName=contacts',
               contentType: 'application/json',
               data: JSON.stringify(r),
               success: (res, s, xhr) => { r.id = xhr.getResponseHeader('entityid'); r.fullname = r.firstname + ' ' + r.lastname; addRecord(r); }
           });
       });

       ajaxCall('Loading...', {
           type: 'GET',
           url: '/_api/serverlogics/dataverse-crud-operations?entitySetName=contacts&additionalParameters=$select=fullname,firstname,lastname,emailaddress1,telephone1',
           contentType: 'application/json'
       }).done(res => {
           try {
               const p = JSON.parse(res.data); const b = JSON.parse(p.Body);
               data = (b.value || []).map(r => ({ ...r, id: r.contactid, fullname: r.fullname }));
               render();
           } catch (e) { console.error(e); }
       });
   });
   </script>
   ```

## Step 3: Configure permissions

### Create a web role

If you currently don't have a web role with permissions to the table you're accessing through the Server logic or require different context of accessing the data, the following steps show you how to create a new web role and assign table permissions.

1. Start the [Portal Management app](/power-pages/configure/portal-management-app).
1. On the left pane, in the **Security** section, select **Web Roles**.
1. Select **New**.
1. In the **Name** box, enter **Server logic User** (or any name that best reflects the role of the user accessing this functionality).
1. In the **Website** list, select your website record.
1. Select **Save**.

### Create table permissions

1. Launch the [Power Pages design studio](/power-pages/getting-started/use-design-studio).
1. Select the **Security** workspace.
1. Under the **Protect** section, select **Table permissions**.
1. Select **New permission**.
1. In the **Name** box, enter **Contact Table Permission**.
1. In the **Table Name** list, select **Contact (contact)**.
1. In the **Access Type** list, select **Global**.
1. Select **Read**, **Write**, **Create**, and **Delete** privileges.
1. Select **+ Add roles** and select the **web role** you selected or created earlier.
1. Select **Save & Close**.

### Add contacts to the web role

1. Start the [Portal Management app](/power-pages/configure/portal-management-app).
1. On the left pane, in the **Security** section, select **Contacts**.
1. Select a contact that you want to use in this example for the Server logic.
   > [!NOTE]
   > This contact is the user account used in this example for testing the Server logic. Be sure to select the correct contact in your portal.
1. Select **Related** > **Web Roles**.
1. Select **Add Existing Web Role**.
1. Select the **Server logic User** role, created earlier.
1. Select **Add**.
1. Select **Save & Close**.

## Step 4: Use the Server logic to read, view, edit, create, and delete

To test the Web API functionality:

1. Select **Preview**, and then choose **Desktop**.
1. Sign in to your site with the user account that has been assigned the **Server logic User** role you created earlier.
1. Go to the **Server logic** webpage created earlier.


### Related information

[Server logic overview](server-logic-overview.md)  
[Author server logic](author-server-logic.md)  
[Server objects](server-objects.md)   


