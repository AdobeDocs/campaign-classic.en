---
product: campaign
title: Extension example
description: Extension example
feature: Interaction, Offers
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: 'https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e739ee2b-6228-412e-878f-45de0791417d
    internal-label: Use cases
---
# Extension example{#extension-example}

 

In the case of an inbound contact (call center or web site), the most relevant offers are suggested to a given contact using a set of eligibility rules. To enrich the eligibility criteria of your offers, extend the **nms:interaction** schema.

* To add a new interaction context, extend the **nms:interaction** schema and create as many **attribute** elements as necessary in the schema.

  In the following example, the criteria added are the country code and the last visited page.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* You can then use the attributes previously created when defining the eligibility criteria definition.

  In the following example, we can create eligibility criteria to display an offer based on the user's country or on the last web page they viewed.

  ![](assets/s_ncs_configuration_offer_context.png)

* When configuring SOAP calls, insert the **context** XML element to reference context information added in the interaction schema. For further information, refer to [Integration via SOAP (server side)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/offers/inbound/interaction-integration){target="_blank"} (Campaign v8 documentation).
