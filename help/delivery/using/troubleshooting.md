---
solution: Campaign Classic
product: campaign
title: Troubleshooting mobile devices
description: Learn how to troubleshoot mobile devices
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
---

# Troubleshooting{#troubleshooting}

If your mobile device is connected to Wi-Fi and you are not receiving notifications, check that the FCM/APNs ports are not being blocked by your firewall.

**Android**: The mobile device connects to the FCM servers on ports 5228 to 5230. You therefore must configure your firewall so that it authorizes connection with FCM. The ports to open are: 5228 (the most frequently used), 5229 and 5230.

**iOS**:

Binary connector: to send notifications, you must authorize inbound and outbound TCP traffic on port 2195. Devices connected to the push service must authorize inbound and outbound TCP traffic on port 5223.

HTTP/2 connector: you must allow communication to and from the following servers:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>For more information on the two connectors, refer to [Configure the mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
