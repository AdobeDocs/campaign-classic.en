---
title: Database
seo-title: Database
description: Database
seo-description: 
page-status-flag: never-activated
uuid: 58f86bbe-d103-4dd8-8bcc-a5410b70feee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 32b2aaa8-0e83-4c39-bce8-a89fede93c64
index: y
internal: n
snippet: y
---

# Database{#database}

The database server can run on any given operating system regardless of the operating system used by the application server or servers, as long as there is network connectivity between them.

The operating system of the database server is not important so long as connectivity with the different components of Adobe Campaign is available.

Also check the [Database access layers](../../installation/using/database.md#database-access-layers) section.

## Microsoft SQL Server {#microsoft-sql-server}

The native client must be installed on the Adobe Campaign application servers.

You can check for the native client on the server via the ODBC driver configuration panel, under **SQL Native Client** (for Microsoft SQL Server 2005 clients), or **SQL Server Native Client 10.0** (for Microsoft SQL Server 2008 and 2008 R2 clients), or **SQL Server Native Client 11.0** (for Microsoft SQL Server 2012 clients).

The following access DLLs must be present:

* **sqlncli.dll** for Microsoft SQL Server 2005 client,
* **sqlncli10.dll** for Microsoft SQL Server 2008 and 2008 R2 clients,
* **sqlncli11.dll** for Microsoft SQL Server 2012 client.

  Access DLLs are found on the Microsoft website.

>[!NOTE]
>
>Access to Microsoft SQL Server from an application server running in Linux is not supported.

## Oracle {#oracle}

>[!NOTE]
>
>Column names with multi-byte characters are not supported.

The **NLS_NCHAR_CHARACTERSET** and **NLS_CHARACTERSET** parameters need to be correctly properly configured in order for the database to work in Unicode or ANSI.

Adobe Campaign uses default Oracle encoding. Using other encoding may trigger compatibility issues: in this case, please contact technical support.

To find out about your encoding, use the following **sqlplus** command:

```
SELECT * FROM nls_database_parameters ;
```

* For a Unicode installation, the encodings supported are:

  ```
  
  NLS_NCHAR_CHARACTERSET         AL16UTF16
  NLS_CHARACTERSET         AL32UTF8
  
  ```

* For an ANSI installation (non-unicode), only the following encoding is supported:

  NLS_CHARACTERSET WE8MSWIN1252

To log on to **sqlplus**, use the Oracle user profile:

```
su - oracle 
sqlplus 
[login] [password]
```

You can also refer to [Oracle Client in Linux](../../installation/using/database.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

We recommend that you install the UTF-8 support when installing the database engine. This way you will be able to create Unicode databases.
