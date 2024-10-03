---
title: Debug your Power Pages site with the DevTools extension
description: Learn how to use the Power Pages DevTools browser extension to debug a Power Pages site.
author: nageshbhat-msft
ms.topic: conceptual
ms.custom: 
ms.date: 06/28/2024
ms.subservice:
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - DanaMartens
    - nageshbhat-msft
---

# Power Pages DevTools extension

The Power Pages extension for Microsoft Edge DevTools is a developer tool designed to enhance the development and troubleshooting experience for makers and administrators working on Power Pages sites. It offers features such as displaying Liquid tracing message and server-side error messages. With this tool, makers and administrators can efficiently identify, diagnose, and resolve issues within the Power Pages environment. By enabling logging and tracing capabilities in liquid code, as well as providing clear insights into error scenarios, the Power Pages extension facilitates smoother development workflows and enhances the overall quality of Power Pages sites.

> [!NOTE]
> The developer tool extension is currently only available for Microsoft Edge.

To work with the developer tools, you need to:

- Install the browser extension.
- Enable diagnostic setting.
- Review server-side error and follow mitigation details.
- View custom log messages added using Liquid code.

## Install the browser DevTools extension

To install the DevTools extension for Power Pages:

1. Go to [Microsoft Power Pages extension for Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2270261).
1. Select **Get**.

## Enable diagnostic setting

> [!NOTE]
> If your [site visibility](../security/site-visibility.md) status is private, the diagnostic setting is enabled by default.

To enable the diagnostic setting for a public website:

1. Open the [Power Pages Management App](portal-management-app.md).
1. Add or update the [Site Setting](configure-site-settings.md) with the name *UserTrace/Debug*.
1. Set the value to *true*.

## Review server-side error messages

When you enable the [diagnostic setting](#enable-diagnostic-setting), the platform logs any errors that occur on the server. To capture these server error messages, you need to:

1. Open the Microsoft Edge web browser.
1. Navigate to your Power Pages website.
1. Open the browser [DevTools](/microsoft-edge/devtools-guide-chromium/overview#open-devtools).
1. Select the **Power Pages** tab.

    :::image type="content" source="media/devtools-extension/devtools-extension-tab.png" alt-text="Screenshot of the Microsoft Edge DevTools with the Power Pages tab selected.":::

1. Reproduce the scenario where you encountered the error.

The tool displays a list of all server-side error messages along with probable resolutions.

> [!NOTE]
> Currently, you may only see a limited number of failure error messages. However, each subsequent release will include additional error messages for various types of failures.

The following are some example error messages:

- Error with Local sign-in provider if the LogonEnabled attribute is false for the Portal contact.

    :::image type="content" source="media/devtools-extension/devtools-error-example.png" alt-text="Screenshot of the Microsoft Edge DevTools with the Power Pages tab selected and an example error message displayed.":::

- Search for external entity isn't configured properly.

## Log custom messages with Liquid

Makers can add log statements in their [Liquid](liquid/liquid-overview.md) code. When the Power pages site is running, the logs added by maker in Liquid code are shown in the Power Pages developer tool extension. Learn more in [Available Liquid objects](liquid/liquid-objects.md#log).
