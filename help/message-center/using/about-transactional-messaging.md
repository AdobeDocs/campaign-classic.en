---
title: About transactional messaging
seo-title: About transactional messaging
description: About transactional messaging
seo-description: 
page-status-flag: never-activated
uuid: 26404226-d9d0-40ec-b00a-ed610d20532a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
topic-tags: introduction
discoiquuid: 74d9b637-f805-4df6-939b-c5b67ceb7a1e
index: y
internal: n
snippet: y
---

# About transactional messaging{#about-transactional-messaging}

Transactional messaging (Message Center) is a Campaign module designed for managing trigger messages. These messages are generated from events triggered from information systems, and can be: invoice, order confirmation, shipping confirmation, password change, product unavailability notification, account statement or website account creation for instance.

Adobe Campaign Message Center module is integrated into an information system which returns events to be changed into personalized transactional messages. These messages can be sent individually or in batches via email, SMS or push notifications.

In this specific architecture, execution cell is separated from the control instance, which ensures higher availability and better load management.

>[!NOTE]
>
>To create new users for Message Center execution instances hosted on Adobe Cloud, you need to contact Adobe Customer Care. Message Center users are specific operators that require dedicated permissions to access 'Real time events' (nmsRtEvent) folders.

