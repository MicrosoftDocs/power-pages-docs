---
title: After School template
description: template
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 3/29/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# After School template

The After School Program template is designed to show you the capabilities of a registration portal application and we have picked chosen the example of registering for after school classes; however, this template may be useful for any industry or organization wishing to create a registration portal.

There are two key users that the template is designed for:

1.  The parent who is trying to register their kids for after school classes.

2.  The school representative is looking to maintain a list of courses, edit and add new ones to the catalog.

As a parent who is looking to register for classes, you can do the following seamlessly:

1.  Register for an after-school class from the list of available classes.

2.  Modify the schedule.

3.  Add and edit attendee information.

4.  Receive emails with information about the class which you can use to modify your registration.

As a representative of the school, you can do the following seamlessly:

1.  Maintain the course catalog.

2.  Add and modify existing classes.

End-to-end registration experience for the parent

![Overview of the end to end experience for a parent using the portal ](media/image1.png)

End-to-end experience of the school representative

![Graphical user interface  application  table Description automatically generated](media/image2.png)**  
**

# Core elements that are part of the After School Program Registration template 

After School Program Registration has many core elements and components which come together to solve the problem end to end. This template has the following components:

| **Component** | **Maker Studio** | **Runtime** |
|-------------------------|-------------------------|-------------------------|
| Basic forms | ![Page in maker studio with a form component ](media/image3.png)<br /></br><br /></br>![Page in maker studio with a form component ](media/image4.png) | ![The create a course form on a web page ](media/image5.png)</br>![Flyout form with a file upload control ](media/image6.png) |
| Lists | ![List control on a page in the maker studio ](media/image7.png) | ![List rendered on a portal page ](media/image8.png) |
| Core components | The Home page uses custom code. The code can be edited using VS Code or the Portal Management app.<br /></br><br /></br>![Registration page ](media/image9.png)</br>Attendee registration uses custom code which can be edited using VS Code or the Portal Management app.<br /></br>![My registration page in the maker studio ](media/image10.png) | ![After school registration home page ](media/image11.png)</br>![A webpage showing children selection ](media/image12.png) |


The **After School Program Registration** has a rich set of out of the box pages that are defined based on the user scenarios and user roles.

The web pages are designed to target two core user personas

1.  The parent who is trying to register for the course.

2.  The representative of the school managing the courses.

In the screenshot below you will see there are 2 sections for page navigation:

-   Main navigation: this section covers the pages you have as part of your main navigation experiences.

-   Other pages: this section houses the subpages that you land on from one of the pages in the main navigation.

![The maker studio displaying the list of pages that are a part of the After School template ](media/image13.png)

| **User persona**                | **Pages**                 | **Components** |
|---------------------------------|---------------------------|----------------|
| Parent registering for a course | Home                      |                |
|                                 | Unregister Attendee       |                |
|                                 | Add Attendee Profile      |                |
|                                 | Attendee Information      |                |
|                                 | Edit Attendee Information |                |
|                                 | My Registrations          |                |
|                                 | Registration Success      |                |
|                                 | View Course Details       |                |
| School Representative           | C1 Courses Home           |                |
|                                 | Edit Course               |                |
|                                 | C1 Delete Course          |                |
|                                 | Create Course             |                |
|                                 | Duplicate Course          |                |
| Misc                            | Page Not Found            |                |
|                                 | Access Denied             |                |

# Edit Page Components 

### Home 

With the in-context editor, you can easily change the logo and the header.

1.  Changing the logo, the name of the organization in the header.

Follow the prompts to change the image and text to reflect the logo and name of the organization.

![The maker studio showing the toolbar that appears when editing the header ](media/image14.png)

This page also has custom code, and has been styled to follow the best-in-class UX patterns. For custom code editing, launch the Portal Management app or VS Code loading the portal metadata using the PAC CLI tools.

1.  Hover over the component and you will see the label "Custom Component" over the components that have custom code associated with them.

![The maker studio highlighting that the particular component is using custom code ](media/image15.png)

2.  Selecting the component will ask you to open the Portal Management app.

![Maker studio showing the Open portal management app from the menu when selecting a custom component ](media/image16.png)

3.  Select the local content and head to choose the advanced tab. You will see the custom JS JavaScript that's driving the page and you can make edits directly to the code.

![Graphical user interface displaying the General menu options in the Maker studio ](media/image17.png)

![Graphical user interface displaying the Advanced menu options in the Maker studio ](media/image18.png)

Alternatively, you can also use the PAC CLI tool and open the code in VS Code to edit. The code for the home page can be found under webpages and home drop-down.

![Graphical user interface for Visual Studio Code showing the code for the home page created in Maker studio ](media/image19.png)

### My Registrations

![My registration page in the Maker studio ](media/image20.png)

This page has the following available for inline editing:

#### Text fields

1.  Choose the text that you'd like to edit.

![Text editing inside of Maker Studio ](media/image21.png)

2.  Follow the prompts to edit the text fields.

#### Images:

To edit the Images component, you can refer to the methodology prescribed within the home page section.

#### Sections:

1.  When you hover over a section you will see a '+' at the end of the section.

![A section inside of Maker Studio with a blue   icon ](media/image22.png)

2.  Follow the prompts to add a section.

#### Custom components

To edit the custom component, you can refer to the methodology prescribed within the home page section.

The code for this page is under the webpages section and can be found under the my-registration drop-down.

![Visual Studio Code allows for the customization of code ](media/image23.png)

### C1 Courses Home

![The C1 Courses Home page displayed inside of Maker Studio ](media/image24.png)

This page has the following that can be edited inline:  
*Text*

1.  Select the text that you'd like to edit.

![Text editing inside of Maker Studio ](media/image21.png)

2.  Follow the prompts to edit the text fields.

#### List

1.  Hover over the list component and click into choose the list component.

![The list component inside of Maker Studio ](media/image25.png)

2.  you can change the active list and/or view being used, the view being used etc. from within the Mmaker Sstudio.

![Graphical user interface displaying options to change the active list and or view used in Maker Studio ](media/image26.png)

3.  To edit the code that's part of the list or to change the actions, navigate to the Portal Management app and choose the list view. Select the list that you'd like to edit. In this example, we'll be editing *Upcoming Courses*.

![Graphical user interface displaying all active Lists in the Makers studio ](media/image27.png)

4.  Browse through the pivots and choose the pivot and experience you'd like to edit.

![Graphical user interface for the Maker space with the Lists menu option selected  ](media/image28.png)

Alternatively, you can edit the code from within VS Code. The code for C1 home page can be found under C1 Courses Home. This houses all of the custom JavaScript, CSS, and the content code.

![Graphical user interface for Visual Studios Code displaying the code for C1 Courses Home ](media/image29.png)

**Note – to be able to create a create a course, edit a course, or duplicate a course you have to add the contacts to the right web roles within the portal management app.**

#### To add someone to the right Web role

Step 1 – Head over to the portal management app and click into the website binding.

![A graphical user interface displaying the Websites Bindings section of Maker Studio  The radio button for the ASP website is selected ](media/image30.png)

Step 2 – Once into the right website binding click into the website.

![A graphical user interface displaying the Websites Bindings section of Maker Studio  The textbox near the Website field reads ASP ](media/image31.png)

Step 3 – Click on related and select the Web Roles option.

![A graphical user interface displaying the Websites section of Maker Studio ](media/image32.png)

Step 4 – Click into the C1 ASP Web role once inside the webroles.

![A graphical user interface displaying the Websites section of Maker Studio  The radio button for C1 ASP is selected ](media/image33.png)

Step 5 – Click into related and select the Contacts option.

![A graphical user interface displaying the Related menu options in Maker Studio ](media/image34.png)

Step 6 – Click on add an existing contact and add the right contact into the C1 ASP role and save.

![A graphical user interface displaying the Add existing content functionality in Maker Studio ](media/image35.png)

Once added successfully you will find the contact under the Contact Associated View Table.

### Create Courses, Edit Courses and Duplicate Courses

Create, Edit and Duplicate courses page have the same layout and components but correspond to various actions that a C1 authenticated user is authorized to take.

![A graphical user interface displaying the main navigation menu options in Maker Studio ](media/image36.png)

This page has the following:  
*Form*

1.  Select the form component in the page and choose Edit.

![A graphical user interface displaying the form component in Maker Studio ](media/image37.png)

To edit the form fields, you can select the "Edit form" icon in this view and you will be redirected to the Dataverse Form Designer.

![A graphical user interface showing the Edit Form options inside the Dataverse Form Designer ](media/image38.png)

#### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

#### Buttons 

1.  Select the button that you'd like to edit.

![A graphical user interface with a button selected for editing  This is indicated by a dashed blue box  the word Button displayed in a white box with blue lettering  and a   icon ](media/image39.png)

2.  Follow the prompts to look at options to edit the button.

#### Text

1.  Select the text that you'd like to edit.

![Text editing inside of Maker Studio ](media/image21.png)

2.  Follow the prompts to edit the text fields.

### View Course Details

![A graphical user interface displaying a page created in Portals named View Course Details ](media/image40.png)

This page has the following components that you can edit inline:  
*Text*

You can look at the examples provided in the Create, Edit and Duplicate courses to edit the text components.

#### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

#### Custom Components 

Custom components cannot be edited inline. If you would like to edit the code associated with these components, open the code within the code editor using the PAC CLI tools.

Code for this page can be found under webpages and View Course details.

![Visual Studio Code  39](media/s graphical user interface with the left-hand menu showing..png)

### Registration Success

*Text*

You can look at the examples provided in the Create, Edit and Duplicate courses to edit the text components.

#### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

![A graphical user interface displaying a page created in Portals named Registration Success ](media/image42.png)

*Text*

You can look at the examples provided in the "Create, Edit and Duplicate courses" to edit the text components.

#### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

#### Buttons 

Refer to the Button editing information in the "Create, Edit and Duplicate courses" page editing details.

### Add and Edit Attendee Profile, C1 Delete Course and Unregister Attendee

All the above four pages have a single component as part of the page.

The page has the following components:

#### Form 

You can look at the examples provided in the Create, Edit and Duplicate courses to edit the form components.

# Data Workspace for After School Program 

The solution template comes with a rich set of sample data that you can edit from within the Maker Studio.  
With the Data workspace, you can look at the tables that are part of the solution, edit the records, and add new records.

| Pages                 | Tables                            |
|-----------------------|-----------------------------------|
| Home                  | Courses and Contact               |
| C1 Courses Home       | Courses and Contact               |
| Edit Course           | Courses, Contact and Registration |
| C1 Delete-Course      | Courses, Contact and Registration |
| Unregister Attendee   | Contact and Registration          |
| Add Attendee Profile  | Courses, Contact and Registration |
| Attendee Information  | Courses, Contact and Registration |
| Create Course         | Courses and Contact               |
| Duplicate Course      | Courses and Contact               |
| Edit Attendee Profile | Contact                           |
| My Registration       | Courses, Contact and Registration |
| Registration Success  | Contact and Registration          |
| View Course Details   | Courses and Contact               |

![A graphical user interface displaying the styling options for tables in Portals ](media/image43.png)

To preview the changes, return head back to the Pages workspace, sync the changes, and select the preview button.

Styling Workspace for After School Program

After School Program comes with a custom theme that's mapped to one of the themes out of the box. There are many themes to choose from. Select the one that you like the best.

![A graphical user interface displaying the Portals styling workspace ](media/image44.png)

You are also able to look at what the theme would look like across pages by using the pages drop-down.

![A graphical user interface displaying the styling options available within Portals ](media/image45.png)

# Setup Workspace for After School Program

Setup workspace allows you to set and edit table permissions. You can also set up identity providers as part of your sign-in/sign-up pages.

![A graphical user interface displaying the Table Permissions feature of Portals ](media/image46.png)

## Enabling new identity providers

![A graphical user interface displaying the configure identity provider in Portals ](media/image47.png)

# Customize Power Automate Flows that are part of the After School Program

# Editing the Custom Components that are part of the After School Program Package 

After School Program has many custom components and custom code, and you can edit these directly using the robust PAC CLI tooling we have enabled for Portals in connection with VS Code.

For more information visit [MS Docs](https://docs.microsoft.com/en-us/powerapps/maker/portals/power-apps-cli).

This template has the folder structure as pasted below and you can edit the code that comes as part of the solution template or extend the capabilities of the template according to your needs.

The styling and CSS can be found under web-files. The various pages and their HTML can be found under web-pages. The components that are integrated as part of the pages can be found under the right components.

The bulk of the code for this template is under basic-forms, lists and web-pages.

![Visual Studio Code  39](media/s graphical user interface with the left-hand menu showing. .png)

# Disclaimer 

This app is a sample and is provided "as is" without warranty of any kind. Customer bears the sole risk and responsibility for any use of this app. Customer is expected to update and customize this app as appropriate for its own needs, and is responsible for ensuring that its implementation complies with all laws and regulations applicable to Customer's use. Microsoft is not responsible for the performance, accuracy or results from the use of the app or any modifications to the app.

Sample data included in this app are for illustration only and are fictitious. No real association is

intended or inferred.

Preview features are features that aren't complete but are made available on a "preview" basis so customers can get early access and provide feedback. Preview features  may have limited or restricted functionality, aren't meant for production use, and may be available only in selected geographic areas.

PREVIEWS ARE PROVIDED "AS-IS," "WITH ALL FAULTS," AND "AS AVAILABLE," AND ARE EXCLUDED FROM THE SERVICE LEVEL AGREEMENTS AND LIMITED WARRANTY. Previews may not be covered by customer support. Microsoft may change or discontinue Previews at any time without notice. Microsoft also may choose not to release a Preview into "General Availability". Previews may be subject to reduced or different security, compliance and privacy commitments.

# Copyright  

This document is provided "as-is". Information and views expressed in this document, including URL and other Internet web site references, may change without notice.   

Some examples depicted herein are provided for illustration only and are fictitious. No real association or connection is intended or should be inferred.   

This document does not provide you with any legal rights to any intellectual property in any Microsoft product. You may copy and use this document for your internal, reference purposes. This document is confidential and proprietary to Microsoft. It is disclosed and can be used only pursuant to a non-disclosure agreement.    

© 2021 Microsoft. All rights reserved.    

Microsoft is trademark of the Microsoft group of companies. All other trademarks are property of their respective owners.  

# Image Attribution 

The Images you see are Photos provided by [<u>Pexels</u>](https://www.pexels.com/) and [<u>https://pixabay.com/</u>](https://pixabay.com/)  

# Font Attribution 

We are using google fonts to bring you the best user experience: 

| <a href="https://fonts.google.com/specimen/Montserrat"><u>Montserrat - Google Fonts</u></a>  </br><a href="https://fonts.google.com/specimen/Nunito"><u>Nunito - Google Fonts</u></a> </br><a href="https://fonts.google.com/specimen/Raleway"><u>Raleway - Google Fonts</u></a>  | These fonts are licensed under the <a href="https://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&amp;id=OFL"><u>Open Font License</u></a>.  |
|-------------------------|-------------------------|
| [Roboto - Google Fonts](https://fonts.google.com/specimen/Roboto) </br>[Open Sans - Google Fonts](https://fonts.google.com/specimen/Open+Sans)  | These fonts are licensed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).  |


