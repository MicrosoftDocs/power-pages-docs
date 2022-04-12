---
title: Edit page components for After School Program template
description: template
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/11/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Edit page components for After School Program template

## Home 

With the in-context editor, you can easily change the logo and the header.

1. Changing the logo, the name of the organization in the header.

    Follow the prompts to change the image and text to reflect the logo and name of the organization.
    
    ![The maker studio showing the toolbar that appears when editing the header ](media/image14.png)

    This page also has custom code, and has been styled to follow the best-in-class UX patterns. For custom code editing, launch the Portal Management app or VS Code loading the portal metadata using the PAC CLI tools.
    
1. Hover over the component and you'll see the label "Custom Component" over the components that have custom code associated with them.

    ![The maker studio highlighting that the particular component is using custom code ](media/image15.png)

1. Selecting the component will ask you to open the Portal Management app.

    ![Maker studio showing the Open portal management app from the menu when selecting a custom component ](media/image16.png)

1. Select the local content and head to choose the advanced tab. You'll see the custom JS JavaScript that's driving the page and you can make edits directly to the code.

    ![Graphical user interface displaying the General menu options in the Maker studio ](media/image17.png)
    
    ![Graphical user interface displaying the Advanced menu options in the Maker studio ](media/image18.png)
    
    Alternatively, you can also use the PAC CLI tool and open the code in VS Code to edit. The code for the home page can be found under webpages and home drop-down.
    
    ![Graphical user interface for Visual Studio Code showing the code for the home page created in Maker studio ](media/image19.png)

## My Registrations

![My registration page in the Maker studio ](media/image20.png)

This page has the following available for inline editing:

### Text fields

1. Choose the text that you'd like to edit.

![Text editing inside of Maker Studio ](media/image21.png)

1. Follow the prompts to edit the text fields.

### Images

To edit the Images component, you can refer to the methodology prescribed within the home page section.

### Sections

1. When you hover over a section, you'll see a '+' at the end of the section.

    ![A section inside of Maker Studio with a blue   icon ](media/image22.png)

1. Follow the prompts to add a section.

### Custom components

To edit the custom component, you can refer to the methodology prescribed within the home page section.

The code for this page is under the webpages section and can be found under the my-registration drop-down.

    ![Visual Studio Code allows for the customization of code ](media/image23.png)

### C1 Courses Home

    ![The C1 Courses Home page displayed inside of Maker Studio ](media/image24.png)

This page has the following that can be edited inline:  
*Text*

1. Select the text that you'd like to edit.

    ![Text editing inside of Maker Studio ](media/image21.png)

1. Follow the prompts to edit the text fields.

### List

1. Hover over the list component and select into choose the list component.

    ![The list component inside of Maker Studio ](media/image25.png)

1. you can change the active list and/or view being used, the view being used etc. from within the Maker Studio.

    ![Graphical user interface displaying options to change the active list and or view used in Maker Studio ](media/image26.png)

1. To edit the code that's part of the list or to change the actions, navigate to the Portal Management app and choose the list view. Select the list that you'd like to edit. In this example, we'll be editing *Upcoming Courses*.

        ![Graphical user interface displaying all active Lists in the Makers studio ](media/image27.png)

1. Browse through the pivots and choose the pivot and experience you'd like to edit.

        ![Graphical user interface for the Maker space with the Lists menu option selected  ](media/image28.png)

Alternatively, you can edit the code from within VS Code. The code for C1 home page can be found under C1 Courses Home, which houses all of the custom JavaScript, CSS, and the content code.

![Graphical user interface for Visual Studios Code displaying the code for C1 Courses Home ](media/image29.png)

**Note – to be able to create a create a course, edit a course, or duplicate a course you have to add the contacts to the right web roles within the portal management app.**

### To add someone to the right Web role

1. Head over to the portal management app and select website binding.

    ![A graphical user interface displaying the Websites Bindings section of Maker Studio  The radio button for the ASP website is selected ](media/image30.png)

1. Once into the right website binding select the website.

    ![A graphical user interface displaying the Websites Bindings section of Maker Studio  The textbox near the Website field reads ASP ](media/image31.png)

1. Select on related and select the Web Roles option.

    ![A graphical user interface displaying the Websites section of Maker Studio ](media/image32.png)

1. Select into the C1 ASP Web role once inside the web roles.

    ![A graphical user interface displaying the Websites section of Maker Studio  The radio button for C1 ASP is selected ](media/image33.png)

Step 5 – select into related and select the Contacts option.

    ![A graphical user interface displaying the Related menu options in Maker Studio ](media/image34.png)

1. Select on add an existing contact and add the right contact into the C1 ASP role and save.
    
    ![A graphical user interface displaying the Add existing content functionality in Maker Studio ](media/image35.png)

Once added successfully, you'll find the contact under the Contact Associated View Table.

### Create Courses, Edit Courses and Duplicate Courses

Create, Edit and Duplicate courses page have the same layout and components but correspond to various actions that a C1 authenticated user is authorized to take.

    ![A graphical user interface displaying the main navigation menu options in Maker Studio ](media/image36.png)

This page has the following:  

### Form

1. Select the form component in the page and choose Edit.

    ![A graphical user interface displaying the form component in Maker Studio ](media/image37.png)

To edit the form fields, you can select the "Edit form" icon in this view and you'll be redirected to the Dataverse Form Designer.

    ![A graphical user interface showing the Edit Form options inside the Dataverse Form Designer ](media/image38.png)

### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

### Buttons 

1. Select the button that you'd like to edit.

    ![A graphical user interface with a button selected for editing  This is indicated by a dashed blue box  the word Button displayed in a white box with blue lettering  and a   icon ](media/image39.png)

1. Follow the prompts to look at options to edit the button.

### Text

1. Select the text that you'd like to edit.

    ![Text editing inside of Maker Studio ](media/image21.png)

1. Follow the prompts to edit the text fields.

### View Course Details

    ![A graphical user interface displaying a page created in Portals named View Course Details ](media/image40.png)

This page has the following components that you can edit inline:  
*Text*

You can look at the examples provided in the Create, Edit and Duplicate courses to edit the text components.

### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

### Custom Components 

Custom components can't be edited inline. If you would like to edit the code associated with these components, open the code within the code editor using the PAC CLI tools.

Code for this page can be found under webpages and View Course details.

![Visual Studio Code  39](media/s graphical user interface with the left-hand menu showing..png)

### Registration Success

### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

    ![A graphical user interface displaying a page created in Portals named Registration Success ](media/image42.png)

### Text

Look at the examples provided in the "Create, Edit and Duplicate courses" to edit the text components.

### Sections 

Refer to the sections editing information in the "My Registrations" page editing details.

### Buttons 

Refer to the Button editing information in the "Create, Edit and Duplicate courses" page editing details.

### Add and Edit Attendee Profile, C1 Delete Course and Unregister Attendee

All the above four pages have a single component as part of the page.

The page has the following components:

### Form 

Look at the examples provided in the Create, Edit and Duplicate courses to edit the form components.

