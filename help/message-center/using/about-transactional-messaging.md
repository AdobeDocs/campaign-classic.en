---
title: About transactional messaging
seo-title: About transactional messaging
description: About transactional messaging
seo-description: 
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
---

# About transactional messaging{#about-transactional-messaging}

Transactional messaging (Message Center) is a Campaign module designed for managing trigger messages. These messages are generated from events triggered from information systems, and can be: invoice, order confirmation, shipping confirmation, password change, product unavailability notification, account statement or website account creation for instance.

>[!CAUTION]
>
>Transactional messaging requires a specific licence. Please check your licence agreement.

Adobe Campaign Message Center module is integrated into an information system which returns events to be changed into personalized transactional messages. These messages can be sent individually or in batches via email, SMS or push notifications.

In this specific architecture, execution cell is separated from the control instance, which ensures higher availability and better load management.

>[!NOTE]
>
>To create new users for Message Center execution instances hosted on Adobe Cloud, you need to contact Adobe Customer Care. Message Center users are specific operators that require dedicated permissions to access 'Real time events' (nmsRtEvent) folders.
