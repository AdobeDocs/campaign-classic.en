---
solution: Campaign Classic
product: campaign
title: Image display issues
description: Image display issues
audience: production
content-type: reference
topic-tags: troubleshooting
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
