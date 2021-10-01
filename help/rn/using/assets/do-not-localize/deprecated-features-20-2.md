---
product: campaign
title: Campaign Classic deprecated and removed features
description: This page lists deprecated and removed features of Adobe Campaign Classic
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
---

# Deprecated and removed features {#deprecated-and-removed-features}

![](../../assets/v7-only.svg)

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
   <td><strong>Replacement</strong></td> 
  </tr>
   <tr>
  <td>SMS connectors<br></td>
  <td><p> Starting Campaign 20.2 release, the following SMS connectors are deprecated.<p>
   <ul>
   <li>Generic SMPP (SMPP version 3.4 supporting binary mode)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>If you are using one of these connectors, you need to adapt your implementation accordingly. <a href="../../delivery/using/sms-channel.md">Learn more</a></p> 
  <p>Learn how to migrate legacy connectors in <a href="../../delivery/using/unsupported-connector-migration.md">this technote</a>.</p>
  <p><em>Target removal date: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Fax channel<br></td>
   <td><p>Starting Campaign 20.2 release, the Fax channel is deprecated.</p> 
   <p>If you are using this channel, you need to adapt your implementation accordingly. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Learn more</a> about Campaign channels.</p>
   <p><em>Target removal date: 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Removed features {#removed-features}

This section lists features and capabilities that have been removed from Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Area - Feature</strong></td>
   <td><strong>Replacement</strong></td> 
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
   <td>Starting Campaign 19.1 release, Campaign Classic APIs are available in a dedicated page. If you were using the legacy jsapi.chm file, you should now refer to <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">the new online version</a>.</td>
  </tr> 
  <tr> 
   <td>Campaign Orchestration - Predictive marketing</td>
   <td>Starting Campaign 18.10 release, the predictive marketing capabilities are no longer available.</td>
  </tr> 
  <tr> 
   <td>Web applications - Microsites</td>
   <td>Starting Campaign 18.10 release, Microsites are no longer available. You can improve security by restricting access to only dedicated domains on Adobe Campaign configuration files, and use personalized URLs in Campaign by using DNS aliases. <a href="https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/ac-domain-name-setup.html">Learn more</a></td>
  </tr> 
  <tr> 
   <td>Push Notifications - iOS Binary Connector</td>
   <td>Per Apple's recommendation, Adobe has removed the legacy iOS Binary Connector starting Campaign 18.10 release. The more capable and more efficient HTTP/2-based connector is already available.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>Starting Campaign 18.6 release, for security reasons, <em>decryptString</em> API is no longer available by default for new installations.</p> 
   <p>In the context of a postupgrade to 18.6 (and later), this API is no longer activated, and has been replaced by the <em>decryptPassword</em> function. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Learn more</a></p></td>
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

## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.

### Adobe Campaign 20.2 release {#compat-20-2-release}

Starting 20.2 release, the following systems are deprecated for Campaign Classic. Compatibility will end in 20.3 release - October 2020.

* Client Console: Windows 7
* Legacy SMS connectors - see [Deprecated features](#deprecated-features)
* DB2 UDB 10.5 for Federated Data Access (FDA)

### Adobe Campaign 19.2 release  {#compat-19-2-release}

Starting 19.2 release, the following operating systems are deprecated for Campaign Classic. Compatibility will end in 2020 EOY.

* Web Server: Apache 2.2.
* Operating System: CentOS 6.

Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system.

## End of compatibility {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic is compatible with all the systems and tools listed in the [Compatibility matrix](../../rn/using/compatibility-matrix.md). When specific versions of these 3rd party systems and tools reach end-of-life (EOL) with their respective creators, Adobe Campaign is no longer compatible with those versions: they are announced as deprecated, and then are removed from our compatibility matrix in the subsequent product release. Please ensure you are on supported versions of any systems listed in the compatibility matrix to avoid any issues.

### Client console {#client-console-eol}

Adobe Campaign Classic Client Console can no longer run on the following systems as they have been deprecated by their editor. Customers running Campaign Client Console on one of these versions need to upgrade to newest version before target removal date. Refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>Starting Campaign 20.1 release, Campaign Classic Client Console 32 bits is no longer compatible with Campaign latest versions. You need to use 64 bits Client Console.


### Operating systems {#o-s-eol}

Starting 19.1 release, Adobe Campaign is no longer compatible with the following operating systems.

* Debian 7. [Learn more](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Learn more](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Learn more](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [Learn more](https://www.suse.com/lifecycle)

### Web servers {#web-server-eol}

Starting 19.1 Spring Release, Adobe Campaign is no longer compatible with the following web server. 

* Microsoft IIS 7. [Learn more](https://support.microsoft.com/en-us/lifecycle/search/810)

### Tools {#tools-eol}

Starting 19.1 Spring Release, Adobe Campaign is no longer compatible with the following tools.

* Java JDK 7. [Learn more](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, except when embedded in another tool. [Learn more](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Database engines {#dbe-eol}

Adobe does not support the following database engines as they have been deprecated by their editor. Customers running in these versions need to upgrade to newest version or move to another one.

Refer to [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md) to access the list of compatible versions.

**FEDERATED DATA ACCESS (FDA)**

Starting 19.1 Spring Release, Adobe Campaign is no longer compatible with the following FDA Servers.

* PostgreSQL 9.3. [Learn more](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Learn more](https://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Learn more](https://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 – 14.1. [Learn more](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic is not compatible with the following servers in Federated Data Access (FDA).

* DB2 UDB 9.5, 9.7. More recent version of DB2 is supported through Federated Data Access (FDA). [Learn more](https://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. More recent versions of Oracle are supported through Federated Data Access (FDA). [Learn more](https://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. More recent versions of PostgreSQL are supported through Federated Data Access (FDA). [Learn more](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. More recent versions of SQL Server are supported through Federated Data Access (FDA). [Learn more](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. More recent versions of MySQL are supported through Federated Data Access (FDA). [Learn more](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB reached end of life. [Learn more](https://www.mysql.com/support)
* Teradata 13, 13.1. More recent versions of Teradata are supported through Federated Data Access (FDA). [Learn more](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza reached end of life. [Learn more](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData reached end of life. [Learn more](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 and Sybase ASE 15.0. More recent versions of Sybase are supported through Federated Data Access (FDA). [Learn more](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic will still support the listed versions of Hadoop via HiveSQL through Federated Data Access (FDA), but these versions are merged with: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) and HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

Adobe Campaign is not compatible with the following RDBMS Servers:
* Oracle 10GR2
* PostgreSQL 9.0 to 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
