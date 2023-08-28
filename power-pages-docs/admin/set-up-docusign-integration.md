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

The Power Pages and DocuSign integration offers a seamless, efficient workflow for incorporating e-signatures into multi-step forms through a low-code Studio experience. This integration uses the DocuSign connector-based Microsoft Power Automate Flow to enable an end user to view and sign documents. The configuration of these components is through a newly introduced **External Apps > Integrations** tab in the Set up workspace and allows you to map to your specific business data tables to DocuSign. With this integration, you can add an e-signature step to your multi-step forms, enabling a smooth and streamlined process for capturing digital signatures.

Integrating DocuSign into your application will require three steps:

- [Install](#install-docusign) the DocuSign package

- [Configure](#configure-docusign) DocuSign + Power Pages

- [Enable](#enable-docusign) e-signature for a multi-step form

## Set up DocuSign

Setup a template in DocuSign. The template can contain one or more documents for viewing and signing. The template is assigned a recipient role but doesn't need any name or email association—these fields will be assigned from the Power Pages website. The document can include tabs or fields including the signature tab. Please see [DocuSign Template documentation](https://support.docusign.com/s/document-item?language=en_US&bundleId=xry1643227563338&topicId=uab1578456394214.html&_LANG=enus) for details or watch [this video](https://support.docusign.com/s/articles/Create-a-DocuSign-Template?language=en_US).

## Install DocuSign

1. Navigate to Setup, then select External Apps.
1. Select the Install action for DocuSign. This installs a solution which contains tables, flows, a Dataverse plugin, and the PCF control to render signed documents.

## Configure DocuSign

Begin by resolving connection references.

1. Resolve both flow connections. You will use DocuSign creds for the DocuSign flow and a connection to Dataverse.
1. Ensure both the flows are turned on.
1. Acknowledge the configuration screen.
1. Add the *DocuSign Envelope Create and Sign* cloud flow to your site by going to **Setup > Cloud Flows**.

Next, add a template by providing details for the DocuSign Template.

1. Input the DocuSign template metadata in the fields provided. This includes Template ID, Template Name, Role Name, and Table.
1. Map the form table fields to DocuSign tabs that are included in the document.

Navigate to your DocuSign account (account.docusign.com) and going into settings \| Integrations \| Connect and modify the "PowerPagesDocusignEnvelopeTrigger v1.0" connect to have these additional triggers.

## Enable DocuSign

To enable DocuSign, complete the following steps:

1. Add form steps using a form from the table you've mapped to your template in the step above.
1. Add table permissions for that table (minimum: create and write + authenticated or higher).
1. Add a child permission to that permission for the DocuSign Output table (minimum: AppendTo + match parent role).
1. Select the Sync button.

Next, add a new form step entitled Sign Document (or similar).

1. Proceed to Step settings.
1. Select Integrations on the left
    - Choose the correct Template to associate with the form
    - Enable form toggle for e-signature.

    > [!NOTE] 
    > You must open the form to give permission to authenticated users.

# Troubleshooting

Ensure the steps have been followed correctly, verify the solution flow has not been added to the site, and the flows have not been turned on.

Review the flow executions by navigating to flow.microsoft.com and see if the flow "DocuSign Envelope Create and Sign" has run and if there are any errors in the run – Contact support if the errors are unexpected.
