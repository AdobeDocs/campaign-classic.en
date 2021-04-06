---
solution: Campaign Classic
product: campaign
title: Collecting all visits
description: Collecting all visits
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
---
# Collecting all visits{#collecting-all-visits}

The web tracking module supplied by Adobe Campaign lets you collect the visits to certain pages of the site performed by a recipient in the context of site tracking following a click in a message.

You can, however, configure your platform so that it collects all visits to pages with a web tracking tag by a user known to the platform.

A user known to the platform is a recipient who has already been targeted by a delivery and who has clicked in a received message at least once. A permanent cookie is used to identify this recipient.

>[!IMPORTANT]
>
>The Adobe Campaign platform is not intended for use as a website tracking tool beyond the context of visiting the site following a click in a message. When this option is enabled, it can cause very high use of resources on the machines hosting your servers (redirection, application, and database). You are advised to ensure that your hardware architecture can support this load, and to avoid placing web tracking tags in the most frequently visited pages, such as the home page.

## Server configuration {#server-configuration}

The servers are configured by overloading certain elements of the **serverConf.xml** file. These files are saved in the **conf** subdirectory of the Adobe Campaign installation directory.

### Redirection server {#redirection-server}

For the redirection server, set the **trackWebVisitors** attribute of the **redirection** element to **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configuring a default matching campaign {#configuring-a-default-matching-campaign}

To view tracking information via your client console, you must:

* Create a **dummy delivery** (the delivery mapping must be identical to the mapping of the target schema),
* Enter the **internal name** of this delivery in the **NmsTracking_WebTrackingDelivery** option.

All site tracking information not directly subsequent to a click in an e-mail can be viewed in the dummy delivery created.
