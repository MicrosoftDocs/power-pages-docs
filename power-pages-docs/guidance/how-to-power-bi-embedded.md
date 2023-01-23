---
title: "How to: Embed Power BI in Power Pages"
description: Learn how to embed a Power BI report in Power Pages.
author: nickdoelman
ms.topic: guidance
ms.custom: 
ms.date: 01/23/2023
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Embed a Power BI report in Power Pages

Just as Pages is the tool of choice to quickly extend your Dataverse deployment to the public in the form of a website, Power BI is the tool of choice to render elegant data-driven visualizations. The beauty of the Power Platform lies in its ability to seamlessly blend the two. In the past, to render a Power BI report in the Pages, administrators had to publish said report to the web and embed it into an iFrame. Even if one did apply Pages permissions to lock down the page with the report, if an individual had the link used to embed the report, anyone would still be able to access the report outside of the website. The purpose of **publish to web** is exactly that --to allow any individual on the web to consume the data and even reshare the report. Sure, this might make sense to display say, geese migration data.. but a report of which employees, by name, made the most retail sales in the month of April? Not so much.

That's where Power BI embedded comes in. With Power BI embedded, one can contextually serve Power BI components to users, pass automatic filters by using a filter parameter, and enable row-level security capabilities to allow an organization to truly secure data visible to users and only display what they are meant to see.

## Prerequisites

- Tenant with a Microsoft Dataverse environment and a Power Pages website deployed
- [A webpage to embed a Power BI report or dashboard](../getting-started/first-page.md)
- Relevant business data stored in Dataverse
- [Power BI Desktop](/power-bi/fundamentals/desktop-get-the-desktop)
- [Capacity for publishing Power BI embedded content](/power-bi/developer/embedded/embedded-capacity?tabs=gen2) 
- Tenant global admin rights
    - Tenant global admin [with Admin role in the Power BI service workspace](/power-bi/collaborate-share/service-roles-new-workspaces)
    - Organization, **not** personal [Power BI workspace](/power-bi/collaborate-share/service-create-the-new-workspaces)
- [Registration/authentication turned on in the website](../security/configure-portal-authentication.md)

## Scenario

You work for a group fitness studio and use Dataverse to track group fitness classes and their attendance. The group fitness instructors do not reside on your tenant, as each is treated as a contractor. Your website is to be used by these group fitness instructors to login and see a history of their taught classes, their upcoming schedule, and attendee rates. They should only be able to see the classes that they themselves have taught though, and not everyone's.

The instructors are represented by **Contact** records in Dataverse. When accessing the Power Pages website, they will be doing so as their **Contact** record. The data that they need to see in the website comes from our custom **Classes** table. The Classes table has a N\*:1 relationship to Contact, as the Classes form has a lookup field named **Instructor**, which is for the Contact table.

:::image type="content" source="media/powerbiembedded/class_record.png" alt-text="A record of a class in Dataverse.":::

To get RLS to work for Power Pages users (Contacts), there needs to be that direct relationship between the Contact and the table you are reporting against. Below is the data model of this scenario:

:::image type="content" source="media/powerbiembedded/contact-relationship.png" alt-text="Contact relationship to classes table.":::

## Configure Power BI report or dashboard

1. Open your Power BI report or dashboard in Power BI Desktop.

    :::image type="content" source="media/powerbiembedded/instructor-report.png" alt-text="Text used by screen readers.":::

1. We must change the relationship between **Contact** and our table (**Classes** in this scenario) to use bidirectional filtering. To do so, click the **Model** tab on the far left.

    :::image type="content" source="media/powerbiembedded/model.png" alt-text="Text used by screen readers.":::

1. Select the line that links your **contact** table to the table that contains your report's data – in the sample case, this is **vbd\_class** since we are reporting on classes.

1. In the **Edit relationship** window, there are two picklists. In the top, choose the table you are reporting on (**vbd\_class**) and select the column that has the record's unique identifier.

1. In the bottom picklist, select the **contact** table and select the **Contact** column.

1. Cardinality will indicate Many to one (\*:1). Change the **Cross filter direction** to **Both**.

    :::image type="content" source="media/powerbiembedded/edit-link.png" alt-text="Editing link between tables.":::

1. Select **OK**.

1. As we are implementing Row Level Security (**RLS**), we need to create our role. In the top **Home** ribbon, click on **Manage roles**.

    :::image type="content" source="media/powerbiembedded/manage-roles.png" alt-text="Manage roles in Power BI.":::

1. Under **Roles**, click **Create**. Name the role. The sample scenario used **pagesuser**.

1. From the **Tables** column, select **contact**.

1. Populate the text box to the right with the DAX expression:

    `[User Name] = username()`

    > [!NOTE] `[Username]` resides on the contact table and is not an actual username. This references the **adx\_externalidentity** table used by Power Pages. This has the GUID that is sent to Power BI in the username() function.

1. Click **Save** and then save your file.

1. From the Home ribbon, click **Publish**.

    :::image type="content" source="media/powerbiembedded/publish.png" alt-text="Publishing the Power BI report.":::

1. Select an organization workspace that you are an owner and that will be used by the Power Pages integration. Choose **Select**.

## Configure Power BI integration

Refer to [Set up Power BI integration](/power-apps/maker/portals/admin/set-up-power-bi-integration) to enable your website for Power BI integration.

## Embed Power BI report

1. Navigate to [Power Pages](https://aka.ms/mpp). Find the Power Pages website that you are going to embed the report into and then click **Edit** to open the Power Pages design studio.

1. From the the **Pages** workspace, select the web page where you want to embed the report.

1. Add a section to the body of the webpage.

    :::image type="content" source="media/powerbiembedded/add-section.png" alt-text="Add a section to a webpage.":::

1. Choose the **Power BI** icon when prompted to choose which component you are adding within the section.

    :::image type="content" source="media/powerbiembedded/powerbi-component.png" alt-text="Add a Power BI component.":::

1. When the component populates the section, select on the top left corner; **Edit Power BI**.

    :::image type="content" source="media/powerbiembedded/edit-powerbi.png" alt-text="Edit Power BI.":::

1. Click **Access type**. The options are:

    1. Embed for your customers: Allows you to share the Power BI with external users without a Power BI license or an Azure AD identity.

    1. Embed for your organization: This will use Azure AD authentication to share the report from Power BI so internal users can see this.

    1. Publish to web: This allows anyone on the internet to access the report and data. 
    
    > [!CAUTION]
    > Make sure that this is not confidential information! 

    Additional information: [Publish to web](/power-bi/collaborate-share/service-publish-to-web)

    Choose either **a** or **b**.

1. Select your workspace that contains the report or dashboard, specify the type as Report or Dashboard, and then choose the report or dashboard from the last dropdown. If this is a report, you will need to specify which page you are embedding.

    :::image type="content" source="media/powerbiembedded/select-report.png" alt-text="Select report.":::

1. To see the code that embedded the report or dashboard, click **Edit code** from the top right corner of the studio.

    :::image type="content" source="media/powerbiembedded/edit-code.png" alt-text="Edit code.":::

1. When prompted, select **Open Visual Studio Code**. On the left, under **PowerPages (Workspace)** the name of the Power Pages website will have a drop down to the web page. Within that section you will see a .css file, a .js file, and the HTML copy. Ensure that you are on the HTML copy file.

    :::image type="content" source="media/powerbiembedded/vscode.png" alt-text="VS Code.":::

1. Select **CTRL + F** and search for `{%` so we can quickly identify the code that contains the reference to our Power BI dashboard or report. `{%` indicates the opening of a tag, which creates logic for the language **Liquid**. Liquid is our bridge between Dataverse and what users interact with on the website. When we use the studio editor to embed components, a piece of liquid code is automatically created in the web page's source code. More information on the powerbi liquid tag can be found here: [Dataverse Liquid tags](/power-apps/maker/portals/liquid/portals-entity-tags#powerbi) and [Add Power BI report](/power-apps/maker/portals/admin/add-powerbi-report).

1. The full line of liquid code that you will see will resemble:

    ```html
    {% powerbi authentication\_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
    ```

1. Close the **Visual Studio Code for the Web** tab.

1. In Power Pages design studio, select the embedded Power BI component and choose **Edit Power BI.**

1. Scroll down to toggle **Apply roles** to **true/yes**.

1. In the **Roles** textbox, type the name of the role that you created in Power BI Desktop.

    :::image type="content" source="media/powerbiembedded/add-roles.png" alt-text="Add roles to Power BI component.":::

1. To see the changes this made to the code that embedded the report or dashboard, again select **Edit code** from the top right corner of the studio.

1. The full line of liquid code that you will see will now resemble:

    ```html
    {% powerbi authentication\_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" **roles:"portaluser"** %}
    ```

1. Close the Visual Studio Code tab to return to the design studio.

1. Preview the resulting embedded report or dashboard in your browser by selecting **Sync** in the top right corner, then selecing **Preview &gt; Desktop**.

    :::image type="content" source="media/powerbiembedded/preview-site.png" alt-text="Preview site.":::

1. To test this, you can see that the RLS has been applied, as there are no records returned navigating to the Power Pages website:

    :::image type="content" source="media/powerbiembedded/blank-report.png" alt-text="Blank report.":::

    There is certainly underlying data in this report, as when you view this from Power BI Desktop without the RLS applied, you can see that there are several records overall, but none of them are related to the contact record:

    :::image type="content" source="media/powerbiembedded/instructor-report.png" alt-text="Text used by screen readers.":::

1. To test this further, you can go into Dataverse and modify records to change the contact field lookup to your own contact record. Once the dataset has refreshed, you can see the updates when you return to the Power Pages website:

    :::image type="content" source="media/powerbiembedded/class_report.png" alt-text="Text used by screen readers.":::

You have embedded a Power BI report or dashboard that uses row-level security into your Power Pages website!

The filter pane will appear by default. Hiding this requires JavaScript. Steps to do this are documented here: 
