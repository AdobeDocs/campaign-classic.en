---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: no
hidefromtoc: yes
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
---
# Apple Push Notification service server certificate update {#apns-certificate-update}

On March 29 2021, an Apple Push Notification service (APNs) infrastructure update will impact Adobe Campaign Classic iOS channel. An OS configuration change is **mandatory** to avoid iOS push channel outage.
 
Learn more about APNs changes [in this page](https://developer.apple.com/news/?id=7gx0a2lp).

As a hosted customer, no action is needed: Adobe has already incorporated the new root certificate to your environment.

As an on-premise/hybrid customer, you need to update your configuration to ensure a seamless transition **before March 29 2021**.

To incorporate the new certificate, follow the steps below:

1. Download the **AAACertificateServices 5/12/2020** root certificate [from this page](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Check the AAA certificate is present in both your OS and JAVA trustores. If not, add it.

1. Restart Adobe Campaign Web Service:

    ```
    nlserver restart web
    ```
