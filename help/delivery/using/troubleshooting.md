---
product: campaign
title: Push Troubleshooting
description: Push Troubleshooting
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
TQID: https://experienceleague.adobe.com/3T6eC52Edyai-8Bn-ioDxvB5C04iDqBNmlZzuxVturE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
---
# Troubleshooting{#troubleshooting}

If your mobile device is connected to Wi-Fi and you are not receiving notifications, check that the FCM/APNs ports are not being blocked by your firewall.

**Android**: The mobile device connects to the FCM servers on ports 5228 to 5230. You therefore must configure your firewall so that it authorizes connection with FCM. The ports to open are: 5228 (the most frequently used), 5229 and 5230.

**iOS**:

HTTP/2 connector: you must allow communication to and from the following servers:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>For more information on the two connectors, refer to [Configuring the mobile application in Adobe Campaign](configuring-the-mobile-application.md).
