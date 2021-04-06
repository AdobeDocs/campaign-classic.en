---
solution: Campaign Classic
product: campaign
title: Define the right audience
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: c0533148-b027-4158-9b95-8d2df769e963
---
# Define the right audience {#define-the-right-audience}

Targeted population is key: build your lists carefully, test your emails on popular email clients and mobile devices, and ensure that your email lists are up-to-date (with no unknown or obsolete addresses). You can also send proofs that help set up a complete validation cycle.

Learn more about target populations [in this section](../../delivery/using/steps-defining-the-target-population.md)

## Target the right audience {#target-the-right-audience}

When you have your content ready, you need to carefully define who will receive your message.

To make your delivery successful, you want to send the most relevant personalized content to the right recipients. Adobe Campaign enables you to build the most accurate target: you can select recipients according to their age, localization, what they bought, if they clicked a link in a previous delivery, etc. With Adobe Campaign, you can also define test profiles, control groups and seed addresses to make sure your target is correct.

## Target mappings {#target-mappings}

In Campaign Classic, by default, delivery templates target **Recipients**. Adobe Campaign offers other target mappings for your deliveries, that you can change based on your needs.

For example, you can deliver to visitors whose profiles have been collected via social networks or to visitors who are subscribed to an information service.

These mappings are presented [in this section](../../delivery/using/selecting-a-target-mapping.md).

You can also create and use a customized target mapping. For more on this, refer to [this section](../../configuration/using/target-mapping.md).

## External recipients {#external-recipients}

You can deliver to recipients who are stored in an external file rather than saved in the database. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## Send to your subscribers {#send-to-subscribers}

To send messages to the subscribers of a newsletter, you can directly target the subscribers to the corresponding information service. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Test recipients and seed addresses {#test-recipients-seed-addresses}

To test your delivery, use proofs before sending to the main target.

Make sure you select appropriate proof recipients, because they validate the form and the content of the message. The steps for defining the proof recipients are presented [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Seed addresses are used to target recipients who do not match the defined target criteria in order to test a delivery before sending to the main target. They are presented [in this section](../../delivery/using/about-seed-addresses.md).

## Deduplicate addresses {#deduplicate-addresses}

It is important to avoid having duplicate email addresses, because this can have an impact on your target:

* The same message can be sent more than once when a target is split.

* If a recipient unsubscribes after receiving a message, their duplicate profile will still receive future messages.

Deduplicating addresses protects your sending reputation and ensures good quarantine management.

**Related topics:**

* [Deduplication activity](../../workflow/using/deduplication.md).
* [Use case: Using the Deduplication activity's merge functionality](../../workflow/using/deduplication-merge.md)

## Index email addresses {#index-addresses}

To optimize the performance of the SQL queries used in the application, an index can be declared from the main element of the data schema.

The steps for adding an index to the email address are presented [in this section](../../configuration/using/database-mapping.md#indexed-fields).
