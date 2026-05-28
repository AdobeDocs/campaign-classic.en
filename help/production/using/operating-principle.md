---
product: campaign
title: Operating principle
description: Operating principle
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
TQID: https://experienceleague.adobe.com/HCoIXlpEtxAHVh-rj51UD1GTNRnXh8Ir8x4t3QZT9YU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Operating principle{#operating-principle}



Technically, the Adobe Campaign platform is based on several modules.

There are many Adobe Campaign modules. Some operate continuously, while others are started up occasionally to perform administrative tasks (e.g. to configure the database connection) or to run a recurrent task (e.g. consolidating tracking information).

There are three types of Adobe Campaign modules:

* Multi-instance modules: a single process is run for all instances. This applies to the following modules: **web**, **syslogd**, **trackinglogd** and **watchdog** (activities from the **config-default.xml** file).
* Mono-instance modules: one process is run per instance. This applies to the following modules: **mta**, **wfserver**, **inMail**, **sms** and **stat** (activities from the **config-`<instance>`.xml** file).
* Utility modules: these are modules that are run occasionally to perform occasional or recurrent operations (**cleanup**, **config**, downloading tracking logs, etc.).

Module administration is performed using the command line tool **nlserver** installed in the **bin** directory of the installation folder.

The general syntax of the **nlserver** tool is as follows:

**nlserver `<command>` `<command arguments>`**

For the list of available modules, use the **nlserver** command.

The available modules are detailed in the following table:

|  Command  | Description  |
|---|---|
|  aliasCleansing  | Standardizing enumeration values  |
|  billing  | Sending the system activity report to billing@neolane.net  |
|  cleanup  | Cleansing the database: deletes obsolete data from the database and runs an update of the statistics used by the database engine optimizer.  |
|  config  | Modifying server configuration  |
|  export  | Exporting to command line: lets you send to the command line an export model created in the Adobe Campaign client console  |
|  fileconvert  | Converting a set size file  |
|  import  | Importing to command line: lets you send to the command line an import model created in the Adobe Campaign client console.  |
|  inMail  | Inbound mail analyzer  |
|  installsetup  | Availability of the customer installation file  |
|  javascript  | Executing JavaScript scripts, with access to SOAP APIs.  |
|  job  | Command line processing  |
|  merge  | Form merge  |
|  midSourcing  | Recovery of delivery information in mid-sourcing mode  |
|  monitor  | XML Displaying of the status of server processes and scheduled tasks, by instance.  |
|  mta  | Main Agent transfer message  |
|  package  | Importing or exporting entity package files  |
|  pdump  | Displaying server process statuses  |
|  prepareda  | Preparing a delivery action  |
|  restart  | Partial server restart  |
|  runwf  | Execution of a workflow instance  |
|  shutdown  | Full system shutdown  |
|  sms  | SMS notification processing  |
|  sql  | SQL script execution  |
|  start  | Additional starts  |
|  stat  | Maintains MTA connection statistics  |
|  stop  | Partial system shutdown  |
|  submitda  | Submitting a delivery action  |
|  syslogd  | Log and trace writing server  |
|  tracking  | Consolidating and retrieving tracking logs  |
|  trackinglogd  | Tracking log writing and purging server  |
|  watchdog  | Startup and monitoring instance  |
|  web  | Application server (HTTP and SOAP)  |
|  wfserver  | Workflow server  |

>[!IMPORTANT]
>
>There is one last module: the tracking and relay module linked to the application server which, for the sake of performance, is integrated via native mechanisms into an Apache or IIS web server via a dynamic library. There is no Adobe Campaign command enabling you to start or administer this module. You must therefore use the commands of the Web server itself.

Module usage and the syntax of its parameters are displayed using the following command: **nlserver `[module]` -?**

Example:

**nlserver config -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key

```
