---
product: campaign
title: Switching to Unicode
description: Switching to Unicode
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
---
# Switching to Unicode{#switching-to-unicode}

For an existing **prod** instance in Linux/PostgreSQL, the steps for switching to unicode are as follows:

1. Stop the processes writing to the database:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Dump the database:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Create a Unicode database:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Restore the database:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Update the option indicating that the database is Unicode:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. On the tracking servers:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Add the **u** character in front of the value relating to the database identifier (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. On servers calling the database:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Modify the database reference:

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Reboot all the machines:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confirm the switch. To do this, connect via the Adobe Campaign console and:

    * check that the data is displayed correctly, in particular the accentuated characters: 
    * launch a delivery and check that the tracking retrieval works.
