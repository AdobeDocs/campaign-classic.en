---
product: campaign
title: Common questions
description: Campaign Classic FAQ
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
---
# Developers FAQ {#dev-faq}

As an open solution, Adobe Campaign is ready for customization and advanced applications development.

## What is the Campaign data model? {#what-is-the-campaign-data-model}

The conceptual data model of the Adobe Campaign database consists in a set of built-in tables and their interaction. The physical and logical structure of the data carried in the application is described in XML. It obeys a grammar specific to Adobe Campaign, called a schema. For more on Adobe Campaign schemas, [refer to this section](../../configuration/using/about-schema-edition.md).

[Click here to learn more about Campaign datamodel](https://helpx.adobe.com/campaign/kb/acc-datamodel.html).

Best practices are listed [in this article](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).

## How to work with Campaign schemas? {#how-to-work-with-campaign-schemas-}

In Adobe Campaign, data schemas are used to:

* Define how data objects within the application are tied to underlying database tables.
* Define links between the different data objects within the Campaign application.
* Define and describe the individual fields included in each object.

Read out the [Tables and schemas getting started](../../configuration/using/about-schema-edition.md) to understand how to work with data schema, extend and customize Campaign to address your needs.

## How to use a custom recipient table? {#how-to-use-a-custom-recipient-table-}

You can create and implement a non-standard recipient table in Campaign to send your messages.

[Click here to learn more](../../configuration/using/about-custom-recipient-table.md)

## What are the best practices to define queries in Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

Adobe Campaign query editor is a powerful tool to explore data and build segments.

The Adobe Campaign query tool can be found on multiple levels of the software: to create a target population, segment customers, extract and filter tracking logs, build filters, etc.

You can query Campaign database using the generic query editor. It is accessed via the **Tools > Generic query editor...** menu. It lets you extract information stored in a database and organize, group, sort, etc. For instance, the user can recover recipients who clicked more than 'n' times on the link of a newsletter over a given period. This tool lets you collect, sort and display results based on your needs. This tool combines all Adobe Campaign querying possibilities. For instance, it lets you create and save restriction filters. This means that a user filter created in the Generic query editor can be used in the Query box of a targeting workflow, etc.

Queries are created using fields of the selected table or using a formula. Main principles to create a query on Campaign database are described [in this page](../../platform/using/about-queries-in-campaign.md).

[Click here](../../workflow/using/query.md) to discover Campaign query editor.

## How can I import a data package? {#how-can-i-import-a-data-package-}

Adobe Campaign allows you to export or import the platform configuration and data through a package system. Data packages let entities of the Adobe Campaign database be displayed via files in XML format. Each entity contained in a package is represented with all of its data.

The principle of data packages is to export a data configuration and integrate it into another Adobe Campaign system.

[Click here](../../platform/using/working-with-data-packages.md) to learn how to work with data packages to import and export Campaign configurations.

## Where can I find the list of Campaign Classic APIs? {#where-can-i-find-the-list-of-campaign-classic-apis}

All Campaign APIs including their full description is available in this [dedicated documentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).
