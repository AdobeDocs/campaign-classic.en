---
title: Sending personalized alerts to operators
seo-title: Sending personalized alerts to operators
description: Sending personalized alerts to operators
seo-description: 
page-status-flag: never-activated
uuid: 7096e1c6-2138-49c0-9d36-5d42cc4c1c9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 6e5cf914-2cc1-4b18-b77b-7cbf39cd1d15
index: y
internal: n
snippet: y
---

# Sending personalized alerts to operators{#sending-personalized-alerts-to-operators}

In this example, we want to send an alert to an operator that will contain the name of profiles who opened a newsletter but did not click the link it contains.

The profiles' first and last name fields are linked to the **Recipients** targeting dimension, whereas the **Alert** activity is linked to the **Operator** targeting dimension. As a result, there is no field available between the two targeting dimensions to perform a reconciliation and retrieve the first and last name fields, and display them in the Alert activity.

The process is to build a workflow as below:

1. Use a **Query** activity to target data.
1. Add a **JavaScript code** activity into the workflow to save the population form the query to the instance variable.
1. Use a **Test** activity to check the population count.
1. Use an **Alert** activity to send an alert to an operator, depending on the **Test** activity result.

![](assets/uc_operator_1.png)

## Saving the population to the instance variable {#saving-the-population-to-the-instance-variable}

Add the code below into the **JavaScript code** activity.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Make sure that the Javascript code corresponds to your workflow information:

* The **queryDef schema** tag should corresponds to the name of the targeting dimension used in the query activity.
* The **node expr** tag should correspond to the name of the fields you want to retrieve.

![](assets/uc_operator_3.png)

To retrieve these information, follow the steps below:

1. Right-click the outbound transition from the **Query** ativity, then select **Display the target**.

   ![](assets/uc_operator_4.png)

1. Right-click the list, then select **Configure list**.

   ![](assets/uc_operator_5.png)

1. The query targeting dimension and fields names display in the list.

   ![](assets/uc_operator_6.png)

## Testing the population count {#testing-the-population-count}

Add the code below into the **Test** activity to check if the targeted population contains at least 1 profile.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Setting up the alert {#setting-up-the-alert}

Now that the population has been added into the instance variable with the desired fields, you can add these information into the **Alert** activity.

To do this, add into the **Source** tab the code below:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>The **<%= item.target.recipient.@fieldName %>** command lets you add one of the fields that have been saved to the instance variable through the **JavaScript code** activity.  
>You can add as many fields as desired, as long as they have been inserted into the JavaScript code.

![](assets/uc_operator_8.png)

