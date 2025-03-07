---
title: FAQ on managing cases
description: Learn about the frequently asked questions (FAQ) on the different features in case management.
ms.date: 06/06/2023
ms.topic: concept
author: gandhamm
ms.author: mgandham
ms.reviewer: neeranelli
ms.custom: bap-template
---

# FAQ on managing cases

A few answers to common questions on the various scenarios in managing cases are listed here.

## General

### How can I create a case when the contact isn't linked to the customer organization?

Out of the box, agents can't create a case because the contact isn't associated with the customer organization. However, you can [customize case forms and remove the validation on contact](remove-validation-contact.md) and allow unrelated contacts be linked with the case. 

### Why can I use only few columns to search in the Case view?

 To search on columns of your choice, make sure that the quick find search is configured for the required search parameters. More information: [Use quick find search](/power-platform/admin/configure-relevance-search-organization#select-searchable-fields-and-filters-for-each-table).

### Why do agents get permission errors when they try to access, create, delete, or update a case?

If the role assigned to agents is missing security privileges, permission errors are displayed when they perform case actions. For example, the following error is displayed when an agent tries to access a case, and the role assigned to the agent is missing read privileges:

Principal user (Id= \<GUID>, type=8, roleCount=5, privilegeCount=465, accessMode=0), is missing prvReadincident privilege (Id=\<GUID>) on OTC=112 for entity 'incident'. context.Caller=\<GUID>

To resolve the error, ensure that role assigned to the agent has read access to the case entity. More information, see: [Security roles and privileges](/power-platform/admin/security-roles-privileges). You can also refer to the out-of-the-box Customer Service Representative role before you create custom roles or modify permissions of roles assigned to agents. More information: [Roles and personas](role-persona-mapping.md)


## FAQ on resolving cases

### Why can't I see Billable time, Remarks, or Total time fields on the case resolution dialog box?

As part of April 2023 wave, by default, agents see the minimal case resolution dialog. The minimal case resolution dialog displays the **Resolution Type** and **Resolution** only. You can disable the minimal case resolution dialog and switch to the legacy experience. More information: [Disable the minimal case resolution dialog](add-enhanced-case-management.md#disable-the-minimal-case-resolution-dialog). 

   > [!NOTE]
   > - You can revert to the legacy case resolution dialog only if the **Case settings** > **Other settings** > **Resolve case dialog** is set to **Standard dialog** in Customer Service admin center.
   > - If **Resolve case dialog**  is set to **Customizable dialog** or **Quick create dialog**, to add **Duration**, **Billable Time**, **Total Time** and other customizations, perform the steps in [Add or remove fields from the case resolution dialog](modify-case-resolution-dialog.md#add-or-remove-fields-from-the-case-resolution-dialog).


### Can I update cases after they're resolved or canceled?

Yes, agents can update the case description or other information after the case has been resolved or canceled. You must configure and run flows in Power Automate or an API to update the case without having to reopen the case records. More information: [Allow updates for resolved and canceled cases](update-resolved-canceled-cases.md).

### Why isn't the billable time isn't automatically updated on the case resolution dialog? 

Billable time is the amount of time the agent spent on the case and can be billed to the customer. The application automatically calculates and displays the **Billable Time** value on the case resolution dialog, only if the **Total Time** field is also available on the dialog. If **Total Time** isn't displayed, agents have to manually add the billable time. More information: [Add or remove fields from the case resolution dialog](modify-case-resolution-dialog.md#add-or-remove-fields-from-the-case-resolution-dialog).

### Can I customize the case resolution dialog?

Yes. More information: [Modify the case resolution dialog](modify-case-resolution-dialog.md).

### Why can't I see the custom value I added to Case resolution type field in the case resolution dialog?

Make sure that you've added the custom value to both the **Case** and **Case Resolution** entity for the custom value to be displayed on the case resolution dialog. More information: [Add custom values to the case resolution dialog](modify-case-resolution-dialog.md#add-custom-values-to-the-case-resolution-dialog).

### Why can't I set the Case Status field on a case to Resolved?

A case is resolved only when you select **Resolve case** on the command bar. You can't set the value of the **Case Status** field to **Resolved**. More information: [Resolve a case](customer-service-hub-user-guide-resolve-cancel-reassign-a-case.md#resolve-a-case).

### Why do I see errors when I try to resolve a case?

 Resolve a case isn't supported if **Regarding** is configured in **Case resolution dialog**, and agents will see errors if they try to resolve the case.

## Enhanced case experience

### I used the form selector on the Enhanced full case form to navigate to another form. Why can't I go back to the enhanced form?

The **ShowInFormSelector** option in Enhanced full case form is set to **False**, by default.  Set **ShowInFormSelector** to **True**, to see the **Enhanced full case form** option in the form selector and navigate back to it.

### Why are agents seeing the Enhanced case form when they create a case even if I haven't enabled Enhanced case experience?

If the **Enhanced full case form** has a higher form order than the default case form, agents might see the enhanced full case form even if you haven't enabled the enhanced case experience. If you'd like agents to see the default case experience, set the form order of the enhanced form lower than that of the default form. More information: [Control access to model-driven app forms](/power-apps/maker/model-driven-apps/control-access-forms#set-the-form-order).

### Why do my existing cases open in the default case form when I've enabled the enhanced case experience?

You must set the **Enhanced full case form** as the default form for your agents to see the enhanced full case form when they open an existing case. More information: [Control access to model-driven app forms](/power-apps/maker/model-driven-apps/control-access-forms).

## Resolve form issues

### How can resolve the discrepancies in the number of buttons displayed on the command bar and ribbon issues in my case form?

If agents see buttons being hidden or extra buttons displayed on the form, you can use the [**Command Checker**](https://powerapps.microsoft.com/blog/introducing-command-checker-for-model-app-ribbons/) tool to troubleshoot the issue and also see what command will run when a button is clicked.

You can follow the steps in [Troubleshooting ribbon issues in Power Apps](/troubleshoot/power-platform/power-apps/create-and-use-apps/ribbon-issues) to resolve ribbon issues.

### How can I identify and resolve form issues effectively?

Form issues occur because of business rules, JavaScript, form events, or client API that administrators and makers have set. Monitor is a tool that can help you debug and diagnose problems, and can also help identify whether the issue experienced is designed out-of-the-box or due to a customization. More information: [Use Monitor to troubleshoot model-driven app form behavior](/power-apps/maker/model-driven-apps/monitor-form-checker).
