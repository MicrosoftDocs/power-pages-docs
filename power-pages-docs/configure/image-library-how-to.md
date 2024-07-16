---
title: "How to: Create an image library using cloud flow and Power Pages"
description: Learn how to create an image library in Power Pages.
author: nageshbhat-msft
ms.topic: how-to
ms.custom: 
ms.date: 16/07/2024
ms.subservice: 
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - nageshbhat-msft
    - ProfessorKendrick
---

# How to: Create an image library using cloud flow and Power Pages

This article provides a step-by-step guide on creating Power Pages and harnessing Power Automate cloud flows to set up an image library website. This website allows authenticated users to effectively manage and organize a gallery of images.<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW1eDxT]

## Prerequisite

To complete this course, you need a Power Automate and Power Pages environment. If you don't have a license, you can sign up for [Power Pages](../getting-started/trial-signup.md) and [Power Automate](/power-automate/sign-up-sign-in) trials.

## Step 1: Create a cloud flow

### Update image flow

In this step, you create a flow using the Power Pages trigger and use OneDrive to store the images.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site **+ Edit**.

1. Under App integrations, navigate to **Set up**, then **Cloud flows**.

1. Select **+ Create new flow**.

1. Search **Power Pages** and select **When Power Pages calls flow** trigger.

1. Select **+ Add an input**. 

    1. Choose **Text**.

    1. Add name **Image Name**.

    1. Select **+ Add an input**. 

    1. Choose **File**. 

    1. Add name **Image Content**.

1. Select **+ New step**. 

1. Search for **OneDrive** and select **Create File** action.
 
1. In the **Create file** action, enter the following values:

    1. Folder Path **/** and select **User ID** from dynamic content.

    > [!NOTE]
    > Don't forget to prepend with '/'

    1. For file Name, select **Image Name** from dynamic content.

    1. For file Content, select **Image Content** from dynamic content.

1. Select **+ New step**. 

1. Search for **OneDrive** and select the **Create share link** action.

1. In the **Create share link** action, enter these values:

    1. File ID: From the Dynamic content

    1. Link type: View from the Dynamic content

1. Select **+ New step**. 

1. Search for **Power Pages** and select **Return value(s) to Power Pages** action.

1. In the Return value(s) to Power Pages action, enter these values:

    1. Select **+ Add an output**.

    1. Choose the type of output **Text**.

    1. Name: **Image Value**.

    1. Image Value: ```{ "Id":"< Id from the dynamic content>", "URL":"<Web URL from the dynamic content>"}``` 
    
    1. Flow name: **Upload image flow**.

1. Select **Save**.

1. Select **+ Add roles**.

1. Select **Authenticated Users**.

1. Select **+ Add**.

1. Copy the flow URL for later use.

### Get Image list flow

Once you create your Image flow, follow the steps in this section to view the flow.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site **+ Edit**.

1. Under App integrations, navigate to **Set up** then **Cloud flows**.

1. Select **+ Add cloud flow**.

1. Select **+ Create new flow**.

1. Search **Power Pages** and select **When Power Pages calls flow** trigger.

1. Select **+ New step**.

1. Search for OneDrive > Find files in folder by path 
    Enter these values:
    - Search query: *
    - Folder path: / + select User ID from dynamic content
    - Files search mode: Pattern

1. Select **+ New step**.

1. Search for **Variable** and select the **Initialize variable** action.

1. Enter these values:

    1. Name: Image Array

    1. Type: Array

1. Select **+ New step**.

1. Search for **Variable** Select **Initialize variable** action.

1. Enter these values:

    1. Name: Image List

    1. Type: String

1. Select **+ New step**.

1. Search for **Control** Select **Apply to each** action.

1. Enter these values:

    1. Select **body** from the Dynamic content.

1. Select **Add an action**.

1. Search for **OneDrive** and select **Create share link** action.

1. In the **Create share link** action enter these values:

    1. File ID: from the Dynamic content

    1. Link type: View from the Dynamic content

1. Select **Add an action**.

1. Search for **Variable** Select **Append to array variable** action.

1. Enter the following values:

    1. Name: Image Array

    1. Value: <br />
        ```{ "Id":"<Id from the dynamic content>", "URL":"<Web URL from the dynamic content>" }```

1. Select **+ New step**.

1. Search for **Variable** Select **Set variable** action.

1. Enter these values:

    1. Name: Image List

    1. Value: Image Array

1. Select **+ New step**.

1. Search for **Power Pages** and select **Return value(s) to Power Pages** action.

1. In the Return value(s) to Power Pages action, enter the following values:

1. Select **+ Add an output**.

1. Choose the type of output as **Text** and enter these values:
    1. Name: **Image List**.
    1. Image List: Choose **Image List** from the Dynamic content.

1. Provide flow name as **Get Image List flow**.

1. Select **Save**.

1. Copy the flow URL for later use.

The final flow appears.

### Delete Image

Once you build your Image List flow, follow the steps outlined in this section create a trigger for deleting images.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site **+ Edit**.

1. Navigate to **Set up** and **Cloud flows** under App integrations.

1. Select **+ Add cloud flow**.

1. Select **+ Create new flow**.

1. Search **Power Pages** and select the **When Power Pages calls flow** trigger.

1. Select **+ Add an input**.

1. Choose **Text**.

1. Add the name **Id**.

1. Select **+ New step**.

1. Search for **OneDrive** Select **Delete file** trigger.

1. Update **File**, then select **Id** from Dynamic content.

1. Select **+ New step**.

1. Search for **Power Pages** and select the **Return value(s) to Power Pages** action, then **+ Add an output**.

1. In the Return value(s) to Power Pages action, enter these values:

    1. Type of output: **Yes / No**

    1. Name: **Status**

    1. Status: **True**

    1. Flow name: **Delete image flow**

1. Select **Save**.

1. Select **+ Add roles**.

1. Select **Authenticated Users**.

1. Select the **Add** button.

1. Copy the flow URL for later use.

## Step 2: Create a page to Manage Image library

After creating the flow and providing access to authenticated web role, you can call it from a control event using JavaScript.

1. Navigate to the **Pages** workspace.

1. Select **+ Page**.

1. Provide the Page Name as *Travel*.

1. Select **...** next to the *Travel* page.

1. Choose **Page settings**, then **Permissions**. 

    1. Select **I want to choose who can see this page**.

    1. Select the **Authenticated Users** role from drop-down.

1. Choose **Ok**. 

1. Select **Edit code** to open Visual Studio Code.

1. Paste the following code:

    ```css
    <link rel="stylesheet" href="https://static2.sharepointonline.com/files/fabric/office-ui-fabric-core/11.0.0/css/fabric.min.css" /> 
    <style> div.image-gallery {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            padding: 100px;
            gap: 36px;
            width: 840px;
    }
        div.image-gallery-header {
            font-family: Helvetica;
            font-size: 32px;
            font-weight: 700;
            line-height: 32px;
            letter-spacing: 0px;
            color: #252729;
    }
        div.subHeader {
            font-family: Segoe UI;
            font-size: 14px;
            font-weight: 600;
            line-height: 20px;
            letter-spacing: 0px;
            color: #323130;
    }
        div.subHeaderLabel {
            font-family: Segoe UI;
            font-size: 12px;
            font-weight: 400;
            line-height: 16px;
            letter-spacing: 0px;
            color: #605E5C;
    }
        .image-gallery button {
            margin-top: 5px;
            font-family: 'Segoe UI';
            padding: 8px 16px;
            font-size: 16px;
            background-color: white;
            color: #8A8886;
            border: 1px solid #8A8886;
            border-radius: 4px;
            cursor: pointer;
            outline: none;
    }
        div.image-gallery-list {
            margin-top: 0px;
    }
        div.date-section {
            font-family: Segoe UI Variable;
            font-size: 14px;
            font-weight: 600;
            line-height: 20px;
            letter-spacing: 0em;
            color: #000000E4;
    }
        div.image-list {
            width: 1024px;
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            margin-bottom: 10px;
            flex-wrap:wrap;
    }
        div.image-1 {
            margin-right: 10px;
            display: flex;
            margin-top: 10px;
            margin-bottom: 20px;
    }
        .image-list img {
            width: 268px;
            height: 289px;
            border-radius: 4px;
    }
        button.image-delete {
            background-color: #FFFFFF;
            width: 32px;
            height: 32px;
            position: relative;
            right: 40px;
            padding-top: 4px;
    }
        .image-delete i {
            display: flex;
            justify-content: center;
    }
        div.status-message {
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            text-align: center;
    }
    </style> 

    <div class="row sectionBlockLayout text-left" style="display: flex; flex-wrap: wrap; margin: 0px; min-height: auto; padding: 8px;"> 
        <div class="container" style="display: flex; flex-wrap: wrap;"> 
            <div class="col-md-12 columnBlockLayout image-gallery" style="flex-grow: 1; display: flex; flex-direction: column; min-width: 310px; word-break: break-word; padding: 0 120px; margin: 60px 0px;"> 
                <div class="image-gallery-header"> 
                    Your travel photos 
                </div> 
                <div> 
                    <div class="subHeader"> Upload file 
                    </div> 
                    <div class="subHeaderLabel"> 
                        You can upload JPG, GIF or PNG file 
                    </div> 
                    <form id="uploadForm"> 
                        <p> 
                            <input type="file" id="fileInput" style="display: none;" accept="image/x-png,image/gif,image/jpeg" /> 
                            <button type="submit"> 
                                <i class="ms-Icon ms-Icon--Upload" aria-hidden="true"></i> Upload 
                            </button> 
                        </p> 
                    </form> 
                </div> 
                <div class="status-message" id="statusMessage"style="display: none;"> 
                    Uploading your image... Please wait while we process your file. 
                </div> 
                <div class="image-gallery-list"> 
                    <div id ="container" class="image-list">
                    </div> 
                </div> 
            </div> 
        </div> 
    </div> 
    <script> 
        var _getImageListFlowURL = "<Get Image List Flow URL>";
        var _uploadImageFlowURL = "<Upload Image Flow URL>";
        var _deleteImageFlowURL = "<Delete Image Flow URL>";
        function createImageElement(element){
            var div1 = document.createElement('div');
            div1.className = "image-1";
             var img = document.createElement('img');
            img.src = element["URL"];
            div1.appendChild(img);
            var button1 = document.createElement('Button');
            button1.type ="submit";
            button1.className = "image-delete";
            button1.data = element["Id"];
            var i = document.createElement('i');
            i.className = "ms-Icon ms-Icon--Delete"; 
            button1.appendChild(i);
            div1.appendChild(button1);
            button1.addEventListener('click', function(){
                this.parentElement.remove();
                var data = {
            }
            ;
                data["Id"] = element["Id"];
                var payload = {
            }
            ;
                payload.eventData = JSON.stringify(data);
                shell .ajaxSafePost({
                    type: "POST", url: _deleteImageFlowURL, data: JSON.stringify(payload) 
            }
            ) .done(function (response) {
                    const result = JSON.parse(response);
            }
            ) .fail(function () {
                    console.log('Error');
            }
            );
        }
        );
            return div1;
    }
        document.addEventListener("DOMContentLoaded", () => {
            var data = {
        }
        ;
            var payload = {
        }
        ;
            payload.eventData = JSON.stringify(data);
            shell .ajaxSafePost({
                type: "POST", url: _getImageListFlowURL, data: JSON.stringify(payload)
        }
        ) .done(function (response) {
                const result = JSON.parse(response);
                var imageList =JSON.parse(result['image_list']);
                var imageContainer = document.getElementById("container");
                for (let index = 0;
                index < imageList.length;
                index++) {
                    imageContainer.appendChild(createImageElement(imageList[index]));
            }
        }
        ) .fail(function () {
                console.log('Error');
        }
        );
    }
    );
        document.getElementById("uploadForm").addEventListener("submit", function (event) {
            event.preventDefault();
            var imageInput = document.getElementById("fileInput");
            imageInput.onchange = _ => {
                let selectedFile = imageInput.files[0];
                UploadImageToBlob(selectedFile);
        }
            function UploadImageToBlob(inputFile) {
                var reader = new FileReader();
                reader.readAsDataURL(inputFile);
                reader.onload = function () {
                    document.getElementById("statusMessage").style.display="block";
                     var file = {
                    }
                    ;
                     file.name = inputFile.name;
                     file.contentBytes = reader.result.split(',')[1];
                     var data = {
                    }
                    ;
                     data["Image Name"] = inputFile.name;
                     data["Image Content"] = file;
                     var payload = {
                    }
                    ;
                     payload.eventData = JSON.stringify(data);
                     shell .ajaxSafePost({
                         type: "POST", url: _uploadImageFlowURL, data: JSON.stringify(payload) 
                }
                ) .done(function (response) {
                     const result = JSON.parse(response);
                     var imageList = JSON.parse(result['image_value']);
                     var imageContainer = document.getElementById("container");
                     imageContainer.prepend(createImageElement(imageList));
                     document.getElementById("statusMessage").style.display="none";
                }
                ) .fail(function () {
                     document.getElementById("statusMessage").style.display="none";
                     console.log('Error');
                }
                );
            }
             reader.onerror = function (error) {
                 console.log('Error: ', error);
            }
            ;
        }
         imageInput.click();
    }
    );
    </script> 
    ```

1. Replace URL with the one copied previously.

1. Save the code by selecting **CTRL + S**.

1. In design studio, select **Sync**.

## Step 3: Test the flow integration

To test the flow integration functionality:

1. Select the **Preview** to open the site.

1. Sign in to the site.

1. Select the **Upload** button.

1. Choose an image.

1. Select **Open**.

