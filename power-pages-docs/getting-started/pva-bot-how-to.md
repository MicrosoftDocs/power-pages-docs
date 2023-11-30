---
title: "How to: replace default Power Pages AI chatbot with PVA bot"
---

This article offers a comprehensive, step-by-step guide for updating default Power Pages AI chatbot with PVA bot.

# Prerequisite

-   You must have a bot created in [Power Virtual Agent](https://learn.microsoft.com/en-in/power-virtual-agents/nlu-gpt-quickstart#create-a-boosted-bot).

-   [AI chatbot](https://learn.microsoft.com/en-us/power-pages/getting-started/enable-chatbot#add-a-chatbot) must be created and published in the site where you are updating the PVA bot.

# Copy the bot schema name

1.  Sign in to [Power Virtual Agents](https://web.powerva.microsoft.com/)

2.  Select the bot which needs to be updated

3.  Navigate to **Copilot details** under **Settings**

4.  Select **Advanced** tab

5.  Copy the **Schema name**

![A screenshot of a computer Description automatically generated](media/image1.gif)

# Verify Data model version

AI chatbot can be enabled for both Standard and Enhanced site data model. The steps to replace it vary based on the data model. Make sure you are following the right steps based on the data model.

1.  Go to the [Set up workspace](https://learn.microsoft.com/en-us/power-pages/configure/setup-workspace)

2.  Select **Site details**

3.  Verify the **Data Model** version

![A screenshot of a computer Description automatically generated](media/image2.gif)

Data Model can be either **Standard** or **Enhanced**.

# Updating bot in Standard data model site

1.  Go to the [Data workspace](https://learn.microsoft.com/en-us/power-pages/configure/setup-workspace)

2.  Search for **Bot consumer** table and select

3.  Locate the row with selected website name

4.  Replace Bot Schema Name column value with new bot schema name copied earlier

# Updating bot in Enhanced data model

1.  Go to the [Data workspace](https://learn.microsoft.com/en-us/power-pages/configure/setup-workspace)

2.  Search for **Site Component** table and select

3.  Find the **Component Type** column and click filter (![](media/image3.png)) icon next to it

4.  Filter records by **Bot Consumer** option

5.  Locate the row with selected website name in **Power Pages Site id** column

6.  Click on **Edit row using form** button

7.  Replace **botschemaname** json value with new bot schema name copied earlier

![A screenshot of a computer Description automatically generated](media/image4.gif)

8.  Click on **Save & Close** button
