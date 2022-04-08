---
title: Book a Meeting template
description: template
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/08/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Book a Meeting template

Book a meeting is designed to show you the capabilities of a scheduling template and we've picked the example of scheduling with a bank representative; however, the scheduling principle will apply to any industry or organization looking to stand up a scheduling portal.

There are two key users that the template is designed for:

- The customer of the bank is trying to book an appointment with the bank representative.

- The bank representative who is looking at the list of appointments and managing their calendars and appointments.

As a customer of a bank, you can do the following seamlessly:

- Book an appointment with a certain bank representative, in a certain bank branch and the time that best suits the customer.

- The customer can also cancel and reschedule the appointments via links present in the email that they receive upon booking confirmation.

## Pages workspace for Book a Meeting

Book a meeting has a rich set of out of the box pages that are well defined based on the user scenarios and user roles.

We have pages that are designed to target two core user personas that will use this portal:

- The customer of the bank is trying to book an appointment with the bank representative.

- The bank representative who is looking at the list of appointments and managing their calendars and appointments.

In the screenshot below you'll see there are two sections for page navigation:

- Main navigation: this section covers the pages you have as part of your main navigation experiences.

- Other pages: this section houses the subpages that you land on from one of the pages in the main navigation.

## Change page components

With in-context edit, you can easily change the logo I the header, changes the background image, and overlay color.

- Change the logo, the name of the bank in the header.

- The background picture and the color gradient of the image.

- The texts are available on the screen.

> [!NOTE]
> moving the block of text to the center of the screen is custom code and to edit you need to use the code editor.

**Example** – in the screen below you can see that the logo and header text have been changed and the maker studio has the right cues in place to help you through the process.

![Maker studio highlighting the change in logo and welcome text ](media/image17.png)

For advanced customizations, you can open the code editor.

You're able to extend the capabilities of the page via VSCode and PAC CLI tooling and for the home page you can find the classes and code within the web-pages drop down.

![A computer screen capture Description automatically generated with medium confidence](media/image18.png)

## C2 Book an Appointment form

There's an advanced form on this page and to edit this form you're redirected to the Portal Management app.

![Button to open the Portal Management app from the Maker studio ](media/image19.png)

![Graphical user interface  text  application  email Description automatically generated](media/image21.png)

To edit the underlying forms within the advanced form, head to the forms within data workspace to add/edit components and fields.

![Graphical user interface  application  email Description automatically generated](media/image22.png)

Select here to learn more about advanced forms and how to set it up.

You can extend the capabilities of the page via VSCode and PAC CLI tooling. There are two key areas to look at for customization here. The Custom JS that comes with the advanced forms and the page content. The Custom JS can be found under advanced forms and the html can be found under the webpages.

![Text Description automatically generated](media/image23.png)

## C1 Specialties page

This page has multiple components and things a maker can change. The components available on this page:

- Image

- Text

- Lists

- Forms

![Using the maker studio to update the profile page ](media/image29.png)

## To update an image

Select the image and change the placeholder.

![Update the profile image using the make studio ](media/image30.png)

## To update the text fields

Select the text and update the placeholder text.

![Updating text fields using the maker studio ](media/image31.png)

## To update the list

Select the list, copy the name and select edit to go to the Portal Management app to view the list details.

![Update the list  button to navigate user from maker studio to Portal Management app ](media/image32.png)

![Using the portal management app to configured details about the list ](media/image33.png)

If you wish to update the underlying table look at the name of the table used here and head over to the solution as started in the **How to update a table** section and make the necessary changes.

## To update a basic form

Select the form and select the **Edit** option you see in the studio.

![Editing a form in the maker studio ](media/image34.png)

To edit the fields within the form, select the edit form icon and you'll be redirected to the Dataverse form editor.

![Edit form link to navigate to the Dataverse form editor ](media/image35.png)

![Editing the form in the Dataverse form editor ](media/image36.png)

To configure the form and form options head copy the name of the basic form you see – in this case BAM C1 Select Specialties, head over the Portal Management app and under the basic forms find this specific form.

![Editing form properties in the Portals Management app ](media/image37.png)

To customize any custom JavaScript that's available as part of the form head over to the form options section within the same basic form and edit/add to the custom JavaScript section.

![Editing JavaScript in the Basic form in the Portals Management app ](media/image38.png)

To extend the capabilities of the page, you can also look at using VS Code with the pac CLI tooling.

![VS Code editing the web page copy ](media/image39.png)

## C1 Home

This page has the following components:

- Buttons

- Text

- Custom List/Calendar

![Editing home page in maker studio](media/image40.png)

For buttons and list follow the instructions under the C1 Specialties page section.

-  For calendar view:  
    The underlying component in this case is a list that can be reached by selecting the component and following the link.

You can follow the steps in the To update a list within the C1 specialties page.

### Other pages 

The following pages have a basic form as the only components, and You can follow the steps in the To update a basic form within the C1 specialties page.

- C1 Edit unavailability

- Create Unavailability

- C1 cancels appointment

- C2 cancels appointment

- C2 cancels confirmation

The basic forms can also be edited from within the Data workspace:  
![Editing forms in the Data workspace ](media/image41.png)

Within the tables you can see the forms view and you can select the form you want to edit and make the necessary changes.

The following pages have an advanced form as the only components, and you can follow the steps in the To **update an advanced form** within the C2 Book an Appointment form.

- C1 Reschedule appointment

- C2 Reschedule appointment

## Data Workspace for Book a Meeting

The solution template comes with a rich set of sample data that you can edit from within the maker studio.  
With the Data workspace you can look at the tables that are part of the solution and edit the records, add new records.

Booking an appointment uses all the pages you see here and also the "Location" that's housed under the other tables.

Bank representative specialties use the contact and service tables.

Bank representative's homepage uses the appointment, appointment request and also the contact tables.

![Editing table in the Data workspace ](media/image42.png)

To preview the changes, head back to the Pages workspace, sync the changes and select the preview button provided.

## Styling workspace for Book a Meeting

Book a meeting comes with a custom theme that's mapped to one of the themes out of the box. You can always change the themes to the available ones and select the ones that best appeal to you. We recommend that you stay with the theme that came out of the box to enable the best styling and UX for the end users.

![Updating the styles in the Styling workspace ](media/image43.png)

## Set up workspace for Book a Meeting

Setup workspace lets you set and edit table permissions, you're also able to set up identity providers that show up as part of your sign in/sign up pages.

![Updating table permissions in the Setup Workspace ](media/image44.png)

Enabling new identity providers:

![Enabling identity providers in the Setup workspace ](media/image45.png)

## Customize Power Automate flows that are part of the Book a Meeting template.

This template comes with a rich set of flows that are built in as part of the template and will get triggered and emails sent depending on the user flow.

There are four emails being sent out:

Four types of emails are sent out:

- Scheduling appointment

- Rescheduling appointment

- Cancelling appointment

- Appointment reminder

You can edit the emails by heading to the solution explorer -&gt; navigate to the book a meeting solution and select the cloud flow to view the available flow and available for you to customize.

![List of cloud flows used in Book a Meeting portal app ](media/image46.png)

The email notifications will have hyperlinks embedded to allow recipients to navigate back to the portal.

To ensure the email notifications have the correct domain embedded, add the website ID to the flows that have been configured as part of the solution.

Grab the website ID from the URL – in this case **c7be234f-d856-ec11-8f8e-002248233fb1** is the website ID that we have.

![Show where the GUID can be extracted from the URL](media/image47.png)

Alternatively, you can also copy the website ID from the website table created within the solution.

![Power Apps solution explorer showing list of website GUIDs ](media/image48.png)

Select the flow you'd like edit.

![Power Automate command bar](media/image49.png)

Sign in and update the information within "Get the website" section.

![Updating the Website action step in Power Automate](media/image50.png)

Save the changes and you should start receiving email notifications with the correct embedded links as expected from the solution.

## Editing the custom components that are part of Book a Meeting package

Book a Meeting has many custom components and custom code, and you can make changes to those. You can use the robust PAC CLI tooling we've enabled for portals with VSCode.

For more information visit [MS Docs](https://docs.microsoft.com/en-us/powerapps/maker/portals/power-apps-cli).

This template has the folder structure as pasted below and you can edit the code that comes as part of the solution template or extend the capabilities of the template according to your needs.

The styling and css can be found under web-files, the various pages and their html can be found under web-pages and the components that are integrated as part of the pages can be found under the right components.

![VS Code editing the web page copy ](media/image51.png)



