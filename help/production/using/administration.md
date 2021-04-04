---
solution: Campaign Classic
product: campaign
title: Administration
description: Administration
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
---
# Administration{#administration}

Automatic startup of the Adobe Campaign modules (**web**, **mta**, **wfserver**, etc.) is provided by the **nlserver** server.

Installing Adobe Campaign automatically configures the machine so that the **nlserver** service starts up during the boot sequence.

The following commands are used to start up and shut down the Adobe Campaign service manually:

* In Windows:

    * **net start nlserver6**
    * **net stop nlserver6**

* In Linux (as root):

    * **/etc/init.d/nlserver6 start**
    * **/etc/init.d/nlserver6 stop**

 >[!NOTE]
 >
 >Starting 20.1, we recommend using the following command instead (for Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Here is a list of the usual administration commands accessible in Linux (as **Adobe Campaign**):

* Display all started Adobe Campaign modules: **/etc/init.d/nlserver6 pdump** or **/etc/init.d/nlserver6 status**

  >[!NOTE]
  >
  >Adding the **-who** parameter to the **pdump** command lets you collect information on current connections (users and processes).  
  >The **/etc/init.d/nlserver6 status** command (without the "-who" parameter) will return:  
  >
  >    * 0 if all of the processes are being executed.
  >    * 1 if a process is missing.
  >    * 2 if no process is being executed.
  >    * another value if there is an error.  
  >

* Start/stop a multi-instance or mono-instance module (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

  **nlserver start `<module>[@<instance>]`**

  **nlserver stop `<module>[@<instance>][-immediate][-noconsole]`**

  You can also use the **nlserver restart `<module>[@<instance>]`** command to restart a module.

  Example:

  **nlserver start web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver restart web**

  >[!NOTE]
  >
  >* If the instance is not specified, the "default" instance will be used.
  >* In the event of an emergency, use the **-immediate** option to force an immediate halt to the process (equivalent to Unix command **kill -9**).
  >* Use the **-noconsole** option to ensure that the module launched will display nothing on the console. Its logs will be written to the disk via the **syslogd** module.
  >* Use the **-verbose** option to display additional information on process actions. 
  >
  >   Example:
  >
  >   **nlserver restart web -verbose**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   This option adds additional logs. We recommend starting the processes again without the **-verbose** option once you have found the desired information, to avoid overloading logs.

* Start up all Adobe Campaign processes (equivalent to starting up the **nlserver6** service):

  **nlserver watchdog -noconsole**

* Shut down all Adobe Campaign processes (equivalent to shutting down the **nlserver6** service):

  **nlserver shutdown**

* Reload the **nlserver web** module configuration (and the web server extension module, where applicable) when the **serverConf.xml** and **config- `<instance>  .xml </instance>`** files have been edited.

  **nlserver config -reload**

  >[!NOTE]
  >
  >Some configuration changes are not taken into account dynamically; Adobe Campaign must be shut down and then restarted.
