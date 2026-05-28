---
product: campaign
title: Temporary files
description: Temporary files
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
TQID: https://experienceleague.adobe.com/eZnGm-WK-etrLLbJ-aeuSqakYAfPNBQd2q3JlEd4rE8
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
# Temporary files{#temporary-files}



Error messages such as the following may display (particularly in delivery logs) when the system is put into production:

*Unable to rename file '/tmp/tmp0000.tmp' to /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

The cause is as follows:

Adobe Campaign generates temporary files under **/tmp**, and then renames them to move them to **/usr/local/neolane/nl6/var**. This error occurs when both folders (**/tmp** and **/usr/local/neolane/nl6/var**, which is in fact a symbolic link to **/var/nl6**) correspond to different devices. The **df** command is used for verification.

To correct this problem, the temporary files must be generated in the same device as the destination.

For example, execute the following:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Then add:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
