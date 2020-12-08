---
solution: Campaign Classic
product: campaign
title: Get started with delivery monitoring
description: Learn more about Campaign Classic delivery monitoring capabilities.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
---

# Get started with delivery monitoring {#about-delivery-monitoring}

Monitoring your deliveries after they have been sent is a key step to ensure your maketing campaigns are efficient and reach out to your customers. In this section, you will learn more about the information you can monitor after sending a delivery, as well as understand how delivery failures and quarantines are managed.

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Monitor your deliveries**

The list of deliveries allows you to see all created deliveries into one single location. For each delivery, a dedicated dashboard is also available, allowing you to monitor various types of information and eventual issues encountered during the sending of messages: delivery reports, mirror pages, exclusions, tracking logs, rendering, etc.

* [Accessing the list of deliveries](../../delivery/using/list-of-deliveries.md)
* [Delivery dashboard](../../delivery/using/delivery-dashboard.md)

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Delivery performances best practices**

Several guidelines should be followed in order to ensure your deliveries perform well. Common issues you may encounter when sending deliveries, and how to troubleshoot them.

**<img src="assets/do-not-localize/icon_system.svg" width="60px">**

Understanding delivery failures
When a message (email, SMS, push notification) cannot be sent to a profile, the remote server automatically sends an error message, which is picked up by the Adobe Campaign platform and qualified to determine whether or not the email address or phone number should be quarantined. See Bounce mail management.

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Understanding quarantine management**

Adobe Campaign manages a list of quarantined addresses. Recipients whose address is quarantined are excluded by default during delivery analysis, and will not be targeted. An email address can be quarantined, for example, when the mailbox is full or if the address does not exist. In any case, the quarantine procedure complies with specific rules described below.

Delivery failure types and reasons
Retries
Bounce mail management

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**quarantines**

Adobe Campaign manages a list of quarantined addresses. Recipients whose address is quarantined are excluded by default during delivery analysis, and will not be targeted. An email address can be quarantined, for example, when the mailbox is full or if the address does not exist. In any case, the quarantine procedure complies with specific rules described below.

Identifying and manage quarantined addresses
Conditions for sending an address to quarantine
Soft error management
Push notification and SMS quarantines
