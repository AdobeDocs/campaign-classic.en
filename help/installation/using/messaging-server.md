---
product: campaign
title: Messaging server
description: Messaging server
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
---
# Messaging server{#messaging-server}



 Adobe Campaign handles outbound email natively, however a traditional email server is required to receive incoming messages linked to returned email (from mailer daemons). The mailboxes configured on this server will be automatically processed by the application.

All servers configured for POP3 access can be used to receive return mail if they preserve the SMTP "Message-ID" headers when picking up the mail. For example, implementations using Qmail, SendMail and Microsoft Exchange are currently in production. However, some installations of Lotus Notes/domino revealed an issue with the maintaining of "Message-Id" headers.

>[!CAUTION]
>
>This mail server may have to handle heavy loads: In initial phases, typical lists can produce up to 10% bounce rates (if you send 100,000 messages, expect to receive 10,000 bounces).
>
>That's why we recommend against using your company messaging server for this task as it can be strongly impacted.
>
>It is advisable to configure a specific sub-domain of your DNS and a dedicated server for bounce mail.
