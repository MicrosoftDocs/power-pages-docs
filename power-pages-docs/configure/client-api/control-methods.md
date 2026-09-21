---
title: Client API Controls Reference (Preview)
description: Explore Power Pages Client API controls and methods for managing form values, states, visibility, requirements, and client-side validation.
author: neerajnandwana-msft
ms.author: nenandw
ms.reviewer: jdaly
ms.date: 09/21/2026
ms.topic: reference
ai.usage: ai-assisted
contributors:
- JimDaly
---
# Client API controls (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Power Pages Client API controls implement the `Control` interface, which provides common methods for managing form values, states, visibility, requirements, and validation. Use this reference to identify available methods and return types. For control-specific value types and additional members, see [Client API control types](controls.md).

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

| Method | Returns | Description |
|--------|---------|-------------|
| `getDisabled()` | `boolean` | Returns `true` if the control is disabled; otherwise, returns `false`. |
| `getRequired()` | `boolean` | Returns `true` if the control is required; otherwise, returns `false`. |
| `getVisible()` | `boolean` | Returns `true` if the control is visible; otherwise, returns `false`. |
| `getName()` | `string` | Returns the control's name. |
| `getType()` | `string` \| `undefined` | Returns the control type, such as `MultiSelectPicklist`, or `undefined` when the type isn't available. See [Client API control types](controls.md). |
| `getLogicalName()` | `string` \| `undefined` | Returns the control's logical name or `undefined` when the logical name isn't available. |
| `getValue()` | Varies | Retrieves the current value. The return type depends on the [control type](controls.md). |
| `setDisabled(isDisabled: boolean)` | `void` | Sets the disabled state of the control. |
| `setRequired(isRequired: boolean, errorMessage?: string)` | `void` | Sets the required state of the control. For more information, see [setRequired method parameters](#setrequired-method-parameters). |
| `setVisible(isVisible: boolean)` | `void` | Sets the visibility of the control. |
| `setValue(value)` | `void` | Sets a new value. The expected value type depends on the [control type](controls.md). |
| `addValidator(id: string, evaluationFn: function, errorMessage: string)` | `void` | Registers a custom client-side validator on this control instance. For more information, see [addValidator method parameters](#addvalidator-method-parameters). |
| `removeValidator(id: string)` | `void` | Removes a custom validator by its ID from this control instance. It does nothing when the ID doesn't exist. |
| `clearValidators()` | `void` | Removes all custom validators added to this control instance with `addValidator`. It doesn't affect the required validator that `setRequired` manages. |

## setRequired method parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `isRequired` | boolean | Specifies whether the control is required. |
| `errorMessage` | string (optional) | The localized validation message. The default is `<field name> is a required field.` |

When `isRequired` is true, the client API registers a validator that runs when the form is submitted. When it's false, the validator is removed. You can't make a control optional when it's marked as required on the server.

## addValidator method parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | A unique identifier on the current control instance. A new validator with the same ID replaces the existing validator. |
| `evaluationFn` | function | Receives the control value and returns true when the value is valid. |
| `errorMessage` | string | The message that appears in the validation summary when validation fails. |

> [!IMPORTANT]
> Keep and reuse the same `Control` object instance when you replace or remove validators. Each access to `form.controls` and each call to `getControlByLogicalName` returns a new control facade.

If the evaluation function or the `getValue` method throws an error, validation fails and the browser console records the error.

```javascript
Microsoft.PowerPages.onPagesClientApiReady(async function ($pages) {
    const form = $pages.currentPage.forms.getFormById('form_#1');
    const control = form.getControlByLogicalName('new_keyword');

    control.setRequired(true, 'This field is mandatory.');
    control.addValidator(
        'keywordCheck',
        (value) => ['alpha', 'beta', 'gamma'].includes(value),
        'Value must be one of: alpha, beta, gamma.'
    );
});
```

## Related information

- [Client API overview](index.md)
- [Client API examples](examples.md)
