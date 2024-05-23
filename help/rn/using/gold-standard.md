---
product: campaign
title: "[!DNL Gold Standard] releases"
description: Release notes and Compatibility matrix for Campaign Classic [!DNL Gold Standard]
feature: Release Notes
role: User
level: Beginner
hidefromtoc: yes
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
---
# [!DNL Gold Standard] releases{#gold-standard}



You can find in this page release notes and compatibility matrix for [!DNL Gold Standard] releases.

## [!DNL Gold Standard] Release Notes


### [!DNL Gold Standard] 12 release{#gs-12}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_September 7, 2021_

The build 9032&#64;554dbcd includes the following fix:

* Fixed an issue which led to a 500 error when opening the link to a web application in a Line delivery with tracking enabled.

_August 27, 2021_

The build 9032&#64;99a3894 includes the following fixes:

* The tracking signature feature has been improved to prevent errors linked to the way third-party tools (email clients, internet browsers, etc.) handle special characters. URL parameters are now encoded.
* Fixed an issue with date pickers which could result in a console displaying blocker error message. (NEO-36345)

### [!DNL Gold Standard] 11 release{#gs-11}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_April 14, 2021_

The build 9032&#64;d030c36 includes the following fix:

* Fixed a client console regression which caused persistent error messages on the IMS connection screen. (NEO-34821)
* This console build is required to maintain [IMS access](../../technotes/using/ims-updates.md).

**Console upgrade only is mandatory. No server upgrade is required.** 

>[!CAUTION]
>
> * If you are connecting to Campaign with your Adobe ID, through Adobe Identity Management Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**. [Learn more](../../technotes/using/ims-updates.md)
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 
> * If you are using the Experience Cloud Triggers integration through oAuth authentication, you need to move to Adobe I/O as described [in this page](../../integrations/using/configuring-adobe-io.md). Legacy oAuth authentication mode with Campaign [has been retired](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) on **September 2021**. Hosted environments benefit from an extension until  **February 23, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to february 2022. You must provide [the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
>
>Learn more in the [[!DNL Gold Standard] section](../../rn/using/gold-standard.md)

_March 2, 2021_

The build 9032&#64;10c2709 includes the following fix:

* Fixed a regression preventing the usage of some components of the console, such as the date picker and images management in deliveries. (NEO-31453, NEO-31454)

**Console upgrade only is mandatory. No server upgrade is required.** 

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_December 22, 2020_

The build 9032&#64;d3b452f includes the following improvements and fixes:

* The connection protocol has been updated to follow the new IMS authentication mechanism. 

* Triggers integration authentication originally based on oAUTH authentication setup to access pipeline has now been changed and moved to Adobe I/O. [Learn more](../../integrations/using/configuring-adobe-io.md)

* Following the [end of support for iOS APNs legacy binary protocol](https://developer.apple.com/news/?id=c88acm2b), all instances using this protocol are updated to HTTP/2 protocol during postupgrade.

* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)

* Fixed an issue that could cause workflows to fail when running an **Enrichment** activity. (NEO-17338)

### [!DNL Gold Standard] 10 release{#gs-10}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_July 7, 2020_

The build 9032&#64;efd8a94 includes the following fix:

Fixed an issue which prevented tracking from working when the signature feature was disabled. (NEO-26411)

>[!CAUTION]
>
>We recommend that you upgrade the client console with the one available in this release. Refer to [this page](../../installation/using/installing-the-client-console.md)

### [!DNL Gold Standard] 9 release{#gs-9}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_22 June 2020_

The build 9032&#64;800be2e includes the following fixes:

* The iOS HTTP2 connector has been improved (third-party updates and error management). (NEO-25904, NEO-25903, NEO-25799)

The following fixes are related to the tracking link security mechanism (learn more in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)):

* Fixed an issue which prevented the tracking of "notification clicks" from working (iOS and Android push notifications). (NEO-25965)
* Fixed an issue which could prevent you from opening/clicking tracking URLs when using certain legacy versions of Outlook.  (NEO-25688)
* Fixed an issue which prevented the tracking of URLs using fragments in personalization parameters (anchor tags with pound-sign) from working. (NEO-25774)
* Fixed an issue with the anti-phishing service. (NEO-25283)
* Fixed a tracking issue when using specific custom tracking formulas. (NEO-25277)

### [!DNL Gold Standard] 8 release{#gs-8}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_April 29, 2020_

The build 9032&#64;3a9dc9c includes the following fixes:

* Improved security on tracking links in email. This is enabled by default for all customers. An additional, enhanced security feature is available which can be enabled by reaching out to Customer Care. More details on the feature and steps for non-hosted customers to enable it can be found in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

 >[!CAUTION]
 >
 >If you experience issues with push notifications using tracking links, or deliveries using anchor tags, we recommend that you disable the new signature mechanism for tracking links. The procedure is detailed [in this page](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* Fixed an issue which could prevent images from being displayed on Line deliveries. (NEO-23207)
* Fixed an issue with the **File Transfer** activity which prevented SFTP key based authentication from working on Debian 9. (NEO-23183) 
* Fixed an issue which could affect push notification when sent at a high frequency. (NEO-20516)
* Fixed an issue in offer response management which could lead to web server crashes. (NEO-19482)
* Fixed an error in LibreOffice management which prevented you from exporting reports. (NEO-20982)
* Fixed an issue which caused an error when upgrading numerous workflows using a survey activity. 
* Improved LibreOffice management to avoid failures on email preview with .odt files. 
* Improved the management of Apache connection to avoid latency on web service.
* Improved the display of version tag (7 digit) in the **About** menu.
* Fixed a regression in list management preventing offers from being published.
* Fixed a regression causing the cleanup workflow to crash. 
* Fixed a minor regression in the cleanup workflow logs.

### [!DNL Gold Standard] 6 release{#gs-6}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_March 9, 2020_

The build 9032&#64;19f73c5 includes the following fix:

* Fixed an issue with external accounts using FTP over SSL. (NEO-20498)

### [!DNL Gold Standard] 5 release{#gs-5}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_December 17, 2019_

The build 9032&#64;d6b8062 includes the following fix:

* Fixed a tracking issue on the following communication channels: mobile (SMS, MMS), push (iOS, Android) and social networks (Facebook, X - formerly known as Twitter). (NEO-19595)

### [!DNL Gold Standard] 4 release{#gs-4}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_December 11, 2019_

The build 9032&#64;bc4a935 includes the following fix:

* Fixed a performance isssue when sending messages with a MSSQL database. (NEO-17558)

### [!DNL Gold Standard] 3 release{#gs-3}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_November 20, 2019_

The build 9032&#64;3468c7b includes the following fixes:

* Fixed a login issue via IMS authentication. (NEO-17312)
* Fixed an issue when displaying cumulative reports on multiple deliveries. (NEO-18165)
* Fixed an issue that could block or make the web server crash.

### [!DNL Gold Standard] 2 release{#gs-2}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_September 19, 2019_

The build 9032&#64;cee805c includes the following fixes:

* Fixed an issue when using the CRM Connector for Salesforce. (NEO-17712)
* Fixed an index issue which could cause performance issues when sending transactional messages.

### Release 19.1.4 - Build 9032{#release-19-1-4-build-9032}

[!BADGE Deprecated]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html#rn-statuses" tooltip="Deprecated"}

_August 13, 2019_

The initial 19.1.4 build includes the following fixes:

* Fixed an issue with the scheduler activity generating undesired error messages during wizard configuration. Reverting update from NEO-11662. (NEO-17097)
* Fixed a regression caused by the NEO-12727 which could lead to workflows being stopped when a Test activity was executed twice. (NEO-16835) 
* Fixed an issue which led to an erroneous HTTP code being returned (HTTP 200 OK instead of HTTP 403 Forbidden) when an invalid or expired session token was used in API calls. (NEO-16826) 
* Fixed an issue with the DKIM key which was not embedded into emails anymore, thus causing deliverability issues. (NEO-16804) 
* Fixed various issues with workflow scheduling. Workflows were scheduled to be executed once a day without taking into account the scheduler configuration. (NEO-16619, NEO-16426)


## [!DNL Gold Standard] Compatibility Matrix{#compatibility-matrix-gs}

This section lists all systems and components supported for **Adobe Campaign Classic [!DNL Gold Standard]** 19.1 builds. Products and versions that are not part of this list are not compatible with this version of Adobe Campaign.

>[!CAUTION]
>Unless mentioned otherwise, all minor releases are supported.
>
>Adobe Campaign Classic is compatible with all the systems and tools listed in this page. As specific versions of these 3rd party systems and tools reach end-of-life (EOL) with their respective creators, Adobe Campaign will no longer be compatible with those versions, and they will be removed from our compatibility matrix in the subsequent product release. Please ensure you are on supported versions of any systems listed in the compatibility matrix to avoid any issues.
>

### Operating Systems{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Important:</strong> If you are using RHEL, you must be willing to disable SELinux or to have your architects write custom SELinux rules to check that an enabled SELinux is not causing issues with Campaign operations.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>    

### Web Servers{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 on Windows Server 2016</p>
<p>8.5 on Windows Server 2012 R2</p>
<p>8.0 on Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</p>
<p>2.2 for RHEL6 - CentOS 6 only (64 bits)</p>
</td>
</tr>
</tbody>
</table>

### Tools{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>The application has been approved for the Java Development Kit (JDK) developed by Oracle as well as for OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (and previous versions if embedded in your system)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

### RDBMS servers{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS driver must match with RDBMS server version.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Note: you can also use Amazon RDS for PostgreSQL with the versions specified above.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 and SP2</p>
<p>Warning: Microsoft SQL Server is not supported as the primary database when the Campaign server is running on Linux.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Warning: DB2 UDB is not allowed for new installations.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL is the default database server for Hosted environments.

### CRM connectors{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce connector API</td>
<td>
<p>API version 37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API version 21</p>
<p>API version 15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap API - On-premise: 2007, 2015, 2016</p>
<p>Soap API - Online: 2015, 2016</p>
<p>Web API - On-premise and Online: 365, 2016, 2016 Update 1</p>
</td>
</tr>
</tbody>
</table>

### Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p>&nbsp;</p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 and SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>version 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>

### Client Console {#ClientConsoleoperatingsystems}

`:warning:` The following operating systems and browser are required to use Campaign Client Console.

#### Operating systems

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (recommended for Japanese instances)</p>
</td>
</tr>
</tbody>
</table>

#### Browser 

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### Mobile SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>with mobile SDK build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>with mobile SDK build 1.0.26, compatible with 32 and 64-bit versions.</p>
</td>
</tr>
</tbody>
</table>

### Browsers{#Browsers}

The following browsers are compatible with Campaign for Web Access.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Latest version</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Latest version</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Latest version</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Latest version</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
