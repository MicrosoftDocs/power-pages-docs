## Understanding Bootstrap framework

Bootstrap is a front-end framework that includes CSS and JavaScript components for common web application interface elements. It includes styles for [navigation elements](https://getbootstrap.com/components/#nav), [forms](https://getbootstrap.com/css/#forms), and [buttons](https://getbootstrap.com/css/#buttons). Bootstrap also includes a [responsive grid layout system](https://getbootstrap.com/css/#grid), which allows site layouts to dynamically adjust to devices that have different screen sizes, such as phones and tablets. By using the Bootstrap layout system, you can develop a single site that presents an appropriate interface to all devices your customers might use.

The templates included with Power Pages are implemented by using standard Bootstrap components with minimal other custom styles. So when you implement the templates, you can take advantage of Bootstrap customization options. You can quickly customize the theme (fonts, colors, and so on) in a way that's applied consistently across the site.

### Customize Bootstrap

Bootstrap supports customization through a set of variables. You can set any or all of these variables to custom values and then download a custom version of Bootstrap that is compiled based on these values.

The power of Bootstrap variables is that they don't dictate the style of a single element. All styles in the framework are based on and derived from these values. For example, consider the variable `@font-size-base`. This variable specifies the size that Bootstrap assigns to normal body text. However, Bootstrap also uses this variable to indicate the font size for headings and other elements. The size for an H1 element might be defined as 300 percent of the size of `@font-size-base`. By setting this one variable, you control the entire typographic scale of your portal in a consistent way. Similarly, the `@link-color` variable controls the color of hyperlinks. For the color you assign to this value, Bootstrap defines the hover color for links as 15 percent darker than your custom value.

The standard way to create a custom version of Bootstrap is [through the official Bootstrap site](https://getbootstrap.com/customize/#less-variables). However, due to the popularity of Bootstrap, many third-party sites have also been created for this purpose. These sites might provide an easier-to-use interface for Bootstrap customization or predesigned versions of Bootstrap for you to download. [The official Bootstrap customizer](https://getbootstrap.com/customize/) site has more information about Bootstrap customization.  

When you download a customized version of Bootstrap, it contains the following directory structure.

```
css/
    |-- bootstrap.min.css 
img/
    |-- glyphicons-halflings-white.png 
    |-- glyphicons-halflings.png 
js/ 
    |-- bootstrap.min.js
```

Or, depending on the customizer application used, it might only contain bootstrap.min.css. Regardless, bootstrap.min.css is the file that contains your customizations. The other files are the same for all custom versions of Bootstrap and are already included in your portal.

### Bootstrap version 5

The styling framework for Power Pages currently is provided via Bootstrap version 3 (v3) framework. Bootstrap released its latest update by launching version 5.2.2 (v5), with enhanced UX functionalities and out-of-the-box components like accordion, offcanvas, RTL support etc.

Now you can create websites in Power Pages using Bootstrap v5 with this support. You can also migrate your existing websites running on Bootstrap v3 to v5 using the PAC CLI based migration tool provided by Power pages. The Bootstrap upgrade for Power Pages will enable you to leverage new components including CSS Flexbox and responsive layout.

### See list of Bootstrap v5 sites

You can see the newly created site from Power pages home page.

The Bootstrap v5 sites are at functional parity, but you might notice some UX changes based on Bootstrap v5 updates made in the recent releases. Changes include UX improvements like spacing, icons, edges of components like buttons, text etc.

You can view a list of the available sites in the Power Pages home page **My Sites** section. This list shows sites which are created on Bootstrap v3 and Bootstrap v5, whether the environment has been enabled for Bootstrap v5 or not.

### Templates supported

You can create a new site using the Power Pages home page with Bootstrap v5 once it is enabled for an environment.

The new site will be created using Bootstrap v5 only if it is supported by the selected template. Currently, all power pages templates are supported on Bootstrap v5. List of templates

1.  Blank template

2.  Starter layout 1

3.  Starter layout 2

4.  Starter layout 3

5.  Starter layout 4

6.  Starter layout 5

7.  Schedule and Manage meetings.

8.  Program Registration

9.  Application processing

You can opt-out of Bootstrap v5 site creation by disabling the **Enable Bootstrap v5 for new sites (preview)** option from top tool bar.