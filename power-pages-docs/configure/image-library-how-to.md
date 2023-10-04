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
------

# How to: Create an image library using cloud flow and Power Pages

This article provides a step-by-step guide on creating Power Pages and harnessing Power Automate cloud flows to set up an image library website. This website allows authenticated users to effectively manage and organize a gallery of images.

## Prerequisite

To complete this course, you need a Power Automate and Power Pages environment. If you don't have a license, you can sign up for [Power Pages](https://learn.microsoft.com/en-us/power-pages/getting-started/trial-signup) and [Power Automate](https://learn.microsoft.com/en-us/power-automate/sign-up-sign-in) trial

## Step 1: Create cloud flow

 Image flow

Create a flow using the Power Pages trigger and use OneDrive to store the images.

1.  Sign into [Power Pages](https://make.preview.powerpages.microsoft.com/)

2.  Select site **+ Edit**

3.  Navigate to **Set up** à **Cloud flows (preview)** under App integrations

4.  Select **+ Add cloud flow**

5.  Click on **+ Create new flow**

6.  Search **Power Pages** and select **When Power Pages calls flow** trigger

9.  Click on **+ Add** **an input** 

10. Choose **Text**

11. Add name **Image Name**

12. Click on **+ Add** **an input** 

13. Choose **File** 

14. Add a name as **Image Content**

15. Click on **+New step** 

16. Search for **OneDrive** à select **Create File** action 

17. In the **Create file** action enter below values

    1.  Folder Path **/** and select **User ID** from dynamic content

Do not forget to prepend with '/'

2.  File Name Select **Image Name** from dynamic content

3.  File Content Select **Image Content** from dynamic content

18. Click on **+New step** 

19. Search for **OneDrive** à select **Create share link** action 

20. In the **Create share link** action enter below values

    1.  File Id from the Dynamic content

    2.  Link type View from the Dynamic content

21. Click on **+New step** 

22. Search for **Power Pages** à select **Return value(s) to Power Pages** action 

23. In the **Return value(s) to Power Pages** action enter below values

    1.  Click **+Add an output**

    2.  Choose the type of output as **Text**

    3.  Enter Name as **Image Path**

    4.  Image Path Web URL from the Dynamic content 
    
1. Provide flow name as **Upload image flow**

25. Click **Save**

26. Click **+Add roles**

27. Select **Authenticated Users**

28. Click **+Add**

### Get Image list flow

1.  Sign into [Power Pages](https://make.preview.powerpages.microsoft.com/)

2.  Select site **+ Edit**

3.  Navigate to **Set up** à **Cloud flows (preview)** under App integrations

4.  Select **+ Add cloud flow**

5.  Click on **+ Create new flow**

6.  Search **Power Pages** and select **When Power Pages calls flow** trigger

7.  Click **+ New step**

8.  Search for **OneDrive List files in folder**

9.  Update **Folder** with **/ +** select User ID from dynamic content

10. Click **+ New step**

11. Search for **Variable** Select **Initialize variable** action

12. Enter the value as below

    1.  Name Image Array

    2.  Type Array

13. Click **+ New step**

14. Search for **Variable** Select **Initialize variable** action

15. Enter the value as below

    1.  Name Image List

    2.  Type String

16. Click **+ New step**

17. Search for **Control** Select **Apply to each** action

18. Enter the value as below

    1.  Select **value** from the Dynamic content

19. Click **Add an action**

20. Search for **OneDrive** à select **Create share link** action 

21. In the **Create share link** action enter below values

    1.  File Id from the Dynamic content

    2.  Link type View from the Dynamic content

22. Click **Add an action**

23. Search for **Variable** Select **Append to array variable** action

24. Enter the value as below

    1.  Name Image Array

    2.  Value ```{ "Id":&lt; Id from the dynamic content&gt;,
"URL":&lt;Web URL from the dynamic content&gt;
}```

25. Click on **+New step**

26. Search for **Variable** Select **Set variable** action

27. Enter the value as below

    1.  Name Image List

    2.  Value Image Array

1. Click on **+New step** 

1. Search for **Power Pages** à select **Return value(s) to Power Pages** action 

1. In the **Return value(s) to Power Pages** action enter below values

1. Click **+Add an output**

1. Choose the type of output as **Text**

    1. Enter Name as **Image List**

    1. Image List **Image List** from the Dynamic content

1. Provide flow name as **Get Image List flow**

1. Click **Save**

1. Final flow appears as below

## Delete Image

1. Sign into [Power Pages](https://make.preview.powerpages.microsoft.com/)

1. Select site **+ Edit**

1. Navigate to **Set up** à **Cloud flows (preview)** under App integrations

1. Select **+ Add cloud flow**

1. Click on **+ Create new flow**

1. Search **Power Pages** and select **When Power Pages calls flow** trigger

1. Click on **+ Add** **an input** 

1. Choose **Text**

1. Add name **Id**

1. Click **+ New step**

1. Search for **OneDrive** Select **Delete file** trigger

1. Update **File** Select **Id** from Dynamic content

1. Click **+ New step**

1. Search for **Power Pages** à select **Return value(s) to Power Pages** action 

1. In the **Return value(s) to Power Pages** action enter below values

    1. Click **+Add an output**

    1. Choose the type of output as **Yes / No**

    1. Enter Name as **Status**

    1. Status True

1. Provide flow name as **Delete image flow**

1. Click **Save**

1. Click **+Add roles**

1. Select **Authenticated Users**

1. Click **+Add**

## Step 2: Create a page to Manage Image library

After creating the flow and providing access to authenticated web role, you can now call it from a control event using JavaScript.

1. Click on **Pages** workspace

1. Click on **+ Page**

1. Provide the Page Name as "Travel*"*

1. Click on **Edit code** to open visual studio code

1. Paste below code

1. Replace URL with the one copied above

1. Save the code by selecting **CTRL + S**

1. Click on **Sync** on design studio

## Step 3: Test the flow integration

To test the flow integration functionality

1. Click on **Preview** to open the site

1. Click on **Upload** button

1. Choose an Image

1. Click **Open**
