---
title: "How to: Create an image library using cloud flow and Power Pages"
description: Learn how to create an image library in Power Pages.
author: nageshbhat-msft
ms.topic: how-to
ms.custom: 
ms.date: 10/04/2023
ms.subservice: 
ms.author: nabha
ms.reviewer: kkendrick
contributors:
    - nageshbhat-msft
    - ProfessorKendrick
---

# How to: Create an image library using cloud flow and Power Pages

This article provides a step-by-step guide on creating Power Pages and harnessing Power Automate cloud flows to set up an image library website. This website allows authenticated users to effectively manage and organize a gallery of images.

## Prerequisite

To complete this course, you need a Power Automate and Power Pages environment. If you don't have a license, you can sign up for [Power Pages](../getting-started/trial-signup.md) and [Power Automate](/power-automate/sign-up-sign-in) trials.

## Step 1: Create a cloud flow

### Image flow

In this step, you'll create a flow using the Power Pages trigger and use OneDrive to store the images.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site **+ Edit**.

1. Under App integrations, navigate to **Set up**, then **Cloud flows (preview)**.

1. Select **+ Add cloud flow**.

1. Select **+ Create new flow**.

1. Search **Power Pages** and select **When Power Pages calls flow** trigger.

1. Select **+ Add** **an input**. 

1. Choose **Text**.

1. Add name **Image Name**.

1. Select **+ Add** **an input**. 

1. Choose **File**. 

1. Add a name as **Image Content**.

1. Select **+New step**. 

1. Search for **OneDrive** and select **Create File** action.
1.  
1. In the **Create file** action, enter the following values:

    1. Folder Path **/** and select **User ID** from dynamic content.

    > [!NOTE]
    > Don't forget to prepend with '/'

    1. File Name Select **Image Name** from dynamic content.

    1. File Content Select **Image Content** from dynamic content.

1. Select **+New step**. 

1. Search for **OneDrive** and select the **Create share link** action.

1. In the **Create share link** action, enter these values:

    1. File Id from the Dynamic content

    1. Link type View from the Dynamic content

1. Select **+New step**. 

1. Search for **Power Pages** and select **Return value(s) to Power Pages** action.

1. In the **Return value(s) to Power Pages** action enter these values:

    1. Select **+Add an output**.

    1. Choose the type of output as **Text**.

    1. Enter Name as **Image Path**.

    1. Image Path Web URL from the Dynamic content.
    
1. Provide flow name as **Upload image flow**.

1. Select **Save**.

1. Select **+Add roles**.

1. Select **Authenticated Users**.

1. Select **+Add**.

### Get Image list flow

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site **+ Edit**.

1. Under App integrations, navigate to **Set up** then **Cloud flows (preview)**.

1. Select **+ Add cloud flow**.

1. Select **+ Create new flow**.

1. Search **Power Pages** and select **When Power Pages calls flow** trigger.

1. Select **+ New step**.

1. Search for **OneDrive List files in folder**.

1. Update **Folder** with **/ +** select User ID from dynamic content.

1. Select **+ New step**.

1. Search for **Variable** Select **Initialize variable** action.

1. Enter the following values:

    1. Name Image Array

    1. Type Array

1. Select **+ New step**.

1. Search for **Variable** Select **Initialize variable** action.

1. Enter the following values:

    1.  Name Image List

    2.  Type String

1. Select **+ New step**.

1. Search for **Control** Select **Apply to each** action.

1. Enter the following value:

    1. Select **value** from the Dynamic content.

1. Select **Add an action**.

1. Search for **OneDrive** and select **Create share link** action.

1. In the **Create share link** action enter the following values:

    1. File Id from the Dynamic content

    1. Link type View from the Dynamic content

1. Select **Add an action**.

1. Search for **Variable** Select **Append to array variable** action.

1. Enter the following values:

    1. Name Image Array

    1. Value <br />```{ "Id":&lt; Id from the dynamic content&gt;,
"URL":&lt;Web URL from the dynamic content&gt;
}```

1. Select on **+New step**.

1. Search for **Variable** Select **Set variable** action.

1. Enter the following values:

    1. Name Image List

    1. Value Image Array

1. Select on **+New step**.

1. Search for **Power Pages** and select **Return value(s) to Power Pages** action.

1. In the **Return value(s) to Power Pages** action enter the following values:

1. Select **+Add an output**.

1. Choose the type of output as **Text**.

    1. Enter Name as **Image List**.

    1. Image List **Image List** from the Dynamic content.

1. Provide flow name as **Get Image List flow**.

1. Select **Save**.

1. Final flow appears as below.

## Delete Image

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site **+ Edit**.

1. Navigate to **Set up** and **Cloud flows (preview)** under App integrations.

1. Select **+ Add cloud flow**.

1. Select on **+ Create new flow**.

1. Search **Power Pages** and select **When Power Pages calls flow** trigger.

1. Select **+ Add** **an input**.

1. Choose **Text**.

1. Add name **Id**.

1. Select **+ New step**.

1. Search for **OneDrive** Select **Delete file** trigger.

1. Update **File**, then select **Id** from Dynamic content.

1. Select **+ New step**.

1. Search for **Power Pages** and select the **Return value(s) to Power Pages** action.

1. In the Return value(s) to Power Pages action, enter these values:

    1. Select **+Add an output**.

    1. Choose the type of output as **Yes / No**.

    1. Enter Name as **Status**.

    1. Status True.

1. Provide flow name as **Delete image flow**.

1. Select **Save**.

1. Select **+Add roles**.

1. Select **Authenticated Users**.

1. Select **+Add**.

## Step 2: Create a page to Manage Image library

After creating the flow and providing access to authenticated web role, you can call it from a control event using JavaScript.

1. Navigate to the **Pages** workspace.

1. Select **+ Page**.

1. Provide the Page Name as "Travel*"*.

1. Select **Edit code** to open Visual Studio Code.

1. Paste the following code:

1. Replace URL with the one copied previously.

1. Save the code by selecting **CTRL + S**.

1. In design studio, elect **Sync**.

## Step 3: Test the flow integration

To test the flow integration functionality:

1. Select the **Preview** to open the site.

1. Select the **Upload** button.

1. Choose an Image.

1. Select **Open**.
