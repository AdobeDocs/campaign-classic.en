---
title: CSR and SSL Certificate request process
description:  Learn how to install SSL Certificates on the subdomains you delegated to Adobe.
feature: Deliverability
kt: 
thumbnail: 
doc-type: article
activity: understand
team: ACS
hidefromtoc: yes
---

# CSR and SSL Certificate request process

Once you have delegated a domain to Adobe for sending email (see [Domain name setup](../../help/additional-resources/domain-name-setup.md)), Adobe will create and use certain subdomains for specific functions.

For example, if you have delegated email.example.com to Adobe for sending emails, Adobe will create subdomains such as the following:
* *t.email.example.com* - for tracking links
* *m.email.example.com* - for mirror pages
* *res.email.example.com* - for hosted resources (such as images)

It is recommended to secure these domains via SSL (HTTPS), as unsecured links (HTTP) are vulnerable to interception and will flag up warnings on modern browsers.

To install SSL Certificates on these subdomains, the process involves requesting a CSR file and subsequently purchasing SSL Certificates for Adobe to install or renew.

>[!CAUTION]
>
>Before installing an SSL Certificate, make sure you are aware of the prerequisites listed on [this page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate).
>
>Adobe will only support up to 2048-bit Certificates. 4096-bit Certificates are not yet supported.

## Glossary

| Term | Description |
|--- |--- |
| CA (Certificate Authority) | An SSL Certificate provider that issues digital certificates to organizations or individuals after verifying their identity, such as DigiCert, Symantec, etc.<ul><li>A trusted CA is usually considered as a third-party CA which issues a Root Certificate.</li><li>If the Certificate is signed by the same organization/company that is using the Certificate, it is classified as untrusted CA even when they are SSL Certificates, such as Self Signed Certificates.</li></ul> |
| Chain Certificate | A Certificate which includes a root Certificate and one or more Intermediate Certificates is called a Chain (or Chained) Certificate. |
| CSR (Certificate Signing Request) | A block of encoded text that is given to a Certificate Authority when applying for an SSL Certificate. It is usually generated on the server where the Certificate will be installed. |
| DER (Distinguished Encoding Rules) |  A certificate extension type. The .der extension is used for binary DER encoded certificates. These files may also support the .cer or .crt extension. |
| EV (Extended Validation) Certificate | An EV Certificate is a new type of Certificate that is designed to prevent phishing attacks. It requires extended validation of your business and of the person ordering the Certificate. |
| High Assurance Certificate | High Assurance Certificates are issued by the CA after verifying ownership of the domain name and valid business registration. |
| Intermediate CA | A Certificate Authority of Intermediate Certificates included in a Chain Certificate. |
| Intermediate Certificate | A Certificate Authority issues certificates in the form of a tree structure. The Root Certificate is the top-most certificate of the tree. Any certificate between your Certificate and the Root Certificate is called a chain or Intermediate Certificate. |
| Low Assurance Certificate | A Low Assurance Certificate, also referred as Domain Validated Certificate, includes only the domain name in the certificate (and not the business/organization name). |
| PEM (Privacy Enhanced Mail) | A certificate with a .pem extension which contains ASCII (Base64) data. Such certificates start with a " - - - - - BEGIN CERTIFICATE - - - - -" line. |
| Root Certificate | A Certificate Authority issues certificates in the form of a tree structure. The Root Certificate is the top-most certificate of the tree. |
| SAN (Subject Alternative Name) | The Subject Alternative Names are additional host names (sites, IP addresses, common names, etc.) that should be signed as part of a single SSL Certificate. |
| Self Signed Certificate | A certificate that is signed by the person creating it rather than a trusted certificate authority. Self-signed certificates can enable the same level of encryption as a certificate signed by a CA, but there are two major drawbacks: a visitor's connection could be hijacked allowing an attacker to view all the data sent (thus defeating the purpose of encrypting the connection) and the certificate cannot be revoked like a trusted certificate can. |
| SSL (Secure Sockets Layer) |  The standard security technology for establishing an encrypted link between a web server and a browser. |
| Wildcard Certificate | A Wildcard Certificate can secure an unlimited number of first level subdomains on a single domain name, such as *.adobe.com. |

## Main steps

1. Get a Certificate Signing Request (CSR) file and provide the required information (country, state, city, organization name, organizational unit name, etc.) to Adobe Customer Care, via the submission of a Support ticket. Adobe generates a Certificate Signing Request (CSR) file and provides it to you.
1. Validate the CSR file and verify that all information you provided is correct.
1. Use the CSR details to generate a Certificate signed by a trusted Certification Authority<!--taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server-->.
1. Validate the SSL Certificate and verify it matches the CSR.
1. Provide the SSL Certificate (and Intermediate Chain/Certificate too if applicable)  to Adobe, who will install it.
1. Test that the SSL Certificate is successfully installed<!--(test the URLs for each secured subdomain)-->.
1. Monitor the SSL Certificate validity period.

## Detailed process

### Prerequisites

You must identify the domain names and the functions (tracking, mirror pages, webapps, etc.) to secure.
>[!NOTE]
>
>Adobe can help in defining the domain names and functions to involve. For more information, contact your Adobe Customer Success Manager.

### Step 1 - Get a CSR file

To obtain a CSR (Certificate Signing Request) file, follow the steps below.

**If you have access to [Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html):**<!--SPECIFIC TO CAMPAIGN?-->

Follow the instructions on [this page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-Certificates/renewing-subdomain-certificate.html#subdomains-and-certificates) to generate and download a CSR file from the Control Panel.

**Otherwise:**

Create a Support ticket via https://adminconsole.adobe.com/ to obtain a CSR file from Adobe Customer Care for the required subdomain(s).

Here are a few best practices to follow:

* Raise one request per delegated subdomain.
* It is possible to combine multiple subdomains into a single CSR request, but only within the same environment. For example, in Campaign Classic, the marketing server, the [mid-sourcing server](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/mid-sourcing-server.html) and the [execution instance](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/instance-configuration/creating-a-shared-connection.html) are three separate environments.
* You must get a new CSR before any SSL Certificate renewal. Do not use an old CSR file from one year ago or more.

You will need to provide the following information :

| Information to provide in CSR Support ticket | Example value | Note |
|--- |--- |--- |
| Common Name [CN] | t.subdomain.customer.com | This can be any of the relevant domains, but usually the tracking domain. |
| Instance URL | mycompany.campaign.adobe.com | Provide the Adobe instance URL. | 
| Subject Alternative Name [SAN] | t.subdomain.customer.com</br>m.subdomain.customer.com</br>res.subdomain.customer.com | Make sure to include tracking subdomain as a SAN. |
| State (or Province Name) [ST] | London | If applicable. The value must be a full name, not abbreviated. |
| Organizational Unit Name [OU] | IT | e.g. section. |
| Country [C] | GB | This must be a two-letter code. Access the full country list [here](https://www.ssl.com/csrs/country_codes/).</br>*Note: For United Kingdom, use GB (not UK).* |
| Environment URL | https://client-mid-prod1.campaign.adobe.com |
| Client Name | My Company Ltd. |
| City/Locality Name [L] | London |
| Organization Name [O] | ACME |

>[!NOTE]
>
>Replace "subdomain.customer.com" with your delegated subdomain, and the other example values with the appropriate values.

### Step 2 - Validate the CSR file

After submitting your request with the relevant information, Adobe generates and provides you with a Certificate signing request (CSR) file.

The text in the resulting CSR file should start with **"-----BEGIN CERTIFICATE REQUEST-----"**.

Once you receive the CSR file from Adobe, check that the correct parameters and domain names are included, and follow the steps below to verify the CSR file:

1. Copy and paste the CSR file text into an online decoder such as https://www.sslshopper.com/csr-decoder.html, https://www.certlogik.com/decoder/, or https://www.entrust.net/ssl-technical/csr-viewer.cfm.
    Alternatively, you can use the *OpenSSL* command locally on a Linux machine. For more on this, refer to [this page](https://www.question-defense.com/2009/09/22/use-openssl-to-verify-the-contents-of-a-csr-before-submitting-for-a-ssl-certificate).
1. Verify that all the checks are successful.
1. Check that all the data match the details you provided upon submitting your request.

<!--Once the CSR is verified, proceed to use the CSR to purchase an SSL Certificate.-->

### Step 3 - Generate the SSL Certificate

Once the CSR file is provided, you must purchase and generate an SSL Certificate for the appropriate domains using the CSR file.

* The SSL Certificate:
    * must be in Apache PEM format;
    * should not be longer than 2048 bits;
    * must be signed by a valid CA (Certification Authority);
    * must include all SANs (Subject Alternative Names) as mentioned in the CSR file.
* If there are one or more Intermediate Certificates, you must provide the Root Certificate and all Intermediate Certificates to Adobe.
* You can set any certificate validity period, but Adobe recommends to choose it long enough, such as two years.

>[!NOTE]
>
>If you are using your own internal tools or a portal provided by a CA to request the Certificate, make sure to use the same details as provided in the CSR request to avoid any delays or discrepancies in the certificate generation process.

### Step 4 - Validate the SSL Certificate

Once the SSL Certificate is generated, you must validate it before sending it to Adobe. To do so, follow the steps below:

1. Make sure the Certificate have the .pem extension. If this is not the case, convert it to PEM format. You can make the conversion using *OpenSSL*.
1. Confirm that the Certificate starts with **"-----BEGIN CERTIFICATE-----"**.
1. Copy the Certificate text into an online decoder, such as https://www.sslshopper.com/certificate-decoder.html.
    Alternatively, you can use the *OpenSSL* command locally on a Linux machine. For more on this, refer to [this page](https://www.shellhacks.com/decode-ssl-certificate/).
1. Make sure the Certificate resolves properly including the Common Name, SAN, Issuer and Validity Period.
1. If the SSL Certificate verification is successful, check that the Certificate matches the CSR using [this page](https://www.sslshopper.com/certificate-key-matcher.html).
1. Select **Check if a CSR and a Certificate match** and enter your Certificate and your CSR in the corresponding fields. They should match.

### Step 5 - Request the SSL Certificate installation

**If you have access to [Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html):**<!--SPECIFIC TO CAMPAIGN?-->

Follow the instructions on [this page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate) to upload the Certificate to Control Panel.

**Otherwise:**

Create another Support ticket via https://adminconsole.adobe.com/ to request Adobe to install the Certificate on the Adobe server(s).

You’ll need to provide:

* The Certificate file, the Root Certificate and any Intermediate Certificates (attached to the ticket), preferably in Apache PEM format.
* The number of the previous Suuport ticket raised for the CSR.
* The same data that was provided for the CSR ticket (including Common Name, Instance URL, State, City/Locality, Organization Name, Organization Unit ID, etc.).

### Step 6 - Test the SSL Certificate installation

Once the SSL Certificates is installed and confirmed by Adobe Customer Care, test that it has been successfully installed for all URLs.

Perform the tests below before closing the SSL installation ticket. Also make sure you update any specific configuration as instructed in [this section](#update-configuration).

Navigate to the following URLs in your browser (replace email.customer.com with your subdomain):

* https://subdomain.customer.com/r/test <!--(for Webapp subdomains only, does not apply for Email subdomains)-->
* https://t.subdomain.customer.com/r/test
* https://m.subdomain.customer.com/r/test
* https://res.subdomain.customer.com/r/test

A successful result will give environment information, and the address bar in the URL will indicate that the connection is secure. For example, you can see the following message in Google Chrome:

![](../../help/assets/ssl-google-successful-result.png)

If the SSL Certificate is not installed properly, you will see the following warning:

![](../../help/assets/ssl-google-unsuccessful-result.png)

### Step 7 - Check the Certificate validity period

In your browser you can also check the validity period of the Certificate. For example, in Google Chrome click **Secure** > **Certificate**.

It is your responsibility to check the validity period. Adobe recommends you implement a process to monitor certificate expiry.

Learn more on what happens when your SSL Certificate expires in [this article](https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/).

You should create a Support ticket to request an updated Certificate to be installed at least two weeks before the Certificate expiry date. You do not need to request an additional CSR, unless the CSR details have changed.

**If you have access to [Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html):**<!--SPECIFIC TO CAMPAIGN?-->

If your environment is hosted by Adobe in an AWS environment, you can use Control Panel to renew the Certificate before it expires. Learn more in [this section](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-ssl-certificates.html#monitoring-certificates).

### Update any specific configuration {#update-configuration}

<!--SPECIFIC TO CAMPAIGN?-->

Once you are confident the SSL Certificates is installed properly, you can update all references in your Adobe solution from HTTP to HTTPS.

>[!NOTE]
>
>For Campaign Classic, the URLs to update are mainly located in the [Deployment wizard](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/initial-configuration/deploying-an-instance.html#deployment-wizard) and in the [External accounts](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/external-accounts.html#installing-campaign-classic) (tracking, mirror page and public resource domains). For Campaign Standard, refer to [Branding configuration](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/application-settings/branding.html#about-brand-identity).

Once configurations are updated, new emails will be sent with HTTPS URLs rather than HTTP. To check the URLs are now secure, you can quickly perform the following tests: 

* Upload an image from your Adobe product. Once the image gets uploaded, the URL returned should be HTTPS.
* Create a test email delivery with a mirror page link, some images, text and an unsubscription link. Send out the email to an external email ID (such as your Gmail address). Once received, open the email and make sure all the links inside the email open correctly in their HTTPS form (not HTTP), without any SSL Certificate warnings or errors.

<!--Then, new emails will be sent with HTTPS URLs rather than HTTP (easiest way to test is to send out a test email that contains at least one mirror page and one public resource/image).-->
