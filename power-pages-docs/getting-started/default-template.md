---
title: Getting started with templates
description: Learn how to get started with templates.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 03/14/2022
ms.subservice: portals
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Getting started with templates

## Overview of the default template design

The default design template is a versatile template that provides basic building blocks for you to customize your portal any way you want. With a few clicks you can customize this template to your use case and business needs.

Follow the steps below to successfully create a site with default design template.

1. Select + Create a site from the Home page.

1. Choose the Default design template from the available options and choose Next.

1. Validate the default site name and web address created. Note: you can edit these as needed. Select Done. The Power Pages takes a few minutes to provision your portal.

## Default template core elements

The Default design template consists of basic components that are essential building blocks of a website design. 
These components include:

- Home page: serves as a landing page for users to learn more about the site. This pages uses some of the building block components like text, image, and buttons.

-  Subpages: allows users to navigate to different sections of the site.

- Contact us: consists of a form component and an iframe component that allows users to submit feedback via form and locate the physical location of the enterprise.

### Text component

Use the Text component within a section to add to your site. You will find several text components used in the default template some are headings while others are paragraphs. With in-context editing you can add/remove text components or edit their content as needed.

### Button component

Button component allows maker to define call to action when a button is clicked on the site. 

### Image component

Image is one of the components that you can add within a section. In default design template you will find several image components used to make the site more aesthetic and pleasing to users. These images are customizable within Maker Studio.

Changes are saved automatically.  You can view these changes at runtime by selecting Preview.

### Form component

The form component in this template allows users to provide feedback. Data collected in this form is stored in the Feedback table.

If you would like to change the table or form (simple contact us form) to something else, you can make changes here and save them.

### Iframe component

Iframe component allows you to embed webpage of another website. In this template, by default the ifram URL is set to Bing maps.

### Video component

A video component allows maker to embed video as a content on the site.

## Pages workspace for default template

The default design template comes with predefined pages for your site. Navigate to the **Pages** tab in the Toolbelt to locate Pages workspace.

There are two sections for page navigation.

- Main navigation: this section covers pages that are part of your main navigation on the site.

- Other pages: this section covers pages that you land on from any of the main navigation pages.

## Change page components

### Home page

This is the prebuilt home page of your site. With in-context editing, you can easily change the logo, header, background image, menu options and text content under various sections.

### Pages

Pages is another page on your site. You can leverage this page to drive users to the subpages. These pages comprise of basic components like text, button, and images. Use in-context editing to make changes you like as per your needs.

Select the &lt;...&gt; option to position these pages as needed on your site.

### Contact us

This page allows visitors to leave feedback. Some of the key components on this page are form and an iframe.

As you make changes in the Pages workspace, they get autosaved. To view the site as it would appear in production select the **Preview** option on the command bar. Select Desktop to view the site in browser or scan the bar code to view it on mobile.

## Data workspace for Default Template

The default design template comes with a rich set of sample tables and data that you can edit from within the maker studio. Select the **Data** workspace on the Toolbelt to look at the tables that are part of the solution.

This template uses the Feedback table to store any feedback that has been received by a user that visits the site. The feedback form is located under the **Contact us** page. From here, you can add new records or edit existing records in the Feedback table or create new tables (or views or forms) as per your business needs.

## Styling workspace for Default Template

To edit the styling of the default template, select the **Styling** icon on the Toolbelt. Here you can select any of the preset themes in the Themes workspace and see how it styles the canvas on the right. As you choose different themes you may notice the styling menu changes accordingly. You can make changes to the preset theme in the styling menu and save changes.

## Set up workspace for Default Template

Navigate to the **Set up** workspace on the Toolbelt to configure settings that will ensure your site is protected and secure. Here you can set up identity provider for sign-in/sign-up flow and set table permissions.

By default, local sign in and Azure Active directory identity providers are enabled. You can enable other identity providers like Facebook, LinkedIn by selectin Configure option. Click the + New provider to add a new identity provide if you like to configure a new one.

Here is a screenshot of the signIn page presented to all the visitors. Based on the authentication supported a user can sign in or register to gain access to the site.

The Set up workspace also includes table permissions. These allow a maker to define the access type, privileges and assign roles. By default, this template has table permissions set to Global access, create privilege and roles set to Anonymous users, authenticated users, and administrators. Meaning all these three roles can create a record in Feedback table which is performed upon Contact us form submission.

## More items

Under More items you can select Portal Management to navigate to the portal management app to configure advanced options or navigate to Flow to set up automated workflows. This default template does not include any prebuilt automated workflows.

