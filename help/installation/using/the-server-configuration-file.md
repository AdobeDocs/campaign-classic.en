---
solution: Campaign Classic
product: campaign
title: The server configuration file
description: The server configuration file
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
---
# The server configuration file{#the-server-configuration-file}

The overall configuration of Adobe Campaign is defined in the **serverConf.xml** file, located in the **conf** directory of the installation directory. This section lists all the different nodes and parameters of the **serverConf.xml** file.

>[!NOTE]
>
>Server-side configurations can only be performed by Adobe for deployments hosted by Adobe. To learn more about the different deployments, refer to the [Hosting models](../../installation/using/hosting-models.md) section or to [this page](../../installation/using/capability-matrix.md). The installation and configuration steps for hosted and hybrid models are presented in this [section](../../installation/using/hosting-models.md).

The first parameters are inside the **shared** node. These are related to the instance. They are potentially used by all the nlserver commands (nlserver web, nlserver wfserver, etc.). The other sections are related to a specific nlserver sub-command.

**Shared parameters**

* [authentication](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [module](#module)
* [monitoring](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**Other parameters**

* [archiving](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [pipelined](#pipelined)
* [repair](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## authentication {#authentication}

Here are the different parameters of the **authentication** node:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Enable IP address checking.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Default identification mode.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Timeout of long sessions in seconds.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Security token timeout in seconds.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Cache duration: cache of session information in seconds.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Session timeout in seconds.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Here are the different parameters of the **authentication > XTK** node:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Password of internal account.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Internal account security zone: authorized zone for the internal account.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Here are the different parameters of the **dataStore** node. This is where the server data sources are defined.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Export directory: path of destination directory for the exported data.<br /> </td> 
   <td> String<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Extra sandboxed directories: other paths to be added in the sandbox (coma separated).<br /> </td> 
   <td> String<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Form cache expiration delay: timeout in seconds after which a cache entry is invalidated. O means that cache entries are only refreshed at publication time.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> DNS masks: list of DNS masks that this instance serves (comma separated, can use * and ? patterns).<br /> </td> 
   <td> String<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Interaction JSSP cache expiration delay: timeout in seconds after which a cache entry is invalidated. A negative value means that the cache is always invalidated. '0', empty or invalid values are considered to be 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Instance language (enumeration). Possible values are 'fr_FR' (Français), 'en_GB' (English (UK)), 'en_US' (English (US)), 'de_DE' (Deutsch) and 'ja_JP' (Japanese).<br /> </td> 
   <td> String<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Upload folder: path of destination directory for the uploaded data.<br /> </td> 
   <td> String<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Authorized files to be downloaded separated by ','. The string must be a valid, regular java expression. See <a href="file-res-management.md" target="_blank">Limiting uploadable files</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Store secrets in Vault: use Hashicorp Vault.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Secret path in Vault<br /> </td> 
   <td> String<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Local path of the file that contains the vault token. $(HOME) can be used in this path (but not other env variables).<br /> </td> 
   <td> String<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Validity period of view cache: timeout in seconds after which a cache entry is invalidated. A negative value means that the cache is always invalidated. '0', empty or invalid values are considered to be 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath of the working directory.<br /> </td> 
   <td> String<br /> </td> 
   <td> workingDirectory : XPath of the working directory. Default: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Here are the different parameters of the **dataStore > proxyAdjust** node. URLs matching the regular expression are regenerated based on the URL defined in urlBase.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Base to use when generating external URLs. Ex: https://server.domain.com<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regular expression to match URLs. Ex: http://server\.lan\.net.*<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Here are the different parameters of the **dataStore > dataSource** node. 

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Data Source name<br /> </td> 
   <td> String<br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

In the **dataStore > dataSource > dbcnx** node, configure the connection settings:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Unicode storage<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Workspace<br /> </td> 
   <td> String<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> encrypted<br /> </td> 
   <td> Encrypted password<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Account<br /> </td> 
   <td> String<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Password<br /> </td> 
   <td> String<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> Type (enumeration). Possible values are 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL, Greenplum), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE, Sybase IQ)), 'Relay' (HTTP relay to remote database).<br /> </td> 
   <td> String<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Server<br /> </td> 
   <td> String<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> Time zone: see <a href="../../installation/using/time-zone-management.md" target="_blank">Time zone management</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Unicode data in the database<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Date fields with time zone: see <a href="../../installation/using/time-zone-management.md" target="_blank">Time zone management</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

In the **dataStore > dataSource > sqlParams** node, configure the SQL parameters: 

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Function prefix<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

In the **dataStore > dataSource > pool** node, configure the parameters of associated connections pool: 

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> Delay between connection validity checks.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Number of free connection kept in the pool.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Maximum number of allowed connections before refusing a new connection. See this <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">technote</a>.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Maximum idle time of connection. 0 means default value.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Here are the different parameters of the **dataStore > virtualDir** node. This is the configuration of the virtual directory to real directory mapping.

For additional information, refer to [Managing public resources](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Name of the virtual directory <br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> path<br /> </td> 
   <td> Full path of the actual directory<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

Here is the default configuration:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Here are the different parameters of the **dataStore > preprocessCommand** node. These are the authorized commands for pre-processing of the 'Load file' workflow activity. 

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Command line <br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Command line label<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Command line name<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

Here is the default configuration:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Here are the different parameters of the **dnsConfig** (DNS configuration) node.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domain name: default domain name. Used by the SMTP HELO command. By default, uses the network parameters of the first network interface declared in Windows; or parses the file/etc/resolv.conf under Linux (domain or search entry). <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS server: comma separated list of domain name servers (DNS). See the note below.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> retry<br /> </td> 
   <td> Number of retries for a DNS query.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout in milliseconds for a DNS query.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Note on **nameSevers**: by default, uses the network
>parameters of the first network interface declared in Windows
>not defined in UNIX. Defines the domain name servers (DNS)
>used by the MTA to get the Mail Exchanger declared for
>a domain.
>
>If this value is not defined, the MTA seeks this information in the host network configuration. If several DNS are possible, the different DNS addresses must be separated by a comma (example: 212.155.207.1,212.155.207.2). If your delivery server has several network interfaces, the DNS list used by the MTA is the first one. In this case, we recommend specifying the **nameServer** parameter to avoid any ambiguity.

>[!CAUTION]
>
>If your network host configuration uses DHCP, the MTA will not find the DNS list provided by DHCP. In this case, we recommend specifying the DNS list in the network parameters of the Windows control panel.

## exec {#exec}

Here are the different parameters of the **exec** (command execution) node.

For additional information, refer to [Restricting authorized external commands](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> Path to the file containing the commands to add to the allowlist. <br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> Execute commands as a different user.<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Here are the different parameters of the **htmlToPdf** node. This is the configuration of the service for converting web pages into PDF documents.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Command line for running the conversion (in 'other' mode).<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. number of conversion processes allowed at a time on one machine.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Tool to use for the conversion. Possible values are: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> String<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout for a conversion: maximum conversion time in seconds. Beyond this threshold, the conversion process is stopped and an error is raised.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Verbose mode: start in verbose mode to diagnose possible errors.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Delay when waiting for a process: delay in seconds, when all processes are used at the same time and when waiting for a process to free up. If this delay is exceeded, conversion is stopped and an error is raised. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Example for phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

Here are the different parameters of the **ims** node. This is the configuration for Campaign connecting to another service using [IMS](../../integrations/using/about-adobe-id.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> Client ID<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Secret key (encrypted in AES)<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Authorization code (encrypted in AES)<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> IMS server URL<br /> </td> 
   <td> String<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> Technical Account Client ID<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Technical Account Secret key (encrypted in AES)<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> Technical Account ID<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Technical Account Private Key (encrypted in AES)<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## javaScript {#javascript}

Here are the different parameters of the **javaScript** node. This is the configuration of the JavaScript interpreter.

For additional information, refer to the [Reporting documentation](../../reporting/using/actions-on-reports.md#memory-allocation) and this [technote](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Maximum size in megabytes before running the garbage collector.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Size of each stack chunk in kilo octets. This is a memory management tuning parameter which most users should not adjust. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Here are the different parameters of the **mailExchanger** node. This is the configuration of the SMTP server.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP server: IP address of SMTP server for the transfer of emails.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> TCP port of SMTP server used for the Email transfer.<br /> </td> 
   <td> String<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## module {#module}

Here are the different parameters of the **module** node. This is the configuration for the namespaces restrictions module xtk.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Default namespace used when creating a new entity.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## monitoring {#monitoring}

Here are the different parameters of the **monitoring** node. This is the monitoring service configuration.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> Maximum preparation time: duration in seconds after which a delivery action should no longer be in preparation.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Unix script ran by the monitoring service.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Windows script to be executed by the monitoring service.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Here are the different parameters of the **ooconv** node. This is the configuration of the document conversion server.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> Maximum number of conversions which an OpenOffice server is allowed to perform. Beyond this number, the server is restarted.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Maximum idle time of OpenOffice server before forced closing.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Interval of ports on which the OpenOffice servers are listening.<br /> </td> 
   <td> String<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL of the document conversion server.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Here are the different parameters of the **proxyConfig** node. This is the configuration of proxy parameters.

For additional information, refer to [Proxy connection configuration](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> Use a proxy server.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Exceptions: list of addresses for which proxy parameters shall be ignored.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Unique proxy server: use the same configuration for all types of proxy.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP Proxy / Secure proxy {#http-proxy---secure-proxy-}

In the **proxyConfig > HTTP Proxy / Secure proxy** node, configure the following parameters.

For additional information, refer to [Proxy connection configuration](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Address of proxy server<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Login for the connection to proxy server<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Password for the connection with proxy server<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Proxy server port<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Here are the different parameters of the **threadPool** node.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Maximum number of threads in pool. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Here are the different parameters of the **urlPermission** node. This is the list of URLs that the Javascript code can access.

List of domains and regular expressions specifying whether a URL encountered in the Javascript code can or cannot be used by the Adobe Campaign server.

If the URL cannot be found, the default action is carried out, according to the default mode specified.

For additional information, refer to [Outgoing connection protection](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> action<br /> </td> 
   <td> Default action if the URL is not in the authorized list (enumeration). Possible values are 'ignore' (authorize without warning message, this requires disabling the protection), 'warn' (authorize and issue a warning message) and 'deny' (prohibit access to the URL).<br /> </td> 
   <td> String<br /> </td> 
   <td> deny<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Debugging trace of the URL selection mechanism: issues additional messages during the URL verification process.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

For each URL, add a **url** node with the following parameters:

For additional information, refer to [Outgoing connection protection](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Domain name, or domain parent, concerned by the URL: all or part of the URL's domain to verify, to accelerate the verification. The URL is only verified with respect to the regular expression if its domain contains dsnSuffix.<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regular expression to refine validating URLs belonging to this domain: regular expression that the URL must verify, should it correspond to dnsSuffix.<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

If a record satisfies **dnsSuffix** but not **urlRegEx**, the following record is examined.

For example, to authorize access to all of the URLs of the domain business.com, we can define two records:

dnsSuffix="business.com" urlRegEx="http://.&#42;"

and

dnsSuffix="business.com" urlRegEx="https://.&#42;"

Here is the default configuration:

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Here are the different parameters of the **xtkJobs** node. This is the configuration of the server jobs.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Memory status refresh period of server processing (in ms).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archiving {#archiving}

Here are the different parameters of the **archiving** node. This is the configuration of the executed archiving operations in the background.

For additional information, refer to [Activating email archiving (on premise)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquireLimit<br /> </td> 
   <td> Number of EMLs to process at the same time<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Archiving strategy of sent messages (enumeration). Possible values are '0' (no archiving) and '1' (transfers archiving of sent messages to a SMTP server).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Size of a compressed archive: max number of files in a compressed archive.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Compression format used during archiving (enumeration). Possible values are '0' (no compression) and '1' (compress sent messages using zip format).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Delay before automatic archiving of unprocessed emails: number of days before unprocessed emails are archived.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Delay (in seconds) between each update event.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Number of days before unprocessed emails are deleted.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Archiving target destination<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Activate SMTPS support: activates the delivery of emails in safe mode (STARTTLS/SMTPS) when supported by the remote server.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Number of connections to the archiving SMTP server.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Comma-separated list of DNS names or IP addresses of SMTP relays to use. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> IP port of SMTP server.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Here are the different parameters of the **inMail** node. This is the configuration of the inbound Email management module.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Verify instance name: if true, the name of the Adobe Campaign instance contained in the Message-ID headers must be the same as the current instance. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Forwarding address: default email transfer address not processed by a rule. <br /> </td> 
   <td> String<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Address for errors: default address used to transfer invalid Emails (bad MIME encoding). <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignore message size: is used to ignore the size of a message returned by POP3 servers. In this case, the module expects a '.' at the end of the messages. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Message reading period: message queue polling frequency.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Maximum number of logs to update: defines the maximum number of log messages to keep in memory before updating the database.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Maximum number of messages to read during POP3 session.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Session duration: maximum duration of message processing session.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3 polling period<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Queue size of read messages<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Communication timeout with POP3 server. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Database reload frequency of accounts to be polled.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

In the **inMail > msgDump** node, configure the following parameters. This is the configuration of the dump of processed messages.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dump<br /> </td> 
   <td> Save all inbound messages in text format. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Message dump path.<br /> </td> 
   <td> String<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Here are the different parameters of the **interactiond** node. This is the configuration of the write daemon for inbound Interaction events.

For additional information, refer to [Interaction - Data buffer](../../installation/using/interaction---data-buffer.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. number of characters stored in the shared memory for call data.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. number of events stored in the shared memory.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Maximum number of eligible offers sorted right after propositions, to be stored for statistics.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Aggregation duration in seconds for the response time statistics. 0 means statistic storage was deactivated.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. number of characters stored in the shared memory for identifying individuals.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Here are the different parameters of the **mta** node. This is the configuration of delivery agents.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Save path of emails sent: if not empty, the path where all source files of sent emails will be saved. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Dump directory:iIf not empty, copy MIME envelopes of sent mail messages in this directory. Used for trouble shooting. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS query logs delay: time in milliseconds to display the logs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Error statistics frequency: time between generation of statistics and storage in the database. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Generate error statistics and store them in the database.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Display level of log messages. Severity level of the logs written in the database. Log messages generated by the MTA are not all always written in the database. With this parameter, you can define the level from which you consider a message must be written in the database. If you define level 2, messages of level 1 and 0 are also written, whereas if you define level 1, only messages of level 1 and 0 are written. Possible values are: 0 (errors), 1 (warning), 2 (info)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximum memory size (in MB) that an mta process can use. Above this limit, the process is re-started so that the memory it uses is released to the system.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Connection threshold to take into account. Error statistics are not generated for a given path if the total number of connections for the period specified by errorPeriodSec is strictly lower than the threshold.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Error threshold to take into account: error statistics are not generated for a given path if the total number of errors for the period specified by errorPeriodSec is strictly lower than the threshold.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Message threshold to take into account. Error statistics are not generated for a given path if the total number of messages sent for the period specified by errorPeriodSec is strictly lower than the threshold.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Notification relay: HostName:Port used to relay notifications.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Delay before archived emails are deleted: number of days before archived emails in the directory specified in dataLogPath are purged.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Retry lost messages: parts of deliveries will be retried if the child process is dead.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Enable the signature mechanism. This improves security on tracking links in email.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Address of the delivery statistics server, given as 
    &lt;dns or ip&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. See 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coordinates of the statistics server</a>. 
      <br /> 
     </td> 
   <td> String<br /> </td> 
   <td> If not defined, the default port is 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> Enable TLS by domain: enables the TLS configurable by MX (requires an up-to-date statistics server).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> If set to "true", your instance is using the <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Verification mode: activates the verify mode (no physical transmission of messages; used for simulation and tests).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Working directory: location of temporary files used by the MTA to communicate with its child processes.<br /> </td> 
   <td> String<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer field: value of field 'X-Mailer' in SMTP mail header.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

In the **cache** node, configure the following parameters. This is the local file cache configuration.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Recycled after: period, expressed in seconds, after which the file is automatically deleted from the cache to reclaim storage.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximum cache size (Mb).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Purge frequency: period in seconds between executions of the cache purge mechanism.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relay {#relay}

In the **mta > relay** node, configure the following parameters. This is the configuration of the mail server for the message delivery.

The list will be handled in the same way as a list of MX returned by a MX DNS query, usually the first MX is used as long as it is available, then the next one is used, and so on.

For additional information, refer to [SMTP relay](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Comma-separated list of DNS names or IP addresses of SMTP relays to use. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> IP port of SMTP server.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

In the **mta > master** node, configure the following parameters. This is the configuration of the main server.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Database polling frequency of the jobs to be delivered. This value indicates the database polling frequency (in seconds). To obtain the list of jobs waiting for delivery, the MTA polls the database on a regular basis. When there is no job waiting, the polling period is defined by this value. Otherwise if a job has been transferred to a child server, then this polling duration is automatically reduced to one second so that a new job can be processed again as soon as possible, i.e. as soon as a child server is available again. This does not mean that database query will be done every second until a child server is available again. In fact, a database access is only done when at least one child server becomes available.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Waiting period after a database connection failure. A database connection failure is usually caused by the database server itself. The server may also be stopped for maintenance purposes, for example. The DataBaseRetryDelay parameter defines the duration between two connection attempts in case of a database connection failure.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Validity period for the cache of private keys (DomainKeys). Private keys used to sign emails following the DomainKeys recommendation (http://antispam.yahoo.com/domainkeys) are stored as options in the database. The domainKeysReloadPeriodSec parameter defines how many seconds the MTA can keep these keys in a cache. After this delay, all keys must be reloaded from the database.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximum number of child servers. Represents the maximum number of servers running. It is recommended to limit this number at an optimum compatible with the server memory resources. This can be checked during a delivery. The used memory should not exceed a third of a the physical memory available otherwise the swap will be used. See <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA child processes</a>.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Minimum number of child servers. The MTA tries to keep at least this number of servers running. If there are less, it restarts new servers every second until this value is reached.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Number of child server at start-up. The number of child servers is dynamically monitored; when the MTA starts, it creates as many child servers as indicated by this value. Normally, child servers cannot be started faster than one server per second in order to save host resources. However, when the MTA starts, this limitation is overruled so that child servers are available as soon as possible.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### child {#child}

In the **mta > child** node, configure the following parameters. This is the configuration of child servers.

For additional information, refer to [Email sending optimization](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Optional command line arguments <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Timeout until idle child servers are stopped. If a child server has an idle time greater than this parameter, it will automatically kill itself to free up host resources.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximum message retention time. If a prepared message could not be sent because of throttling or was not able to connect to the target MTA, the message is abandoned and will be processed at the next retry.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximum of parallel Http requests to the FCM initiated by each child server.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximum count of messages per child server. Each MTA child processes this number of messages and dies. It is important to specify a number such that memory or resource leaks in the MTA are harmless (typically a few thousands). Even if there are no known memory leaks in the MTA code, the embedded JavaScript and XSL engines are not fully reliable.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Pending messages: maximum number of messages waiting in memory to be delivered. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximum memory size (in MB) that a child process can use. Above this limit, the process is stopped so that the memory it uses is released to the system. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (in seconds) after which a SOAP connection for a delivery connector is abandoned.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Always start with the highest priority MX.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximum number of consecutive attempts when resumed.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

In the **mta > child > smtp** node, configure the following parameters. This is the configuration of SMTP sessions. 

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Activates the delivery of emails in safe mode (STARTTLS/SMTPS) when supported by the remote server.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Idle session timeout. This parameter is only used if the session is reused for transmitting several messages to a given domain. When the MTA has completed the message transmission, the SMTP session it has used is not systematically closed. If a message is ready to be sent for this same domain then the same SMTP session will be reused and this is why the session is not automatically closed. The parameter IdleSessionTimeout parameter lets you define the time during which an SMTP session can remain active waiting for another message. Once the duration has elapsed, the session is automatically closed.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Initial delay before retrying connection. This delay is doubled each time connection fails.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Maximum number of SMTP sessions by child server. To deliver a message, the MTA initializes an SMTP connection with the recipient MTA. The maximum number of concurrent and active SMTP sessions for a given child server is limited by this value. If you multiply this value by maxSpareServers, you get the maximum number of messages that can be concurrently processed by a given child server.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

In the **mta > child > smtp > IPAffinity** node, configure the following parameters. This is the configuration of the management of affinities with IP addresses for optimized outgoing SMTP traffic.

For additional information, refer to [List of IP addresses to use](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) and [Managing outbound SMTP traffic with affinities](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domain name: local domain name linked to the IP address. Used when issuing an SMTP HELO command.<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Logical name: names linked to the affinity by users. Names are separated using semicolons;<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

In the **mta > child > smtp > IP** node, configure the following parameters.

For additional information, refer to [List of IP addresses to use](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Associated physical address. Eg: '192.168.0.1'<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Associated public address ID. Used as a key for the statistics server. Must be numeric. See this <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">section</a>.<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> weight<br /> </td> 
   <td> Specifies the frequency of use for this IP, relative to other IPs (bigger weights lead to higher frequencies).<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Comma separated list of domain masks to include.<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Comma separated list of domain masks to exclude.<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Computer name linked to the IP address. Used when issuing an SMTP HELO command.<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Here are the different parameters of the **nmac** node. This is the configuration of for push notification deliveries.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Use HTTP proxy defined in shared/proxyHTTP. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relay {#relay-1}

Here are the different parameters of the **nmac > relay** node. This configures the use of a relay for the message delivery (ios http2 connector).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> DNS address or name of the relay to use. <br /> </td> 
   <td> String<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Relay port<br /> </td> 
   <td> Long<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Certificate chain (PEM file). Useful when using a mock server.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## pipelined {#pipelined}

Here are the different parameters of the **pipelined** node. This is the configuration of the event processing module for Pipeline Services.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Name of the application generated in the Developer connection when the public key is saved. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL to obtain a gateway token.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Private key to obtain tokens (encrypted in AES with the XtkKey option).<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Disable authentication: connect to Pipeline Services without authentication. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL to discover the Pipeline Services URL.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Status save period: frequency that the process's internal information is saved in a file. Inactive if 0. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> Listening URL: force the listening URL of the Pipeline Services. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Status server port: HTTP server port allowing you to query the status of the process. Inactive if 0.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> The pointer will be stored in the database every time that this number of messages are processed.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Delay before the pointer is stored: the pointer will be stored in the database at least once during this period (useful in case of low activity).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Number of threads for event processing with a personalized JavaScript connector.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Number of threads for event processing.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Delay between processing if there is a failure.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Abandon after this period: abandon the event if the processing is still failing after this period.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## repair {#repair}

Here are the different parameters of the **repair** node. This is the configuration of the database repair module.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> repairActionDelayMin<br /> </td> 
   <td> Delivery actions repair module: delay (in minutes) after which delivery actions can be processed by the repair module. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Here are the different parameters of the **securityZone** node.

For additional information, refer to [Define security zones](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Authorize debug mode for Web applications.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Authorize the user to use the application without a password.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Authorize the use of HTTP for operator logon.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Authorize the use of SQLDATA in expressions.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Authorize user/password session tokens.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Label<br /> </td> 
   <td> String<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Internal name<br /> </td> 
   <td> String<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Do not use the security token.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Display error details<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Here is the default configuration:

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

Here are the different parameters of the **securityZone > subNetwork** node.

For additional information, refer to [Define security zones](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> label<br /> </td> 
   <td> Label<br /> </td> 
   <td> String<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> mask<br /> </td> 
   <td> Mask or address<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Internal name<br /> </td> 
   <td> String<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Mask or address of (reverse) proxy used by this sub-network to access the instance. In this case, the 'X-Forwarded-For' header will be tested instead of this proxy.<br /> </td> 
   <td> String<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Here are the different parameters of the **sms** node. This is the configuration of the inbound SMS management module.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Maximum number of days files working files kept by the SMPP connector.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximum size in MB of the SMPP working files.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Recurrence of the session continuity frame: max. period in seconds between two frames for notifying that the receiving session is still enabled.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Search frequency: SMS account poll period.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Account reload frequency: database reload frequency of accounts to be polled.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Number of seconds late for SR processing: only SRs with a recovery date earlier than the current time minus the duration in seconds given by srReadDelay. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Communication timeout with SMS gateway.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Here are the different parameters of the **sms > netsize** node. 

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Timeout in seconds when establishing a connection with Netsize.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Here are the different parameters of the **stat** node. This is the configuration of the MTA statistics module.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Server listening port. See this <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">section</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Here are the different parameters of the **syslogd** node. This is the configuration of the Log management module.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Maximum size in Mb for a log file. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Maximum number of logins.log files to keep. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Here are the different parameters of the **tracking** node. This is the configuration of the tracking server.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Disable malformed URLs generated from previous builds.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> Consolidation period<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Deduplicate openings: remove duplicate open tracking logs to limit the effects of mail previews in mail readers like Outlook.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignore up to X% of errors: do not update tracking indicators as long as the ratio of journals not already taken into account does not reach this value. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Update error indicators: maximum duration before error indicators are recomputed.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Compute indicators during: duration after the validity date of a delivery after which consolidated indicators are no longer computed.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Number of logs requested by call to the remote tracking server.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> API key for the Phishbowl Service Endpoint Integration. This protects redirection of malformed URLs generated from older builds. <br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpoint for the Phishbowl Service Endpoint Integration. This protects redirection of malformed URLs generated from older builds.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignore up to X% of tracking: do not update tracking indicators as long as the ratio of journals not already taken into account does not reach this value.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Update tracking indicators: maximum duration before tracking indicators are recomputed.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Size of browser identifier cache.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Here are the different parameters of the **trackinglogd** node. This is the configuration of the tracking log writing daemon.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Max writing retries: maximum number of files that can be created in case of writing failure in log files.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Maximum log size: maximum space used by logs on disk (in MB). May not be less than 100 MB. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximum log count: maximum number of logs stored in shared memory. Cannot be less than 10000. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Number of logs before purge: number of logs inserted before starting the purge of log files. May not be lower than 50000.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Maximum number of characters saved in shared memory for extra web tracking parameters.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Here are the different parameters of the **web** node. This is the configuration of the Web Module.

For additional information, refer to this [section](configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> Options of the JVM passed as a string.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Maximum number of threads.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Minimum number of threads.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat listening control port: refer to <a href="configure-tomcat.md" target="_blank">Configure Tomcat</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP listening port: refer to <a href="configure-tomcat.md" target="_blank">Configure Tomcat</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Size of the queue for SubmitDelivery calls: maximum number of SubmitDelivery SOAP calls that can be queued.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Notification relay: HostName:Port enabling relay of notifications.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Start the SOAP router in module mode.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Here are the different parameters of the **web > jsp** node. This is the configuration of the parameters used by the JSPs.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debug<br /> </td> 
   <td> Execution of JSP in debug mode or not.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Download folder: download path of installation programs for the client consoles.<br /> </td> 
   <td> String<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Path of .fo file.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL of SOAP router (http://myserver/xxx, http://jni or mailto:xxx).<br /> </td> 
   <td> String<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

The **web > jsp > classpath** node contains the list of all class paths to use when starting JVM. Here is the default configuration:

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

Here are the different parameters of the **web > jssp** node. This is the configuration of the parameters used by the JSSPs.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> Enables the garbage collector of the JavaScript context after each query.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximum number of pages served by a JavaScript context. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

The **web > jsp > classpath** node contains the list of all class paths to use when starting JVM.

### relay {#relay-2}

Here are the different parameters of the **web > relay** node. This is the configuration of the relay for HTTP requests between two zones.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Start the HTTP relay module within the Web server in debug mode.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Forbidden character(s) (Domain): list of forbidden characters in the 'authority' section of a URI.<br /> </td> 
   <td> String<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Forbidden character(s) (Path): list of forbidden characters in the 'path' section of a URI.<br /> </td> 
   <td> String<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Value of the 'mod_dir' module option: list of files to be used during a query on a folder.<br /> </td> 
   <td> String<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Start the HTTP relay module.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Start the HTTP relay module within the Web server. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Wait time before deleting banned url.<br /> </td> 
   <td> String<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Add a **web > relay > url** node for each URL to relay (insert order defines priority) with the following parameters.

For additional information, refer to [Dynamic page security and relays](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) and [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> Authorized IPs: comma separated list of source IP addresses allowed to use the relay for this mask.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> deny<br /> </td> 
   <td> Deny access to these URLs (return an HTTP 403 error)<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> DNS alias to relay: comma separated list of DNS alias masks to relay (ex: '*.adobe.com').<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> HTTP access authorized no matter what the security zone (like webApps). <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Add original host: use the HTTP 'Host' header of the original request when relaying.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Add initial URL path: append the complete path of the URLs to relay to the URL of the target page. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Synchronization status of a public resource (enumeration). Possible values are 'normal' (normal execution), 'blacklist' (url added to denylist in case of error 404) and 'spare' (file upload on spare server if existing).<br /> </td> 
   <td> String<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL of the target page: refer to <a href="configure-tomcat.md" target="_blank">Configure Tomcat</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Maximum execution time (in seconds) of the request being relayed.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Mask of URLs to relay (ex: '/nl*', '*.jsp').<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Here is the default configuration:

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Add a **web > relay > responseHeader** node for each HTTP header to add to replies forwarded to the relay.

For additional information, refer to [Managing HTTP headers](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Header name<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> Header value <br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

Here is the default configuration:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### redirection {#redirection}

Here are the different parameters of the **web > redirection** node. This is the configuration of the redirection module.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Identity Management System (IMS) organization identifier: unique organization identifier within the Adobe Experience Cloud, used in particular for the VisitorID service and the IMS SSO. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Value describing the policy used for permanent cookies (compliant with the P3P Compact Policy format). <br /> </td> 
   <td> String<br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Comma separated list of domains to be configured to explicitly indicate your domain to set cookie. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Database identifier associated with the tracking instance.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Log count by call: number of logs returned by default upon a call of method GetTrackingLogs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Page for expired redirections: URL of Web page used by default by the redirection server when redirection for a delivery action has expired.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximum job count: maximum number of delivery actions in cache. May not be lower than 50. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Start the redirection service.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Start the redirection service in module mode.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Web tracking: creation of logs for the pages visited by unknown users. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Password used by the redirection server.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Here are the different parameters of the **web > redirection > spareServer** node.

For additional information, refer to [Redundant tracking](../../installation/using/configuring-campaign-server.md#redundant-tracking). 

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Taken into account if: the tracking server is taken into account if the expression returns true. <br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Name<br /> </td> 
   <td> String<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> Extra redirection server URL<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Here are the different parameters of the **web > spamCheck** node. This is the configuration the Email anti-spam scoring evaluation parameters.

For additional information, refer to [Configuring SpamAssassin](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Command to execute to evaluate the anti-spam score of an email (e.g. 'perl spamcheck.pl').<br /> </td> 
   <td> String<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Here are the different parameters of the **wfserver** node. This is the workflow process configuration.

For additional information, refer to [High availability workflows and affinities](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Description </th> 
   <th> Type </th> 
   <th> Default value </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> affinity<br /> </td> 
   <td> Affinity<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Start-up parameters<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatic start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Period<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID of JavaScript to execute when starting the process.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Memory consumption alert: alert concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Memory consumption warning: warning concerning the amount of RAM consumed (in Mb) by a given process.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Notification relay: HostName:Port enabling relay of notifications.<br /> </td> 
   <td> String<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Time of the day when the process is automatically restarted. See <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatic process restart</a>.<br /> </td> 
   <td> String<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priority at start. Low priority modules are first started and last stopped. The syslogd module must therefore have the priority 0.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
