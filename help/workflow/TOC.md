---
audience: all
product: campaign
title: Adobe Campaign Workflow Guide
breadcrumb-title: Campaign Workflows
product: campaign
title: Campaign Workflow Guide
user-guide-description: Design, execute, manage, and monitor your workflows in Adobe Campaign.
---

# Design and execute workflows in Campaign {#design-and-execute-wf}

+ Get started with workflows {#introduction}
    + [About workflows](workflow/using/about-workflows.md)
    + [About activities](workflow/using/about-activities.md)
    + [Building a workflow](workflow/using/building-a-workflow.md)
    + [Targeting data](workflow/using/targeting-data.md)
    + [How to use workflow data](workflow/using/how-to-use-workflow-data.md)
    + [Workflow best practices](workflow/using/workflow-best-practices.md)
+  Executing a workflow {#executing-a-workflow}
    + [Starting a workflow](workflow/using/starting-a-workflow.md)
    + [Workflow life cycle](workflow/using/workflow-life-cycle.md)
    + [Data life cycle](workflow/using/data-life-cycle.md)
    + [Defining approvals](workflow/using/defining-approvals.md)
    + [Architecture](workflow/using/architecture.md)
+ Targeting activities {#targeting-activities}
    + [About targeting activities](workflow/using/about-targeting-activities.md)
    + [Query](workflow/using/query.md)
    + [Incremental query](workflow/using/incremental-query.md)
    + [Read list](workflow/using/read-list.md)
    + [Union](workflow/using/union.md)
    + [Intersection](workflow/using/intersection.md)
    + [Exclusion](workflow/using/exclusion.md)
    + [Split](workflow/using/split.md)
    + [Cells](workflow/using/cells.md)
    + [Offers by cell](workflow/using/offers-by-cell.md)
    + [Delivery outline](workflow/using/delivery-outline.md)
    + [Enrichment](workflow/using/enrichment.md)
    + [Edit schema](workflow/using/edit-schema.md)
    + [Offer engine](workflow/using/offer-engine.md)
    + [Deduplication](workflow/using/deduplication.md)
    + [Change dimension](workflow/using/change-dimension.md)
    + [List update](workflow/using/list-update.md)
    + [Subscription Services](workflow/using/subscription-services.md)
    + [Update data](workflow/using/update-data.md)
    + [CRM Connector](workflow/using/crm-connector.md)
+ Flow control activities {#flow-control-activities}
    + [About flow control activities](workflow/using/about-flow-control-activities.md)
    + [Start and end](workflow/using/start-and-end.md)
    + [Fork](workflow/using/fork.md)
    + [AND-join](workflow/using/and-join.md)
    + [Scheduler](workflow/using/scheduler.md)
    + [Test](workflow/using/test.md)
    + [Wait](workflow/using/wait.md)
    + [Time constraint](workflow/using/time-constraint.md)
    + [Sub-workflow](workflow/using/sub-workflow.md)
    + [Jump (start point and end point)](workflow/using/jump--start-point-and-end-point-.md)
    + [External signal](workflow/using/external-signal.md)
    + [Approval](workflow/using/approval.md)
    + [Alert](workflow/using/alert.md)
    + [Task](workflow/using/task.md)
+ Action activities {#action-activities}
    + [About action activities](workflow/using/about-action-activities.md)
    + [Delivery](workflow/using/delivery.md)
    + [Delivery control](workflow/using/delivery-control.md)
    + [Continuous delivery](workflow/using/continuous-delivery.md)
    + [Recurring delivery](workflow/using/recurring-delivery.md)
    + [Cross-channel deliveries](workflow/using/cross-channel-deliveries.md)
    + [Local approval](workflow/using/local-approval.md)
    + [Data loading (RDBMS)](workflow/using/data-loading--rdbms-.md)
    + [Loading (SOAP)](workflow/using/loading--soap-.md)
    + [Data loading (file)](workflow/using/data-loading--file-.md)
    + [Content Management](workflow/using/content-management.md)
    + [Data extraction (file)](workflow/using/extraction--file-.md)
    + [SQL code and JavaScript code](workflow/using/sql-code-and-javascript-code.md)
    + [SQL Data Management](workflow/using/sql-data-management.md)
    + [Nlserver module](workflow/using/nlserver-module.md)
    + [Update aggregate](workflow/using/update-aggregate.md)
+ Event activities {#event-activities}
    + [About event activities](workflow/using/about-event-activities.md)
    + [File collector](workflow/using/file-collector.md)
    + [File transfer](workflow/using/file-transfer.md)
    + [Web download](workflow/using/web-download.md)
    + [Inbound Emails](workflow/using/inbound-emails.md)
    + [Inbound SMS](workflow/using/inbound-sms.md)
+ Use cases {#use-cases}
    + [About workflow use cases](workflow/using/about-workflow-use-cases.md)
    + Deliveries {#deliveries}
        + [Using the local approval activity](workflow/using/using-the-local-approval-activity.md)
        + [A/B testing](workflow/using/a-b-testing.md)
        + [Sending a birthday email](workflow/using/sending-a-birthday-email.md)
        + [Loading delivery content](workflow/using/loading-delivery-content.md)
        + [Cross-channel delivery workflow](workflow/using/cross-channel-delivery-workflow.md)
        + [Email enrichment with custom date fields](workflow/using/email-enrichment-with-custom-date-fields.md)
    + Monitoring {#monitoring}
        + [Sending a report to a list](workflow/using/sending-a-report-to-a-list.md)
        + [Supervising workflows](workflow/using/supervising-workflows.md)
        + [Sending personalized alerts to operators](workflow/using/sending-personalized-alerts-to-operators.md)
    + Data management {#data-management}   
        + [Coordinating data updates](workflow/using/coordinating-data-updates.md)
        + [Creating a summary list](workflow/using/creating-a-summary-list.md)
        + [Enriching data](workflow/using/enriching-data.md) 
        + [Using aggregates](workflow/using/using-aggregates.md)
        + [Using the Deduplication activity's merge functionality](workflow/using/deduplication-merge.md)
        + [Setting up a recurring import workflow](workflow/using/recurring-import-workflow.md)
    + Designing queries {#designing-queries}
        + [Quarterly list update using an incremental query](workflow/using/quarterly-list-update.md)
    + Targeting {#designing-queries}
        + [Querying the recipient table](workflow/using/querying-recipient-table.md)
        + [Querying delivery information](workflow/using/querying-delivery-information.md)
        + [Performing aggregate computing](workflow/using/performing-aggregate-computing.md)
        + [Querying using grouping management](workflow/using/querying-using-grouping-management.md)
        + [Querying using a many-to-many-relationship](workflow/using/querying-using-many-to-many-relationship.md)
        + [Adding an enumeration type calculated field](workflow/using/adding-enumeration-type-calculated-field.md)
        + [Creating a filter](workflow/using/creating-a-filter.md)
        + [Filtering duplicated recipients](workflow/using/filtering-duplicated-recipients.md)
+ Monitoring workflows {#monitoring-workflows}
    + [Monitoring workflow execution](workflow/using/monitoring-workflow-execution.md)
    + [Monitoring technical workflows](workflow/using/monitoring-technical-workflows.md)
    + [Workflow HeatMap](workflow/using/heatmap.md)
+ Advanced management {#advanced-management}
    + [Workflow properties](workflow/using/workflow-properties.md)
    + [Advanced parameters](workflow/using/advanced-parameters.md)
    + [JavaScript scripts and templates](workflow/using/javascript-scripts-and-templates.md)
    + [Accessing an external database](workflow/using/accessing-an-external-database--fda-.md)
    + [Managing rights](workflow/using/managing-rights.md)
    + [Managing activity images](workflow/using/managing-activity-images.md)
    + [Managing propensity](workflow/using/managing-propensity.md)
    + [Managing time zones](workflow/using/managing-time-zones.md)
    + [Technical workflows](workflow/using/about-technical-workflows.md)