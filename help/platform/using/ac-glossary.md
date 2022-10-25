---
product: campaign
title: Glossary for Adobe Campaign
description: Glossary for Adobe Campaign
role: User, Data Architect
level: Beginner
hide: yes
hidefromtoc: yes
---
# Adobe Campaign Glossary{#ac-glossary}

Below is the definition of the key terms and concepts in Adobe Campaign, with links to related documentation. Click a term to display its definition.

## A - D{#sec-1}

+++**A/B testing**

A/B testing is a capability which lets the user define two to three email variants: each variant is sent to population samples in order to determine which has the best result. Once determined, the winning variant is then sent to the remaining population.

Learn more about [A/B testing](../../delivery/using/get-started-a-b-testing.md).
+++

+++**Access management**

Access management enables admins to assign access and permissions to users of Adobe Campaign. Permissions include the ability to view and/or use Adobe Campaign features, such as executing workflows, defining schemas, and managing audiences.

Learn more about [Access management](access-management.md).
+++

+++**ACS Connector**

ACS Connector (Prime Offering) bridges Adobe Campaign v7 and Adobe Campaign Standard. It is an integrated feature in Campaign v7 that automatically replicates data to Campaign Standard, uniting the best of both applications. Campaign v7 has advanced tools to manage the primary marketing database. The data replication from Campaign v7 allows Campaign Standard to leverage the rich data in a user-friendly environment. 

Learn more about [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++

+++**Activity**

An activity is a palette item which is added to a workflow to define an execution functionality. The activity is a container that executes a task. In a workflow, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

Learn more about [Workflow activities](../../workflow/using/about-activities.md).
+++

+++**Active profile**

Profiles are considered active if they have been targeted or communicated with in the past 12 months via any channel. According to your contract, each of your Campaign instances is provisioned with a specific number of active profiles that are counted for billing purposes.

Learn more about [Active profiles](about-profiles.md#active-profiles).
+++

+++**Approval workflow activity**

*Context: Campaign Distributed Marketing*

The Local Approval activity is a workflow activity which is used to set up a delivery approval process before the messages are sent.

Learn more about the [Local Approval Activity](../../workflow/using/local-approval.md).
+++

+++**Audience**

An audience is the resulting set of profiles that meet the criteria of a filter definition, based on rules and attributes. 

Learn more about [Audiences](../../campaign/using/marketing-campaign-target.md).
+++

+++**Audit trail**

Audit trail captures, in real-time, a comprehensive list of actions and events occurring within your Adobe Campaign instance. It includes a self-serve way to access a history of data to help answer questions such as: what happened to your workflows, and who last updated them or what did your users do in the instance. 

Learn more about [Audit trail](../../production/using/audit-trail.md).
+++

+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**Batch mode**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the batch mode lets the Offer Engine select the best offer (or offers) for a set of contacts. Eligibility/prioritization rules are applied to all of the set’s contacts. 

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Campaign**

Campaign is an interface to coordinate, define and execute marketing campaigns. Campaigns can contain one or more workflows, deliveries, documents and other related data points into a single, easy-to-use interface. 

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Channel**

A channel is a medium through which a communication is sent. Built-in channels in Adobe Campaign are email, SMS, direct mail, Push notifications, LINE, and Twitter. Custom channels can be implemented for non-standard channel requirements. 

Learn more about [Channels](../../delivery/using/communication-channels.md).
+++

+++**Client console**

Campaign client console is a rich client which enables you to connect to your Campaign application server(s). The client console executable (.exe) application is installed on a computer with a Microsoft Windows operating system. Campaign Client console centralizes all capabilities and settings. 

Learn more about [Client console](../../platform/using/adobe-campaign-workspace.md).
+++

+++**Content approval**

Content approval is the process of having a separate Operator or group of Operators approve the content of a delivery before it can be sent. 

Learn more about [Content approval](../../campaign/using/marketing-campaign-approval.md).
+++

+++**Control groups**

Use Control groups to measure the impact of your campaigns by excluding a portion of their audience. Operators can compare the behavior of the target population who did receive the message with the behavior of contacts who were not targeted. Based on the sending logs, Operators can also target a control group in future campaigns.

Learn more about [Content approval](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**Control Panel**

The Control Panel helps you increase efficiency in your work as a product admin of Adobe Campaign, by allowing you to manage settings and track usages for each of your instances. Its intuitive interface lets you easily monitor usage of key assets, as well as perform administrative tasks such as IP addresses allow list addition, SFTP storage monitoring, key management, and more.

Learn more about [Content approval](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html).
+++

+++**Cubes**

*Context: Marketing Analytics*

Cube is an Adobe Campaign intuitive data exploration tool which helps users create and share dynamic reports.

Learn more about [Cubes](../../reporting/using/about-cubes.md).
+++

+++**Custom resources**

Adobe Campaign comes with a pre-defined data model, where data types are defined through the installation of various packages. Operators can enrich the data model that is provided by extending the resources to add custom fields or custom tables, such as transaction or product tables.

Learn more about [Custom resources](../../configuration/using/about-schema-edition.md).
+++

+++**Data Model**

Campaign data model is a set of schemas that define the data types and their relationships (links). The data model is an abstract definition that is physically implemented with a database that contains the actual data.

Learn more about [Custom resources](../../configuration/using/about-data-model.md).
+++

+++**Database cleanup workflow**

The Database cleanup workflow deletes obsolete data to avoid exponential growth of the database. The workflow is triggered automatically without user intervention.

Learn more about [Database cleanup workflow](../../production/using/database-cleanup-workflow.md).
+++

+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The “Per-Dedicated Server” designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++

+++**Deliverability**

*Context: Email Deliverability*

A metric that allows Operators to measure the success of a campaign in reaching their recipients’ inbox without bouncing or being marked as spam.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++

+++**Delivery**

A delivery is a specific marketing communication item which is sent to an audience on a specific channel (email, SMS, Push notification, etc.). Also known as a "touch" in marketing terminology. 

Learn more about [Deliveries](../../delivery/using/communication-channels.md).
+++

+++**Delivery analysis**

Delivery analysis is the preparation of the delivery. This process combines the content with the recipient profile data to produce the personalized email that the recipient receives. The delivery analysis logic can exclude recipients from the target or stop the delivery altogether, based on the defined logic. This process also includes the evaluation of dynamic content logic and the insertion of offers specific to the individual recipient profile. 

Learn more about [Delivery analysis](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**Delivery logs**

Delivery logs contain information generated when sending of a message. These logs show the detail of the sending, which message has been prepared, ignored, sent or failed. They can be accessed directly from the delivery dashboard.

Learn more about [Delivery logs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

+++**Delivery Fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++

+++**Delivery outline**

*Context: Direct Mail*

A delivery outline is a structured set of elements (documents, stores, promotional coupons, etc.) created by the company and for a particular campaign. It is used in the context of direct mail deliveries.

Learn more about [Direct Mail](../../delivery/using/about-direct-mail-channel.md).
+++

+++**Deployment Wizard**

The deployment wizard defines the parameters of the Campaign instance, such as the default namespace, database cleanup schedule, data retention periods, and other technical settings.

Learn more about [Deployment Wizard](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**Descriptive Analysis**

Descriptive Analysis is a context-sensitive reporting tool which can be used to examine data in the worktable of a workflow, data selected in a folder or to do deep dives on the targets and exclusions of selected deliveries.

Learn more about [Descriptive Analysis](../../reporting/using/about-descriptive-analysis.md)
+++

+++**Distributed marketing**

*Context: Distributed marketing*

The Distributed Marketing add-on offers to Campaign operators a collaborative workspace for implementing campaigns between central entities (headquarters, marketing departments, etc.) and local entities (sales points, regional agencies, etc.). This cooperation is based on a shared workspace known as the **list of Campaign packages**, where centrally created campaign templates and instances are offered to local entities.

Learn more about [Distributed marketing](../../distributed/using/about-distributed-marketing.md)
+++

+++**Distribution of values**

The Distribution of values is a tool which shows the distribution of the values for a schema attribute that currently exist in the database. This helps you determine what values are available, their counts and percentages, and to avoid issues with capitalization and spelling of values when creating a query or expression.

Learn more about [Distributed marketing](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**Domain delegation**

Subdomain configuration allows you to configure a sub-section of your domain (technically a “DNS zone”) for use with Adobe Campaign.
Domain delegation lets Adobe control and maintain all aspects of DNS that are required for delivering, rendering and tracking of email campaigns.

Learn more about [Domain delegation](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html)
+++

## E - H {#sec-2}

<!--
+++**E4X**

The version of Javascript that is used in Adobe Campaign Classic. Sometimes called ECMAScript, it is an extension of Javascript that allows the mixing of Javascript and XML primitives in the same code. Note that E4X is classified as a deprecated language. 
+++
-->

+++**Eligibility rules**

*Context: Campaign Interaction*

Eligibility rules are constraints applied to an environment, category or offer concerning the validity period, target and weight. They let Operators ensure that an offer is in line with the targeted contact. In the offer environment, eligibility rules include presentation rules applied to the offers and the recipients to target. In the category, eligibility rules let Operators limit the validity of the category in time, define application themes and determine the recipients to target. They can also define a multiplier weight for a given period of time. This lets Operators share the rules for offers in other categories and so simplifies their management. In an offer, eligibility rules let Operators limit the validity of offers in time and determine the recipients to target. 

Learn more about [Eligibility rules](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Eligible offer**

*Context: Campaign Interaction*

An eligible offer is an offer meeting the constraints defined upstream that can be consistently offered to a target.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Email BCC**

Email BCC capability sends an exact copy in EML format of a corresponding delivered email, which is saved to a dedicated BCC email address where the emails can be processed and archived by the sender in an external system.

Learn more about [Email BCC](../../delivery/using/email-parameters.md#email-bcc).
+++

+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++

+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++

+++**Enrichment activity**

The Enrichment activity is an advanced workflow activity that allows Operators to enrich the generated worktable data that will be processed in the workflow. This activity is generally used following targeting activities or after importing a file and before activities that use of targeted data. Enrichments can transform the inbound transition data and configure the activity to complete the output transition with enhanced data. It allows the Operator to combine data from multiple data sets, or to create links to a temporary resource.

Learn more about [Enrichment activity](../../workflow/using/enrichment.md).
+++

+++**Enumerations**

An enumeration is a data type defined in schemas or at the Platform level that defines the valid input values for a field. Enumerations appear in the user interface and in query builders as a picklist.

Learn more about [Enumerations](../../platform/using/managing-enumerations.md).
+++

+++**Explorer view**

The Explorer view is a hierarchical display of the folders that hold Adobe Campaign artifacts and data. Note that the folder system in Adobe Campaign does not function like a typical treeview, in that each folder holds data of a specific type, such as Deliveries, Workflows or Offers.

Learn more about [Explorer view](../../platform/using/adobe-campaign-explorer.md).
+++

+++**External accounts**

External accounts are entry and exit points for the product to connect to other environments and technologies. External accounts define the connection parameters the product uses to send data to or receive data from other sources. Typical external account types are connections for SFTP sites, telecoms to support the sending of SMS, mailboxes for the processing bounces, or connections to external databases. 

Learn more about [External accounts](../../installation/using/external-accounts.md).
+++

+++**Fatigue management**

*Context: Campaign Optimization*

Fatigue management helps you control the frequency and quantity of messages to avoid over-solicitation of recipients and is often applied using a typology rule.

Learn more about [Fatigue management](../../campaign-opt/using/pressure-rules.md).
+++

+++**Federated Data Access (FDA)**

Federated Data Access supports the extension of the client data model to include a third-party database. It will automatically detect the structure of the targeted tables and use data from the SQL sources. You can access external data without changing the structure of Adobe Campaign data.

Learn more about [Federated Data Access](../../installation/using/about-fda.md).
+++

+++**File extraction approval**

*Context: Direct Mail*

The File extraction approval is the process of having a separate Operator or group of Operators approve the content and configuration of an extracted file before it is sent to an outside vendor, such as for a direct mail delivery.

Learn more about [File extraction approval](../../delivery/using/validating.md).
+++

+++**Filtering dimension**

The filtering dimension is the schema that contains the data or attributes used by a query to filter the desired rows. The Filtering dimension schema must be directly linked to the defined Targeting dimension to allow Adobe Campaign to cross the database join and return the respondent rows.

Learn more about [Filtering dimension](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**Folder**

A folder is an Explorer view item that holds database records of a specific data type. The exception is the Generic folder type that is used as an organizing element and does not contain any data itself, only other folders. 

Learn more about [Folders](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Folder View**

The Folder View is a special Explorer folder type that is used to display all records of a selected data type, no matter what folder it belongs to. Folder views are used as an administrative tool to manage partitioned data or data that is distributed among many folders.

Learn more about [Folder View](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Forms**

Forms define the interface representation for a specific schema type. Forms are the means used to easily create and edit data elements in the product, such as Recipients, Deliveries and Campaigns. All interface elements in Adobe Campaign are created in the product itself using Forms. Note that forms are optional and not all schemas have forms. 

Learn more about [Forms](../../configuration/using/identifying-a-form.md).
+++

+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++

+++**Heatmap**

Campaign Heatmap is a table showing workflow execution information for a 24-hour period. It displays the distribution of workflows across the period by hour and by 5-minute intervals. Heatmap is used to evaluate server load and to determine the workflow activities that are consuming the most resources.

Learn more about [Heatmap](../../workflow/using/heatmap.md).
+++

+++**Hybrid deployment**

Hybrid deployment is a combination of on-demand services and on-premise software deployed to function together.

Learn more about [Hybrid deployment](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

+++**Identification mode**

*Context: Campaign Interaction*

Refers to a Contact’s status. It can be explicit, implicit or anonymous. 

* **explicit**: the contact is identified following their login onto the channel interface.
* **implicit**: the contact has been identified by a cookie (permanent or session). It can be processed as an anonymous or identified contact.
* **anonymous**: the contact cannot be identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery’s recipients. The insertion of the images based on an emails system’s “download images” functionality is what generates an “open” entry in Campaign’s tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++

+++**Inbound interaction**

*Context: Campaign Interaction*

An inbound interaction is an interaction following an incoming call generated by the action of a contact in a channel, such as web, call center or mobile. This type of interaction is generally processed in unitary mode (i.e., per recipient).

Learn more about [Inbound interaction](../../interaction/using/about-inbound-channels.md).
+++

+++**Inbox rendering**

Inbox rendering is the generation of email previews, which ensures the message will be displayed to the recipients in an optimal way on a variety of web clients, web mails and devices. Adobe Campaign leverages the Litmus, which allows email content creators to preview their message content in over 70 email renderers, such as the Gmail inbox or the Apple Mail client.

Learn more about [Inbox rendering](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**Instance Settings**

Instance settings are configuration details of an Adobe Campaign instance. These settings are defined in the Deployment wizard (Tools>Advanced>Deployment Wizard) or in the server and/or instance configuration files.

Learn more about [Instance Settings](../../installation/using/about-initial-configuration.md).

+++

+++**Jobs (Import and export)**

Jobs are managed by a wizard system that simplifies the import and export of data into and out of the product. Jobs use the templating system for simplicity and consistency and can be defined to execute on a schedule.

Learn more about [Import and Export jobs](../../platform/using/get-started-data-import-export.md).
+++

+++**Lists**

A list is a static dataset. Lists are audiences or segments that are imported into Campaign from other sources (Audience Manager, Experience Platform, database, etc.), and are seen in the interface as Imported Lists.   

Learn more about [Lists](../../platform/using/creating-and-managing-lists.md).
+++

+++**Local Cache**

Information that is stored locally on the operator’s computer. Cached information is used by the console to reduce the required traffic to the server and improve performance. Periodic clearing of the local cache (on the File menu) updates the stored information and improves performance and stability.  

Learn more about [Local Cache](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**Marketing Resource Management (MRM)**

*Context: Marketing Resource Management (MRM)*

The **Marketing Resource Management (MRM)** module in Adobe Campaign lets you control marketing actions in a collaborative mode by providing complete management and real-time tracking of the tasks, budgets, and marketing resources involved. Adobe Campaign operators can coordinate their actions and approve their progress at all stages via complete validation processes and appropriate tracking tools: reporting, tracking of approvals, notifications, discussion forums, etc.

Learn more about [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**Named rights**

The granular database access rights that are used to define Operator Group access and privileges (roles). Named rights are populated during the installation of the product and by importing various packages that define specific functionality of the tool. Custom Named Rights can be created to support client business requirements. 

Learn more about [Named rights](../../platform/using/access-management-named-rights.md).
+++

+++**Namespace**

A partition that separates customer data types from Adobe Campaign’s native datatypes in the data model. Also used to facilitate the migration of definitions from one instance to another, such as moving a schema or template from the Development instance to the Production instance. 

Learn more about [Namespace](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

+++**Navigation Bar**

The navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++

+++**Navigation Tree**

The main navigation in the Explorer view of Adobe Campaign. The navigation tree works like a file browser (e.g. Windows Explorer). Folders may contain sub-folders. Selecting a node displays the view corresponding to the node. The view displayed is a list associated with a schema and an input form to edit the selected line. You can customize the navigation tree and set permissions on folders.

Learn more about [Navigation Tree](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**Objectives**

*Context: Marketing Resource Management (MRM)*

Within the campaign, program or plan, Operators can state a list of objectives. These are quantified values to be reached. At the end of the campaign, program or plan, the MRM module lets Operators compare the objectives and results in dedicated reports. 

Learn more about [Objectives](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**Offer Catalog**

*Context: Campaign Interaction*

Set of offers defined in Adobe Campaign that can be selected during an interaction. The catalog is organized hierarchically with each node corresponding to a category. 

Learn more about [Offer Catalog](../../interaction/using/offer-catalog-overview.md).
+++

+++**Offer contact**

*Context: Campaign Interaction*

A contact from an inbound interaction. During engine call processing, the contact is associated with a targeting dimension. Non-identified, anonymous contacts are attributed to the visitor targeting dimension. There are two types of contacts, identified and anonymous:

* **Identified contact**: a contact that has voluntarily been identified on the channel. In outbound interactions, the contact is automatically identified.
* **Anonymous contact**: a contact that has not voluntarily subscribed through the channel but can be implicitly identified through a cookie. This terminology is only used for incoming interactions.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Offer Design environment**

*Context: Campaign Interaction*

The Offer **Design Environment** is the environment in which operators create offers, define typology rules, and select the schema that will be targeted by the offers. The table for storing generated offer propositions are also defined by the environment. By default, the Interaction add-on comes with a **Design** environment and a **Live** environment linked to it. Both environments are pre-configured to target the built-in recipient table.

Learn more about [Design environments](../../interaction/using/fundamental-principles.md).
+++

+++**Offer engine arbitrage**

*Context: Campaign Interaction*

Selecting offers that will be shown on an environment (eligible offers). The arbitrage principle ranks offers by priority according to the criteria defined in the categories and offers. 

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Offer engine pruning**

*Context: Campaign Interaction*

The process of deleting offers that are not eligible for selection. Executed prior to the offer engine arbitrage step. 

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Offer environment**

*Context: Campaign Interaction*

The root folder which defines an offer catalog, its available spaces and the environment’s pre-defined filters. Operators need to create one environment for each targeting dimension. There are two types of Offer environments: Design and Live.

Learn more about [Environments](../../interaction/using/fundamental-principles.md).
+++

+++**Offer Live environment**

*Context: Campaign Interaction*

Environment linked to a Campaign **Design environment**. It contains read-only offers whose content and eligibility have been approved via the **Design environment**. They can be selected for presentation on a website or to be inserted in an outbound message. 

Learn more about [Live environments](../../interaction/using/fundamental-principles.md).
+++

+++**Offer preview**

*Context: Campaign Interaction*

Preview of the offer as it is displayed in its folder. It is accessible from the offer preview tab or from the contact profile. 

Learn more about [Offer preview](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**Offer presentation rules**

*Context: Campaign Interaction*

Typology rules referenced in the offer environment, which let Operators exclude specific offers by taking the recipient’s proposition history into account. 

Learn more about [Offer presentation rules](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**Offer proposition**

*Context: Campaign Interaction*

An offer proposition is the result of the action which consists of presenting an offer to a contact in a given offer space, for example the banner on a website, an email or SMS content. This result is stored in the offer propositions table which defines the offer, the recipient and the timestamp, providing a record of all offers a recipient has received.

Learn more about [Offer propositions](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**Offer representation**

*Context: Campaign Interaction*

An offer proposition is the result of the action which consists of presenting an offer to a contact in a given offer space, for example the banner on a website, an email or SMS content. This result is stored in the offer propositions table which defines the offer, the recipient and the timestamp, providing a record of all offers a recipient has received.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Offer simulation**

*Context: Campaign Interaction*

An offer simulation lets Operators test offer distribution across a defined scope (delivery date, target segment, number of offers, theme, etc.) before actually sending the offers. It can be used to adjust offer priorities and eligibility rules to maximize offer effectiveness.

Learn more about [Offer simulations](../../interaction/using/about-offers-simulation.md).
+++

+++**Offer space**

*Context: Campaign Interaction*

An offer space is a folder defining the location where the offer is exposed. Defining a space lets you specify the channel used, build the content of the offer, and specify the offers presented. The offer space is the interface between the channel and the offer engine. 

Learn more about [Offer simulations](../../interaction/using/creating-offer-spaces.md).
+++

+++**Offer themes**

*Context: Campaign Interaction*

Offer themes are keywords defined in a category, which lets Operators filter offers when they are presented. Themes allow for the non-hierarchical selection of offers from the catalog structure. 

Learn more about [Offer themes](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**Offer weight**

*Context: Campaign Interaction*

The offer weight is based on formulas which precisely define the relevance of an offer in order to allow the engine to select the most relevant offer. Weights are defined in the offers and multipliers are defined in the categories. Eligible offers are taken into account in decreasing weight order. 

Learn more about [Offer weight](../../interaction/using/creating-an-offer.md#offer-weight).
+++

## Q - T {#sec-5}

## U - Z {#sec-6}