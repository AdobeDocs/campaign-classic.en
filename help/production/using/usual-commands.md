---
product: campaign
title: Usual commands
description: Usual commands
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
---
# Usual commands{#usual-commands}

![](../../assets/v7-only.svg)

This section lists the usual commands in Adobe Campaign.

The command **nlserver** is the input command for the whole Adobe Campaign application.

This command has the following syntax: **nlserver **`<command>`** **`<arguments>`****

The parameter **`<command>`** corresponds to the module.

>[!NOTE]
>
>* In any case, you can add the **-noconsole** argument to delete comments displayed once the modules are started.
>* Conversely, you can add the argument **-verbose** to display more information.
>

## Monitoring commands {#monitoring-commands-}

>[!NOTE]
>
>To list all modules, you need to use the **nlserver pdump** command.

You can add the parameter **-who** to list the connections in progress (database and application).

```
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400

```

Another useful command is **nlserver monitor**. It lists the monitoring XML file (obtained in the Adobe Campaign client or via the **monitor.jsp** web page).

You can add the parameter **-missing** to list the absent modules (error in modules, modules shut down, etc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test

```

This corresponds to the modules with automatic startup but which have not been launched.

## Module launch commands {#module-launch-commands}

The syntax to launch modules will still have the following format:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corresponds to the name of the instance as entered in the configuration files, or **default** for mono-instance modules.

## Shut down services {#shut-down-services}

To stop Adobe Campaign services, use one of the following commands:

* If you have root or administrator access:

    * In Linux:

      ```    
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >Starting 20.1, we recommend using the following command instead (for Linux): **systemctl stop nlserver**

    * In Windows:

      ```    
      net stop nlserver6
      ```

* If not, then in the Adobe Campaign account:

  ```
  nlserver shutdown 
  ```

## Restart services {#restart-services}

Similarly, in order to restart Adobe Campaign you can use one of the following commands:

* If you have root or administrator access:

    * In Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >Starting 20.1, we recommend using the following command instead (for Linux): **systemctl start nlserver**

    * In Windows: net start nlserver6

* Otherwise, in the Adobe Campaign account: **nlserver watchdog -svc -noconsole**

## The config command {#the-config-command}

The **config** command lets you manage server configuration, including the reconfiguration of the database connection.

Use the **config** command of the **nlserver** executable file with the **-setdblogin** parameter.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Enter the password.

To change the **internal** password: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>To log on with the **Internal** identifier, you need to have defined a password beforehand. For more on this, refer to [this section](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* In general, instead of modifying the configuration files by hand, you can use the **config** command 
>* To get the list of parameters, use the **-?** parameter: **nlserver config -?**
>* In the case of an Oracle database, you must not specify the account. The syntax will be as follows:
>
>  nlserver config -setdblogin:Oracle:test6@dbserver
>
