---
title: Configuring the integration
seo-title: Configuring the integration
description: Configuring the integration
seo-description: 
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
---

# Configuring pipeline {#configuring-pipeline}

Authentication parameters such as the customer ID, the private key, and the authentication endpoint are configured in the instance configuration files.
The list of triggers to be processed is configured in an option. It is in JSON format.
The trigger is processed immediately using Javascript code. It is saved into a database table with no further processing in real time.
The triggers are used for targeting by a campaign workflow that sends emails. The campaign is set up so that a customer that has both trigger events receives an email.

>[!CAUTION]
>
>In case of Hybrid deployment, ensure pipeline is configured on mid instance.

## Prerequisites {#prerequisites}

Using [!DNL Experience Cloud Triggers] in Campaign requires:

* Adobe Campaign 19.1.9 version or 20.3.1. and above.
* Analytics Standard version.

Prerequisite configurations are:

* Adobe IO project authentication
* The IMSOrgId, the identifier of the Experience Cloud customer with Adobe Analytics added.
* The provisioning team must have System Administrator Privileges for the customer's IMS Org
* Configuration of the triggers in Adobe Analytics.

## Authentication and configuration files {#authentication-configuration}

Authentication is required since Pipeline is hosted in the Adobe Experience Cloud.
It uses a pair of public and private keys. This process is the same function as a user/password, only more secure.
Authentication is supported for the Marketing cloud via Adobe IO Project.

## Step 1: Creating/updating Adobe IO Project

For Hosted customers, please create a customer care ticket to Enable your org with Adobe IO Technical Account Tokens for Triggers Integration.

For On Premise customers, please visit this article to set it up: Adobe IO Project provisioning for ACC . Please select "Adobe Analytics" while adding API to the Adobe IO Credential.

## Step 2: Pipeline option NmsPipeline_Config

Once the authentication works, pipelined will retrieve the events and process them. It will only process triggers that are configured in Adobe Campaign, ignoring the others. Of course, the trigger must have been generated from Analytics and pushed to the pipeline beforehand.
The option can also be configured with a wildcard in order to catch all triggers regardless of name.
The configuration of the triggers is done in an option, under Administration > Platform > Options. The option name is NmsPipeline_Config. Data type is "long text". It's in JSON format.

Example 1
This example specifies two triggers.
Paste the JSON code from this template into the option value. Make sure to remove comments.

{
    "topics": [ // list of "topics" that the pipelined is listening to.
       {
            "name": "triggers", // Name of the first topic : triggers.
            "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
            "triggers": [ // Array of triggers.
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}


Example 2
This example catches all triggers.

 {
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }

Important Note:  The trigger UID value to a specific trigger name in the Analytics UI and can found as part of the URL querystring parameters on the trigger UI. The triggerType UID is passed in the pipeline data stream and code can be written into the pipeline.JS to map the trigger UID to a friendly label that can be stored in a Trigger Name column in the pipelineEvents schema.

Careful notation and logging of which triggers are active should be kept until the Analytics UI can be updated to visually include the triggerType ID that is passed in the pipeline data stream.

### The Consumer parameter

The pipeline works with a “supplier and consumer” model. There can be many consumers on the same queue. Messages are “consumed” only for an individual consumer. Each consumer gets its own “copy” of the messages.

The “consumer” parameter identifies the instance as one of these consumers. It’s the identity of the instance calling the pipeline. You can fill it with the instance name which can be found on the Monitoring page of the Client Console.

The pipeline service keeps track of the messages retrieved by each consumer. Using different consumers for different instances makes sure that every message is sent to each instance.

### How to configure Pipeline option

Add or edit triggers under the "triggers" array; do not edit the rest.
Make sure the JSON is valid; this website can help: http://jsonlint.com/

"name" is the trigger ID. A wildcard "*" will catch all triggers.
"Consumer" is the name of the calling instance or application. It should be configured with the instance name and customer name.
Pipelined also supports the "aliases" topic.
Restart pipelined after making changes.

## Step 3: Optional configuration

Optional Configuration
You can tweak some internal parameters as per your load requirements. Please be careful and be sure to test them before putting them into production. The list of optional parameters is available in the Optional Configuration section in the Annexes below.

Pipelined process auto-start
The pipelined process needs to be started automatically.

For this, set the <pipelined> element in the config file to autostart="true":

 <pipelined autoStart="true" ... "/>
Pipelined process restart
A restart is required for the changes to take effect:
nlserver restart pipelined@instance

## Step 4: Validation

To validate the pipeline setup for provisioning., follow the steps below:

Make sure the pipelined process is running.
Check the pipelined.log for pipeline connection logs.
Verify the connection and pings are received. (Hosted customers can use the Monitoring Universe from the Client Console)
Manual validation is completed.