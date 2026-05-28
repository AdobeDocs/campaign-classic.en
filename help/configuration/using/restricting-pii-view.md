---
product: campaign
title: Restrict PI view
description: Learn how to restrict PI view
feature: PI
role: Developer
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
TQID: https://experienceleague.adobe.com/sgAVeWQxzJ6c4DB9VIA-5joGq0Y8bZ8UZfA9dg9xdeU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
feature_v2: []
subfeature_v2: []
---
# Restrict PI view{#restricting-pii-view}

## Overview {#overview}

Some customers need marketing users to be able to access data records but do not want them to see Personally Identifiable Information (PII), such as first name, last name or email address. Adobe Campaign proposes a way to protect privacy and prevent data from being misused by regular campaign operators.

## Implementation {#implementation}

A new attribute that can be applied to any element or attribute has been added to the schemas, it complements the existing attribute **[!UICONTROL visibleIf]** . This attribute is: **[!UICONTROL accessibleIf]** . When containing an XTK expression related to the current user context, it can leverage **[!UICONTROL HasNamedRight]** or **[!UICONTROL $(login)]** , for instance.

You can find a sample of a recipient schema extension that shows this usage below:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

The main properties are:

* **[!UICONTROL visibleIf]** : hides the fields from the metadata, hence they cannot be accessed within a schema view, or column selection, or an expression builder. But this does not hide any data, if the field name is manually entered in an expression the value will show up.
* **[!UICONTROL accessibleIf]** : hides the data (replacing it with empty values) from resulting query. If visibleIf is empty, then it gets the same expression as **[!UICONTROL accessibleIf]** .

Here are the consequences of using this attribute in Campaign:

* Data will not be shown using generic query editor in the console,
* Data will not be visible in overview lists and record list (console).
* Data will become read-only in detailed view.
* Data will only be usable within filters (meaning that using some dichotomy strategies, you can still guess values).
* Any expression that is built using a restricted field becomes restricted too: lower(@email) becomes as accessible as @email.
* In a workflow, you can add the restricted column to the targeted population as an extra column of the transition, but it is still inaccessible to Adobe Campaign users.
* When storing the targeted population in a group (list), the characteristics of the stored fields are the same as the source of data.
* Data is not accessible to JS code by default.

>[!IMPORTANT]
>
>Using the **accessibleIf** attribute on critical parameters (such as those in composite keys) can result in errors for users that are not allowed to read the data due to hidden data. This may lead to query failures or unexpected behavior. Ensure essential parameters are accessible to prevent disruptions.

## Recommendations {#recommendations}

In each delivery, email addresses are copied into the **[!UICONTROL broadLog]** and the **[!UICONTROL forecastLog]** tables: as a consequence, those fields needs to be protected too.

Below is a sample of log table extension to implement this:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>This restriction applies to non technical users: a technical user, with related permissions, will be able to retrieve data. This method is therefore not 100% secure.
