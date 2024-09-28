---
title: Implement privacy protections
description: Learn how to implement privacy protections in Power Pages. Identify minor users, get parental consent, and have site users agree to terms and conditions.
author: sandhangitmsft
ms.topic: conceptual
ms.custom: 
ms.date: 5/11/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - sandhangitmsft
---

# Implement privacy protections

As an administrator, you can configure your Power Pages sites to implement privacy protections.

The settings described in the documentation are general capabilities to support user privacy on Power Pages websites and can be useful when planning for compliance with the applicable standard regulations.

## Audit logging

The **Last Successful Sign-in** field in the contact record shows when a user has last signed in. The date is picked up by an audit of the contact record and makes that information available in the standard audit stream, allowing the administrator to see inactive community members and delete their records.

> [!NOTE]
> The login tracking feature has been deprecated. It's recommended to use an analytics technology like Azure Application Insights to capture this kind of information. To see the list of deprecated features, click [here](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/).

## Identifying minor users and obtaining parental consent

Regulations for identifying minor users vary by country/region. Because a minor can only access the page with parental consent, you can configure the page to identify minors using these fields in the contact record:

- **Is Minor**: Indicates that the contact is considered a minor in their jurisdiction. By default, **No** is selected.
- **Is Minor with Parental Consent**: Indicates that the contact is considered a minor in their jurisdiction and has parental consent. By default, **No** is selected.

The following site settings control the use of Power Pages by minors and minors without parental consent:

| Name  | Description   |
|-----------------------|------------------------------------------|
| Authentication/Registration/DenyMinors  | Denies use of the site by minors. By default, this value is set to false.                          |
| Authentication/Registration/DenyMinorsWithoutParentalConsent | Denies use of the site by minors without parental consent. By default, this setting is set to false. |
|||

If a site user is determined to be a minor and the site is configured to block minors, an appropriate message appears and content isn't shown.

If a site user is determined to be a minor without parental consent, and the site is configured to block minors without parental consent, an appropriate message appears and content isn't shown.

The following content snippets control messages that appear when the site is used by minors and minors without parental consent. You can change the message according to your requirements.

| Name                                                        | Type | Value                                                                    |
|-------------------------------------------------------------|------|--------------------------------------------------------------------------|
| Account/Signin/MinorNotAllowedHeading                       | Text | Age Requirements                                                         |
| Account/Signin/MinorNotAllowedCopy                          | HTML |  |
| Account/Signin/MinorWithoutParentalConsentNotAllowedHeading | Text | Parental Consent                                                         |
| Account/Signin/MinorWithoutParentalConsentNotAllowedCopy    | HTML |           |
|||

When someone registers using an external provider and the webpage is configured to block minors or minors without parental consent, the contact record isn't created, and the user isn't authenticated.

## Agreeing to terms and conditions

Some privacy laws and regulations may require users to agree to the terms and conditions to allow marketing, profiling, or access to private information. As an administrator, you can publish your own terms and conditions to get consent of the user before they're authenticated to the site.

The following content snippets control the display of terms and conditions on the screen. You can change the text according to your requirements.

| Name                                           | Type | Value                                 |
|------------------------------------------------|------|---------------------------------------|
| Account/Signin/TermsAndConditionsHeading       | Text | Terms and Conditions                  |
| Account/Signin/TermsAndConditionsCopy          | HTML |                                       |
| Account/Signin/TermsAndConditionsAgreementText | Text | I agree to these terms and conditions. |
| Account/Signin/TermsAndConditionsButtonText    | Text | Continue                              |
|||

The `Account/Signin/TermsAndConditionsCopy` content snippet is empty by default. An administrator must enter the terms and conditions to be displayed in this content snippet.

The following site settings control the terms publication date and whether the terms should be displayed:

| Name  | Description |
|------------|---------------|
| Authentication/Registration/TermsPublicationDate  | A date/time value (GMT) to represent the effective date of the current published terms and conditions. If the terms agreement is enabled, users that haven't accepted the terms after this date will be asked to accept them the next time they sign in. If the date isn't provided, and the terms agreement is enabled, the terms are presented every time users sign in. <br /> **Note**: If you want a user to agree to the terms and conditions every time they sign in, don't provide a value for this site setting.|
| Authentication/Registration/TermsAgreementEnabled | A true or false value. If set to true, the page displays the terms and conditions of the site. Users must agree to the terms and conditions before they're considered authenticated and can use the site. By default, this value is set to false.        |
|||

The following field is added in the contact record to store the date and time a user agreed to the terms and conditions:
- **Terms Agreement Date**: Indicates the date and time the user agreed to the terms and conditions.
