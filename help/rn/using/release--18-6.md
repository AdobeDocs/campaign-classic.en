---
solution: Campaign Classic
product: campaign
title: Campaign 18.6 release notes
description: Release notes for Campaign 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
---
# Release 18.6{#release-18-6}

## Release 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 August 2018

>[!CAUTION]
>
>This build has been recalled. Please [upgrade to the latest build](../../production/using/build-upgrade.md) or contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**What's new?**

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
   <td> <p>When multiple Campaign users connect to the same FDA Teradata external account, you can now pass a query band (key/value pairs) specific to each user. Each time a Campaign user performs a query on the Teradata database, Adobe Campaign is now able to send meta data associated to the user. These data, which consist in a list of keys and values can then be used by Teradata administrators for audit purposes or to manage access rights, for example.</p><p>For more information, refer to the <a href="../../installation/using/external-accounts.md">detailed documentation</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Improvements**

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

**Technical evolutions**

Query banding

A specific key (PROXYUSER or PROXYROLE) is used to associate a Teradata user or role to a Campaign user. A new permission has been added to use this proxy user/role. You need to add the GRANT CONNECT THROUGH access right to the database account (the one defined in the Teradata external account).

A new tab has been added in the Teradata external accounts. The **[!UICONTROL Query banding]** tab includes the following options:

* **[!UICONTROL Active]**: check this box to activate the feature.
* **[!UICONTROL Default]**: enter a default query banding that will be used if a user has no associated query banding. If there is no default query banding defined, the users who have no associated query banding will not be able to use Teradata.
* **[!UICONTROL Users]**: for each user, specify a query banding. You can add as many key/value pairs as you need. For example: ‘priority=1;workload=high;’

For more information on query banding, refer to these articles:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw) 
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Release 18.6 - Build 8947{#release-18-6-build-8947}

25 June 2018

>[!CAUTION]
>
>This build has been recalled. Please [upgrade to the latest build](../../production/using/build-upgrade.md) or contact [technical support](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**What's new?**

<table> 
 <thead> 
  <tr> 
   <th> Functionality<br /> </th> 
   <th> Description<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Security improvements<br /> </td> 
   <td> A series of security improvements has been added to Campaign Classic. Improvements and fixes are listed below.<br /> </td> 
  </tr> 
  <tr> 
   <td> Support of Windows Server 2016<br /> </td> 
   <td> Adobe Campaign is now compatible with Windows Server 2016. Refer to <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic Compatibility matrix</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

decryptString

The **decryptString** function is deprecated. Refer to the [Deprecated and Removed Features](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) article.

For new customers, this function is now only used to decrypt the recipient's crypted ID in landing pages. To decrypt passwords stored in an external account, use the new **decryptPassword** function.

For existing customers, the behavior of this function is not changed but we recommend that you use **decryptPassword** instead of **decryptString**. The **XtkSecurity_Unsafe_DecryptString** compatibility option is added by the postupgrade and activated by default, allowing you to keep using the function. If you want to deactivate **decryptString**, deactivate the option.

decryptPassword

The **decryptPassword** function has been added. It allows you to decrypt a password stored in an external account. Refer to the [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) documentation for more information.

File APIs

For new installations, folder access via file APIs is limited to the **var**, **sftp** and temporary folders of Adobe Campaign.

For existing customers, file APIs can no longer access the **conf** folder of Adobe Campaign. The **XtkSecurity_Disable_JSFileSandboxing** compatibility option is added by the postupgrade and activated by default, allowing you to keep accessing the other folders. If you want to limit the access to the **var**, **sftp** and temporary folders of Adobe Campaign, deactivate the option.

**Patch**

* Fixed an issue that could affect SMS transactional message performance. (NEO-9812)
