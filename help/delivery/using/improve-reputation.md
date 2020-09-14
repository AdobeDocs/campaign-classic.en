---
title: Improving your reputation when using Adobe Campaign Classic
description: Learn more about improving your reputation when using Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
---

# Improving your reputation{#improve-reputation}

To avoid exhausting your recipients, delete duplicate email addresses from your target. This step protects your sending reputation and ensures good quarantine management. Adobe Campaign offers the necessary tools to implement these recommendations and avoid the risk of being added to denylist by the ISP.

To avoid duplicates as much as possible, the following actions must be carried out:

* Imports must be configured carefully
* Pay attention when modifying email addresses
* Pay attention during automatic imports
* Profiles should be sorted into different folders

Quarantine management is presented in [this section](../../delivery/using/understanding-quarantine-management.md).

Below you will find details on duplicate and quarantine management.

You have the possibility to monitor the sent email volume by IP address. A schema extension is needed for this. You need to extend the broadlogs table to add the "public identifier" and create a workflow to extract and display the data. Contact Adobe if you need this.

## Duplicates {#duplicates}

Having duplicate email addresses can have multiple consequences:

* The same message being sent more than once. Even if Campaign performs a deduplication procedure by default before sending, there is nothing to stop the same message being sent by different actions having the same content when a target is split.
* Unsubscription requests not honored. If a recipient unsubscribes after receiving a message, their duplicate profile will still be eligible for future messages.

Besides this side-stepping of opt-in procedures, this situation will likely lead users to consider the messages as spam and to trigger a denylist procedure at the ISP.

You must be especially prudent when performing operations on the database:

* Imports must be meticulously configured, in particular when choosing the reconciliation key.
* Changed email addresses can also be a source of duplicates. In particular, two addresses with different domains may be routed to the same mailbox, for example in the case of a company that has changed name and has maintained the former domain for a certain period of time: joe.doe@amce-co.com and joe.doe@acme-rebranded.com.
* Automatic imports, whether they be of lists or from other databases are elements to be taken into account when managing profiles. What happens when you delete or move a profile in another partition? It might be recreated in the initial partition by an automatic import, for example, when a purchase order is placed.
* Storing profiles in different folders can be implemented using views rather than partitions. In this way, you are sure that the profiles are in the same physical partition while still enabling the adequate rights to be displayed and managed.

There are, all the same, cases in which duplicates between the different partitions are normal. For example, when sending for third-parties or different company entities, it is logical for the same person to be a recipient for different reasons. It is, however, rarely normal to find duplicates within the same partition.

## Quarantines {#quarantines}

Adobe Campaign manages a list of quarantined addresses. The recipients whose addresses are quarantined are excluded by default during the delivery analysis: they are not targeted. An email address can be quarantined for example when the inbox is full or if the address does not exist. In all cases, quarantining corresponds to the specific rules detailed below.

Quarantine management is presented in [this section](../../delivery/using/understanding-quarantine-management.md).