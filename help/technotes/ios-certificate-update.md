---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: no
hidefromtoc: yes
---

# Apple Push Notification service server certificate update {#apns-certificate-update}

On March 29 2021, an Apple Push Notification service (APNs) infrastructure update will impact Adobe Campaign Classic iOS channel. An OS configuration change is **mandatory** to avoid iOS push channel outage.
 
Learn more about APNs changes [in this page](https://developer.apple.com/news/?id=7gx0a2lp).

As a hosted customer, no action is needed: Adobe has already incorporated the new root certificate to your environment.

As an on-premise/hybrid customer, you need to update your configuration to ensure a seamless transition **before March 29 2021**.

To incorporate the new certificate, follow the steps below:

1. Download the **AAACertificateServices 5/12/2020** root certificate [from this page](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Check the AAA certificate is present in both your OS and JAVA trustores. If not add it as detailed in the section below.

1. Restart Adobe Campaign Web Service:

    ```
    nlserver restart web
    ```

## Add Geotrust Global CA certificate

The GeoTrust Global CA certificate must be present as server SSL certificate in the Java Keytrust.

Use the following command to add the certificate:

```
wget --no-check-certificate -c https://www.geotrust.com/resources/root_certificates/certificates/GeoTrust_Global_CA.pem 
openssl x509 -in GeoTrust_Global_CA.pem -inform pem -out GeoTrust_Global_CA.der -outform der
keytool -v -printcert -file GeoTrust_Global_CA.der
keytool -importcert -alias startssl -keystore /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/security/cacerts -storepass changeit -file GeoTrust_Global_CA.der
```

Starting **March 29, 2021** the root certificate needed is the AAA.
