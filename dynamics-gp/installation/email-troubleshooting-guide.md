---
title: Dynamics GP Email Troubleshooting Guide
description: Get tips and tricks about some of the errors you may run into when emailing out of Microsoft Dynamics GP.
keywords: "email"
author: theley502
manager: edupont
ms.prod: dynamics-gp
ms.topic: article
ms.reviewer: edupont
ms.author: theley
ms.date: 09/10/2021
---

# Microsoft Dynamics GP Email Troubleshooting Guide

This document is meant to walk through most of the errors you may run into when emailing out of Microsoft Dynamics GP.  

The goal is to make everyone an emailing expert!  

This document can be leveraged with all email functionality in Microsoft Dynamics GP, from the old Standard Report Writer Statement emailing method, to Word Templates.

> [!NOTE]
> Currently, TLS 1.0 and Basic Authentication (no MFA) are required for Exchange and Workflow emailing in Dynamics GP.
>
> We are aware of the changes that are coming to the supportability of TLS 1.0 and Basic Authentication within our other Microsoft applications. TLS 1.2 and Multi-Factor Authentication (MFA) functionality was included in the 18.3 update released.

All email issues can be safely split up into three sets of issues:

* Items unique to MAPI  
* Issues unique to Exchange  
* Those that both methods have in common  

This is how the documentation is organized: Starting with MAPI, moving onto Exchange, and ending with the common errors.  

Find system preferences under Dynamics GP Tools -> Setup -> System -> System Preferences.  

> [!IMPORTANT]
> This setting is stored in the DYNAMICS database and is system-wide, so changing this setting will affect all users.  

![Form](media/syspref.jpg)

## MAPI Specific Errors

### Dynamics GP uses MAPI to open Outlook to send emails directly from the Outlook client

Emails Stuck in Outbox within Outlook.  

Note: Issue appears to be unique to Gmail accounts.  

Issue:  
Emails are getting stuck in the Outbox in Outlook. 

When you use the Send/Receive button, or close/reopen Outlook, the email sends without delays. 

Cause: 
Add-in for Gmail Multi-factor authentication. This is a paid add-in that we believe causes the issue.  

Solution: 
Compare a clean Outlook add-in list to the client having the issue to make sure there are no extra add-ins. 
Recommend that they [remove the add-in as it appears like it is no longer needed](https://support.office.com/article/add-a-gmail-account-to-outlook-701916679c52-4581-990e-e30318c2c081)

### No default mail client, or the current mail client cannot fulfill the message request

Please run Microsoft Outlook and set it as the default mail client. 

Note: Recommend you review Outlook version first – MAPI only works with 32bit! 

Issue:  Error appears when attempting to email using MAPI anywhere in GP Cause: Either a Profile is not setup, or Outlook cannot reach it using MAPI.  

Solution: You can go through [this KB](https://support.microsoft.com/en-us/help/4052892/e-mail-error-in-microsoftdynamics-gp-either-there-is-no-default-mail), focus on A and B as these are common causes.  

You will want to make sure that Outlook is also set up as the default application for mail when you search for Default Apps in Windows 10.  