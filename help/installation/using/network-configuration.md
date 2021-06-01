---
product: campaign
title: Network configuration
description: Learn system communication guidelines
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
---
# Network configuration{#network-configuration}

## Communication between processes {#communication-between-processes}

Certain processes of the application need to communicate with others or to access the LAN and internet. This means that some TCP ports need to be open for these processes.

Use the embedded Apache Tomcat port as a priority (8080 by default) for internal communications between the various application servers of an Adobe Campaign platform.

### Delivery server {#delivery-server}

For the delivery server (**nlserver mta**), the following ports must be open:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Comments<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> SMTP traffic for e-mail broadcasting.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domain)<br /> </td> 
   <td> DNS servers<br /> </td> 
   <td> DNS queries.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (default port)<br /> </td> 
   <td> SMS gateway<br /> </td> 
   <td> Used to send SMS traffic to the NetSize SMS router [option].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Statistics server<br /> </td> 
   <td> Accessing the statistics server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Inbound mail {#inbound-mail}

For the inbound mail recovery process (**nlserver inMail**), the following ports must be open:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Comments<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Internal mail server<br /> </td> 
   <td> POP3 traffic to pick up bounce messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Internal mail server<br /> </td> 
   <td> SMTP traffic to send remaining bounce messages that are not automatically processed by the pre-defined rules.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Application server {#application-server}

For the application server (**nlserver web**), the following ports must be open:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Comments<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> HTTP or HTTPS traffic (including for the deliverability offer).<br /> </td> 
  </tr> 
 </tbody> 
</table>

When several application servers of an Adobe Campaign platform need to communicate with each other, we recommend using the port of the Apache Tomcat server (by default: 8080) rather than that of the HTTP port of the Web server which redirection module integration was carried out with. This means the port needs to be open between these servers.

### SMS delivery status {#sms-delivery-status}

To track SMS deliveries (**nlserver sms**), the following port must be open:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Comments<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (default port)<br /> </td> 
   <td> SMS gateway<br /> </td> 
   <td> Queries the delivery queue status managed by the NetSize SMS gateway [option].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Rich client {#rich-client}

For the Adobe Campaign rich client (**nlclient**), the following ports must be open:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Destination<br /> </td> 
   <td> Comments<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Application server<br /> </td> 
   <td> SOAP traffic (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Database access {#database-access}

All components that use the database must be able to connect to it. This is the case for most components, with the exception of the redirection server, which can work alone, and the thin Win32 client, which uses HTTP (or HTTPS) only to communicate with the application server.

The default ports are the following: 

<table> 
 <tbody> 
  <tr> 
   <td> Database type<br /> </td> 
   <td> Port (default)<br /> </td> 
   <td> Destination<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Database server<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## External access {#external-access}

In addition, certain components must be accessible from the public internet so that e-mail campaigns executed directly from Adobe Campaign can be viewed. This means that some ports need to be open for components.

### Redirection server {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Listening port<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Anywhere. Each click on a tracked link generates a HTTP request on the server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### External Web server {#external-web-server}

This server hosts Web forms, mirror pages, etc. The following ports need to be open:

<table> 
 <tbody> 
  <tr> 
   <td> Listening port<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Anywhere. Necessary when Web forms are managed directly from the Adobe Campaign platform or when mirror pages are used.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Internal application server (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Listening port<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> All computers executing the thin client or rich client.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration with Adobe Experience Manager {#integration-with-adobe-experience-manager}

Integration between Adobe Campaign and Adobe Experience Manager requires opening several ports if the installation is "on-premise". For more information on configuring this integration, refer to the [detailed documentation](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Listening port<br /> </td> 
   <td> Description<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM connection to Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign connection to AEM's "authoring" and "publishing" instances. The ports to open may be different from the default ports, depending on your AEM configuration.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bandwidth {#bandwidth}

Another key parameter of the network configuration to take into account. It is almost always outbound and much in demand during e-mail broadcasts. Here are a few examples of configurations based on our experience:

* 1 Mb/s for 10,000 emails per hour (average size of 30 Kb)
* 8 to 10 Mb/s for 100,000 emails per hour (average size of 30 Kb)

If you have constraints in terms of bandwidth, it is possible to schedule campaigns to run during the night when demand is lower.
