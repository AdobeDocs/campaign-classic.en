---
product: campaign
title: About web tracking
feature: Configuration, Instance Settings
description: About web tracking
role: User, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
TQID: 'https://experienceleague.adobe.com/FfA6FEH5WP2JJGVR4BhpjO19Yj4mt8irvyJLwuzCThs'
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
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# About web tracking{#about-web-tracking}

In addition to standard tracking that shows the behavior of an internet user clicking on a link in an email message, the Adobe Campaign platform lets you collect information on how internet users browse your website. This data collection is performed by the web tracking module.

When an internet user clicks a tracked link in an email from a given delivery, the redirection server contacted deposits a session cookie containing the broadlog identifier (broadlogId) and the delivery identifier (deliveryId).

The web client then sends this cookie to the server each time the user visits a page containing a web tracking tag. This continues throughout the session, i.e. until the web client is closed.

The redirection server collects the following data in this way:

* URL of the page viewed, via an identifier sent as a parameter,
* the delivery from which the web page was visited, via the session cookie,
* identifier of the internet user who clicked, via the session cookie,
* additional information such as the business volume generated.

The following diagram shows the stages of the dialog between the client and the various servers.

![](assets/d_ncs_integration_webtracking_structure1.png)
