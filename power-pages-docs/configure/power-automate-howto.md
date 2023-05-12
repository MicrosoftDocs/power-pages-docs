---
title: "How to: Integrate Power Automate cloud flow with Power Pages site"
description: Learn how to add and configure a Dataverse choices column on Power Pages lists, forms, and templates.
author: nageshbhat-msft

ms.topic: conceptual
ms.custom: 
ms.date: 05/12/2023
ms.subservice: 
ms.author: nabha
ms.reviewer: ndoelman
contributors:
    - nageshbhat-msft
    - nickdoelman

---

# How to: Integrate Power Automate cloud flow with Power Pages site

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

This article explains how to create Power Pages and use Power Automate cloud flow to invoke an MSN weather app, which displays the current weather details on the page.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisite

To complete this course, you need a Power Automate and Power Pages environment. If you don't have a license, you can sign up for [Power Pages](https://learn.microsoft.com/en-us/power-pages/getting-started/trial-signup) and [Power Automate](https://learn.microsoft.com/en-us/power-automate/sign-up-sign-in) trial

## Step 1: Create cloud flow

Create a flow using the Power Pages trigger and use the MSN weather action to fetch weather data.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/)

1. On the left pane, click on **Solutions**

1. Either [create a new solution](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-solution) or select an existing solution

![](media/image1.gif)

1.  Select **+New** **Automation** **Cloud flow** **Instant**

![](media/image2.gif)

1.  Click **Skip**

1.  Search for **Power Pages** Select **When Power Pages calls a flow** trigger

![](media/image3.gif)

1.  Click on **+ Add an input**

1.  Choose **Text**

1.  Add a name as **Location**

![](media/image4.gif)

1. Click on **+New step**

1. Search for **MSN Weather** select **Get current weather** action

![A screenshot of a computer Description automatically generated](media/image5.gif)

1. Focus cursor on **Location** input text Select **Location** parameter under **When Power Pages calls a flow** from dynamic content

![](media/image6.gif)

You can either keep the Imperial units or change to metric

1. Click on **+ New step**

1. Search for **Power Pages** Select **Return value(s) to Power Pages** action

1. Click on **+ Add and output**

1. Select **Text**

1. Enter title a **Pressure**

1. Choose dynamic content **Pressure** under **Get current weather**

1. Add below output variable with **text** type

    1. Humidity

    1. Temperature

    1. UV index

    1. Wind speed

    1. Dew point

    1. Visible distance

    1. Latitude

    1. Longitude

    1. Temperature Units

    1. Pressure Units

    1. Speed Units

    1. Distance Units

    1. Wind direction

![](media/image7.gif)

1. Click on **Save**

1. Name the flow as **Get current weather**

## Step 2: Add flow to site

After saving the flow, you need to add it to the site and assign a proper webrole.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/)

1. Create a site with [default template](https://learn.microsoft.com/en-us/power-pages/getting-started/create-manage)

1. Select the site click on **Edit**

1. Navigate to **Set up** **Cloud flows (preview)** under **App integrations**

![](media/image8.gif)

1. Select **+ Add cloud flow**

1. Search for **Get current weather flow**

1. Click **+ Add roles** under Roles

1. Select **Anonymous Users** role

![](media/image9.gif)

1. Click **Add**

1. Copy the URL

![](media/image10.gif)

This is the unique URL used to connect to the associated cloud flow. You will use this URL later to call the current weather flow.

# Step 3: Create a page to display MSN weather data

After creating the flow and attaching it to the Power Pages site, you can now call it from a control event using JavaScript.

1. Click on **Pages** workspace

![](media/image11.gif)

1. Click on **+ Page**

1. Provide the Page Name as "*Todays weather report"*

![](media/image12.png)

1. Click on **Edit code** to open visual studio code

![A screenshot of a computer Description automatically generated](media/image13.png)

1. Paste below code

|                         |
|-------------------------|
| Code will be added here |

1. Replace URL with the one copied above

1. Save the code by selecting **CTRL + S**

1. Click on **Sync** on design studio

# Step 4: Test the flow integration

To test the flow integration functionality

1.  Click on **Preview** to open the site

1.  Enter Postal code or City in **Location** text box

1.  Click **Submit** button
