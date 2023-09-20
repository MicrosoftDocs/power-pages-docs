---
title: Bootstrap overview
description: Learn how to create Power Pages sites with Bootstrap.
author: ankitavish 
ms.topic: conceptual
ms.custom: 
ms.date: 09/20/2023
ms.subservice:
ms.author: avishwakarma
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---
# Bootstrap overview

Bootstrap is a front-end framework that includes CSS and JavaScript components for common web application interface elements. It includes styles for [navigation elements](https://getbootstrap.com/components/#nav), [forms](https://getbootstrap.com/css/#forms), and [buttons](https://getbootstrap.com/css/#buttons). Bootstrap also includes a [responsive grid layout system](https://getbootstrap.com/css/#grid), which allows site layouts to dynamically adjust to devices with different screen sizes, such as phones and tablets. By using the Bootstrap layout system, you can develop a single site that presents an appropriate interface to all devices your customers might use.

Power Pages templates are implemented by using standard Bootstrap components with minimal other custom styles. When you implement the templates, you can take advantage of Bootstrap's customization options. You can quickly customize the theme (fonts, colors, and so on) in a way that's applied consistently across the site.

The styling framework for Power Pages currently is provided via Bootstrap version 3 (v3) framework. Bootstrap released its latest update by launching version 5.2.2 (version 5), with enhanced UX functionalities and out-of-the-box components such as accordion, offcanvas and RTL support.

> [!NOTE]
> - You can create websites in Power Pages using Bootstrap version 5 (preview). More information: [Create Power Pages sites with Bootstrap version 5 (preview)](../configure/bootstrap-version-5.md)
> - You can also migrate your existing version 3 websites to version 5. More information: [Migrate an existing site to Bootstrap version 5 (preview)](../configure/migrate-bootstrap.md)

## Customize Bootstrap

Bootstrap supports customization through a set of variables. You can set any or all of these variables to custom values and then download a custom version of Bootstrap that is compiled based on these values.

The power of Bootstrap variables is that they don't dictate the style of a single element. All styles in the framework are based on and derived from these values. For example, consider the variable `@font-size-base`. This variable specifies the size that Bootstrap assigns to normal body text; however, Bootstrap also uses this variable to indicate the font size for headings and other elements. The size for an H1 element might be defined as 300 percent of the size of `@font-size-base`. By setting this one variable, you control the entire typographic scale of your website in a consistent way. Similarly, the `@link-color` variable controls the color of hyperlinks. Based on the color assigned to this value, Bootstrap defines the hover color for links as 15 percent darker than your custom value.

The standard way to create a custom version of Bootstrap is [through the official Bootstrap site](https://getbootstrap.com/customize/#less-variables); however, due to the popularity of Bootstrap, many third-party sites also exist for this purpose. These sites may provide an easier-to-use interface for Bootstrap customization or offer predesigned versions of Bootstrap for you to download. [The official Bootstrap customizer](https://getbootstrap.com/customize/) site has more information about Bootstrap customization.  

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

Depending on the customizer application used, the directory structure might only contain bootstrap.min.css. Regardless, bootstrap.min.css is the file that contains your customizations. The other files are the same for all custom versions of Bootstrap and are already included in your website.

## Next steps

[Create and manage sites using Bootstrap version 5 (preview)](bootstrap-version-5.md)

### See also

- [Migrate an existing site to Bootstrap version 5 (preview)](../configure/migrate-bootstrap.md)
- [Manage CSS files](manage-css.md)
