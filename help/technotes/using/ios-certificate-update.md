---
product: campaign
title: Technote - Apple Push Notification service server certificate update
description: Apple Push Notification service server certificate update
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
---
# Apple Push Notification service server certificate update {#apns-certificate-update}



On October 17, 2024, an Apple Push Notification service (APNs) infrastructure update impacted Adobe Campaign Classic iOS channel. An OS configuration change is **mandatory** to avoid iOS push channel outage.
 
Learn more about APNs changes [in this page](https://developer.apple.com/news/?id=09za8wzy).

As a hosted customer, no action is needed: Adobe has already incorporated the new root certificate to your environment.

As an on-premise/hybrid customer, you need to update your configuration to ensure a seamless transition **before February 24, 2025**.

To incorporate the new certificate, follow the steps below:

1. Download the **SHA-2 Root : USERTrust RSA Certification Authority certificate** root certificate [from this page](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. Check the AAA certificate is present in both your OS and JAVA trustores. If not, add it.

1. Restart Adobe Campaign Web Service:

    ```
    nlserver restart web
    ```
