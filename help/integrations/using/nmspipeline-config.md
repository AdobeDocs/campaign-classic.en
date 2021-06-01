---
product: campaign
title: Configuring the integration
description: Configuring the integration
audience: integrations
content-type: reference
---

# Pipeline option NmsPipeline_Config {#nmspipeline_config}

Once the authentication works, [!DNL pipelined] can retrieve the events and process them. It only processes triggers that are configured in Adobe Campaign, ignoring the others. The trigger must have been generated from Analytics and pushed to the pipeline beforehand.
The option can also be configured with a wildcard to catch all triggers regardless of name.

The configuration of the triggers is done in an option, under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. The option name is **[!UICONTROL NmsPipeline_Config]**. Data type is "long text" in JSON format.

This example specifies two triggers.

Paste the JSON code from this template into the option value. Make sure to remove comments.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
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
```

This second example catches all triggers.

```
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
```

>[!NOTE]
>
>The [!DNL Trigger] UID value to a specific trigger name in the Analytics interface can found as part of the URL querystring parameters in the Triggers interface. The triggerType UID is passed in the pipeline data stream and code can be written into the pipeline.JS to map the trigger UID to a user-friendly label that can be stored in a Trigger Name column in the pipelineEvents schema.

## The consumer parameter {#consumer-parameter}

The pipeline works with a “supplier and consumer” model. There can be many consumers on the same queue. Messages are “consumed” only for an individual consumer. Each consumer gets its own “copy” of the messages.

The “consumer” parameter identifies the instance as one of these consumers. It is the identity of the instance calling the pipeline. You can fill it with the instance name. The pipeline service keeps track of the messages retrieved by each consumer. Using different consumers for different instances ensures that every message is sent to each instance.

## How to configure the Pipeline option {#configure-pipeline-option}

Add or edit Experience Cloud triggers under the "triggers" array; do not edit the rest.
Make sure that the JSON is valid with the help of this this [website](http://jsonlint.com/).

* "name" is the trigger ID. A wildcard "*" catches all triggers.
* "Consumer" is any unique string that uniquely identifies the nlserver instance. It can usually be the instance name itself. For multiple environments (dev/stage/prod), please ensure it is unique for each of them so that each instance gets a copy of the message.
* [!DNL Pipelined] also supports the "aliases" topic.

Restart [!DNL pipelined] after making changes.
