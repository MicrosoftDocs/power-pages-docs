---
title: How to use the Web API to upload files to Azure Blob Storage
description: This page walks you through example steps for using portal Web API requests to upload files to Azure Blog Storage.
author: ankitavish
ms.topic: how-to
ms.custom: 
ms.date: 09/23/2024
ms.subservice: 
ms.author: avishwakarma
ms.reviewer: dmartens
contributors:
  - ankitavish
  - DanaMartens
---

# Use Web API to upload files to Azure Blob Storage

This guide demonstrates how to implement the Azure File API. These steps empower your website's users or visitors to view, edit, create, and delete attachments stored in Azure.

> [!NOTE]
> * Azure File size of up to 10 GB is supported.
> * You can change the column names or use a different table while following the steps in this example.
> * These APIs only work for records already created. Attachments uploaded using these APIs will be linked to that record.
> * These APIs will perform multiple updates on the note (Annotation) entity as files are uploaded in chunks.

## Prerequisites

This walk-through depends on a custom table named File Test. You can create a custom table with the same name or choose to use another table. Learn more about how to create a custom table in [Create and edit tables using Power Apps](/power-apps/maker/data-platform/create-edit-entities-portal).

## Step 1: Create site settings

Before you can use the portals Azure File API, you have to enable the required [site settings](configure-site-settings.md) with the [Portal Management app](portal-management-app.md). The site settings depend on the table that you want to use when interacting with the Azure File API.

1. Open the [Portal Management app](portal-management-app.md).

1. On the left pane of the Portal Management app, select **Site Settings**.

1. **Select New**.

1. For the **Name**, enter **Site/FileManagement/EnableWebAPI**.

1. In the **Website** list, select your website record.

1. For the **Value**, enter **true**.

1. Select **Save & Close**.

1. Add the following [site settings](configure-site-settings.md):

    |Site setting name  |DefaultValue   |Description    |Mandatory   |
    |---------|---------|---------|---------|
    |Site/FileManagement/EnableWebAPI       |         |   Enables the file management Web API     |    Yes       |
    |Site/FileManagement/BlobStorageAccountName      |         |      Storage Account Name    |      Yes     |
    |Site/FileManagement/BlobStorageContainerName      |         |    Container Name      |      Yes   |
    |Site/FileManagement/SupportedFileType      |         |   Comma separated values of the file types. For example: .jpeg,.jpg        |     Yes      |
    |Site/FileManagement/SupportedMimeType     |         |      ; separated Mime types     |    Yes      |
    |Site/FileManagement/MaxFileSize      |     1048576 (1 GB)     |     Max file size in KB     |   No      |
    |Site/FileManagement/DownloadViaSASUri      |   True (enabled by default)       |   To decide whether to use SAS URI to download file      |    No     |
    |Site/FileManagement/DownloadSASUriExpiryTimeSpan      |    00:10:00 (10 minutes)      |     Max expiry time span for sas uri(needed if 7 is true)     |     No     |
    |Site/FileManagement/DownloadChunkSizeInKB      |    4096 (4 MB)      |    To decide chunk size to download(needed if 7 is false)      |     No     |

1. Add these extra site settings to enable Web API for annotations (notes):

    |Site setting name   |Value  |
    |---------|---------|
    |Webapi/annotation/enabled       |    true     |
    |Webapi/annotation/fields       |      *   |

## Step 2: Configure permissions

You have to configure permissions so that users are able to use the Azure File API feature. In this example, you need to set up or create a new web role that uses the API. Next, you add the table permissions for the File Test and Note tables and associate the table permissions to the web role. Finally, you assign the web role to users in order to allow them to use the API.

> [!NOTE]
> The API follows [table permissions ](../security/table-permissions.md) from the [web role ](../security/create-web-roles.md) context of the authenticated user or the anonymous web role. Consider if your users already have a web role that has access to the specific tables in your website needed by the API. You don't need to create additional web roles just to use the API.

### Create a web role

If you don't have a web role with permissions to the required table, use the following steps to create a web role and assign table permissions.

1. Open the [Portal Management app](portal-management-app.md).

1. In the left pane, within the **Security** section, select **Web Roles**.

1. Select **New**.

1. For the **Name**, enter **Azure File API User** or any name that best reflects the role of the user accessing this functionality.

1. In the **Website** list, select your website record.

1. Select **Save**.

### Create table permissions

1. Open [Power Pages design studio](../getting-started/use-design-studio.md).

1. Select the **Security** workspace.

1. Under the **Protect** section, select **Table permissions**.

1. Select **New permission**.

1. For the **Name**, enter **File Test Table Permission**.

1. In the **Table Name** list, select **File Test (cr463_filetest)**.

1. In the **Access Type** list, select **Global access**.

1. Select the **Read** and **Append to** privileges.

1. Select **+ Add roles** and select the web role you created earlier.

1. Select **Save**.

1. Follow similar steps to create one more permission for the Note (annotation) table with **Write**, **Read**, **Create**, **Append** privileges, and add the same web role.

### Add contacts to the web role

1. Open the [Portal Management app](portal-management-app.md).

1. In the left pane, within the **Security** section, select **Contacts**.

1. Select a contact you want to use in this example for the API.

> [!NOTE]
> This contact is the user account used in this example for testing the API. Be sure to select the correct contact in your portal.

1. Select **Related** > **Web Roles**. Verify you're using the Portal Contact form. If you use the Power Pages Management App, the Web Roles subgrid is located at the bottom of the General tab.

1. Select **Add Existing Web Role**.

1. Select the **Azure File API User** role you created earlier.

1. Select **Add**.

1. Select **Save & Close**.

### Add role based permissions for Microsoft Entra app

1. Sign into to [Azure](https://portal.azure.com/) where the storage account was created.

1. Go to the resource group, which contains the storage account.

1. Select **Access control (IAM)** > **Add** > **Add role assignment**.

1. Select the **Reader** role and then select **Next**.

1. Select **User, group, or service principal** and then select **+ Select members**.

1. In the right side panel, choose the portal Enterprise application by searching your site name and then select **Select**. The name of the application is in the following format:

    `Portals-<site name>`

1. Select **Review + assign** >  **Review + assign** .

1. Go to storage account and then select **Access Control (IAM)** > **Add** > **Add role assignment**.

1. Select the **Storage Blob Data Contributor** role and then select **Next**.

1. Select **User, group, or service principal** and then select **+ Select members**.

1. In the right side, select the portal Enterprise application by searching your site name and then select **Select**.  

1. Select **Review + assign** > **Review + assign**.

## Step 3: Create a webpage

Now that you enabled the Azure File API and configured user permissions, create a webpage with an entity list for the File Test table.

1. Open [Power Pages design studio](../getting-started/use-design-studio.md).

1. In the **Pages** workspace, select **+ Page**, and select **Other ways to add a page**.

1. In the Add a page dialog, for the **Page name**, enter **File Test Page** and then select **Start from blank**.

1. Select **Add**.

1. Select **List** and then add a new list or choose an existing list for the File Test table.

    Create a page for attachments with the following sample code to view, edit, create, and delete records.

1. Open [Power Pages design studio](../getting-started/use-design-studio.md).

1. In the **Pages** workspace, select **+ Page**, and select **Other ways to add a page**.

1. In the Add a page dialog, for the **Page name**, enter **Attachments** and select **Start from blank**.

1. Select **Add**.

1. Select the **Edit code** option in the upper right corner.

1. Select **Open Visual Studio Code**.

1. Copy the following sample code snippet and paste it in between the `<div></div>` tags of the page section.

    ```html
    <style>
    .containerforfile
    {
        display:flex;
        margin-bottom:30px; 
    }
    .btn-for-file
    {
        margin-right:10px;
    }
    .file-name
    {
        padding-top:6px;
    }
    .fileinput
    {
        margin-right:10px;
    }
    .container-progress
    {   
         width: 70%;
         max-width: 400px;  
         margin-top: 10px;   
         position: relative;
    } 
    .parent-progress
    {    
        width: 100%;    
        background-color: #2f5fef;    
        height: 30px;    
        margin-top: 25px;    
        margin-bottom: 20px;
    } 
    .child-progress
    {    
        width: 0%;    
        background-color: #53b453;    
        height: 100%;
    } 
    .prog 
    {    position: absolute;  
      display: block;   
       right: 0; 
    }
    
    #attachments{
        font-family: Arial, Helvetica, sans-serif;
        border-collapse: collapse;
        width: 100%;
      }
      #attachments td,
      #attachments th {
        border: 1px solid #ddd;
        padding: 8px;
      }
      #attachments tr:nth-child(even) {
        background-color: #f2f2f2;
      }
      #attachments tr:hover {
        background-color: #ddd;
      }
      #attachments th {
        padding-top: 12px;
        padding-bottom: 12px;
        text-align: left;
        background-color: #2f5fef;
        color: white;
      }
    </style>
    
    <script>
    function selectFile()
    {var child = document.getElementsByClassName("child-progress")[0];
                                    var progSpan = document.getElementsByClassName("prog")[0];
                                        child.style.width = 0 + "%";
                                    progSpan.innerHTML = 0 + "%";
        var elementToChooseFile = document.getElementById("fileinput");
        elementToChooseFile.click();
    }
    function chooseFile()
    {
        var elementToChooseFile = document.getElementById("fileinput");
        var filename =elementToChooseFile.files[0].name;
        var elementforfilename = document.getElementById("filename");
        elementforfilename.innerText = filename;
        uploadFileinChunks();
    }
    
    (function(webapi, $){
                    function safeAjax(ajaxOptions) {
                        var deferredAjax = $.Deferred();
    
                        shell.getTokenDeferred().done(function (token) {
                        // add headers for AJAX
                        if (!ajaxOptions.headers) {
                        $.extend(ajaxOptions, {
                            headers: {
                                "__RequestVerificationToken": token
                            }
                        }); 
                        } else {
                        ajaxOptions.headers["__RequestVerificationToken"] = token;
                    }
                    $.ajax(ajaxOptions)
                        .done(function(data, textStatus, jqXHR) {
                            validateLoginSession(data, textStatus, jqXHR, deferredAjax.resolve);
                        }).fail(deferredAjax.reject); //AJAX
                }).fail(function () {
                    deferredAjax.rejectWith(this, arguments); // on token failure pass the token AJAX and args
                });
    
                return deferredAjax.promise();  
            }
            webapi.safeAjax = safeAjax;
        })(window.webapi = window.webapi || {}, jQuery)
    
    function getFileName(fileName)
    {
        return fileName.replace(/\.azure\.txt$/, '');
    }
    function downloadFile()
    {
        var entityName = document.getElementById("entity_name").value;
        var entityId = document.getElementById("entity_id").value;
        var url = "/_api/file/download/" + entityName + "(" + entityId + ")/blob/$value";
        window.open(url, "_blank");
    }
    
    function uploadFileinChunks()
    {
        var filesizeelement = document.getElementById("filesize");
        var starttimelement = document.getElementById("starttime");
        starttimelement.innerText = new Date().toLocaleString();
        var endtimeelement = document.getElementById("endtime");
        var entityName = "cr463_filetest";
        var entityId = window.location.search.substring(4);
        var url = "/_api/file/InitializeUpload/" + entityName + "(" + entityId + ")/blob"
        var elementToChooseFile = document.getElementById("fileinput");
        var filename = "";
        if (elementToChooseFile.files.length > 0) {
            filename = elementToChooseFile.files[0].name;
        filesizeelement.innerText = elementToChooseFile.files[0].size / 1048576;
            const encodedFileName = encodeURIComponent(filename);
            filename = encodedFileName;
        }
        if (elementToChooseFile.files.length > 0 && elementToChooseFile.files[0].size > 0)
        {
                const chunkSize = 50*1024 *1024;
                let numberOfBlocks;
                let token;
                if (elementToChooseFile.files[0].size % chunkSize == 0)
                {
                    numberOfBlocks = elementToChooseFile.files[0].size / chunkSize;
                }
                else
                {
                    numberOfBlocks = parseInt(elementToChooseFile.files[0].size / chunkSize, 10) + 1;
                }
                webapi.safeAjax({
                    type: "POST",
                    url: url,//replace this with url 
                    headers: { "x-ms-file-name": elementToChooseFile.files[0].name, "x-ms-file-size": elementToChooseFile.files[0].size },
                    contentType: "application/octet-stream",
                    processData: false,
                    data: {},
                    success: function (response, status, xhr)
                    {
                        token = response;
                        uploadFileChunk(0);
                    },
                    error: function (XMLHttpRequest, textStatus, errorThrown)
                    {
                        alert(XMLHttpRequest.responseText);
                    }
                });
    
                function uploadFileChunk(blockno)
                {
                    var fileReader = new FileReader();
    
                    if (blockno < numberOfBlocks)
                    {
                        var end = (blockno * chunkSize + chunkSize) > elementToChooseFile.files[0].size ? blockno * chunkSize + elementToChooseFile.files[0].size % chunkSize : blockno * chunkSize + chunkSize;
                        var content = elementToChooseFile.files[0].slice(blockno * chunkSize, end);
                        fileReader.readAsArrayBuffer(content);
                    }
                    fileReader.onload = function ()
                    {
                        webapi.safeAjax({
                            type: "PUT",
                            url: "/_api/file/UploadBlock/blob?offset=" + (blockno * chunkSize) + "&fileSize=" + elementToChooseFile.files[0].size + "&chunkSize=" + chunkSize + "&token=" + token,
                            headers: { "x-ms-file-name": elementToChooseFile.files[0].name },
                            contentType: "application/octet-stream",
                            processData: false,
                            data: content,
                            success: function (res) {
                                var child = document.getElementsByClassName("child-progress")[0];
                                    var progSpan = document.getElementsByClassName("prog")[0];
                                    var percentComplete = ((parseFloat(end) / parseFloat(elementToChooseFile.files[0].size)) * 100).toFixed(2);
    
                                    child.style.width = percentComplete + "%";
                                    progSpan.innerHTML = percentComplete + "%";
                                    if (percentComplete == 100) {
                                        var table = document.getElementById('attachments');
                                        if(table.hidden)
                                        {
                                        var divForNoAttachment = document.getElementById("no-attachment-found");
                                        divForNoAttachment.hidden = true;
                                        table.hidden = false;
                                        }
                                        var row = document.createElement("tr"); 
                                        row.id = token;
                                        row.innerHTML=`<td><a target="_blank" href="/_api/file/download/annotation(` + token + `)/blob/$value" >` + elementToChooseFile.files[0].name + `</a></td>
                                                <td>`+  new Date().toLocaleString() + `</td>     
                                                <td><button class="btn btn-default" onClick="deleteFile('` + token + `');"><i class="glyphicon glyphicon-trash" aria-hidden="true"></i></button></td>`;
                                        table.firstElementChild.nextElementSibling.appendChild(row);
                                        endtimeelement.innerText = new Date().toLocaleString();
                                    }
                                uploadFileChunk(blockno + 1);
                            },
                            error: function (XMLHttpRequest, textStatus, errorThrown) {
                                alert(XMLHttpRequest.responseText);
                            }
                        });
                    }
                }
        }
        else
        {
        alert("no file chosen");
        }
    }
    
    function loadAllAttachments()
    {
        var fetchXmlQuery = `<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="false">
      <entity name="annotation">
        <attribute name="filename" />
        <attribute name="annotationid" />  
        <attribute name="createdon"/>
        <attribute name="objectid" />
        <attribute name="objecttypecode" />
        <filter type="and">
        <condition attribute="filename" operator="like" value="%.azure.txt" />
        </filter>
        <link-entity name="cr463_filetest" from="cr463_filetestid" to="objectid" link-type="inner" alias="ad">
        <filter type="and">
        <condition attribute="cr463_filetestid" operator="eq" value="{` + window.location.search.substring(4) +`}"/>
    </filter>
    </link-entity>
      </entity>
    </fetch>`;
    
    var req = new XMLHttpRequest();
    
    req.open("GET", "/_api/annotations?fetchXml=" +  
        encodeURIComponent(fetchXmlQuery), true);
    
    req.setRequestHeader("Accept", "application/json");
    
    req.setRequestHeader("Content-Type", "application/json; charset=utf-8");
    
    req.onreadystatechange = function ()
    {
        if (this.readyState === 4)
        {
            this.onreadystatechange = null;
            if (this.status === 200)
            {
                var returned = JSON.parse(this.responseText);
                var results = returned.value;
                var loading = document.getElementById('loading');
                if (results.length == 0)
                {
                    var divForNoAttachment = document.getElementById("no-attachment-found");
                        divForNoAttachment.hidden = false;
                }
                else
                {
                for (var i = 0; i < results.length; i++)
                {
                    var table = document.getElementById('attachments');
                    if(table.hidden)
                    {
                        var divForNoAttachment = document.getElementById("no-attachment-found");
                        divForNoAttachment.hidden = true;
                        table.hidden = false;
                    }
                    var row = document.createElement("tr"); 
    
                    var fileName = results[i]["filename"];
                    fileName = fileName.replace(".azure.txt", "");
                    var createdOn = results[i]["createdon"];
                    var annotationid = results[i]["annotationid"];
                    row.id = annotationid;
                    row.innerHTML=`<td><a target="_blank" href="/_api/file/download/annotation(` + annotationid + `)/blob/$value" >` + fileName + `</a></td>
                    <td>`+  createdOn + `</td>     
                    <td><button class="btn btn-default" onClick="deleteFile('` + annotationid + `');"><i class="glyphicon glyphicon-trash" aria-hidden="true"></i></button></td>`;
                    table.firstElementChild.nextElementSibling.appendChild(row);
                }
                }
                loading.hidden= true;
            }
            else
            {
                alert(this.status);
            }
        }
    };
    req.send();
    }
    
    document.addEventListener("DOMContentLoaded", function(){
        loadAllAttachments();
    });
    function deleteFile(entityId)
    {
        var entityName = "annotation";
        var url = "/_api/file/delete/" + entityName + "(" + entityId + ")/blob/$value";
        webapi.safeAjax({
            url: url,
            type: "DELETE",
            success: function(){
    
                var row = document.getElementById(entityId);     
                row.parentNode.removeChild(row);
                var table = document.getElementById('attachments');
    
                if(table.hidden == false && table.tBodies[0].children.length == 0)
                { 
                var divForNoAttachment = document.getElementById("no-attachment-found");
                    divForNoAttachment.hidden = false;
                    table.hidden = true;
                }
            },
            error: function (XMLHttpRequest, textStatus, errorThrown)
            {
                alert(XMLHttpRequest.responseText); 
            }
        });
    }
    </script> 
    <div style="margin-left:40px;"> 
    <div class="containerforfile" style="display: flex;"> 
      <input type="file" multiple="true" id="fileinput" onchange="chooseFile()" style="display: none;"> 
      <button type="button" id="button-to-choosefile" onclick="selectFile()" class="btn btn-default btn-for-file">Choose File</button> 
      <div id="filename" class="file-name">No File Selected</div> 
    </div> 
    <br> 
    <div> 
    <label for="filesize" id="file_size_label" class="field-label">FileSize(In MB): </label><div class="filesize" id="filesize"></div> 
    <label for="starttime" id="start_time_label" class="field-label">StartTime:</label><div class="starttime" id="starttime"></div> 
    <label for="endtime" id="end_time_label" class="field-label">EndTime:</label><div class="endtime" id="endtime"></div> 
    </div> 
     <div class="container-progress"> 
         <div class="parent-progress" style="width: 100%;background-color: #c1c1c1;    height: 30px;     margin-top: 25px;    margin-bottom: 20px;">         
            <div class="child-progress" style="width: 0%;    background-color: #53b453;    height: 100%;"></div>    
          </div>            
         <span class="prog">0%</span> 
    </div> 
    <br> 
    <br> 
    <h1>Attachments:</h1> 
    <div id="loading"> Loading Attachments...</div> 
     <div id="no-attachment-found" hidden>No Attachment Found!!</div> 
     <table id="attachments" hidden> 
      <thead> 
        <tr> 
          <th>File</th> 
          <th>Created On</th>       
          <th>Actions</th> 
        </tr> 
      </thead> 
    <tbody> 
    </tbody> 
    </table> 
    </div> 
    ```

1. Select **CTRL**+**S** to save the code.

1. Go back to the **File Test Page**, select the list, and then select **Edit list**.
1. Go to **Actions** and then enable **Edit record**.
1. For the **Target Type**, select **Webpage**.
1. For the **Webpage**, select **Attachments**.
1. For the **Display label**, enter **Upload Attachments**.
1. Select **Done**.
1. In the upper-right corner of design studio, select **Sync** to update the site with the code edits.

## Step 4: Use the API to upload, download, and delete attachments

To test the Web API functionality:

1. Select **Preview**, and then select **Desktop**.

1. Sign in to your site with the user account that is assigned the **Azure File API User** role you created earlier.

1. Go to the **File Test Page** webpage created earlier.

1. From the right side, select **Upload Attachments**.

1. Choose a file and try uploading it.

1. Try downloading and deleting an existing file.

Now that you created a webpage with a sample to upload, download, and delete attachments, you can customize the forms and layout.

## Error codes and messages

The following table includes the different error codes and messages you might encounter when you use the Web API to upload files to Azure:

|Description  |Http Status  |Error Code  |Error Message  |
|---------|---------|---------|---------|
|No file is attached to upload     |   400      |     FU00001    |   File content isn't specified      |
|Entity ID or name provided in params isn't correct     |    404     |      FU00002   |     Record isn't found    |
|User doesn't have permission     |   403      |      FU00003   |    You don't have permissions to perform this operation     |
|Given file extension isn't configured     |    400     |     FU00004    |    File extension isn't supported.     |
|File mime type isn't supported     |     400    |     FU00005    |       File mimetype isn't supported  |
|File size is greater than configured     |     400    |   FU00006      |    File size is greater than {0}MB     |
|Azure configurations are incorrect     |   400      |    FU00007     |    Azure configurations are incorrect     |
|File name not provided     |     400    |   FU00008      |     Header x-ms-file-name is missing in the request    |
|API not enabled     |   501      |   FU00009      |     Azure webapi isn't enabled for use    |
|Not a valid Azure  file for update/uploadblock/delete/download     |       400  |      FU00010  |    Requested file isn't available for {0}     |
|IP  restriction is enabled in Azure on storage account     |     403    |      FU00011   |   IP restriction is enabled      |
|File doesn't  exist in Azure to download     |  400       |     FU00012    |      File doesn't exist   |
|Chunk size is greater than 100 mb     |     400    |    FU00013     |      Chunk size is greater than 100mb   |
|File size not given     |     400    |     FU00014    |    File size not provided     |
|Supported file types aren't set     |    400     |     FU00015    |     File extension is not supported    |
|Supported mime types aren't set     |   400      |     FU00016    |     File mimetype is not supported    |
|More than 128-mb file without chunking     |    400     |    FU00017     |    File size is more than 128mb     |
|Permission not provided to Microsoft Entra app     |     403    |     FU00018    |    Microsoft Entra application doesn't have permissions to perform this operation    |
|Certificate doesn’t exist to create connection with Azure     |     400    |      FU00019   |    Certificate doesn't  exist     |
|When tenant ID or client ID or thumbprint not set in app setting     |   500      |      FU00020   |    Internal server error     |
|File mime type/file extension isn't supported     |  400       |     FU00021    |    File mime type or extension is not supported     |
|Account name or container name doesn’t exist or isn't provided     |    400     |     FU00022    |    Azure configurations are incorrect     |

### Related information

* [Enable Azure storage](enable-azure-storage.md)
* [Web API overview](web-api-overview.md)
* [Write, update, and delete operations using the Web API](write-update-delete-operations.md)
