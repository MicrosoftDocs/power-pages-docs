---
title: Bootstrap overview
description: Learn how to use Bootstrap, a popular front-end framework, to create stunning Power Pages sites that adapt to any device.
ms.topic: overview
ms.date: 09/27/2023
author: ankitavish
ms.author: avishwakarma
ms.reviewer: kkendrick
contributors:
  - ProfessorKendrick
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:11/16/2023
  - bap-template
---

# Bootstrap overview

Bootstrap is a front-end framework that helps you design web interfaces with ready-made CSS and JavaScript components for common elements like [navigation](https://getbootstrap.com/components/#nav), [forms](https://getbootstrap.com/css/#forms), and [buttons](https://getbootstrap.com/css/#buttons). It also has a [responsive grid layout system](https://getbootstrap.com/css/#grid) that adjusts your site for devices with different screen sizes, such as phones and tablets. Using the Bootstrap layout system, you can create a single site that looks good on any device your customers might use.

Power Pages templates use standard Bootstrap components with minimal custom styles. Using these templates, you can easily change the theme (fonts, colors, and so on) to match your brand and preferences consistently across your entire site.

Power Pages supports Bootstrap version 3.3.6 and Bootstrap version 5. Bootstrap version 5 offers improved user experience (UX) features and new components like accordion, offcanvas, and RTL support.

[Learn how to set up Bootstrap version 5 in your environment](../configure/bootstrap-version-5.md).

[Learn how to migrate your Bootstrap version 3 websites to version 5 (preview)](../configure/migrate-bootstrap.md).

## Customize Bootstrap

To customize Bootstrap, you change the values of variables and then download a version of Bootstrap that's compiled with your custom values.

The power of Bootstrap variables is that they define all the styles in the framework, not just one element. For example, the variable `@font-size-base` specifies the default size of text on your site&mdash;body text, headings, and all other text elements. An H1 heading might be defined as 300 percent of `@font-size-base`. By setting this one variable, you control the entire typographic scale of your website in a consistent way.

You can create a custom version of Bootstrap [through the official Bootstrap site](https://getbootstrap.com) or use a third-party site that might offer an easier interface or predesigned themes. [The official Bootstrap customizer](https://getbootstrap.com/docs/5.2/customize/overview/) site has more information about Bootstrap customization.

When you download a customized version of Bootstrap, it contains the following directory structure:

```
css/
    |-- bootstrap.min.css 
img/
    |-- glyphicons-halflings-white.png 
    |-- glyphicons-halflings.png 
js/ 
    |-- bootstrap.min.js
```

Depending on the customizer application you used, the directory structure might only contain `bootstrap.min.css`. It's the file that contains your customizations. The other files are the same for all custom versions of Bootstrap and are already included in your website.

## Next steps

- [Enable Bootstrap version 5 in your environment](bootstrap-version-5.md)

### See also

- [Migrate an existing site to Bootstrap version 5 (preview)](../configure/migrate-bootstrap.md)
- [Manage CSS files](manage-css.md)
