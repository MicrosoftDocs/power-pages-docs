---
title: Set up DocuSign integration
description: Learn how to set up DocuSign integration with your website. Include document generation and e-signature functionality in multi-step forms using DocuSign in Power Pages.
author: 

ms.topic: conceptual
ms.custom: 
ms.date: 08/28/2023
ms.subservice:
ms.author: 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---
# Set up DocuSign integration

The Power Pages and DocuSign integration offers an efficient workflow for incorporating e-signatures into multi-step forms through a low-code Studio experience. This integration uses the DocuSign connector-based Microsoft Power Automate Flow to enable an end user to view and sign documents. The configuration of these components is through a newly introduced **External Apps > Integrations** tab in the Set up workspace and allows you to map to your specific business data tables to DocuSign. With this integration, you can add an e-signature step to your multi-step forms, enabling a streamlined process for capturing digital signatures.

Integrating DocuSign into your application requires three steps:

- [Install](#install-docusign) the DocuSign package

- [Configure](#configure-docusign) DocuSign + Power Pages

- [Enable](#enable-docusign) e-signature for a multi-step form

## Set up DocuSign

Set up a template in DocuSign. The template can contain one or more documents for viewing and signing. The template is assigned a recipient role but doesn't need any name or email association—these fields are assigned from the Power Pages website. The document can include tabs or fields including the signature tab. See [DocuSign Template documentation](https://support.docusign.com/s/document-item?language=en_US&bundleId=xry1643227563338&topicId=uab1578456394214.html&_LANG=enus) for details or watch [this video](https://support.docusign.com/s/articles/Create-a-DocuSign-Template?language=en_US).

## Install DocuSign

1. In the design studio, choose **Set up > External Apps**.
1. Select the **Install** action for DocuSign. 
    :::image type="content" source="Media/docusign/install-docusign.png" alt-text="The Set up workspace in Power Pages design studio with the External Apps menu option selected and the install button for DocuSign emphasized.":::

This installs a solution, which contains tables, flows, a Dataverse plugin, and the PCF control to render signed documents.

## Configure DocuSign

Once you've installed DocuSign, you can begin to configure DocuSign for your Power Pages site.

1. In the design studio, choose **Set up > External Apps**.
1. In the Integrations table, Select the **Configure** action for DocuSign.
The Enable integration menu displays.
:::image type="content" source="Media/docusign/enable-integrations.png" alt-text="The Enable integration options inside design studio.":::
1. Select the links to resolve the connection references and enable cloud flows in Power Automate, ensuring both cloud flows are **on**.
    > [!NOTE]
    > Use your DocuSign credentials for the DocuSign flow and a connection to Dataverse.
1. Return to the Enable integration side panel in design studio and select the checkbox next to the text *I have resolved the connection references*.
1. Select **Next**.
1. Select **Close**.

### Add the DocuSign Envelope Create and Sign cloud flow

Next, add a DocuSign Template and fill in the details for your cloud flow.

1. In the design studio, choose **Setup > Cloud Flows**.
1. Input the DocuSign template metadata in the fields provided, including *Template ID*, *Template Name*, *Role Name*, and *Table*.

ADD PHOTO HERE

1. Map the form table fields to DocuSign tabs in the document.

ADD PHOTO HERE

1. Sign into your [DocuSign account](https://account.docusign.com).
1. Choose **Settings > Integrations > Connect**.
1. Modify the *PowerPagesDocusignEnvelopeTrigger v1.0* connection to incorporate other triggers.

## Enable DocuSign

To enable DocuSign, complete the following steps:

1. Add form steps using a form from the table you've mapped to your template in the previous step. More information: [Add a multistep form](../getting-started/multistep-forms.md)
1. Add table permissions for your table (minimum: create and write + authenticated or higher). More information: [Configuring table permissions](../security/table-permissions.md)
1. Add a child permission to that permission for the DocuSign Output table (minimum: AppendTo + match parent role).
1. Select the **Sync** button.

Next, add a new form step entitled Sign Document (or similar).

1. Proceed to Step settings.
1. Select Integrations on the left
    - Choose the correct Template to associate with the form
    - Enable form toggle for e-signature.
    
        ADD IMAGE HERE

    > [!NOTE] 
    > You must open the form to give permission to authenticated users.

# Troubleshooting

Ensure the steps have been followed correctly, verify the solution flow hasn't been added to the site, and the flows haven't been turned on.

Review the flow executions by navigating to flow.microsoft.com and see if the flow "DocuSign Envelope Create and Sign" has run and if there are any errors in the run – Contact support if the errors are unexpected.
