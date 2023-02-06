---
product: campaign
title: Update bounce qualification after Italia Online outage
description: Learn how to update bounce qualification after Italia Online outage
feature: Deliverability
hide: yes
hidefromtow: yes
---
# Update incorrect hard bounces after Italia Online outage {#update-bounce-italia}

![](../../assets/common.svg)

## Context{#outage-context}

Since January 22nd (local time), Italia Online has gone through an outage that has resulted on several delays and rejected emails. The service started to resume with limited capacity on Jan 26. 

Impacted domains are: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it**, and **blu.it**.

This issue occurred from 1/22/2023 to 1/26/2023, but most of the wrongly quarantines happened on Jan 26. 

Learn more in the official communication [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impact{#outage-impact}

As in most of the cases when there’s an outage of an ISP, some emails sent through Campaign were wrongly marked as bounces. This was not only impacting Adobe, but everyone trying to get email delivered to Italia Online during the duration of the outage.

Symptoms were:

* **Deferral bounces** with the message `452 requested action aborted: try again later` – these were automatically retried, and no actions are needed.

* **Hard bounces** with the message `550 <email address> recipient rejected` have been returned by the ISP on January 26th, between 8am – 2pm local time, to prevent senders to keep overloading their servers. As confirmed by the Italia Online Postmaster, these are not real hard bounces, so we recommend to un-quarantine all the email addresses that got excluded on January 26, 2023 due to that message.

## Process to update{#outage-update}

Per standard bounce handling logic, Adobe Campaign automatically added these recipients to the quarantine list with a **[!UICONTROL Status]** setting of **[!UICONTROL Quarantine]**. To correct this, you need to update your quarantine table in Campaign by finding and removing these recipients, or changing their **[!UICONTROL Status]** to **[!UICONTROL Valid]** so that the nightly clean-up workflow will remove them. 

To find the recipients who were affected by this issue, or in case this happens again with any other ISP, please see the instructions [in this page](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
