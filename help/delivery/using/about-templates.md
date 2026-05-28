---
product: campaign
title: Work with delivery templates
description: Get started with delivery templates
feature: Delivery Templates
role: User
hide: true
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
TQID: https://experienceleague.adobe.com/Pk7P-N4pOwS9bP2HcL4Y6etV3tVK8-80FyZZQUNASwg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer (Campaign)
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages (Campaign)
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging (Campaign)
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design (Campaign)
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing (Campaign)
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability (Campaign)
---
# Work with delivery templates {#about-templates}

A delivery configuration can be saved in a delivery template in order to be re-used. The template may contain a complete or partial configuration of the delivery.

![](assets/s_user_template_list.png)

There are two types of template:

1. Adobe Campaign native delivery templates - Native templates MUST NOT be deleted from the system. They include a minimum configuration for each delivery channel. The administrator can, however, restrict certain functions or offer default values to users (tracking activation, sender email addresses, etc.). Native scenarios appear in bold in the list of templates. They must be duplicated in order to modify them.

1. Predefined delivery templates - The Adobe Campaign administrator can create new delivery templates. They can be reused by operators (those with suitable access rights) or automatically by server processes. For example, you can configure an email delivery template, and when users creates a delivery using this template, they simply need to enter the text or HTML content and then deliver it; the other choices have already been defined by the administrator.


Learn how to create and use delivery templates in [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-templates){target="_blank"}.