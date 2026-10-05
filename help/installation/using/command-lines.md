---
product: campaign
title: Command lines
description: Command lines
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: 'https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
---
# Command lines{#command-lines}



The following command lines require the ability to access the application server. For deployments hosted by Adobe, these commands can only be executed by Adobe.

## Create an instance {#creating-an-instance}

Instance creation can be executed using command lines, with the syntax:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(where **eng** and **fra** are possible values for the `[lang]` parameter)

The command **nlserver config -addinstance:instance1/demo&#42;/eng** enables you to create an instance called **instance1** in English with the DNS mask demo&#42;.

## Declare a database {#declaring-a-database}

You can associate an existing database with an instance from the command line by using the following syntax:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

The following values are possible for the **`[rdbms]`** parameter:

* **postgresql**: for PostgreSQL,
* **oracle**: for Oracle,
* **mssql**: for Microsoft SQL Server,

The following command configures the **demo** instance with the SQL type server known as **base6**, linked to the **campaign** account and its **password** on the **dbsrv** server:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
