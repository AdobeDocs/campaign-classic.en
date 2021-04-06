---
solution: Campaign Classic
product: campaign
title: Additional web tracking parameters
description: Learn more about parameters for web tracking
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
---
# Additional parameters{#additional-parameters}

## Definition of parameters {#definition-of-parameters}

Your Adobe Campaign platform offers two TRANSACTION-type web-tracking parameters as a standard:

* **amount**: represents the amount of a transaction,
* **article**: represents the number of items in a transaction.

These parameters are defined in the **nms:webTrackingLog** schema, and are some of the indicators seen in reporting.

To define additional parameters, you must extend this schema.

**Example**:

```

<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>

```

You can display the values of these parameters by configuring the tracking log list (of a delivery or recipient).

## Redirection server configuration {#redirection-server-configuration}

In the server configuration, you can define the maximum number of characters to be taken into account for your web tracking parameters.

>[!IMPORTANT]
>
>Increasing the maximum number of characters to be taken into account can impact the web tracking performance of your platform.

To do this, modify the **webTrackingParamSize** attribute of the **`<trackinglogd>`** element in the **serverConf.xml** file. This file is saved in the **conf** subdirectory of the Adobe Campaign installation directory.

**Example**:

The default value is 64 characters. This value lets you take into account the **amount** and **article** ("amount=xxxxxxxx&article=xxxxxxxx") standard parameters.

By taking into account both parameters (size of name + size of value) indicated in the above extension schema example, you can modify the configuration to take 100 characters into account ("amount=xxxxxxxx&article=xxxxxxxx&mode=xxxxxxxxxx&code=xxxxx").

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

When the configuration has been modified, you must:

* Stop the web server that hosts the redirection module (Apache, IIS, etc.),
* Stop the Adobe Campaign server: **net stop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux,

   >[!NOTE]
   >
   >Starting 20.1, we recommend using the following command instead (for Linux): **systemctl stop nlserver**

* In Linux, delete the shared memory segments using the **ipcrm** command,
* Restart the Adobe Campaign server: **net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux,

   >[!NOTE]
   >
   >Starting 20.1, we recommend using the following command instead (for Linux): **systemctl start nlserver**

* Restart the web server.

**Example**: taking into account the configuration under Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>For Linux, if you increase the size of the **webTrackingParamSize** or **maxSharedLogs** parameters, you may need to increase the size of the shared memory (SHM).
