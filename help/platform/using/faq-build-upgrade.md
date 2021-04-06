---
solution: Campaign Classic
product: campaign
title: Build upgrade FAQ
description: Common questions related to Campaign build upgrades
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 85e2135d-a1a3-44f0-a4f9-de38db5c8726
---
# Build Upgrade FAQ {#build-upgrade-faq}

Adobe Campaign is regularly updated. If you are familiar with our published [Release Notes](../../rn/using/rn-overview.md), you are probably aware of the fact that on the average 2/3 minor versions packed with new features, improvements and fixes are released every year. In addition, we periodically release builds with cumulative fixes only. This regular cadence of updates aims at getting the latest and greatest in your hands, keeping your environment fully secure and obviously improving your experience with our product.

It is critical that our customers run the most recent version of Adobe Campaign. It also allows Adobe to help much more efficiently in case you run into issues – identifying, reproducing and fixing an issue on an old build typically takes more time, not to mention that some issues you may encounter may very well have already been fixed in a recent build.

[!DNL Gold Standard] is Campaign Classic Long-Term support release. As a hosted [!DNL Gold Standard] user, you automatically benefit from the [!DNL Gold Standard] upgrade with the latest stable version without any action. On-premise and Hybrid customers can also benefit from [!DNL Gold Standard] releases. If you migrate from an old build, we recommend that you upgrade to this version first. [Learn more](../../rn/using/gs-overview.md).

## What is a build upgrade?

A Build Upgrade is when the Adobe Campaign Classic software is updated to the latest secure build number, yet stays in the same major/minor build Level. For example: Campaign Classic v7 build 9026 to Campaign v7 build 9032. 

Learn more [in this section](../../rn/using/rn-overview.md).

## What is the latest version of Adobe Campaign Classic?

The latest Campaign Classic version, including new features and documentation, is detailed in the latest [Release Notes](../../rn/using/latest-release.md).

## How do I know which version I am running?

Check your version from **[!UICONTROL Help > About...]** menu in the Adobe Campaign Client console. The **[!UICONTROL About]**  box contains detailed information on the version and build you are running both for the console and the server. 

Learn more [in this section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## What does the build status mean?

Starting Campaign Classic 19.2, a status is associated to each build.

Learn more [in this section](../../rn/using/rn-overview.md).

## Is a build upgrade the same thing as a version upgrade?

No. A build upgrade is an incremental update within a given major version, whereas a version upgrade is a change from one major version to another. Build upgrades are straightforward as they do not typically involve any major architectural, technical or data model changes.

Version upgrades on the other hand usually come with significant technical changes and, depending on the depth of the configuration for a given customer, may require significant configuration changes and/or partial re-implementation.

For instance, using the server information from the screenshot in the previous section:

*  A build upgrade would involve moving from build 6880 to any build greater that 6880. For example, v6.1.1 build 8222 to v6.1.1 build 8666

* A version upgrade would involve moving from version 6.0.2 to any version greater than 6.0.2.  For example: v6.0.1 build 2222 to v6.1.1 build 8666

## Should I backup my data prior to these updates?

Adobe will take a backup of your system prior to any changes. However, if there is critical customization work that is in your non-production system (development or staging servers), it is HIGHLY RECOMMENDED you export that work as a package prior to any upgrade.

![](assets/do-not-localize/how-to-video.png) For more information, [watch this how to video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## When will the upgrades take place?

Customers will be offered a date range to choose from. Production system changes are not performed on holidays.

Build upgrades can be done from Monday to Thursday, and Fridays are only used for non-production instances. 

## How long will the build upgrade take?

The time required to perform a build upgrade is dependent on several factors:

* The size of the database to be backed up or restored (larger databases require more time to upgrade)
* The size of the environments (many of our customers have several different servers that each handle specific functions, with larger environments requiring more time to upgrade)
* The complexity of the system (some systems have more dependent services and connections to verify, necessitating verification of the stability and performance of such systems)

Build upgrade is a two-step process:

1. Preparing the system for upgrade - Taking into account the specificities of your environment, this phase leads essentially to a fully qualified upgrade on a non-production environment. Once the upgraded environment has been greenlighted from a technical and functional standpoint, phase 2 can happen. This first phase, depending on the aforementioned factors, can take from a few days to a couple of weeks.

1. The upgrade itself - The production environment is upgraded. This phase is usually performed in a few hours. For very complex environments a longer downtime should be expected. In the event that something goes wrong, a rollback strategy is defined and can be executed.

For more information, [refer to this document](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html). 

## What resources are needed for the build upgrade?

The build upgrade process requires the following resources:

* Adobe Architect -  For hosted or cloud messaging/hybrid architectures, the architect must coordinate with Customer Care.
* Project Manager -  Hosted: the hosting team will partner with the Customer Care team and the customer to coordinate the upgrade timeline for all instances.
* Adobe Campaign Administrator - Hosted: the hosting team performs the upgrade.
* Adobe Campaign operator\marketing user -  The operator runs tests on development, test and production instances.

## How can I prepare for the build upgrade?

In your development and staging systems, export any work that is critical and must be preserved. For more information please [watch this how to video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Refresh your knowledge of the critical path workflows and deliveries developed in your run books (or by your consulting team/partner) by reviewing the documentation provided to your team at the end of your implementation.

Identify low volume or low traffic times that would be ideal for maintenance windows as they will produce the lowest business impact.

Review our [build upgrade checklist below](#check-list) and your test plans and ensure that resources who can perform these tests are available within 24– 48 hrs. of the completion of an upgrade.

For more information, [refer to this document](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html). 

## Can build upgrades be performed at night or during business off-hours?

Upgrades can be performed off-hours. It is always recommended to upgrade the environment during business off-hours when no business users are connected to the instance.    

## What are the costs associated with a build upgrade?

There is no cost to install the build upgrade for hosted Customers. If there are custom developments in the system, the Customer will need to identify resources needed to test those developments post upgrade and to correct any issues found with those custom developments.    

## Will there be access to the instance during the upgrade process?

No. The server is shutdown during an upgrade to ensure that the data integrity is preserved while the product is upgraded. Once completed, it is restarted, and all services resume.    

## Will the emails continue to be sent from Message Center during the upgrade process?

When the upgrade happens for Message Center (RT), it will not send emails from the instance. Note, any processes that are stopped when a Campaign system is shut down are automatically resumed when the system is re-started. This includes active or scheduled deliveries, tracking, and metrics calculations for previously sent deliveries.    

## Will the workflows continue to run and send the deliveries?

No. During build upgrade, workflow and mail services are both stopped. This means workflows will not run and deliveries are not sent. They will resume once the system is restarted. However, Adobe strongly advises that all critical path workflows be checked after an upgrade to ensure that they’re running and healthy.

## Will my tracking links still work during the upgrade?

Tracking links will work during the upgrade. New emails cannot be sent during the upgrade but tracking links included in already sent emails will be operational.  

## Do I need to be available during the build upgrade process?

Yes. Customers should provide Adobe with a point of contact available during or immediately after the upgrade of their production instance.  Adobe will contact this person via email unless other arrangements are made. This will ensure a smooth transition and immediate validation of critical tasks. Adobe will contact the Customer once the build upgrade is complete for confirmation.  

## Do I need to update the client console?

Yes. The client console must be on the same build as the server instance. Once the upgrade has been completed, your client console should prompt you to upgrade to the latest build to ensure that it stays aligned with the server build.    

## What is the rollback plan? Are backups of my data kept?

The rollback plan is to restore the system with the latest available backup. Backups are stored for 7 days for data center customers and for 14 days for customers on Amazon Web Service (AWS).

## How much time will it take to rollback?

It depends on database backup size. The average time it takes is 4 hours to complete. 

## What types of tests are performed on my system after the upgrade?

Refer to the [build upgrade checklist below](#check-list).

## What type of test do I have to carry out after my upgrade?

Development and stage environments are either upgraded in sequence or together but a sign-off is needed before upgrading the production instance. This allows each customer to conduct thorough testing before signing off on any changes to production.

See list [build upgrade checklist below](#check-list). Customers should run similar tests as well as others they may need for the environment.    

## How often do I have to carry out a build upgrade?

In order to ensure optimal performance, availability, and security of the system, Adobe will partner with Customers to ensure that systems are upgraded at least once per year.    

## Will there be a shutdown for with a build upgrade?

Yes. The server is shutdown during an upgrade to ensure that the data integrity is preserved while the product is upgraded. Once completed, it is restarted, and all services resume.    

## Who should I contact to open the build upgrade ticket?

If you face issues after a build upgrade, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Customer Care schedules the build dates and opens build upgrade related tickets.

Learn more in [Help and Support options for Campaign Classic](../../support.md)

## Build upgrade checklist {#check-list}

### Cloud Messaging server post upgrade checklist

1. Send a test delivery
    1. Validate the delivery logs and related workflow
    1. Validate the tracking logs are updated
    1. Validate mirror page and tracking links
1. Confirm all technical workflows are in started state
1. Verify all process are active as well

### Marketing server post upgrade checklist

* Can you login to the server? Check Campaign Client Console is working without any error/warning popups.
* Make sure to use the same console version as build version after the upgrade.
* Do you have any web applications that insert data into the Campaign Database? If so, run them and
verify that they can insert new records through API.
* Can you send out a test email successfully? Create new delivery using a known template, send it to
one test recipient, verify personalization, unsub link, mirror page all work.
* Are all of your critical path workflows running? Check workflows, open up workflow journal, verify
that there are no errors.
* Are all of your folders present, visible, and accessible? Browse through different folders and check.
all content is displayed and present.
* Are your deliveries coming through with the correct time zone?

    * Verify the creation date and modification date with the timestamp and time zone
    * Verify that the execution of scheduler works in a workflow on the specified time
    * Fetch list of workflows which are in PAUSED and FAILED state. Start and monitor them
    * Run AB Testing for one scenario
    * Test Push notifications along with their tracking functionality for deep links
    * Test sending SMS
    * If you have any external FDA connected, test if the data is being sent both ways
    * If you use integrations such as Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, test if they still work like before

**See also**

* [Performing a build upgrade](../../production/using/build-upgrade.md)
* [Campaign Classic Release Notes](../../rn/using/rn-overview.md)
* [Help and Support options for Campaign Classic](../../support.md)
* [[!DNL Gold Standard] program](../../rn/using/gs-overview.md)
