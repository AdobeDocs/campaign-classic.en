---
product: campaign
title: Campaign Classic deprecated and removed features
description: This page lists deprecated and removed features in Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
---
# Deprecated and removed features {#deprecated-and-removed-features}



Adobe constantly evaluates product capabilities to identify older features that should be replaced with more modern alternatives to improve overall customer value, always under careful consideration of backward compatibility. As Adobe Campaign Classic works with 3rd party tools, compatibility is updated on a regular basis, in order to implement supported versions only. Versions which are no longer compatible with Adobe Campaign Classic are listed below and in the [Compatibility matrix](../../rn/using/compatibility-matrix.md).

To communicate the impending removal/replacement of Campaign Classic capabilities, the following rules apply:

* Announcement of deprecation comes first. While deprecated capabilities can still be available and supported for existing users, they will not be further enhanced, nor documented. 
* Removal of deprecated capabilities will occur in the following release at the earliest. Actual target date for removal is announced in this page. 

This process gives customers at least one release cycle to adapt their implementation to a new version or successor of a deprecated capability, before actual removal. 

>[!NOTE]
>Adobe Campaign releases and new capabilities are listed in the [Release Notes](../../rn/using/latest-release.md).

## Deprecated features {#deprecated-features}

This section lists features and capabilities that have been marked as deprecated with latest Campaign Classic releases. 

Generally, features that are planned to be removed in a future release are set to deprecated first. These features and capabilities are either no longer available for new Campaign Classic customers, or should not be used for any new implementation. They are also removed from product documentation.

Customers are advised to review if they make use of the feature/capability in their current deployment, and make plans to change their implementation. Please refer to the target removal date to plan your environment and project updates accordingly.

<table> 
 <tbody> 
   <tr>
   <td><strong>Feature</strong></td>
   <td><strong>Details</strong></td>
  </tr>
  <tr>
 <td>Campaign (Neolane) legacy SDK</td>
 <td><p>The Campaign (Neolane) SDK for mobile applications is now deprecated. Instead, use the Adobe Experience Platform Mobile SDK by configuring the Adobe Campaign extension in the Data Collection UI. The Adobe Experience Platform Mobile SDK helps power Adobe's Experience Cloud solutions and services in your mobile apps. SDKs configuration is managed through the Data Collection UI for flexible configuration and extensible, rules-based integrations. Learn how to configure the Mobile App channel in <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push-settings">Campaign v8 documentation</a>.</p>
<p>Target removal date: Summer 2025 </p>
</td>
</tr>
<tr>
 <td>Social Marketing with Facebook</td>
 <td><p>Social Marketing with Facebook is now deprecated. You can use X (formerly known as Twitter) integration to post on social media, or work with Adobe to create a custom channel.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>ACS Connector</td>
 <td><p>ACS Connector (Prime offering) is now deprecated. You can use Campaign export/import capabilities to extract and inject data in both products.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Removed features {#removed-features}

This section lists features and capabilities that have been removed from Campaign Classic.

<table> 
 <tbody>
  <tr> 
   <td><strong>Feature</strong></td>
   <td><strong>Details</strong></td>
  <tr>  
      <tr>
  <td>Adobe Analytics Data Connector<br></td>
   <td><p>The Adobe Analytics Data Connector has been removed on August 17,2022. It had been deprecated with Campaign 21.1.3 release.</p>
   <p>If you are using this connector, you need to adapt your implementation accordingly. <a href="../../integrations/using/gs-aa.md">Learn more</a></p>
  </td>
 </tr>
    <tr>
  <td>Technical Deliverability Monitoring Report<br></td>
   <td><p>The Technical Deliverability Monitoring Report is no longer available. It had been deprecated with Campaign 21.1.3 release.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>OAuth Authentication (OAuth and JWT)<br></td>
  <td><p> Triggers integration authentication originally based on OAuth authentication setup to access pipeline has now been changed and moved to Adobe I/O. This authentication mode had been deprecated with Campaign 20.3 release.<p>
  <p>If you were using Triggers integration, learn how to adapt your implementation <a href="../../integrations/using/about-triggers.md#implement">in this page</a>.</p> 
  <p>For more information on OAuth Authentication depreciation, refer to this <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">page</a></p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Reporting<br></td>
   <td><p>Following Adobe Flash Player EOL, the Gauge report and Chart rendering engine are no longer available. <a href="../../reporting/using/creating-a-new-report.md">Learn more</a></p>
  </tr>
  <tr>  
   <td>Fax channel<br></td>
   <td><p>Starting Campaign 21.1.3 release, the Fax channel is no longer available. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Learn more</a></p>
  </tr>
  <tr>
  <td>Demdex domain<br></td>
  <td><p> Starting Campaign 21.1.3 release, the demdex domain used to import and export audiences to the Adobe Experience Cloud is no longer available. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Learn more</a></p> 
  </td>
  </tr>
   <tr> 
   <td>Windows NT authentication<br></td>
   <td><p>Starting Campaign 20.3 release, Windows NT authentication has been removed from the available authentication methods when configuring a new database with a Microsoft SQL Server.. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Learn more</a></p></td>
  </tr>
   <tr> 
   <td>File-based email archiving<br></td>
   <td><p>Starting Campaign 20.2 release, file-based email archiving is no longer available. Email archiving is now available through a dedicated BCC email address. <a href="../../installation/using/email-archiving.md">Learn more</a></p></td>
  </tr> 
   <tr> 
   <td>Lead management</td>
   <td><p>Starting Campaign 20.2 release, the Leads Management package is no longer available. Similar functionality can be implemented via other native workflow activities and data model modifications.</p></td>
   </tr>
   <tr>
   <td>Campaign APIs documentation - jsapi.chm file</td>
   <td>Starting Campaign 19.1 release, Campaign Classic APIs are available in a dedicated page. If you were using the legacy jsapi.chm file, you should now refer to <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html">the new online version</a>.</td>
  </tr> 
  <tr> 
   <td>Campaign Orchestration - Predictive marketing</td>
   <td>Starting Campaign 18.10 release, the predictive marketing capabilities are no longer available.</td>
  </tr> 
  <tr> 
   <td>Web applications - Microsites</td>
   <td>Starting Campaign 18.10 release, Microsites are no longer available. You can improve security by restricting access to only dedicated domains on Adobe Campaign configuration files, and use personalized URLs in Campaign by using DNS aliases.</td>
  </tr> 
  <tr> 
   <td>Push Notifications - iOS Binary Connector</td>
   <td>Per Apple's recommendation, Adobe has removed the legacy iOS Binary Connector starting Campaign 18.10 release. The more capable and more efficient HTTP/2-based connector is already available.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>Starting Campaign 18.6 release, for security reasons, <em>decryptString</em> API is no longer available by default for new installations.</p> 
   <p>In the context of a postupgrade to 18.6 (and later), this API is no longer activated, and has been replaced by the <em>decryptPassword</em> function. <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">Learn more</a></p></td>
  </tr> 
   <tr> 
   <td>Mobile channel - MMS and WAP Push messages</td>
   <td>Starting Campaign 18.4 release, MMS and Wap Push channels are no longer available. As a replacement, you can leverage <a href="../../delivery/using/sms-channel.md">SMS</a> and <a href="../../delivery/using/about-mobile-app-channel.md">Push</a> deliveries.</td>
  </tr> 
   <tr> 
   <td>Mobile channel - LINE v1</td>
   <td>Starting Campaign 18.4 release, LINE Connect package is no longer available. Adobe recommends using the new LINE Channel package as a replacement. <a href="../../delivery/using/line-channel.md">Learn more</a></td>
  </tr>
 </tbody> 
</table>

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

## End of compatibility {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic is compatible with all the systems and tools listed in the [Compatibility matrix](../../rn/using/compatibility-matrix.md). When specific versions of these 3rd party systems and tools reach end-of-life (EOL) with their respective creators, Adobe Campaign is no longer compatible with those versions: they are announced as deprecated, and then are removed from our compatibility matrix in the subsequent product release. Please ensure you are on supported versions of any systems listed in the compatibility matrix to avoid any issues.

### Client console {#client-console-eol}

Adobe Campaign Classic Client Console can no longer run on the following systems as they have been deprecated by their editor. Customers running Campaign Client Console on one of these versions need to upgrade to newest version before target removal date. Refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>Starting Campaign 20.1 release, Campaign Classic Client Console 32 bits is no longer compatible with Campaign latest versions. You need to use 64 bits Client Console.

### Operating systems {#o-s-eol}


* Starting 22.1 release, Adobe Campaign is no longer compatible with CentOs 8.x (64 bits). CentOS Linux 8 reached End Of Life (EOL) on December 31st, 2021. [Learn more](https://www.centos.org/centos-linux-eol/).

  If you were using this operating system, adapt your implementation accordingly. CentOS 7.x (64 bits) and RHEL 8.x/7.x (64 bits) are still supported.

* Starting 21.1.3 release, Adobe Campaign is no longer compatible with Debian 8.

* Starting 19.1 release, Adobe Campaign is no longer compatible with the following operating systems.

  * CentOS 6. [Learn more](https://wiki.centos.org/Download)
  * Debian 7. [Learn more](https://wiki.debian.org/DebianReleases)
  * RHEL 6.x. [Learn more](https://access.redhat.com/support/policy/updates/errata)
  * Windows Server 2008. [Learn more](https://support.microsoft.com/en-us/lifecycle/search/1163)
  * SLES 11. [Learn more](https://www.suse.com/lifecycle)

### Web servers {#web-server-eol}

Starting 19.1 Spring Release, Adobe Campaign is no longer compatible with the following web server. 

* Apache 2.2. [Learn more](https://httpd.apache.org/)
* Microsoft IIS 7. [Learn more](https://support.microsoft.com/en-us/lifecycle/search/810)

### Tools {#tools-eol}

Starting 19.1 Spring Release, Adobe Campaign is no longer compatible with the following tools.

* Java JDK 7. [Learn more](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, except when embedded in another tool. [Learn more](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Database engines {#dbe-eol}

Adobe does not support the following database engines as they have been deprecated by their editor. Customers running in these versions need to upgrade to newest version or move to another one.

Refer to [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md) to access the list of compatible versions.

**FEDERATED DATA ACCESS (FDA)**

Starting 20.2 release, Adobe Campaign is no longer compatible with the following FDA Server:

* DB2 UDB 10.5

Starting 19.1 Spring Release, Adobe Campaign is no longer compatible with the following FDA Servers:

* PostgreSQL 9.3. 
* MySQL 5.5. 
* DB2 9.5. 
* Teradata 14 – 14.1. 

Campaign Classic is not compatible with the following servers in Federated Data Access (FDA). Please use more recent versions, or systems.

* DB2 UDB 9.5, 9.7. 
* Oracle 9i, 10G R2.
* PostgreSQL versions up to 9.6 reached end of life. 
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1. 
* InfiniDB reached end of life. 
* Teradata 13, 13.1.
* Netezza 6.02, 7.0. Netezza reached end of life.
* AsterData 5.0. AsterData reached end of life.
* Sybase IQ 15.2, 15.4, 15.5 and Sybase ASE 15.0. 
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic still support the listed versions of Hadoop via HiveSQL through Federated Data Access (FDA), but these versions are merged with: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) and HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

Starting 19.1 Spring Release, Adobe Campaign is no longer compatible with the following RDBMS Servers:

* Oracle 10GR2
* PostgreSQL 9.0 to 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

PostgreSQL versions up to 9.6 reached end of life. They are therefore not supported by Adobe Campaign.

### SMS connectors {#sms-eol}

Starting 20.2 release, Legacy SMS connectors are deprecated. Adobe Campaign is not compatible with:

* Generic SMPP (SMPP version 3.4 supporting binary mode)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### CRM connectors {#crm-connectors}

Starting Campaign 21.1 release, the following CRM connectors are no longer compatible with Campaign:

* Soap API - On-premise: 2007, 2015, 2016
* Soap API - Online: 2015, 2016
* Web API – Microsoft Dynamics CRM  2016
* Web API – Microsoft Dynamics CRM 2016 Update 1
* Oracle On Demand API
