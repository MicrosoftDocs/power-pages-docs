---
title: "How to: Integrate Power Automate cloud flow with a Power Pages site"
description: Learn how to add and configure a Power Automate cloud flow to retrieve the weather in Power Pages.
author: nageshbhat-msft

ms.topic: how-to
ms.custom: 
ms.date: 8/22/2024
ms.subservice: 
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - nageshbhat-msft
    - nickdoelman

---

# How to: Integrate Power Automate cloud flow with a Power Pages site

This article explains how to create Power Pages and use Power Automate cloud flow to invoke an MSN weather app, which displays the current weather details on the page.

## Prerequisite

To complete these steps, you need a Power Automate and Power Pages environment. If you don't have a license, you can sign up for [Power Pages](../getting-started/trial-signup.md) and [Power Automate](/power-automate/sign-up-sign-in) trials.

## Step 1: Create cloud flow

Create a flow using the Power Pages trigger and use the **MSN weather** action to fetch weather data.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site + **Edit**

1. Navigate to the **Set up workspace**, then select **Cloud flows** under App integrations.

1. Select **+ Create new flow**

1. Search for **Power Pages**.

    - Select **When Power Pages calls a flow** trigger.

    :::image type="content" source="media/cloud-flow/power-automate-power-pages.png" alt-text="Selecting Power Pages options in Power Automate.":::

1. Select **+ Add an input**.

1. Choose **Text**.

1. Add a name as **Location**.

1. Select **+ New step**.

1. Search for **MSN Weather**.

1. Select the **Get current weather** action.

1. Focus cursor on **Location** input text Select **Location** parameter under **When Power Pages calls a flow** from dynamic content.

    :::image type="content" source="media/cloud-flow/build-cloud-flow.png" alt-text="Build cloud flow.":::

    > [!NOTE]
    > You can either keep the Imperial units or change to metric.

1. Select **+ New step**.

1. Search for **Power Pages**.

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
    1. Location
    1. Visibility Distance
    1. Latitude
    1. Longitude
    1. Temperature Units
    1. Pressure Units
    1. Speed Units
    1. Distance Units
    1. Conditions

1. Select **Save**

1. Name the flow **Get current weather**.

## Step 2: Add flow to site

After saving the flow, you need to add it to the site and assign a proper web role.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Create a site with one of the [starter layouts](../getting-started/create-manage.md).

1. Choose the site and select **Edit**.

1. Navigate to the **Set up** workspace.
1. Under **App integrations**, select **Cloud flows**.

1. Select **+ Add cloud flow**.

1. Search for **Get current weather flow**.

1. Select **+ Add roles** under Roles.

1. Select **Anonymous Users** role.

1. Select **Add**.

1. Copy the URL.

    :::image type="content" source="media/cloud-flow/add-to-website.png" alt-text="Add cloud flow to website.":::

    > [!NOTE]
    > This is the unique URL used to connect to the associated cloud flow. You'll use this URL later to call the current weather flow.

## Step 3: Create a page to display MSN weather data

After creating the flow and attaching it to the Power Pages site, you can now call it from a control event using JavaScript.

1. Select **Pages** workspace.

1. Select **+ Page**.

1. Name the Page "*Today's weather report*".

1. Select **Edit code** to open Visual Studio Code.

1. Paste this code:

    ```javascript
        <style>
            div.weatherdetail {
                border: 1px solid #F3F2F1;
                border-radius: 12px;
                box-shadow: 0px 1.2px 3.6px rgba(0, 0, 0, 0.1), 0px 6.4px 14.4px rgba(0, 0, 0, 0.13);
                padding: 24px;
            }
            .weather label {
                font-family: 'Nunito';
                font-style: normal;
                font-weight: 600;
                font-size: 18px;
                color: #323130;
            }
            .weather button {
                font-family: 'Segoe UI';
                padding: 8px 16px;
                font-size: 16px;
                background-color: #6219D9;
                color: white;
                border: none;
                border-radius: 4px;
                cursor: pointer;
                outline: none;
            } 
            div.weather {
                display: flex;
                flex-direction: column;
                align-items: flex-start;
                padding: 100px;
                gap: 36px;
                width: 840px;
            }
            span.temperature {
                font-family: Segoe UI;
                font-size: 96px;
                font-style: normal;
                font-weight: 600;
                color: #6219d9;
            }
            span.weatherinfov1 {
                font-family: Segoe UI;
                font-size: 28px;
                font-style: normal;
                font-weight: 400;
                color: #201f1e;
            }
            span.weatherinfov2 {
                font-family: Segoe UI;
                font-size: 24px;
                font-style: normal;
                font-weight: 600;
                color: #a19f9d;
            }
        </style>
        
        <div class="row sectionBlockLayout text-left" style="display: flex; flex-wrap: wrap; margin: 0px; min-height: auto; padding: 8px;">
            <div class="container" style="display: flex; flex-wrap: wrap;">
                <div class="col-md-12 columnBlockLayout weather" style="flex-grow: 1; display: flex; flex-direction: column; min-width: 310px; word-break: break-word; padding: 0 180px; margin: 60px 0px;">
                    <h1>What's the weather?</h1>
                    <form id="cityForm">
                        <label for="locationInput">Enter a location to find out</label>
                        <br>
                        <input type="text" style="width: 840px; border: 1px solid #D2D0CE;" id="locationInput" required />
                        <p>
                        <p>
                            <button type="submit">Submit</button>
                        </p>
                    </form>
                    <div id="weatherdetail" class="weatherdetail" style="display: none;width: 840px">
                        <div>
                            <div>
                                <span class="temperature" id="temperature"> </span>
                                <span class="weatherinfov1" id="temperature_units"></span>
                            </div>
                            <div>
                                <span class="weatherinfov1" style="font-size: 36px;" id="location"> </span>
                                <br>
                                <span class="weatherinfov1" style="font-size: 24px;" id="cordinates"></span>
                                <p>
                            </div>
                        </div>
                        <div style="display: flex;">
                            <div style="flex: 1;">
                                <span class="weatherinfov2">Wind: </span>
                                <span class="weatherinfov1" id="windspeed"></span>
                                <span class="weatherinfov1" id="speed_units"> </span>
                            </div>
                            <div style="flex: 1;">
                                <span class="weatherinfov2">Visibility: </span>
                                <span class="weatherinfov1" id="visibility"></span>
                                <span class="weatherinfov1" id="distance_units"></span>
                            </div>
                        </div>
                        <div style="display: flex;">
                            <div style="flex: 1;">
                                <span class="weatherinfov2">UV Index: </span>
                                <span class="weatherinfov1" id="uv"></span>
                            </div>
                            <div style="flex: 1;">
                                <span class="weatherinfov2">Conditions: </span>
                                <span class="weatherinfov1" id="condition"></span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <script>
            document.getElementById("cityForm").addEventListener("submit", function (event) {
                event.preventDefault(); // Prevent form submission
                var weatherDiv = document.getElementById("weatherdetail");
                weatherDiv.style.display = "none";
        
                var location = document.getElementById("locationInput").value;
        
                var _url = "<Cloud flow URL>";
                
              var data = {};
              data["Location"] = location;
        
                var payload = {};
                payload.eventData = JSON.stringify(data);
                shell
                    .ajaxSafePost({
                        type: "POST",
                        url: _url,
                        data: payload
                    })
                    .done(function (response) {
                        const result = JSON.parse(response);
                        document.getElementById("temperature").innerHTML = result["temperature"];
                        document.getElementById("windspeed").innerHTML = result["wind_speed"];
                        document.getElementById("visibility").innerHTML = result["visibility_distance"];
                        document.getElementById("uv").innerHTML = result["uv_index"];
                        document.getElementById("location").innerHTML = result["location"];
                        document.getElementById("condition").innerHTML = result["conditions"];
                        document.getElementById("temperature_units").innerHTML = result["temperature_units"];
                        document.getElementById("speed_units").innerHTML = result["speed_units"];
                        document.getElementById("distance_units").innerHTML = result["distance_units"];
                        document.getElementById("cordinates").innerHTML = parseFloat(result["latitude"]).toFixed(2) + ', ' + parseFloat(result["longitude"]).toFixed(2);
                        weatherDiv.style.display = "block";
                    })
                    .fail(function () {
                        alert("failed");
                    });
            });
        </script>
    ```

1. Replace the URL with the one you copied in the previous step.

1. Save the code by selecting **CTRL + S**.

1. Select **Sync** in design studio.

## Step 4: Test the flow integration

To test the flow integration functionality:

1. Select **Preview** to open the site.

1. Enter a postal code or city in **Location** text box.

1. Select the **Submit** button.

    :::image type="content" source="media/power-automate-how-to/weather-report.png" alt-text="A rendering of the flow integration displaying Today's weather report.":::
