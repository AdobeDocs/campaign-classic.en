---
product: campaign
title: Latest Release
description: Latest Campaign Classic Release Notes
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
---
# Latest release{#latest-release}

This page lists new capabilities, improvements and fixes coming with the **latest Campaign Classic Release Candidate version**.

>[!NOTE]
>
>Campaign **General Availability (GA) builds** are: [[!DNL Gold Standard] 11 release](../../rn/using/gold-standard.md#gs-11) and [Campaign 20.2.5 release](../../rn/using/release--20-2.md).

## ![](assets/do-not-localize/blue_2.png) Release 21.1.3 - Build 9330 {#release-21-1-3-build-9330}

_June 5, 2021_

**What's new?**

<table>
<thead>
<tr>
<th><strong>Integration with Adobe Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>The integration between Journey Orchestration and Adobe Campaign Classic is now GA. It allows Journey Orchestration to send emails, push notifications and SMS using Adobe Campaign Classic Transactional Messaging capabilities.</p>
<p>The connection between the Journey Orchestration and Campaign Classic instances is setup by Adobe at provisioning time.</p>
<p>For more information, refer to the <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html">Journey Orchestration documentation</a>. A step-by-step use case is presented in this <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html">section</a></p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>LINE channel enhancements</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>The following improvements have been added to LINE channel:
</p>
<ul> 
<li><p>Support for LINE video message type</p></li>
<li><p>Support for LINE Partner Registration API</p></li>
<li><p>Support retry of message sending in the event of LINE server-side error or network timeout</p></li>
</ul>
<p>For more information refer to the <a href="../../delivery/using/line-channel.md">detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA connector</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>You can now connect your Adobe Campaign Classic instance to your Vertica external database. This connection is managed through a new external account.</p>
<p>For more information refer to the <a href="../../installation/using/configure-fda-vertica.md">detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA connector</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>You can now connect your Adobe Campaign Classic instance to your Google Big Query external database. This connection is managed through a new external account.
</p>
<p>For more information refer to the <a href="../../installation/using/configure-fda-google-big-query.md">detailed documentation</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Security enhancements**

* Access to the **xtk:session#GetCnxInfo** API method returning the full database connection details is now restricted to admin users only. (NEO-27779)
* The deprecated decryptString function has been replaced with decryptPassword in CRM related JavaScript files.
* The tracking signature feature has been improved to reduce the risk of tracking redirection errors when third-party tools (email clients, internet browsers, safe link security tools) modify the tracked link.
* Fixed an issue which could prevent tracked URLs from working when containing uppercase characters. Tracked URLs signing mechanism is now case sensitive. (NEO-28414)

**Compatibility updates**

The following systems are now supported with Campaign:
* Google Big Query FDA connector
* Vertica FDA connector
* PostgreSQL 13

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Deprecated features**

* Starting Campaign 21.1 release, the Adobe Analytics Data Connector is deprecated. If you are using this connector, you need to adapt your implementation accordingly with the new connector Adobe Analytics Connector. 
For more information refer to the [detailed documentation](../../platform/using/adobe-analytics-connector.md).
* Support for Debian 8 is now deprecated.
* Following the deprecation of Oracle CRM in 20.3, the related external account has been removed from the interface.

Learn more in the [Deprecated and removed features page](../../rn/using/deprecated-features.md).

**Improvements**

* Extra checks have been added when saving a workflow to make sure that activity names are unique and that transitions are always followed by an activity.
* The **Billing (billing)** technical workflow now includes the tasks originally performed by the **Number of active billing profiles** (billingActiveContactCount) workflow, which has been removed. The email report sent each month by the workflow will now provide information on the number of active profiles on the instance. [Read more](../../workflow/using/about-technical-workflows.md).
* New **_keyOnMData** attribute has been added to be able to use a key for operations on memo data.

**Other changes**

* The openssl third-party for Windows has been updated to version 1.1.1h.
* In the Debian package description, nlserver has been changed to Adobe Campaign Classic server. 

**Patches**

* Fixed an issue when editing the session timeout to log out users after a specific amount of time where users remained logged in even after the set time.
* Fixed an issue where deliveries were displayed as read-only but could still be edited in the deliveries properties.
* Fixed an error which caused the editing tool bar to disappear when designing a web application.
* Fixed an error which displayed the text version of an email with Adobe Campaign Classic headers when adding a link to an email. (NEO-29211
* When using FDA over HTTPs connection, the **Mid-sourcing (delivery logs)** (defaultMidSourcingLog) workflow was stuck in the timeframe set by the **NmsMidSourcing_LogsPeriodHour** option. This would prevent records from being updated with data that occurred after this set timeframe. (NEO-30833)
* Fixed an issue which occurred after executing the message center synchronization workflow. Every time a delivery objects folder was moved to a custom folder, the workflow would move the deliveries back to the generic **Transactional message history** folder. (NEO-27445)
* Fixed an issue which displayed an error message when trying to display the **Broadcast statistics**, **Tracking indicators**, and **Statistics of the sharing activities** reports. 
* The **Oracle On Demand** workflow activity has been removed from the interface following Oracle CRM connector deprecation.
* Fixed an issue which stopped the execution of processing workflows after the daily restart of the workflow server (wfserver) module. (NEO-30047)
* Fixed an issue that prevented the MX management document from being updated, which could negatively impact IP reputation. (NEO-29897)
* Fixed issues that caused web process crashes when receiving a SOAP call. (NEO-28796) (NEO-29600)
* Fixed an issue that caused the SAP HANA FDA index creation to fail. (NEO-29664)
* Fixed an issue which could keep transactional messages in **Waiting** state when performing SOAP calls containing a header. (NEO-28737)
* Fixed an issue that occurred when using the Teradata FDA connector: all the temporary tables were created on only one node of the cluster, which could end up consuming the whole spool space and make Teradata crash. The temporary tables are now generated on many nodes. (NEO-28230)
* Fixed an issue when using web applications which led tracking tags to generate incorrect primary keys into the **nms:trackingURL** schema. (NEO-27931)
* Compatibility to ODBC 3.x has been enhanced to ensure error message accuracy.
* Fixed an issue which could lead to console crashes when custom content templates were used in email deliveries. (NEO-31547)
* Fixed an issue that prevented Tomcat from sending valid responses due to a slow connection or large response size.
* Fixed an issue which could occur when reading UUID from a PostgreSQL database.
* Fixed an issue which could lead to performance issues when searching on proposition data linked to offers. (NEO-27554)
* Fixed an issue which lead to the Web process not responding when the IMS service was activated but not responding.
* Fixed an issue which prevented you from sending a delivery with a group of proofs due to a specific joining mechanism that failed the delivery personalization. (NEO-14391)
* Fixed an issue which failed to send an alert with the alert activity if a query and an enrichment activity targeted the delivery table. (NEO-25157)

## ![](assets/do-not-localize/red_2.png) Release 21.1.2 - Build 9282 {#release-21-1-2-build-9282}

_April 15, 2021_

* Password management has been improved to optimize security.
* Fixed an issue that could cause MTA crashes.

## ![](assets/do-not-localize/red_2.png) Release 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_February 22, 2021_

**Security enhancements**

* The console authentication mechanism has been improved to optimize security. (NEO-26944)
* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-28532)

**Compatibility updates**

The following systems are now supported with Campaign:

* Salesforce API version 49 is now supported when using Salesforce CRM external account.

**Deprecated features**

The **Technical Deliverability Monitoring** report is now deprecated. 

Learn more in the [Deprecated and removed features page](../../rn/using/deprecated-features.md).

**Improvements**

**Email Feedback Service (EFS)** is a scalable service which captures feedback from the Enhanced MTA directly, thus improving reporting accuracy. This capability is released as a private beta and will be progressively available to all customers in future releases.

* All categories of feedback are now captured for complete and precise reporting.
* Calculation of the Delivered indicator is now based on real-time feedback from the Enhanced MTA for improved accuracy and reactivity.
* EFS solves the problem of delays with synchronous soft bounces reporting.

For more information refer to the [detailed documentation](../../delivery/using/sending-with-enhanced-mta.md#efs).
If you’re interested in participating in this private beta, fill out this [form](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) and we’ll get back to you.

**Other changes**

* Transfer speed has been improved for large tracking logs by using compression.
* Workflow Heatmap has been improved to avoid timeouts when running workflows with multiple activities. (NEO-27423).
* Fixed an issue which could allow an offer to be presented even if its end date was passed. Campaign Classic now takes into account the end date's whole timestamp rather that the date only. (NEO-27590)
* The Google+ link has been removed from the **Social network sharing links** personalization block.
* Fixed an issue after the implementation of a bug fix in the last release. A check was added on the hostname when connecting using SSL/TLS which led SMS deliveries to fail. Hostname verification has been disabled for most protocols such as POP3, SMS and HTTP with proxy and the certificate check for the SMS external account has been improved with three values (NEO-29581). [Learn more](../../delivery/using/sms-protocol.md#skip-tls)

**Patches**

* Fixed an issue which prevented the Tab, Enter and Escape keyboard shortcuts from working on the new logon screen.
* Fixed a refresh issue which caused the name of a newly created workflow to be replaced with the default value after saving (NEO-26106).
* Fixed an issue that occurred when running workflows where a new field was added as part of an **Enrichment** activity prior to a **Delivery** activity using an **External file** target mapping: unwanted fields were added to the **External file** target mapping. (NEO-27687)
* Fixed an issue that caused some characters in the source code to be altered when reopening a web application previously created and saved. (NEO-27597)
* Fixed an issue that could occur when upgrading to a build including the new signature mechanism for tracking links (from Build 19.1.4 and Campaign 20.2): when several templates were associated to an event, upgrading could cause the wrong template to be selected when sending the transactional message. (NEO-28326)
* Fixed an issue that caused the MTA to become unresponsive and unable to process deliveries unless restarted. (NEO-27455)
* Fixed an issue on MSSQL database related to timestamp management during bulk load operations for a datetime type column.
* Fixed a workflow query issue when using Redshift xtk functions. The SubDays, SubSeconds, SubMinutes and SubHours now accept both Redshift timestamp types (NEO-24962).
* Fixed an issue which displayed a script error message when trying to preview a report with Anonymous access. (NEO-27081)
* Fixed an issue which could reduce the memory usage on the server when performing delivery analysis.
* Fixed an issue which could prevent the instance from working when trying to run specific complex queries.
* Fixed an issue which could prevent the **Synchronizing Twitter pages** technical workflow from running. (NEO-28634)
* Fixed an issue which could display an error message related to the decryptPassword function when trying to publish on Twitter using the **Tweet (twitter)** delivery template. (NEO-28216)
* Fixed an issue which occurred when using a **Javascript** activity to make an HTTP request in a workflow. After defining the port number in the Host name, the call would fail with the following error (NEO-29146): 

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
``` 

* Fixed an issue that prevented new deliveries with target data personalization from being sent (NEO-30323).
* Fixed an issue where several crashes occurred in the marketing instance causing core files.
* Fixed an issue which led the **Tracking** workflow to fail with the following error (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Fixed an issue which occurred when creating and saving a delivery within the **Targeting & Workflow** tab of a campaign: the preview would fail with the following error (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Fixed an error which occurred when setting up an external account between a marketing instance and an Adobe Campaign Standard instance or a Campaign Classic mid-sourcing instance and using the option "DisableFOH2=1". When using the "DisableFOH2=1" option in the external account, connections were not properly closed and would pile up resulting in the following error (NEO-26258): 

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Fixed an error with SMS when connection issues occurred between the server and provider. The connection would then be automatically disabled by the MTA child. Adobe Campaign Classic would not try to connect to this failing connection as long as a new child had not been started.
