---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic Documentation Updates
description: This page lists all the new features and updates in Adobe Campaign Classic documentation
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
---
# Documentation Updates{#documentation-updates}

This page lists all the new features and documentation updates per month and Campaign release.

Refer to the [Adobe Campaign Classic Release Notes](../../rn/using/latest-release.md) for release related updates.

## March 2021 {#march-2021}

The [Get started with SMS section](../../delivery/using/sms-channel.md) has been reorganized and improved. You can now learn how to [configure the SMS channel](../../delivery/using/sms-set-up.md), [create a SMS](../../delivery/using/sms-create.md), [send and track SMS](../../delivery/using/sms-send.md) in dedicated sections.

The "Help & support options" page for Campaign Classic has been integrated into the core documentation. [Read more](../../support.md)

A new section has been added with best practices and checks to perform regarding security and privacy. [Read more](../../installation/using/get-started-security-privacy.md)

The [permission management chapter](../../platform/using/access-management.md) has been improved and split into sections, including details about [Operators](../../platform/using/access-management-operators.md) , [Groups of operators](../../platform/using/access-management-groups.md) , [Named rights](../../platform/using/access-management-named-rights.md)  and [Folder management](../../platform/using/access-management-folders.md) .

Learn how to create and manage your campaigns through these new pages: 
* [Create and configure campaign templates](../../campaign/using/marketing-campaign-templates.md)
* [Marketing campaign deliveries](../../campaign/using/marketing-campaign-deliveries.md)
* [Select the audience of your campaigns](../../campaign/using/marketing-campaign-target.md)
* [Manage associated documents](../../campaign/using/marketing-campaign-assets.md) 
* [Set up and manage the approval process](../../campaign/using/marketing-campaign-approval.md)

Information has been added in the **[!UICONTROL Advanced JavaScript]** activity section on how to use the task.setCompleted() method to terminate the task and prevent future recalls. [Read more](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

The [Deliverability](../../delivery/using/about-deliverability.md) section has been updated and now includes links to the new [Adobe Deliverability Best Practice Guide](https://experienceleague.corp.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html). All generic information related to deliverability that can apply to various Adobe solutions has been moved to the [Best Practice Guide Appendix](https://experienceleague.corp.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html#additional-resources).

## February 2021 {#release-21.1}

**Documentation updates coming with the 21.1 release**

The new **Email Feedback Service** capability (private beta) is documented [here](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service).

The **Server configuration file** section has been updated with the configuration parameters needed for Campaign to connect to another service using IMS. [Read more](../../installation/using/the-server-configuration-file.md#ims)

In the list of delivery statuses, the description for **Taken into account by the service provider** has been updated: this status is now also used for email deliveries sent using the [Email Feedback Service](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service). [Read more](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

The keyboard shortcuts available on the new logon screen to connect to Adobe Campaign are now documented. [Read more](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**Other updates**

A new section has been added with detailed information on how to perform A/B testing using workflows. [Read more](../../delivery/using/get-started-a-b-testing.md)

The Adobe Campaign Enhanced MTA section has moved [here](../../delivery/using/sending-with-enhanced-mta.md).

A new page has been added to provide an overview of tracking capabilities in [!DNL Campaign Classic]. [Read more](../../delivery/using/about-message-tracking.md)

A troubleshooting section has been added to help you solve common issues related to tracking. [Read more](../../delivery/using/tracking-troubleshooting.md)

The **Sending an email** section has been reorganized and clarified with new subsections. [Read more](../../delivery/using/sending-messages.md)

Information has been added on how to add links in emails that can be personalized and that support tracking. [Read more](../../delivery/using/tracking-personalized-links.md).

## January 2021 {#jan-2021}

The **[!UICONTROL Fork]** activity section has been enriched with best practices. [Read more](../../workflow/using/fork.md)

The **CRM Connectors** section has been updated, improved and reorganized. [Read more](../../platform/using/crm-connectors.md).

Steps to connect **Adobe Campaign and Microsoft Dynamics** are now detailed in a dedicated page. [Read more](../../platform/using/crm-ms-dynamics.md).

Oracle On Demand API is now deprecated as a CRM connected with Campaign. [Read more](../../rn/using/deprecated-features.md).

Learn how to find out the current version of embedded Tomcat web servlet used in an instance of Adobe Campaign [here](../../production/using/locate-tomcat-version.md).

The list of technical workflows with their associated packages has been enhanced and centralized into one single page. [Read more](../../workflow/using/about-technical-workflows.md)

The troubleshooting section of the **Monitoring** guide has been reorganized and enhanced with a landing page. [Read more](../../production/using/troubleshooting.md).

A new **Importing and exporting data** section is available with new pages related to workflows, data compression, encryption, and import best practices. [Read more](../../platform/using/get-started-data-import-export.md)

## December 2020 {#dec-2020}

The **Delivery monitoring** section has been reorganized into thematic topics. [Read more](../../delivery/using/about-delivery-monitoring.md)

A use case has been added on how to add senders' IP addresses to the delivery logs. [Read more](../../delivery/using/delivery-dashboard.md#use-case)

Privacy FAQ has been moved to [this section](../../platform/using/privacy-faq.md).

A use case has been added on how to use the **[!UICONTROL Deduplication]** activity's merge functionality. [Read more](../../workflow/using/deduplication-merge.md)

The complete description of SMS connector protocol and settings page is now available [here](../../delivery/using/sms-protocol.md).

A note has been added to the **Transactional messaging** section to warn that the event folders must not be set as views on the execution instances, to avoid access right issues. [Read more](../../message-center/using/event-collection.md)

## November 2020 {#nov-2020}

Campaign data model overview has been improved and reorganized. [Read more](../../configuration/using/about-data-model.md).

External account configuration has moved to [this section](../../installation/using/external-accounts.md).

Campaign Federated Data Access (FDA) documentation has been improved with details for each external database configuration, and moved to [this section](../../installation/using/about-fda.md).

[Campaign 20.2.3 release](../../rn/using/release--20-2.md#release-20-2-3-build-9182) has moved to General Availability (GA).

The Privacy section has been moved and enriched with two new pages: [Privacy management](../../platform/using/privacy-management.md) and [Managing privacy requests](../../platform/using/privacy-requests.md).

A note has been added in the mid-sourcing server configuration page to specify that the external account's internal name should not be updated once the server has been setup. [Read more](../../installation/using/mid-sourcing-server.md)

Information has been added on the syntax to use when specifying a path to an external SFTP server. [Read more](../../platform/using/sftp-server-usage.md#external-SFTP-server)

The Personal Data and Personas section has been updated with a use case scenario to illustrate how the different personas are interacting when it comes to Privacy. [Read more](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

A new section listing Frequently Asked Questions on Privacy has been added. [Read more](../../platform/using/privacy-faq.md)

## October 2020 {#oct-2020}

**New capabilities included in 20.3 release**

Push notifications improvements for iOS - [Read more](../../delivery/using/configuring-the-mobile-application.md)

Push notifications improvements for Android - [Read more](../../delivery/using/configuring-the-mobile-application-android.md)

**Other documentation updates coming with the release**

The Compatibility matrix has been updated. [Read more](../../rn/using/compatibility-matrix.md)

The Deprecated and removed features page has been updated. [Read more](../../rn/using/deprecated-features.md)

Release notes and Compatibility matrix for [!DNL Gold Standard] release are now available in a dedicated section.
[Read more](../../rn/using/gold-standard.md#gs-11).

Triggers integration originally based on oAUTH authentication setup to access pipeline has now been changed and moved to Adobe I/O. [Read more](../../integrations/using/configuring-adobe-io.md)

**Other updates**

Documentation pages have been updated to reflect the Tomcat 8 update. 

Details have been added in the 'About' box description in the 'Getting your Adobe Campaign version' section. [Read more](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

Guidelines to perform a build upgrade have been added to the 'Updating Adobe Campaign Classic' section. Read more [Read more](../../production/using/build-upgrade.md)

FAQs about Campaign build upgrade have been added to Campaign common questions. Read more [Read more](../../platform/using/faq-build-upgrade.md)

Campaign on-premise, hosted and hybrid hosting models are now described in a dedicated section. [Read more](../../installation/using/hosting-models.md)

Campaign capability matrix per hosting model has been updated and moved in the Installation guide. [Read more](../../installation/using/capability-matrix.md)

Campaign Reporting advanced capabilities section has been improved to detail how to use URL parameters and variables in custom reports. [Read more](../../reporting/using/advanced-functionalities.md)

The reports properties page has been reorganized and enriched to facilitate configuration. [Read more](../../reporting/using/properties-of-the-report.md)

A new technote has been created with details on how to migrate from the legacy binary protocol to HTTP/2-based APNs provider API. [Read more](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

## September 2020 {#september-2020}

A note has been added to specify that Active profiles count is available for Marketing instances only. [Read more](../../platform/using/about-profiles.md#active-profiles)

A new sample about schema edition has been added to link a field to an existing reference table. [Read more](../../configuration/using/examples-of-schemas-edition.md#uc-link)

A note has been added regarding the use of additional data with seed addresses in deliveries. [Read more](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## August 2020 {#aug-2020}

Learn best practices related to delivery design and sending with Campaign in a dedicated section. [Read more](../../delivery/using/delivery-best-practices.md)

The Deliverability best practices landing page has been improved to facilitate access to sub-sections. [Read more](../../delivery/using/about-deliverability.md)

How-to videos are now available on the following topics:

* [How to set up fatigue management using typology rules and predefined filters](../../campaign/using/about-campaign-typologies.md)

* [How to create an email in a campaign](../../campaign/using/marketing-campaign-deliveries.md)

* [How to create a multilingual newsletter with conditional content](../../delivery/using/conditional-content.md)

* [How to configure and deploy a delivery template](../../delivery/using/creating-a-delivery-template.md)

* [How to activate and use AMP for emails](../../delivery/using/defining-interactive-content.md)

* [How to personalize emails using dynamic content blocks](../../delivery/using/personalization-blocks.md)

* [How to personalize emails using personalization fields](../../delivery/using/personalization-fields.md)

* [How to manage seed and proofs in an email](../../delivery/using/steps-defining-the-target-population.md)

* [How to set up a recurring delivery](../../workflow/using/recurring-delivery.md)

* [How to set up a continuous delivery](../../workflow/using/continuous-delivery.md)

Information has been added on the checks and actions to perform when getting the "Couldn't resolve host name" error after connecting to an FTP server. [Read more](../../platform/using/sftp-server-usage.md)

New use cases have been referenced in the list of [workflow use cases](../../workflow/using/about-workflow-use-cases.md):

* Automating content creation, edition and publishing
* Setting up a recipient approval process before a delivery is sent
* Calling an instance variable in a query
* Applying a split percentage on a population

The **[!UICONTROL AND-join]** activity section has been enriched with additional information on its usage, as well as a note regarding the use of variables. [Read more](../../workflow/using/and-join.md)

## July 2020 {#july-2020}

A use case on how to automatically update a list using an incremental query has been added to the workflow use cases. [Read more](../../workflow/using/about-workflow-use-cases.md)

The [Release Notes](../../rn/using/latest-release.md) have been reorganized: an [overview page](../../rn/using/latest-release.md) has been added with information on build statuses, upgrade process, recommendations and important links. A dedicated page for [[!DNL Gold Standard] releases](../../rn/using/gold-standard.md) has also been added and the [Compatibility matrix](../../rn/using/compatibility-matrix.md) has been integrated.

A new section has been added with guidelines related to Campaign Classic monitoring. [Read more](../../production/using/monitoring-guidelines.md)

The Privacy and Consent section has been enhanced with more detailed information and useful links. [Read more](../../platform/using/privacy-and-recommendations.md)

The Privacy Management in Campaign Classic page has been updated with information on the 'regulation' field which is now available when using the API allowing to setup automatic Privacy request process. [Read more](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

The Privacy Management Overview page has been updated to include information on the Thailand’s Personal Data Protection Act (PDPA) and the Brazil's Lei Geral de Proteção de Dados (LGPD). [Read more](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

Information has been added on sub-workflows logs and behaviour in case of error. [Read more](../../workflow/using/sub-workflow.md)

Best practices have been added in the **[!UICONTROL Scheduler]** activity section. [Read more](../../workflow/using/scheduler.md)

## June 2020 {#june-2020}

The Removing a quarantined address section has been updated. This includes clarification of the cases in which addresses are automatically removed from the quarantine list. [Read more](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Use cases have been added on how to [encrypt](../../platform/using/zip-encrypt.md) and [decrypt](../../platform/using/unzip-decrypt.md) data using Control Panel and Campaign workflows.

The Experience Cloud Triggers and Adobe Campaign Classic integration page has been moved [here](../../integrations/using/about-triggers.md).

## July 2020 {#release-20-2}

**New capabilities included in 20.2 release**

Support of Emoticons - [Read more](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA Connector - [Read more](../../installation/using/configure-fda-synapse.md)

Thailand and Brazil Privacy Laws - [Read more](https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Other documentation updates coming with the release**

The new option enabling to unpublish a transactional message template is documented in [this section](../../message-center/using/template-unpublication.md).

The new options allowing to set limitations when sending emails that include images downloaded from a personalized URL and attachments have been added to the list of Campaign Classic options. [Read more](../../installation/using/configuring-campaign-options.md#delivery)

The new **Prepare the delivery parts in the database** option is documented in [this section](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

The Validating the delivery section has been clarified and updated. [Read more](../../delivery/using/steps-validating-the-delivery.md)

The parameters related to the new tracking link signature mechanism have been added to the [Server configuration file](../../installation/using/the-server-configuration-file.md) section.

The Compatibility matrix has been updated. [Read more](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

The cleanup workflow section has been updated. [Learn more](../../production/using/database-cleanup-workflow.md)

The Campaign network endpoints have been moved to this [section](../../installation/using/campaign-network-endpoints.md).

The Spam Assassin installation section has been updated with the new installation file name. [Learn more](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

The section on duplicating environments has been updated. [Learn more](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## May 2020 {#may-2020}

The Monitoring deliverability section has been moved and improved. [Read more](../../delivery/using/monitoring-deliverability.md)

The Deliverability troubleshooting section has been moved and improved. [Read more](../../delivery/using/deliverability-faq.md)

Deliverability guidelines when starting a new platform have been enhanced. [Read more](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html#transition-process)

The Sending transactional emails with attachments section has been moved and updated. [Read more](../../message-center/using/transactional-email-with-attachments.md)

The Data package best practices section has been moved and updated. [Read more](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## April 2020 {#april-2020}

The FDA rights table has been moved to the Accessing an external database (FDA) documentation. [Read more](../../installation/using/remote-database-access-rights.md)

The FAQ has been updated with tips on how to clear soft and hard cache. [Read more](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Data model best practices have been improved with additional information on indexes. [Read more](../../configuration/using/data-model-best-practices.md#indexes)

The section describing the Adobe Campaign built-in data model has been updated with more details on each table. [Read more](../../configuration/using/data-model-description.md)

Workflow use cases have been updated and reorganized into thematic sections. [Read more](../../workflow/using/about-workflow-use-cases.md)

The [Bounce mail qualification](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) and [Email management rules](../../delivery/using/understanding-delivery-failures.md#email-management-rules) sections have been enhanced with updated information.

The Adobe Campaign Enhanced MTA article has been updated. It now only applies to Campaign Classic. [Read more](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

## March 2020 {#march-2020}

Data model best practices have been updated with new sections including [Sequences](../../configuration/using/data-model-best-practices.md#sequences), [Performance](../../configuration/using/data-model-best-practices.md#performance) and [Large tables](../../configuration/using/data-model-best-practices.md#large-tables), amongst others. [Read more](../../configuration/using/data-model-best-practices.md)

A new section describing the Adobe Campaign built-in data model and interaction between tables is now available. [Read more](../../configuration/using/data-model-description.md)

Additional key links have been added to the documentation home page. [Read more](../../campaign-classic-home.md)

A use case has been added on how to integrate a dynamic offer from Adobe Target into an email in Adobe Campaign. [Read more](../../integrations/using/inserting-a-dynamic-image.md)

A new section detailing the different languages available in Adobe Campaign is now available. [Read more](../../platform/using/adobe-campaign-workspace.md#languages)

Access management guidelines have been updated with more information on Named rights. [Read more](../../platform/using/access-management-named-rights.md)

## February 2020 {#february-2020}

A new section outlining best practices and key recommendations while designing the Adobe Campaign data model is now available. [Read more](../../configuration/using/data-model-best-practices.md)

A new section is available about Technical email configurations. [Read more](../../installation/using/email-deliverability.md)

The Deliverability FAQ has been updated with more details on the "quotas met" error message. [Read more](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP for Email is now supported by new email providers: the related documentation has been updated. [Read more](../../delivery/using/defining-interactive-content.md)

The Email archiving section has been improved. [Read more](../../installation/using/email-archiving.md#recommendations-and-limitations)

## January 2020 {#release-20-1}

**New capabilities included in 20.1 release**

Snowflake FDA Connector - [Read more](../../installation/using/configure-fda-snowflake.md)

Hadoop FDA Connector Enhancements - [Read more](../../installation/using/configure-fda-hadoop.md)

**Other documentation updates coming with the release**

The [installation](../../installation/using/general-architecture.md), [production](../../production/using/foreword.md) and [configuration](../../configuration/using/additional-parameters.md) guides have been updated with the new systemd unit used by the nlserver service startup. You can still use /etc/init.d/nlserver6, but Adobe recommends that you now use the systemctl command for interacting with the nlserver service.

The installation guide has been updated and synchronized with the latest version of the compatibity matrix. New supported systems have been added. Occurences to deprecated and unsupported systems have been removed. [Read more](../../installation/using/general-architecture.md)

The Compatibility matrix has been updated with the Hadoop 3.0 and Snowflake FDA connectors. [Read more](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

A best practice on IP affinity has been added to the installation guide. [Read more](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

The database cleanup workflow section has been updated. The provided batch figures now reflect the code implementation. [Read more](../../production/using/database-cleanup-workflow.md)

A limitation on FDA over HTTP has been added to the transactional messaging guide. [Read more](../../production/using/database-cleanup-workflow.md)

Information has been added on the new option that allows you to define a time-out period for the **[!UICONTROL JavaScript code]** and **[!UICONTROL Advanced JavaScript code]** workflow activities. [Read more](../../workflow/using/sql-code-and-javascript-code.md)

Information has been added on the new **[!UICONTROL Start Pending]** view available in the **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** node. [Read more](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

The [Sending push notifications](../../delivery/using/about-mobile-app-channel.md) guide has been moved, reorganized and improved with clarified information.

The new parameter for URLs report configuration has been documented [here](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

The **Campaign Classic On-premise & Hosted capability matrix** page has been updated with the new FDA connectors. [Read more](../../installation/using/capability-matrix.md).

The **Campaign Classic Capability matrix** page has been updated. [Read more](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

The new **[!UICONTROL Cleanup of Nmsaddress]** workflow has been documented [here](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

A limitation has been added when using a query activity in a workflow. [Read more](../../workflow/using/query.md).

A new section has been added to detail the enhanced email address validation rules to send an address to quarantine in case of soft error. [Read more](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

The parameter from the configuration file indicating that an instance is using the Enhanced MTA or not is now documented. [Read more](../../installation/using/the-server-configuration-file.md#mta)

The Deliverability section has been moved, reorganized, and enhanced with updated content. [Read more](../../delivery/using/about-deliverability.md)

A new section describing the Adobe Campaign Classic data model basics and how to access the description of each table is now available. [Read more](../../configuration/using/about-data-model.md)

The Adobe Campaign Enhanced MTA article has been updated with more detailed information on installing a specific Typology package on instances that do not add the required Enhanced MTA headers to every message. [Read more](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

The use cases related to query designing have been reorganized into separate sections. [Read more](../../workflow/using/querying-recipient-table.md)

A new section about tips and tricks on managing offers and using the Interaction module in Adobe Campaign Classic is now available. [Read more](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

The Interaction documentation has been enriched with links to several videos that help understand better how to manage offers. [Read more](../../interaction/using/interaction-and-offer-management.md)

The best practices article on how to optimize the queries running on your instance has been integrated into the documentation. [Read more](../../workflow/using/query.md#optimizing-queries)

Reporting guide has been updated and reorganized. [Read more](../../reporting/using/about-adobe-campaign-reporting-tools.md)

An example of how to use an instance variable in a workflow has been added. [Read more](../../workflow/using/javascript-scripts-and-templates.md)

## December 2019 {#december-2019}

The "WdbcOptions_TempDbName" option has been added to the list of Campaign options. [Read more](../../installation/using/configuring-campaign-options.md)

The FDA matrix page has been moved [here](../../installation/using/remote-database-access-rights.md).

The Access Rights Matrix page has been moved [here](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en).

The section describing how to define interactive content with AMP has been moved. [Read more](../../delivery/using/defining-interactive-content.md)

**New capabilities included in 19.2 release**

California Consumer Privacy Act (CCPA) - [Read more](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Interactive content with AMP - [Read more](../../delivery/using/defining-interactive-content.md)

Workflow live monitoring - [Read more](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Secure SMS Messaging (TLS) - [Read more](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**Other documentation updates coming with the release**

The Adobe Campaign Enhanced MTA documentation is now available. [Read more](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

A new section has been added on how to troubleshoot a workflow staying in the "Start as soon as possible" state within a campaign. [Read more](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

The new "NmsOperation_DeliveryPreparationWindow" and "WdbcKillSessionPolicy" options have been added to the list of Campaign options. [Read more](../../installation/using/configuring-campaign-options.md)

A new document describing the Adobe Campaign Classic data model basics is now available. [Read more](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

The new **Maximum personalization run time** option in the delivery properties is documented in this [section](../../delivery/using/personalization-fields.md#timing-out-personalization).

The examples for API calls using an **HttpServletRequest** with logon() and query() have been updated. [Read more](../../configuration/using/web-service-calls.md).

A recommendation for **sqlDefault** attribute in schema definition has been added. [Read more](../../configuration/using/schema/attribute.md)).

The integration between Adobe Campaign and Adobe Real-time Customer Data Platform is now referenced in the **Integrating with Adobe Experience Cloud** guide. [Read more](../../integrations/using/about-campaign-integrations.md).

## November 2019 {#november-2019}

A warning has been added to the [Multiplexing the mid-sourcing server](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) and [Supporting several control instances](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) sections mentioning that these deployments are not supported for fully hosted and hybrid clients.

A new section has been added to describe how to force the character encoding used when sending an email. [Read more](../../delivery/using/sending-messages.md#character-encoding)

The Access management section has been updated with the **Privacy Data right**. [Read more](../../platform/using/access-management-named-rights.md)

Information was added to specify that personalization fields content cannot exceed 1024 characters. [Read more](../../delivery/using/personalization-fields.md)

The Control Panel documentation has been integrated into the new collaborative documentation set. [Read more](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

The Delivery Best Practices getting started guide has been updated. [Read more](../../delivery/using/delivery-best-practices.md)

## October 2019 {#october-2019}

The list of error messages for Campaign Standard and Campaign Classic has been updated. [Read more](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html)

The GDPR getting started guide has been improved and enriched. It is now a privacy management documentation including GDPR and CCPA. [Read more](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

A new troubleshooting page has been added for tracking in Campaign Classic. [Read more](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

A new page of best practices for Adobe Analytics Data Connector has been added. [Read more on Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

The Delivery Best Practices getting started guide has been moved and updated. [Read more](../../delivery/using/delivery-best-practices.md)

A recommendation has been added to the SMS channel documentation to avoid issues when using multiple external accounts leveraging the Extended generic SMPP connector with the same provider account. [Read more](../../delivery/using/sms-set-up.md#automatic-reply)

Information was added in the Scheduler activity documentation on how to prevent simultaneous executions of a workflow. [Read more](../../workflow/using/scheduler.md)

The steps to configure Inbox rendering for on-premise installations have been added to documentation. [Read more](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## September 2019 {#september-2019}

A new page has been added to provide general guidelines for maintaining Campaign Classic. [Read more](../../production/using/monitoring-guidelines.md)

Information related to workflows monitoring has been centralized into a new dedicated section. [Read more](../../workflow/using/monitoring-workflow-execution.md).

A new page about general guidelines for tracking in Adobe Campaign Classic has been added. [Read more](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

The best practices for performance improvements of workflows and deliveries have been updated. [Read more on workflows](../../workflow/using/workflow-best-practices.md) and [more on deliveries](../../delivery/using/delivery-performances.md#best-practices-performance).

## May 2019 {#release-19-1}

**New capabilities included in 19.1 release**

Control Panel - [Read more](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Audit trail - [Read more](../../production/using/audit-trail.md)

**Other documentation updates coming with the release**

A new Build upgrade FAQ has been created. [Read more](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

The [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) has been updated. The list of supported database systems has been updated as well as Android/iOS versions and related SDKs. The [19.0 Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) has been archived.

The 'Deprecated and Removed Features in Campaign Classic' page has been updated. [Read more](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

The description of the server configuration file has been added to the Installation guide. [Read more](../../installation/using/the-server-configuration-file.md)

A section has been added describing the installation and configuration steps for hosted and hybrid models. [Read more](../../installation/using/hosting-models.md)

A section has been added describing the Campaign server uninstallation steps. [Read more](../../installation/using/uninstalling-campaign.md)

The [security](https://helpx.adobe.com/campaign/kb/acc-security.html), [deliverability](../../delivery/using/about-deliverability.md) and [privacy](../../platform/using/privacy-management.md) getting started guides have been updated.

The description of the pre-process workflow option has been updated to reflect product changes. [Read more](../../workflow/using/data-loading--file-.md)

The Marketing Cloud Triggers technote has been updated. [Read more](../../integrations/using/about-triggers.md)

The list of error messages has been updated. [Read more](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html)

Added more information on SOAP authentication methods for transactional messaging. [Read more](../../message-center/using/event-description.md)

The Apache configuration steps have been updated. [Read more](../../installation/using/integration-into-a-web-server-for-linux.md)

A new page has been added including the list of endpoints for Campaign Standard and Classic. [Read more](../../installation/using/campaign-network-endpoints.md)

The Data package best practices article has been updated. [Read more](../../configuration/using/data-model-best-practices.md)

The Managing Offers documentation has been updated with a new section listing best practices. [Read more](../../interaction/using/interaction-best-practices.md)

A new Knowledge base article on using the offer catalog in Adobe Campaign Classic has been created. [Read more](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

The Sub-workflow activity section has been enhanced with an example of usage. [Read more](../../workflow/using/sub-workflow.md)

The [Campaign Classic On-premise & Hosted capability matrix](../../installation/using/capability-matrix.md) page has been updated with information relating to Email BCC.

The Transactional Messaging documentation has been updated with a note regarding template publication. [Read more](../../message-center/using/template-publication.md)

The Unprocessed bounce mails section has been updated with more details on the Forwarding address and Address for errors fields. [Read more](../../installation/using/deploying-an-instance.md)

A new section on workflow planning best practices has been added. [Read more](../../workflow/using/workflow-best-practices.md)

Added two new options to the list of Campaign options: XtkSecurity_Restrict_EditXML and NmsOperation_OperationMgtDebug.
 [Read more](../../installation/using/configuring-campaign-options.md)

Added information on the different external accounts available in Campaign Classic and how to configure them.
 [Read more](../../installation/using/external-accounts.md)

Updated Analytics Data Connector section to reflect interface changes.
 [Read more](../../platform/using/adobe-analytics-data-connector.md)

Added information on the Billing report.
 [Read more](../../production/using/monitoring-processes.md)

Updated documentation on the Shared audiences integration.
 [Read more](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

The following technotes have been updated: [SMS connector protocol and settings](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) and [Sequence auto generation](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

The Technical workflows section has been updated. [Read more](../../workflow/using/about-technical-workflows.md)

The Campaign Domain Name Setup procedure has been improved and updated. [Read more](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)

The Migration procedure for Android Apps from Google Cloud Messaging (GCM) to Firebase Cloud Messaging (FCM) has been updated. [Read more](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

The Campaign Hardware Sizing Guide has been updated. [Read more](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Information was added on Query Banding for the Teradata external account. [Read more](../../installation/using/external-accounts.md)

## January 2019{#release-doc-16-01-2019}

The Marketing Cloud Triggers technote has been updated. [Read more](../../integrations/using/about-triggers.md)

A note was added in the offer approval section to specify  that the "Content approved" mention indicates that the content approval process has been achieved, whether all offers have been enabled/approved or not. [Read more](../../interaction/using/offer-catalog-overview.md)

A new section was added in the Installation guide, listing options from the Administration / Platform / Options node. [Read more](../../installation/using/configuring-campaign-options.md)

Information was added about the use of seed addresses to protect your mailing list. [Read more](../../delivery/using/creating-seed-addresses.md)

Key steps when creating and sending a delivery have been regrouped into a new section, with references to the various channels when needed. [Read more](../../delivery/using/steps-about-delivery-creation-steps.md)

The [Email archiving](../../installation/using/email-archiving.md) section has been moved, reorganized and improved with clarified information:

* Best practices have been added regarding emails per connection and BCC sending IPs parameters.

* We've updated the steps to upgrade to the new email archiving system (BCC) if you were already using email archiving with an older build (prior to Adobe Campaign 17.2 – build 8795).

A use case has been added to the Automating with Workflows guide: Sending personalized alerts to operators. [Read more](../../workflow/using/sending-personalized-alerts-to-operators.md)

The "Migrating to a new version" section has been updated. The documentation now only details the steps for a migration to Adobe Campaign Classic v7 from any older version, as it is no longer possible to migrate to Adobe Campaign v6.11. [Read more](../../migration/using/about-migration.md)

The "Retries after a delivery temporary failure" section has been clarified. [Read more](../../delivery/using/understanding-delivery-failures.md)

Links to the "Digital Content Editor" section have been added to the "Defining the email content" section. [Read more](../../delivery/using/defining-the-email-content.md)

The "Transactional messaging architecture" section has been updated with a warning specifying that the control and the execution instances cannot be installed on the same machine. [Read more](../../message-center/using/transactional-messaging-architecture.md)

The "Workflow monitoring" section has been updated with a note for builds between 8700 and 8977 (18.10), including a link to the technote on how to install the Workflow HeatMap package for these builds. [Read more](../../workflow/using/heatmap.md)

Added a use case on how to send an email with custom data fields using the Enrichment activity in a workflow. [Read more](../../workflow/using/email-enrichment-with-custom-date-fields.md)

Feature videos have been moved [here](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/overview.html).
