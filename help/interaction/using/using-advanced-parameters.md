---
solution: Campaign Classic
product: campaign
title: Using advanced parameters
description: Using advanced parameters
audience: interaction
content-type: reference
topic-tags: advanced-parameters
---

# Advanced parameters{#using-advanced-parameters}

This chapter details available advanced parameters in Campaign Interaction module.

>[!IMPORTANT]
>
>The following chapter is intended for **technical administrators**.

* You can use additional contextual data. [Learn more](../../interaction/using/additional-data.md)
* You can enrich the application contexts of the suggested offers via an incoming channel. To do this, the **nms:interaction** interaction schema must be extended. [Learn more](../../interaction/using/extension-example.md)
* Creating a test environment is detailed in [this section](../../interaction/using/creating-a-test-environment.md) 
* You can modify standard engine behavior using hooks. [Learn more](../../interaction/using/hooks.md)
* Finally, using Interaction with a distributed architecture is detailed in [this section](../../interaction/using/distributed-architectures.md)

## Configure data buffer

You can configure a data buffer zone to increase inbound Interaction performance by desynchronizing offer proposition calculations. This configuration is to be carried out in the instance's own configuration file (config-Instance.xml). For more on this, refer to [this section](../../installation/using/configuring-campaign-server.md#interaction-data-buffer).

>[!NOTE]
>
>This parameter is essential if you use Interaction with a distributed architecture.

