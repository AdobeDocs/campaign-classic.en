---
product: campaign
title: Technote - Apple Push Notification service server certificate update
description: Apple Push Notification service server certificate update
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
TQID: 'https://experienceleague.adobe.com/3tQ4npyE0-ZfCgVPYy3kiRv1q0HPcq-DI4rpAXTCXb0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: ab81f6c3-9317-564f-af92-6670a8784294
    internal-label: Technote
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
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
