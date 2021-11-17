---
product: campaign
title: Examples of JavaScript code in workflows
description: These examples show how you can use JavaScript code in a workflow
audience: workflow
content-type: reference
topic-tags: advanced-management
---
# Examples of JavaScript code in workflows{#javascript-in-workflows}

![](../../assets/common.svg)

These examples show how you can use JavaScript code in a workflow:

* [Write to the database](#write-example)
* [Query the database](#read-example)
* [Trigger a workflow, using a static SOAP method](#trigger-example)
* [Interact with the database, using a non-static SOAP method](#interact-example)

[Learn more](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) about static and non-static SOAP methods.

In these examples, the ECMAScript for XML (E4X) extension is used. With this extension, you can combine JavaScript calls and XML primitives in the same script.

To try out these examples, follow these steps:

1. Create a workflow and add these activities to the workflow:
   1. Start activity
   1. JavaScript code activity
   1. End activity

    [Learn more](building-a-workflow.md) about building workflows.

1. Add the JavaScript code to an activity. [Learn more](advanced-parameters.md).
1. Save the workflow.
1. Test the examples:
   1. Start the workflow. [Learn more](starting-a-workflow.md).
   1. Open the journal. [Learn more](monitoring-workflow-execution.md#displaying-logs).

## Example 1: write to the database{#write-example}

To write to the database, you can use the static `Write` method on the `xtk:session` schema:

1. Compose a write request in XML.

1. Write the record:

   1. Call the `Write` method on the `xtk:session` schema.
      
      >[!IMPORTANT]
      > If you use Adobe Campaign v8, we recommend that you use the staging mechanism with the **Ingestion** and **Data update/delete** APIs for the `Write` method in a Snowflake table. [Read more](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

   1. Pass the XML code as an argument for the write request.

### Step 1: compose a write request

You can add, update, and delete records.

#### Insert a record

Because the `insert` operation is the default operation, you do not need to specify it.

Specify this information as XML attributes:

* The schema of the table to be modified
* The table fields to be populated

Example:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Update a record

Use the `_update` operation. [Learn more](../../configuration/using/data-oriented-apis.md).

Specify this information as XML attributes:

* The schema of the table to be modified
* The table fields to be updated
* The key argument that is required to identify the record to be updated

Example:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Delete a record

Use the `DeleteCollection` method. [Learn more](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html). 

Specify this information:

* The schema of the table to be modified
* The `where` clause that is required to identify the record to be updated, in the form of an XML element

Example:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Step 2: write the record

Call the non-static `Write` method on the `xtk:session` schema:

```javascript
xtk.session.Write(myXML)
```

No value is returned for this method.

Add the complete code to a JavaScript code activity in the workflow:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

This video shows how to write to the database:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Example 2: query the database{#read-example}

To query the database, you can use the non-static `xtk:queryDef` instance method:

1. Compose a query in XML.
1. Create a query object.
1. Run the query.

### Step 1: compose a query

Specify the XML code for a `queryDef` entity.

Syntax:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Specify this information:

* The schema of the table to be read
* The operation
* The columns to be returned, in a `select` clause
* The conditions, in a `where` clause
* The filtering criteria, in an `orderBy` clause

You can use these operations:

| Operation | Result |
| --- | --- |
| `select` | Zero or more elements are returned as a collection. |
| `getIfExists` | One element is returned. If no match element exists, then an empty element is returned. |
| `get` | One element is returned. If no match element exists, then an error is returned. |
| `count` | The number of matching records is returned in the form of an element with a `count` attribute. |

Write the `select`, `where`, and `orderBy` clauses as XML elements:

* `select` clause

    Specify the columns to be returned. For example, to select the person's first name and last name, write this code:

    ```xml
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
    ```

    With the `nms:recipient` schema, elements are returned in this form:

    ```xml
    <recipient firstName="Bo" lastName="Didley"/>
    ```

* `where` clause

    To specify conditions, use a `where` clause. For example, to select the records that are located in the **Training** folder, you can write this code:

    ```xml
    <where>
        <condition expr="[folder/@label]='Training'"/>
    </where>
    ```

    When combining multiple expressions, use the boolean operator in the first expression. For example, to select all the persons who are named Isabel Garcia, you can write this code:

    ```xml
    <condition boolOperator="AND" expr="@firstName='Isabel'"/>
    <condition expr="@lastName='Garcia'"/>
    ```

* `orderBy` clause

    To sort the result set, specify the `orderBy` clause as an XML element with the `sortDesc` attribute. For example, to sort the last names in ascending order, you can write this code:

    ```xml
    <orderBy>
        <node expr="@lastName> sortDesc="false"/>
    </orderBy>
    ```

### Step 2: create a query object

To create an entity from the XML code, use the `create(`*`content`*`)` method:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Prefix the `create(`*`content`*`)` method with the schema of the entity to be created.

The *`content`* argument is a string argument and is optional. This argument contains the XML code that describes the entity.

### Step 3: run the query

Follow these steps:

1. Call the `ExecuteQuery` method on the `queryDef` entity:

    ```javascript
    var res = query.ExecuteQuery()
    ```

1. Process the results:
   1. Iterate over the results of the `select` operation, using a loop construct.
   1. Test the results, using the `getIfExists` operation.
   1. Count the results, using the `count` operation.

#### Results of a `select` operation

All the matches are returned as a collection:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

To iterate over the results, use the `for each` loop:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

The loop includes a local recipient variable. For each recipient that is returned in the collection of recipients, the recipient's email is printed out. [Learn more](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) about the `logInfo` function.

#### Results of a `getIfExists` operation

Each match is returned as an element:

```xml
<recipient id="52,378,079">
```

 If there is no match, then an empty element is returned:

```xml
<recipient/>
```

You can refer to the primary key node—for example, the `@id` attribute:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Result of a `get` operation

One match is returned as an element:

```xml
<recipient id="52,378,079">
```

If there is no match, then an error is returned.

>[!TIP]
>
>If you know that there is a match, use the `get` operation. Otherwise, use the `getIfExists` operation. If you use this best practice, then errors reveal unexpected problems. If you use the `get` operation, do not use the `try…catch` statement. The problem is handled by the error handling process of the workflow.

#### Result of a `count` operation

An element with the `count` attribute is returned:

```xml
<recipient count="200">
```

To use the result, refer to the `@count` attribute:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

For the `select` operation, add this code to a JavaScript code activity in the workflow:

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

Because the `select` operation is the default operation, you do not need to specify it.

This video shows how to read from the database:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Trigger a workflow {#trigger-example}

You can trigger workflows programmatically, for example, in technical workflows or to process information that a user has entered on a web application page.

Workflow triggering works through the use of events. You can use these features for events:

* To post an event, you can use the static `PostEvent` method. [Learn more](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* To receive an event, you can use the **[!UICONTROL External signal]** activity. [Learn more](external-signal.md).

You can trigger workflows in different ways:

* You can trigger a workflow inline, that is, from the main script of a **[!UICONTROL JavaScript code]** activity.
* You can trigger a workflow upon completion of another:
  * Add an initialization script to the **[!UICONTROL End]** activity of the initial workflow.
  * Add the **[!UICONTROL External signal]** activity at the start of the target workflow.

    Upon completion of the initial workflow, an event is posted. The outgoing transition is activated and the event variables are populated. Then, the event is received by the target workflow.

    >[!TIP]
    >
    >As a best practice, when you add a script to an activity, enclose the activity name in double hyphens, for example, `-- end --`. [Learn more](workflow-best-practices.md) about workflow best practices.

Syntax of the `PostEvent` method:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In this example, upon completion of the workflow, a short text is passed to the **signal** activity of the **wkfExampleReceiver** workflow:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Because the last parameter is set to `false`, the **wkfExampleReceiver** workflow is triggered every time the initial workflow is completed.

When you trigger workflows, bear these principles in mind:

* The `PostEvent` command runs asynchronously. The command is placed on the server queue. The method returns after the event is posted.
* The target workflow must be started. Otherwise, an error is written to the log file.
* If the target workflow is suspended, then the `PostEvent` command is queued until the workflow resumes.
* The triggered activity does not require that a task be in progress.

This video shows how to use static API methods:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

This video shows how to trigger workflows:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interact with the database {#interact-example}

These examples show how to perform these actions:

* Use the `get` and `create` methods on schemas to use non-static SOAP methods
* Create methods that perform SQL queries
* Use the `write` method to insert, update, and delete records

Follow these steps:

1. Define the query:

   * Retrieve an entity by using the `create` method on the corresponding schema—for example, the `xtk:workflow` schema. [Learn more](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Use the `queryDef` method to issue an SQL query.

1. Run the query using the `ExecuteQuery` method. [Learn more](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Use the `for each` loop to retrieve the results.

### Syntax of the `queryDef` method with a `select` clause

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create` method

#### Example 1: select records and write to the journal

The internal names of the workflows that are located in the **wfExamples** folder are selected. The results are sorted by internal name, in ascending order, and written to the journal.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Example 2: delete records

The first name, the last name, the email and the ID of all the recipients who are named Chris Smith are selected. The results are sorted by email, in ascending order, and written to the journal. A `delete` operation is used to delete the selected records.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Example 3: select records and write to the journal

In this example, a non-static method is used. The email and birth year of all the recipients whose information is stored in the **1234** folder and whose email domain name starts with "adobe" are selected. The results are sorted by birth date in descending order. The recipients' email is written to the journal.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write` method

You can insert, update, and delete records. You can use the `Write` method on any schema in Adobe Campaign. Because this method is static, you do not need to create an object. You can use these operations:

* The `update` operation
* The `insertOrUpdate` operation, with the `_key` argument to identify the record to be updated

  If you do not specify the **Recipients** folder, then, if a match exists, the record is updated in any subfolder. Otherwise, the record is created in the root **Recipients** folder.

* The `delete` operation

>[!IMPORTANT]
> If you use Adobe Campaign v8, we recommend that you use the staging mechanism with the **Ingestion** and **Data update/delete** APIs for the `Write` method in a Snowflake table. [Read more](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}.

#### Example 1: insert or update a record

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Example 2: delete records

This example combines a static method and a non-static method.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

This video shows how to use non-static API methods:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

This video shows an example of use of a non-static API method in a workflow:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Related topics

* [Data-oriented APIs](../../configuration/using/data-oriented-apis.md)
* [JavaScript scripts and templates](javascript-scripts-and-templates.md)
* [SOAP methods in JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### API documentation

* [Samples of SOAP calls](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Methods:
  * [Create](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
  * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
  * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
  * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
  * [Write](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [logInfo function](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)