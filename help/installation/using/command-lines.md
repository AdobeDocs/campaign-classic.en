---
title: Command lines
seo-title: Command lines
description: Command lines
seo-description: 
page-status-flag: never-activated
uuid: d7b5d402-59f6-4e77-92c6-6a7940fb7c76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: cee7d05c-db4c-4470-99e7-845ce919d9cc
index: y
internal: n
snippet: y
---

# Command lines{#command-lines}

The following command lines require the ability to access the application server. For deployments hosted by Adobe, these commands can only be executed by Adobe.

## Creating an instance {#creating-an-instance}

Instance creation can be executed using command lines, with the syntax:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(where **eng** and **fra** are possible values for the [lang] parameter)

The command **nlserver config -addinstance:instance1/demo&#42;/eng** enables you to create an instance called **instance1** in English with the DNS mask demo&#42;.

## Declaring a database {#declaring-a-database}

You can associate an existing database with an instance from the command line by using the following syntax:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

The following values are possible for the **[rdbms]** parameter:

* **postgresql**: for PostgreSQL,
* **oracle**: for Oracle,
* **mssql**: for Microsoft SQL Server,
* **DB2**: for the DB2 engine.

The following command configures the **demo** instance with the SQL type server known as **base6**, linked to the **campaign** account and its **password** on the **dbsrv** server:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

