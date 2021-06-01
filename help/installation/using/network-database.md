---
product: campaign
title: Network, database and SSL/TLS
description: Learn more about network, database, and SSL/TLS configuration best practices.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
---
# Network, database and SSL/TLS {#network-database}

## Network configuration

A very important thing to check when deploying an on-premise type of architecture is the [networking configuration](../../installation/using/network-configuration.md). Ensure that the Tomcat server is NOT directly accessible outside the server:

* Close the Tomcat port (8080) on external IPs (must work on localhost)
* Do not map the standard HTTP port (80) to the Tomcat one (8080)

When it's possible, use a secure channel: POP3S instead POP3 (or POP3 over TLS).

## Database

You must apply your database engine security best practices.

## SSL/TLS Configuration

To check the certificate, you can use openssl. To check active ciphers, you can use nmap:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

You can also use an [sslyze](https://github.com/nabla-c0d3/sslyze/releases) python script which does both.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
