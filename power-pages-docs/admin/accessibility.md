---
title: Accessibility in Power Pages
description: Learn how to make your Power Pages sites accessible.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 04/22/2025
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - carltoncolter
    - nageshbhat-msft
---
 
# Accessibility in Power Pages

Microsoft is committed to make products and services accessible to everyone. For more information about accessibility at Microsoft, go to the [Microsoft Accessibility](https://www.microsoft.com/accessibility) website.

## Accessibility standards

Power Pages conforms to global accessibility standards. The following accessibility standards and conformance reports provide details about accessibility in Power Pages.

For more details about each of the follow accessibility standards, go to [Microsoft Accessibility Conformance Reports](https://cloudblogs.microsoft.com/industry-blog/government/2018/09/11/accessibility-conformance-reports/).

### WCAG 2.2

The [Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/WCAG22/) cover a wide range of recommendations to create accessible web content. Following the guidelines makes your content accessible to a wide range of users and includes accommodations for people with visual impairments, hearing loss, limited mobility, inability to speak, blindness and low vision, deafness and hearing loss, limited movement, photo sensitivity, and cognitive or developmental disabilities. These guidelines also address the accessibility of web content on desktops, laptops, tablets, and mobile devices. 

Power Pages conforms to the WCAG 2.2 accessibility standard.

### US Section 508

The US General Services Administration (GSA) Office of Government-wide Policy (OGP) is tasked under [Section 508](https://www.section508.gov/) of the Rehabilitation Act to provide technical assistance to help Federal agencies comply with these requirements, and ensure that covered information and communication technology (ICT) is accessible to, and usable by, individuals with disabilities.

Power Pages conforms to the Section 508 guidelines defined by the US GSA. 

### EN 301 549

[EN 301 549](https://www.etsi.org/deliver/etsi_en/301500_301599/301549/02.01.02_60/en_301549v020102p.pdf) from the European Telecommunications Standards Institute (ETSI) provides an open, inclusive, and collaborative environment. This environment supports the timely development, ratification, and testing of globally applicable standards for ICT-enabled systems, applications, and services.

Power Pages conforms to ETSI EN 301 549. 

## Creating an accessible webpage

To create an accessible website, follow the [WAI-ARIA Authoring Practices 1.1](https://www.w3.org/TR/wai-aria-practices/) authoring practices.

### Customizing your Power Pages site and accessibility

When you customize your Power Pages site, you're responsible for meeting accessibility standards.

### Basic forms

A basic form uses a model-driven Power Apps form to display a form on a webpage. Basic forms typically don't require a developer to design and configure; however, it might be helpful to involve a developer to extend some of the form features.

More information: [How to create and modify Dataverse forms using the Data workspace](../configure/data-workspace-forms.md)

### Basic form options

The controls included in basic forms are built to follow WCAG 2.2. The following options help make forms more accessible.

| **Name**                        | **Description**    |
|---------------------------------|----------|
| ToolTips Enabled                | The tooltip is set by using the description of the attribute on the target table. This setting adds the title attribute, providing screen readers with more information. The default value is false. |
| Enable Validation Summary Links | A Boolean value of true or false that indicates whether anchor links should be rendered in the validation summary to scroll to the field containing an error. The default value is true.          |

More information: [Add a form](../getting-started/add-form.md)

### Liquid templates and content snippets

When custom HTML and [Use Liquid](../configure/liquid-overview.md) content are added to your Power Pages site, accessibility must be taken into consideration. The person making the changes to the Liquid templates and [Content snippets](../configure/content-snippets.md) is responsible for ensuring that the content they add is accessible. It's important to make sure that customizations adhere to the required policies, such as WCAG 2.1, US Section 508, or ETSI EN 301 549.

The [WCAG 2.2 Quick Reference](https://www.w3.org/WAI/WCAG22/quickref/) provides a list of the WCAG requirements with links to the full descriptions.

### Power BI

Power Pages allows you to bring your Power BI reports/dashboard as a [first party component](../getting-started/add-power-bi.md); however, as a Power BI report and dashboard author, you should make sure your Power BI reports and dashboards are accessible.  For more information, see [Power BI accessibility guide](/power-bi/create-reports/desktop-accessibility-creating-reports).

### Quick tips for accessible content

- Make sure a non-sighted or visually impaired person can do everything a sighted user can do.

- Test your Power Pages site by zooming in to 400 percent. Make sure the text is readable, and pages and controls function as expected. For more information, go to [WCAG 1.4.10](https://www.w3.org/WAI/WCAG22/Understanding/reflow).

- Color contrast matters. Use a color contrast tool to help you see the contrast ratio. For more information, go to [WCAG 1.4.3](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html).

- Color shouldn't be the only visual way of conveying an action or information. If changing the color to highlight text, ensure the color, or descriptive information, is also available in the text. For more information, go to [WCAG 1.4.1](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html).

- Use the alt attribute for every image (IMG tag). Use an empty alt attribute to hide the image from screen readers. Ideally, you can use CSS to define decorative images hidden from screen readers. For more information, go to [WCAG C9](https://www.w3.org/WAI/WCAG22/Techniques/css/C9.html).

- Use the Microsoft [Accessibility Insights](https://accessibilityinsights.io/) tool to perform two types of scans:

    - [FastPass](https://accessibilityinsights.io/docs/web/getstarted/fastpass/): automatically checks for compliance with dozens of accessibility requirements.

    - [Assessment](https://accessibilityinsights.io/docs/web/getstarted/assessment/): measures compliance with WCAG 2.2 Level AA success criteria.

- Follow [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices/) while creating page layout and adding widgets.

- Test your site using the same accessibility tools as your users:

    - Use a screen reader, such as [Windows Narrator](https://support.microsoft.com/windows/chapter-1-introducing-narrator-7fe8fd72-541f-4536-7658-bfc37ddaf9c6#WindowsVersion=Windows_11).

    - Use [Immersive Reader](https://education.microsoft.com/resource/9b010288) in Microsoft Edge to make sure your Power Pages site is rendered and readable, making adjustments to the website as needed.

## Microsoft accessibility features

Microsoft accessibility features help various agencies address accessibility requirements and conform to the standards laid out. More information: [Accessibility features of Microsoft products](https://www.microsoft.com/en-us/accessibility)

