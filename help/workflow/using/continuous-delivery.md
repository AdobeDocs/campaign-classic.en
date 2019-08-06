---
title: Continuous delivery
seo-title: Continuous delivery
description: Continuous delivery
seo-description: 
page-status-flag: never-activated
uuid: 493881c2-ed7f-4ffd-bcb6-e00ae6d603b0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 610128ce-f908-496a-9681-15c9a9665464
index: y
internal: n
snippet: y
---

# Continuous delivery{#continuous-delivery}

A **Continuous delivery** type action lets you add new recipients to an existing delivery. This delivery type avoids you having to create a new delivery each time: This mode is often more efficient, in particular for low-volume alerts or notifications sent out as and when needed. At a delivery template level, you can specify a script to calculate the label (and the campaign folder) of the associated delivery. If the script calculates a delivery that does not yet exist, it is created on the fly.

![](assets/edit_diffusion_fil.png)

The **Process errors** option displays a particular transition which will be activated if an error is generated. In this case, the workflow does not go into error mode and carries on with the execution.

Errors taken into account are file system errors (file could not be moved, directory could not be accessed, etc.).

This option does not process errors related to activity configuration, i.e. invalid values.

## Input parameters {#input-parameters}

* tableName
* schema

Each inbound event must specify a target defined by these parameters.

Only when the **Specified by the inbound event** option is selected.

## Output parameters {#output-parameters}

* tableName
* schema
* recCount

This set of three values identifies the target resulting from the on the fly delivery. **tableName** is the name of the table which memorizes the target's identifiers, **schema** is the schema of the population (usually nms:recipient) and **recCount** is the number of elements in the table.

The transition associated with the complement has the same parameters.
