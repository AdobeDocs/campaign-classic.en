---
solution: Campaign Classic
product: campaign
title: Technical workflows
description: Learn more about the technical workflows available with Campaign Classic packages.
audience: workflow
content-type: reference
topic-tags: technical-workflows
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
---
# Technical workflows{#about-technical-workflows}

## About technical workflows {#overview}

The workflows detailed in this section are installed with the different Adobe Campaign built-in packages. These packages, and related technical workflows, depend on your licence agreement. Built-in packages are detailed in [this section](../../installation/using/installing-campaign-standard-packages.md).

By default, technical workflows are available in a sub-folder of the following node: **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>Technical workflows related to the Message Center module are available by default in the **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]** node.

For more on how to monitor technical workflows, refer to the [dedicated section](../../workflow/using/monitoring-technical-workflows.md).

## List of technical workflows {#list-technical-workflows}

|Technical workflow|Package|Description|
|------|--------|-----------|
|**Alias cleansing** (aliasCleansing)|Delivery|This workflow standardizes enumeration values. It is triggered every day at 3am by default.|
|**Billing** (billing)|Delivery|This workflow sends the system activity report to the 'billing' operator by email. It is triggered the 25th of every month by default.|
|**Calculation of Twitter statistics** (statsTwitter)|Social networks (Social Marketing)|This workflow calculates statistics linked to retweets and visits on Twitter.|
|**Campaign jobs** (operationMgt)|Marketing campaigns (Campaign)|This workflow manages the jobs for marketing campaigns (launches targeting, file extraction, etc.). It also creates workflows related to recurring and periodic campaigns.|
|**Collect data for HeatMap service** (collectDataHeatMapService)|Installed by default|This workflow retrieves data required by the HeatMap service.|
|**Collect privacy requests** (collectPrivacyRequests)|Privacy Data Protection Regulation|This workflow generates the recipient's data stored in Adobe Campaign and makes it available for download in the privacy request's screen.|
|**Cost calculation** (budgetMgt)|Marketing campaigns (Campaign)|This workflow starts the calculation of expense and cost lines on the budgets, plans, programs, campaigns, deliveries and tasks.|
|**Database cleanup** (cleanup)|Delivery|This workflow is the database maintenance workflow: it makes different calculations from the statistics and processes, and deletes obsolete data from the database according to the defined configuration in the deployment assistant. It is triggered every day at 4am by default. For more information, refer to [this page](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic).|
|**Delete blocked LINE users** (deleteBlockedLineUsersV2)|LINE channel|This workflow ensures that the LINE V2 users' data is deleted after they have blocked the LINE official account for 180 days.|
|**Delete privacy requests data** (deletePrivacyRequestsData)|Privacy Data Protection Regulation|This workflow deletes the recipient's data stored in Adobe Campaign.|
|**Delivery indicators** (deliveryIndicators)|Mid-sourcing platform|This workflow updates delivery tracking indicators for a delivery. This workflow is triggered every hour by default.|
|**Discussion forum processes** (newsgroupMgt)|Marketing resources (MRM)|This workflow manages the delivery of notifications from discussion forums. It is triggered when an approval signal is received|
|**Distributed marketing processes** (centralLocalMgt)|Central/local Marketing (Distributed Marketing)|This workflow starts processing related to using the distributed marketing module. It launches the creation of local campaigns and manages notifications related to orders and campaign package availability.|
|**Event purge** (webAnalyticsPurgeWebEvents)|Web Analytics connectors|This workflow lets you delete every event from the database field according to the period configured in the Lifespan field.|
|**Export audiences to the Adobe Experience Cloud** (exportSharedAudience)|Integration with Adobe Experience Cloud|This workflow exports audiences as shared audiences/segments. These audiences can be used in the different Adobe Experience Cloud solutions that you use.|
|**Forecasting** (forecasting)|Delivery|This workflow analyzes deliveries saved in the provisional calendar (creates provisional logs). It is triggered every day at 1am by default.|
|**Full aggregate calculation (propositionrcp cube)** (agg_nmspropositionrcp_full)|Offer engine (interaction)|This workflow updates the Full aggregate for the Offer proposition cube. It is triggered every day at 6am by default. This aggregate captures the following dimensions: Channel, Delivery, Marketing Offer and Date. The Offer proposition cube is then used to generate reports based on offers. You can learn more about cubes in [this section](../../reporting/using/about-cubes.md).|
|**Identification of converted contacts** (webAnalyticsFindConverted)|Web Analytics connectors|This workflow indexes site visitors that have completed their purchase after a re-marketing campaign. The data recovered by this workflow can be accessed in the Re-marketing efficiency report (Refer to this page).|
|**Import audiences from the Adobe Experience Cloud** (importSharedAudience)|Integration with Adobe Experience Cloud|This workflow allows you to import audiences/segments from different Adobe Experience Cloud solutions into Adobe Campaign.|
|**Jobs on deliveries in campaigns** (deliveryMgt)|Marketing campaigns (Campaign)|This workflow triggers the approved deliveries and starts post-processing the service provider for an external delivery. It also sends approval notifications and reminders.|
|**Jobs on service providers** (supplierMgt)|Marketing campaigns (Campaign)|This workflow starts processing the provider (email to the router and post-processing) once deliveries have been approved.|
|**LINE V2 access token update** (updateLineV2AccessToken)|LINE channel|This workflow refreshes the access token to LINE V2.|
|**MID to LineUserID migration** (MIDToUserIDMigration)|LINE channel|This workflow generates the LINE V2 users' ID for migration from LINE V1 to LINE V2.|
|**Marketing resource notifications** (assetMgt)|Marketing resources (MRM)|This workflow manages notifications linked to the approval and publication of marketing resources.|
|**Message Center &lt;external_account_name&gt;** (mcSynch_&lt;external_account_name&gt;)|Transactional message control (Message Center - Control)|This workflow: <ul><li>recovers the list of events processed by the operation(s).</li><li>synchronizes with the NmsBroadLogMsg table in order to recover delivery message qualifications.</li><li>recovers event delivery logs as soon as synchronization with the NmsBroadLogMsg table has been completed.</li><li>synchronizes with the NmsTrackingUrl table in order to recover the tracking for delivery URLs.</li><li>recovers event tracking URLs as soon as synchronization with the NmsTrackingUrl table has been completed.</li><li>lets you recover all email addresses placed in quarantine every three hours after a delivery has been sent.</li></ul>|
|**MessageCenter full aggregate calculation** (agg_messageCenter_full)|Transactional message control (Message Center - Control)|This workflow updates the Full aggregate for the Message center cube. It is triggered every day at 3am by default. This aggregate captures the following dimensions: Channel, Date, Status and Event type. The Message center cube is then used to generate reports based on events. You can learn more about cubes in [this section](../../reporting/using/about-cubes.md)|
|**Mid-sourcing (delivery counters)** (defaultMidSourcingDlv)|Transfer to Mid-sourcing|This workflow collects count information for deliveries on the mid-sourcing server. Count information includes general delivery indicators such as number of deliveries sent, etc. Tracking information such as opens are not included. It is triggered every ten minutes by default.|
|**Mid-sourcing (delivery logs)** (defaultMidSourcingLog)|Transfer to Mid-sourcing|This workflow collects delivery logs on the mid-sourcing server. It is triggered every hour by default.|
|**NMAC opt-out management** (mobileAppOptOutMgt)|Mobile App Channel|This workflow updates notification unsubscriptions on mobile devices. It is triggered every 6 hours between 1am and midnight. For more details, refer to [this section](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines).|
|**Number of active billing profiles** (billingActiveContactCount)|Delivery|This wokflow counts the number of active profiles. It is triggered every night at 1am by default. “Profile” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead. Billing only concerns Profiles that are “active”. A Profile is considered “active” if the Profile has been targeted or communicated within the past 12 months via any channel. Facebook and Twitter channels are not taken into account. You can have an overview of the Number of active profiles from the Administration > Campaign Management > Customer metrics menu.|
|**Offer notification** (offerMgt)|Delivery|This workflow deploys approved offers onto the online environment, as well as every category contained in the offer catalog.|
|**Paused workflows cleanup** (cleanupPausedWorkflows)|Delivery|This workflow analyzes paused workflows that have severity set to normal and triggers warnings and notifications when they have been paused for too long. After a month, paused technical workflows are stopped unconditionally. By default, it is triggered every Monday at 5 am. For more information, refer to [Handling of paused workflows](../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows).|
|**Privacy request cleanup** (cleanupPrivacyRequests)|Privacy Data Protection Regulation|This workflow erases the access request files that are older than 90 days.|
|**Processing batch events** (batchEventsProcessing)|Transactional message execution (Message Center - Execution)|This workflow lets you put batch events into a queue before associating them with a message template.|
|**Processing real time events** (rtEventsProcessing)|Transactional message execution (Message Center - Execution)|This workflow lets you put real-time events into a queue before associating them with a message template.|
|**Proposition synchronization** (propositionSynch)|Control of offer engine with execution instance|This workflow synchronizes propositions between the marketing instance and the execution instance used for interactions.|
|**Recovery of web events** (webAnalyticsGetWebEvents)|Web Analytics connectors|Every hour, this workflow downloads segments on internet user behavior on a given site, puts them into the Adobe Campaign database and launches the re-marketing workflow.|
|**Reporting aggregates** (reportingAggregates)|Delivery|This workflow updates aggregates used in reports. It is triggered every day at 2am by default.|
|**Sending of indicators and campaign attributes** (webAnalyticsSendMetrics)|Web Analytics connectors|This workflow lets you send email campaign indicators from Adobe Campaign to Adobe Experience Cloud Suite via the Adobe® Genesis connector. The indicators concerned are as follows: Sent (iSent), Total count of opens (iTotalRecipientOpen), Total number of recipients who clicked (iTotalRecipientClick), Errors (iError), Opt-Out (opt-out) (iOptOut).|
|**Stock: Orders and alerts** (stockMgt)|Marketing campaigns (Campaign)|This workflow launches stock calculation on the order lines and manages warning alerts thresholds.|
|**Synchronizing Facebook fans** (syncFacebookFans)|Social networks (Social Marketing)|This workflow imports Facebook fans into Adobe Campaign every day at 7am.|
|**Synchronizing Facebook pages** (syncFacebook)|Social networks (Social Marketing)|This workflow synchronizes Facebook pages with Adobe Campaign every day at 7am.|
|**Synchronizing Twitter pages** (syncTwitter)|Social networks (Social Marketing)|This workflow imports Twitter followers into Adobe Campaign every day at 7am.|
|**Task notification** (taskMgt)|Marketing resources (MRM)|This workflow lets you send notification messages related to tasks in marketing campaigns.|
|**Tracking** (tracking|Delivery|This workflow performs the recovery and consolidation of tracking information. It also assures the recalculation of tracking and delivery statistics, especially those used by Message Center archiving workflows. By default, it is triggered once per hour.|
|**Update event status** (updateEventsStatus)|Transactional message execution (Message Center - Execution)|This workflow lets you assign a status to an event. Event statuses are as follows:<ul><li>Pending: the event is in a queue. No message template has yet been associated to it.</li><li>Pending delivery: the event is in a queue, a message template has been associated to it and is currently being processed by the delivery.</li><li>Sent: this status is copied from the delivery logs. It means that the delivery has been sent.</li><li>Ignored by the delivery: this status is copied from the delivery logs. It means that the delivery has been ignored.</li><li>Delivery error: this status is copied from the delivery logs. It means that the delivery has failed.</li><li>Event not covered: the event has failed to be associated with a message template. The event will not be reprocessed.</li></ul>|
|**Update for deliverability** (deliverabilityUpdate)|Delivery|Once Deliverability monitoring (Email Deliverability) package is installed, this workflow runs nightly and manages the bounce emails qualification rules, as well as the list of domains and MXs. This requires HTTPS port to be open on the platorm|
|**Update seed network for Inbox Rendering** (updateRenderingSeeds)|Inbox Rendering (IR)|This workflow updates email addresses used for Inbox rendering and only works if the HTTPS port is open for deliverability.neolane.net.|
