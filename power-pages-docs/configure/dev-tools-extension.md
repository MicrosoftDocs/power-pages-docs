---
title: Debug with the DevTools Extension
description: Learn how to use the DevTools Extension for debugging a Microsoft Power Pages site.
author: nageshbhat-msft
ms.topic: conceptual
ms.custom: 
ms.date: 05/01/2024
ms.subservice:
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - DanaMartens
    - nageshbhat-msft
---

# Power pages site developer tool extension

The Power Pages extension for Microsoft Edge is a developer tool designed to enhance the development and troubleshooting experience for makers and administrators working on Power Pages sites. It offers features such as displaying Liquid tracing message and server-side error messages. With this tool, makers and administrators can efficiently identify, diagnose, and resolve issues within the Power Pages environment. By enabling logging and tracing capabilities in liquid code, as well as providing clear insights into error scenarios, the Power Pages extension facilitates smoother development workflows and enhances the overall quality of Power Pages sites.

> [!NOTE]
> Currently developer tool extension available only for Microsoft edge browser.

To work with the developer tools, you need to:

- Install the extension to browser
- Enable diagnostic setting
- Review server-side error and follow mitigations
- View the added custom log messages by using liquid object

## Install the Power Pages site developer tool

1. Go to [Microsoft Power Pages Addon for Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2270261)
1. Select **Get**.
1. Open browser developer console from the Power Pages site.

## Enable diagnostic setting

> [!NOTE]
> If your site visibility status is private, the diagnostic setting is enabled by default

To enable the diagnostic setting for a public website:

1. Open the [Power Pages Management App](portal-management-app.md).
1. Add or update the [Site Setting](configure-site-settings.md) with the name UserTrace/Debug.
1. Set the value to *true*.

## Review server-side error messages

When you enable the diagnostic setting, the platform logs any errors that occur on the server. To capture these server error messages, you need to open the browser developer extension and navigate to the Power Pages tab. Then reproduce the scenario where you encountered the error. The tool displays a list of all server-side error messages along with probable resolutions.

> [!NOTE]
> Currently, you may only see a limited number of failure error messages. However, each subsequent release will include additional error messages for various types of failures.

For example:

- Error while Local login if LogonEnabled attribute is false for Portal contact.
- Search for external entity is not configured properly.

## Log custom messages using Liquid

Makers can add log statements in their [Liquid](liquid/liquid-overview.md) code. When the Power pages site is running, the logs added by maker in Liquid code are shown in the Devtool extension. Makers have the ability to incorporate log statements within their Liquid code. These logs, embedded by the maker, are displayed in the Developer tool extension when diagnostic is enabled.

Syntax of liquid log:

`{% log message:'Custom message' level:'Warning' %}`

|Parameter  | Description  |
|---------|---------|
|log     | Liquid object name |
|message     | string representing any custom messages to be shown in the tool |
|level     | log the message as 1 (Info), 2 (Warning), or 3 (Error)      |

Example:

```xml
{% log message: 'Log from Home page' %}

{% fetchxml query %}
<fetch version="1.0" mapping="logical" >
<entity name="cr441_employee">
<attribute name="cr441_employeeid"/>
<attribute name="cr441_name"/>
</entity>
</fetch>
{% endfetchxml %}

{% assign emps = query.results.entities %}

{% for emp in emps %}
<div> Employee name: {{emp.cr441_name}} </div><br/>
{% capture msgg %} 
Employee id is {{ emp.id }} for employee name {{emp.cr441_name}}
{% endcapture %}
{% log message: msgg %}
{% endfor %}
```
