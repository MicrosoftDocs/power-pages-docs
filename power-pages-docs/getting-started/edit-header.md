---
title: Edit header
description: Learn how to customize the header for your Power Pages site.
author: clromano
ms.topic: conceptual
ms.custom: 
ms.date: 1/19/2023
ms.subservice:
ms.author: clromano 
ms.reviewer: kkendrick
contributors:
    - clromano
    - ProfessorKendrick
---

# Edit header

Makers can establish their site’s brand using the header. By using the “Edit site header” button, makers can modify/update the following elements: 

- Title + logo 
- Site title  
- Site logo and it’s corresponding alt text 

Out of the box structure vs. Customized header [same style that we used in Semantic slots] 

Refer to the section “Considerations for editing the header” 

Styling 

Set the color palette for the site [screenshot needs to be updated] 

Establish styling options for the header  

Background color 

Title 

Site navigation 

 

Layout (placeholder) 

Note: [in the future more controls coming here – remove the screenshot] 

 

 
 

Considerations for editing the header (to be anchored) 

Needs to be linked to from the CSS troubleshooting guide 

The “Edit site header” feature works by setting up 3 underlying content snippets and plugging them into the “Mobile Header” content snippet. To verify functionality, look for the following content snippets: 

Site name 

Logo URL 

Logo alt text 

Out of the box structure vs. Customized header (anchor) 

 

If the header web template has been customized and Studio is not able to recognize the out of the box structure, a message is presented with instructions on how to resolve potential issues. Please note that changes made through the “Edit site header” modal will not reflect in the underlying canvas in real-time until the fix is applied. 

[Note vs screenshot – to be removed] 

 

Sample solution to resolve the issue: 

Open the Mobile Header in PMA (Portal Management App) (or the corresponding content snippet being used for the header) 

Replace the HTML with 

`
<a href="~/">{% if snippets['Logo URL'] %}<img src="{{ snippets['Logo URL'] }}" alt="{{ snippets['Logo alt text'] }}" style="width: auto; height: 32px; margin: 0 10px;">{% endif %} 

{% if snippets['Site name'] %}<h1 class="siteTitle">{{ snippets['Site name'] }}</h1>{% endif %}</a> 
`

The critical part is to leverage the 3 content snippets so that the “Edit site header” functionality is coordinated with the underlying structure 

{{ snippets['Site name'] }} 

{{ snippets['Logo URL'] }} 

{{ snippets['Logo alt text'] }} 

### See also

[Add text](add-text.md)<br />
[Add button](add-button.md)<br />
[Add image](add-image.md)<br />
[Add video](add-video.md)<br />
[Add spacer](add-spacer.md)<br />
[Add Power BI](add-power-bi.md)<br />
[Add list](add-list.md)<br />
[Add form](add-form.md)<br />
[Add IFrame](add-iframe.md)<br />
[Add multistep form](multistep-forms.md)<br />
[Edit code with Visual Studio Code for the Web](../configure/visual-studio-code-editor.md)<br />
[Structure site map](structure-site.md)<br />
