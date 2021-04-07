---
solution: Campaign Classic
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
>

## ![](assets/do-not-localize/blue_2.png) Release 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

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
