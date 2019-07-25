---
title: Messaging server
seo-title: Messaging server
description: Messaging server
seo-description: 
page-status-flag: never-activated
uuid: c074d372-c111-4035-bb33-3d83b7bcf9c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 20119432-54aa-4b95-9146-b67ed63b6708
index: y
internal: n
snippet: y
---

# Messaging server{#messaging-server}

 Adobe Campaign handles outbound email natively, however a traditional email server is required to receive incoming messages linked to returned email (from mailer daemons). The mailboxes configured on this server will be automatically processed by the application.

All servers configured for POP3 access can be used to receive return mail if they preserve the SMTP "Message-ID" headers when picking up the mail. For example, implementations using Qmail, SendMail and Microsoft Exchange are currently in production. However, some installations of Lotus Notes/domino revealed an issue with the maintaining of "Message-Id" headers.

>[!CAUTION]
>
>This mail server may have to handle heavy loads: In initial phases, typical lists can produce up to 10% bounce rates (if you send 100,000 messages, expect to receive 10,000 bounces).   
>That's why we recommend against using your company messaging server for this task as it can be strongly impacted.  
>It is advisable to configure a specific sub-domain of your DNS and a dedicated server for bounce mail.

