---
product: campaign
title: Log precision
description: Log precision
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
---
# Log precision{#log-precision}

You can apply this process to all Adobe Campaign modules to increase log precision.

It involves relaunching the processes with a higher level of logs.

>[!IMPORTANT]
>
>This procedure cancels the services in progress on this module.

Adobe Campaign can operate with two levels of log:

1. The **Verbose** mode is the first level after the standard level. The following command activates it:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Check that the error actually occurred, and then restart the process in the normal way:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. The **TraceFilter** mode, which lets you save the greatest number of logs. It is activated by the following command:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >If you use **tracefilter:&#42;**, all log types are activated: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail  
   >The most useful log types are: **wdbc** (displays all SQL queries), **soap** (displays all SOAP calls), **ldap** (displays all LDAP queries after authentication), **xtkquery** (displays the list of all the querydef).  
   >You can use them individually (**tracefilter:soap,wdbc** for example). You can also activate them all and choose to exclude certain others: **-tracefilter:&#42;,!soap**

   Check that the error actually occurred, and then restart the process in the normal way:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>The logs of these commands are stored in the log file of the module.

Here is an example specific to the Web module. The other modules operate as indicated above.

Before sending this command, check that no job in progress will be affected:

```
nlserver pdump -who
```

Next, shut down and restart the module in **TraceFilter** mode:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Another example:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>The **Tracefile** mode lets you save the logs. In the examples above, the logs are saved in the **var/`<instance-name>`/mta_debug.log** and **var/default/web_debug.log** files.

>[!IMPORTANT]
>
>In Windows, do not add the LD_PRELOAD option. The following command suffices:   
>nlserver web -tomcat -verbose -tracefilter:&#42;

Check that the problem occurs again, and then restart the module:

```
nlserver restart web -tomcat -noconsole
```

All information is available in the file **/usr/local/neolane/nl6/var/default/log/web.log**.
