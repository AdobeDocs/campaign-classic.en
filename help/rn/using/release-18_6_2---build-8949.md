---
title: Release 18.6.2 - Build 8949
seo-title: Release 18.6.2 - Build 8949
description: Release 18.6.2 - Build 8949
seo-description: 
page-status-flag: never-activated
uuid: 72941f8f-0b84-4868-a768-8aa972459ef2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 79a6d3cf-2425-49b9-9b92-b56be26438bf
index: y
internal: n
snippet: y
---

# Release 18.6.2 - Build 8949{#release-build}

22 August 2018

## What's new? {#what-s-new-}

<table> 
 <thead> 
  <tr> 
   <th> Functionality<br /> </th> 
   <th> Description<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Query banding<br /> </td> 
   <td> When multiple Campaign users connect to the same FDA Teradata external account, you can now pass a query band (key/value pairs) specific to each user. Each time a Campaign user performs a query on the Teradata database, Adobe Campaign is now able to send meta data associated to the user. These data, which consist in a list of keys and values can then be used by Teradata administrators for audit purposes or to manage access rights, for example. <br /> The configuration steps are detailed below.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Improvements {#improvements}

* Email archiving logs have been enhanced, which makes it easier and clearer to check which emails have been successfully delivered or have failed through BCC archiving. (NEO-10675)
* Fixed an issue which led to the display of load balancer IPs instead of customer IPs in the tracking broadlogs. (NEO-11295)
* Fixed a random issue causing the properties of a delivery to be wrongly overwritten. (NEO-11015)
* Fixed a syntax error when sorting enrichment activity results. (NEO-11394)
* Fixed an issue when using calculated fields in a **[!UICONTROL Survey answers]** workflow activity. (NEO-11382)
* Tomcat has been updated to prevent vulnerabilities exploitation. (NEO-11503)
* Fixed an error with LATIN1 encoding when using an FDA Connection to a PostgreSQL database. (NEO-11299)
* Fixed an issue that occured when using the **[!UICONTROL Prepare the personalization data with a workflow]** delivery option. (NEO-11047)
* Fixed a postupgrade issue which prevented sending SMS from being sent when using an extended connector.
* Improved package import/export (log and region were added in the interface).
* Fixed an issue which displayed useless errors in the postupgrade log when a **[!UICONTROL Survey answers]** workflow activity was not fully configured.

## Technical evolutions {#technical-evolutions}

**Query banding**

A specific key (PROXYUSER or PROXYROLE) is used to associate a Teradata user or role to a Campaign user. A new permission has been added to use this proxy user/role. You need to add the GRANT CONNECT THROUGH access right to the database account (the one defined in the Teradata external account).

A new tab has been added in the Teradata external accounts. The **[!UICONTROL Query banding]** tab includes the following options:

* **[!UICONTROL Active]** : check this box to activate the feature.
* **[!UICONTROL Default]** : enter a default query banding that will be used if a user has no associated query banding. If there is no default query banding defined, the users who have no associated query banding will not be able to use Teradata.
* **[!UICONTROL Users]** : for each user, specify a query banding. You can add as many key/value pairs as you need. For example: ‘priority=1;workload=high;’

For more information on query banding, refer to these articles:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw) 
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

