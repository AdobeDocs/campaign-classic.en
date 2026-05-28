---
product: campaign
title: Image display issues
description: Image display issues
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
TQID: https://experienceleague.adobe.com/aBPQb0Yp8o7goe2CS4h6ydnZV5gjPYINHMxGcc-d140
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring (Campaign)
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines (Campaign)
---
# Image display issues{#image-display-issues}



If you face image display issues in a sent message, reasons may be linked to bad location:

* Locations may not match, or images may not have been correctly pushed to duplicate tracking server: check your configuration.
* Images may not reside in the public resource folder on the marketing instance: upload the images into your resource folder to solve the issue.
* If you work in a mid-sourcing architecture: check images are uploading without errors when proofs are sent (information is displayed in the analysis logs).

How to troubleshoot:

1. Send a proof that will show the images.
1. Validate the resources configuration in the instance setup is correct. 
1. Check the public resources folder or, if not in the public resources folder, the folder referenced in the delivery.
