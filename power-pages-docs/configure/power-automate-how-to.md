---
title: "How to: Integrate Power Automate cloud flow with a Power Pages site (preview)"
description: Learn how to add and configure a Power Automate cloud flow to retrieve the weather in Power Pages.
author: nageshbhat-msft

ms.topic: how-to
ms.custom: 
ms.date: 05/23/2023
ms.subservice: 
ms.author: nabha
ms.reviewer: ndoelman
contributors:
    - nageshbhat-msft
    - nickdoelman
    - ProfessorKendrick

---

# How to: Integrate Power Automate cloud flow with a Power Pages site (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

This article explains how to create Power Pages and use Power Automate cloud flow to invoke an MSN weather app, which displays the current weather details on the page.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisite

To complete these steps, you need a Power Automate and Power Pages environment. If you don't have a license, you can sign up for [Power Pages](../getting-started/trial-signup.md) and [Power Automate](/power-automate/sign-up-sign-in) trials.

## Step 1: Create cloud flow

Create a flow using the Power Pages trigger and use the **MSN weather** action to fetch weather data.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. On the left pane, select **Solutions**.

1. Either [create a new solution](/power-apps/maker/data-platform/create-solution) or select an existing solution.

1. Select **+New** **Automation** **Cloud flow** **Instant**.

1. Select **Skip**.

1. Search for **Power Pages** Select **When Power Pages calls a flow** trigger.

    :::image type="content" source="media/cloud-flow/power-automate-power-pages.png" alt-text="Selecting Power Pages options in Power Automate.":::

1. Select **+ Add an input**.

1. Choose **Text**.

1. Add a name as **Location**.

1. Select **+New step**.

1. Search for **MSN Weather**.

1. Select the **Get current weather** action.

1. Focus cursor on **Location** input text Select **Location** parameter under **When Power Pages calls a flow** from dynamic content.

    :::image type="content" source="media/cloud-flow/build-cloud-flow.png" alt-text="Build cloud flow.":::

You can either keep the Imperial units or change to metric.

1. Select **+ New step**.

1. Search for **Power Pages**. 
1. 
1. Select **Return value(s) to Power Pages** action.

1. Select **+ Add and output**.

1. Select **Text**.

1. Enter **Pressure** as the title.

1. Under **Get current weather**, choose dynamic content **Pressure**.

1. Repeat to create the following output steps using **text** type:

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

1. Select **Save**

1. Name the flow **Get current weather**.

## Step 2: Add flow to site

After saving the flow, you need to add it to the site and assign a proper web role.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Create a site with one of the [starter layouts](../getting-started/create-manage.md).

1. Choose the site and select **Edit**.

1. Navigate to the **Set up** workspace.
1. Under **App integrations**, select **Cloud flows (preview)**.

1. Select **+ Add cloud flow**.

1. Search for **Get current weather flow**.

1. Select **+ Add roles** under Roles.

1. Select **Anonymous Users** role.

1. Select **Add**.

1. Copy the URL.

    :::image type="content" source="media/cloud-flow/add-to-website.png" alt-text="Add cloud flow to website.":::

    >[!NOTE] 
    > This is the unique URL used to connect to the associated cloud flow. You'll use this URL later to call the current weather flow.

## Step 3: Create a page to display MSN weather data

After creating the flow and attaching it to the Power Pages site, you can now call it from a control event using JavaScript.

1. Select **Pages** workspace.

1. Select **+ Page**.

1. Name the Page "*Today's weather report*".

1. Select **Edit code** to open Visual Studio Code.

1. Paste this code:

    ```javascript
    //code to be added
    alert("hello world");

    ```

1. Replace the URL with the one you copied in the previous step.

1. Save the code by selecting **CTRL + S**.

1. Select **Sync** on design studio.

## Step 4: Test the flow integration

To test the flow integration functionality:

1. Select **Preview** to open the site.

1. Enter a postal code or city in **Location** text box.

1. Select the **Submit** button.
