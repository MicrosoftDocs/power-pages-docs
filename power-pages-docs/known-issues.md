---
title: Known issues for Power Pages release
description: A list of known issues in Power Pages.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 09/23/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---
# Known issues

## Power Pages trial

- If your administrator disabled the self-service sign-up, you won't be able to sign up for a trial of Power Pages. 

- If your administrator disables portal creation for non-administrator–type users in your company, you won't be able to create a portal. You'll be redirected to the Power Pages home page in the default environment. You'll have to reach out to your administrator to provide you with an environment that has enough privileges for you to edit an existing site in the environment. 

- If your administrator disables the creation of a trial environment for non-administrator–type users in your company, you won't be able to create an environment. However, you can still create a portal inside an existing environment in the tenant, where you have necessary minimum privileges. 

- When you create a site for the first time in a new environment, you won't be able to rename the environment; however, the ability to rename the environment when it's created will be available in a future update. 

- If you don't see your site created when you sign up for a Power Pages trial, the site creation may have failed due to your company's tenant being in a different region than your chosen environment. You can attempt to create another site by selecting the **Create a Site** button on the Power Pages home page.

## Pages workspace

- Buttons added in portals built with the starter template can't be resized.

- You can't add a deleted header logo or text in the new design studio.  If you need to delete these items, you'll need to do so using Power Apps portals Studio. Use the toggle in the command bar to return to Power Apps portals Studio, and use the code editor to add the text or logo.

- The code editor doesn't support editing header or footer code.

## Style workspace

- Power Pages doesn't support Google Fonts due to privacy concerns.

- The section padding/margin settings feature in the Style workspace won't work for portals built on starter templates.

## Adjusting the background color for your Power Pages site

This known issue applies only to sites created using Power Pages prior to September 23, 2022.

Power Pages themes have been updated to meet the highest visual accessibility standards.  To ensure that your existing Power Pages sites created prior to September 23, 2022 adhere to these standards, you'll need to update your theme settings by recompiling the site.

### How to recompile your Power Pages site

Makers can update and recompile their Power Pages site and adjust the background color using one of several methods.

#### Add a new color to the theme's palette

To adjust the background color, makers can add a new color to the theme's palette using the Color Palette in the Style workspace.

:::image type="content" source="media/known-issues/styling-more-colors.png" alt-text="Add a new color to the theme's palette using the Color Palette in the Style workspace.":::

#### Edit a background on a section of the page

To adjust the background color, makers can select the desired color while editing the background on a section in the Pages workspace.

:::image type="content" source="media/known-issues/styling-fonts-title.png" alt-text="Select the desired color while editing the background on a section in the Pages workspace.":::

#### Modify the theme

Makers can adjust the background color by modifying the theme in the Style workspace using the following steps:

1. From the Style workspace, select a different theme.

2. Choose your original theme.

3. Select **Save**.

### Modify a theme setting

Makers can adjust the background color in the Style workspace by modifying a theme setting (like the Background color). To do this, choose the original value and select **Save**.





