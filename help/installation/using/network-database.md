---
solution: Campaign Classic
product: campaign
title: Network, database and SSL/TLS
description: xxxx
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
---

# Network, database and SSL/TLS {#network-database}

A very important thing to check when deploying an on-premise type of architecture is the networking configuration. Ensure that the Tomcat server is NOT directly accessible outside the server:

Close the Tomcat port (8080) on external IPs (must work on localhost)
Do not map the standard HTTP port (80) to the Tomcat one (8080)
When it's possible, use a secure channel: POP3S instead POP3 (or POP3 over TLS).

### Database

It is imperative that you follow your database engine security.

SSL/TLS Configuration

To check the certificate, you can use openssl. To check active ciphers, you can use nmap:

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
You can also use an sslyze python script which does both.

python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com