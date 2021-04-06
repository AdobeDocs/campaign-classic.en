---
solution: Campaign Classic
product: campaign
title: About transactional messaging
description: Send trigger messages based on events generated from information systems. 
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
---
# About transactional messaging{#about-transactional-messaging}

Transactional messaging (Message Center) is a Campaign module designed for managing trigger messages. These messages are generated from events triggered from information systems, and can be: invoice, order confirmation, shipping confirmation, password change, product unavailability notification, account statement or website account creation for instance.

>[!IMPORTANT]
>
>Transactional messaging requires a specific licence. Please check your licence agreement.

Adobe Campaign Message Center module is integrated into an information system which returns events to be changed into personalized transactional messages. These messages can be sent individually or in batches via email, SMS or push notifications.

In this specific architecture, execution cell is separated from the control instance, which ensures higher availability and better load management.

>[!NOTE]
>
>To create new users for Message Center execution instances hosted on Adobe Cloud, you need to contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Message Center users are specific operators that require dedicated permissions to access 'Real time events' (nmsRtEvent) folders.
