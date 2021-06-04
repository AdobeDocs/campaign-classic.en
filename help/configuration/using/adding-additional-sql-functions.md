---
product: campaign
title: Adding additional SQL functions
description: Adding additional SQL functions
audience: configuration
content-type: reference
topic-tags: api
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
---
# Adding additional SQL functions{#adding-additional-sql-functions}

## Introduction {#introduction}

Adobe Campaign allows the user to define **their own functions** that can access SQL functions, both those offered by the database and those which are not already available in the console. This is useful for aggregate functions (average, maximum, sum) for example, which can only be calculated on the server or when the database provides an easier way to implement certain functions, rather than "manually" write the expression in the console (e.g. date management).

This mechanism can also be used if you wanted to use a recent or uncommon database engine SQL function, which is not yet offered by the Adobe Campaign console.

Once these functions have been added, they will appear in the expression editor just like other predefined functions.

>[!IMPORTANT]
>
>SQL function calls in the console are no longer naturally sent to the server. The mechanism described here therefore becomes **the only way to call** on the unplanned SQL function server.

## Installation {#installation}

The function(s) to add are in a **"package" file in XML format**, whose structure is detailed in the following paragraph.

To install it from the console, select the **Tools/Advanced/Import package** options from the menu, then the **[!UICONTROL Install from file]** , and follow the instructions in the import wizard.

>[!IMPORTANT]
>
>Warning: even if the list of imported functions appears in the function editor straight away, they will not be usable until Adobe Campaign has been restarted.

## General structure of package to import {#general-structure-of-package-to-import}

The function(s) to be added can be found in the **"package" file** in XML format. Here is an example:

```

<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>

```

* The **name**, **namespace** and **label** are for information purposes only. They let you view a summary of the package in the installed packages list (Explorer/Administration/Package management/Installed packages).
* The **buildVersion** and **buildNumber** fields are mandatory. They must correspond to the server number to which the console is connected. This information can be found in the "Help/About" box.
* The following blocks, **entities** and **funclist** are mandatory. In funcList, the fields "name" and "namespace" are mandatory, but their name is left up to the user to decide, and they uniquely designate the function list.

  This means that if another list of functions with the same namespace/name pair (here "cus::myList") is imported, the previously imported functions will be deleted. Conversely, if you change this namespace/name pair, the new series of imported functions will be added to the previous one.

* The **group** element lets you specify the function group in which the imported function(s) will appear in the function editor. The @name attribute can either be a name that already exists (in which case the functions will be added to the considered group) or a new name (in which case it will appear in a new group).
* Reminder: possible values for the @name attribute in the `<group>` element are:

  ```

    name="aggregate"      ( label="Aggregates"         )
    name="string"             ( label="String"           )
    name="date"               ( label="Date"             )
    name="numeric"          ( label="Numeric"        )
    name="geomarketing" ( label="Geomarketing"     )
    name="other"              ( label="Others"           )
    name="window"          ( label="Windowing functions" )
    
  ```

>[!IMPORTANT]
>
>Make sure to complete the @label attribute: this is the name that will be displayed in the list of available functions. If you do not enter anything, the group will not have a name. However, if you enter a name other than the existing name, the name of the entire group will change.

If you wish to add functions to several different groups, you can make several `<group>`  elements become tracked in the same list.

Finally, a `<group>` element can contain the definition of one or several functions, that is the purpose of the package file. The  `<function>`   element is detailed in the following paragraph.

## Function descriptor &lt;function>&lt;/function> {#function-descriptor--function-}

The case presented here is a general case whereby we wish to provide the **function implementation**.

Below is an example of a "relative maturity" function which, using an age, indicates for how many years the person has been considered mature.

```

 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>

```

The **@name** field refers the name of the function, and "args" is the list of parameters that will be displayed in the description. In this case, the function will appear as "relativeMaturity ( `<age>` )" in the function selection window.

* **help** is the field displayed at the bottom of the expression editor window.
* **@display** is an informative message.

  >[!NOTE]
  >
  >In the @help and @display attributes, the string "$1" represents the name that was given in the first function parameter (here, "Age"). $2, $3... would represent the following parameters. In the @body attribute detailed below, $1 designates the argument value passed to the function during the call.

  >[!NOTE]
  >
  >The description must be a string of valid XML characters: please note the use of '<' and '>' instead of < and >.

* **@type** is the function return type and is a standard value (long, string, byte, datetime...). If it is omitted, the server determines the best type among the available types within the expression implementing the function.
* **@minArgs** and **maxArgs** designates the number of parameters (minimum and maximum) for a parameter. For example, for a function with 2 parameters, minArgs and maxArgs will be 2 and 2. For 3 parameters, plus 1 optional, they will be 3 and 4 respectively.
* Finally, the **providerPart** element provides the function implementation.

    * The **provider** attribute is mandatory, it specifies the database systems for which the implementation is provided. As shown in the example, when expression syntaxes or underlying functions differ, alternative implementations can be provided according to the database.
    * The **@body** attribute contains the function implementation. Please note: this implementation must be an expression, in database language (not a block of code). Depending on the databases, expressions can be sub-queries ("(select column from table where...)") returning only a single value. For example, this is the case in Oracle (the query must be written in brackets).

  >[!NOTE]
  >
  >If only one or two databases are likely to be queried by the function defined, we can always provide only the definitions corresponding to these databases.

## 'Pass-through' function descriptor {#pass-through--function-descriptor}

A special function descriptor is the **"pass-through"** block, with an unspecified "provider" database system. In this case, "body" implementation can only contain a single function call with a syntax that is not dependent on the database used. Meanwhile, the "ProviderPart" block is unique.

```

    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>

```

In this case, adding a function only serves to make a database function that would not have been available by default, now visible to the client.

## Examples {#examples}

Further function examples can be found in the predefined package "xtkdatakitfuncList.xml".
