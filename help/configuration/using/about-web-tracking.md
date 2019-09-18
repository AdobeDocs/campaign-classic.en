---
title: About web tracking
seo-title: About web tracking
description: About web tracking
seo-description: 
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
---

# About web tracking{#about-web-tracking}

In addition to standard tracking that shows the behavior of an internet user clicking on a link in an e-mail message, the Adobe Campaign platform lets you collect information on how internet users browse your website. This data collection is performed by the web tracking module.

When an internet user clicks a tracked link in an e-mail from a given delivery, the redirection server contacted deposits a session cookie containing the broadlog identifier (broadlogId) and the delivery identifier (deliveryId).

The web client then sends this cookie to the server each time the user visits a page containing a web tracking tag. This continues throughout the session, i.e. until the web client is closed.

The redirection server collects the following data in this way:

* URL of the page viewed, via an identifier sent as a parameter,
* the delivery from which the web page was visited, via the session cookie,
* identifier of the internet user who clicked, via the session cookie,
* additional information such as the business volume generated.

To track opens, a 0x0 tracking pixel/image, embedded at the bottom of the email, contains a link to the Adobe Campaign redirect server along with a unique code that is generated based on message ID, delivery ID, and trackingURL ID.

For more information on tracking, refer to the [Campaign Classic tracking guide](https://helpx.adobe.com/campaign/kb/acc-tracking.html) page.


The following diagram shows the stages of the dialog between the client and the various servers.

![](assets/d_ncs_integration_webtracking_structure1.png)
