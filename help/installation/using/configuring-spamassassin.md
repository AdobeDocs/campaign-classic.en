---
product: campaign
title: Configuring SpamAssassin
description: Configuring SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
---
# Configuring SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>Some configurations can only be performed by Adobe for deployments hosted by Adobe. For example, to access the server and instance configuration files. To learn more about the different deployments, refer to the [Hosting models](../../installation/using/hosting-models.md) section or to [this page](../../installation/using/capability-matrix.md).

## Overview {#overview}

SpamAssassin is a piece of software designed to filter undesirable emails. In conjunction with this software, Adobe Campaign can assign a score to emails and determine whether a message is likely to be deemed undesirable before delivery is launched. To do this, SpamAssassin must be installed and configured on the application server(s) of Adobe Campaign and requires a certain number of additional Perl modules to operate.

The deployment and integration of SpamAssassin as described in this chapter are based on default software installation, as are filtering and scoring rules, which are those provided by SpamAssassin without any alterations or optimizations. Score attribution and message qualification are based exclusively on the configuration of SpamAssassin options and on filtering rules. Network administrators are responsible for adapting them to their company's needs.

>[!IMPORTANT]
>
>The qualification of emails as undesirable by SpamAssassin is based entirely on filtering and scoring rules.
>
>These rules therefore have to be updated at least once a day in order for your SpamAssassin installation and its integration into Adobe Campaign to be fully functional and to guarantee the relevance of scores assigned to your deliveries before sending.
>
>This update is the responsibility of the server administrator hosting SpamAssassin.

Using SpamAssassin in Adobe Campaign provides an indication on the possible behavior of mail servers which use SpamAssassin when they receive email sent by Adobe Campaign. However, it is possible that the mail servers of internet providers or online mail servers still consider the messages sent by Adobe Campaign as undesirable.

Deploying SpamAssassin and its modules in Perl requires Adobe Campaign application servers equipped with internet access via a HTTP connection (TCP/80 flow).

## Installing on a Windows machine {#installing-on-a-windows-machine}

To install and configure SpamAssassin on Windows to enable integration with Adobe Campaign, apply the following steps:

1. Install SpamAssassin
1. Integrate SpamAssassin into Adobe Campaign

### Installing SpamAssassin {#installing-spamassassin}

1. Connect to the [Software distribution portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) using your user credentials. Learn more about Software distribution in [this page](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).
1. Download the **Neolane Spam Assassin (Windows Installation) (2.0)** file (neolane_spamassassin.2.0.zip).
1. Copy this file onto the Adobe Campaign server then unzip it.

   >[!NOTE]
   >
   >You can choose to unzip the file wherever you want provided that the path is made up of any of the following regular expression characters: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. The installation path must not include any whitespace characters.

1. Go to the file in which you have unzipped the file then double click on the **run_me.bat** file to launch the installation script.

   If a Windows Shell appears and continues to be displayed for a few seconds, wait until the installation and the update have finished, then click **Enter**.

   If the Windows Shell does not appear or is not displayed before instantly disappearing, follow these steps, double-click the **portableShell.bat** file to display a Windows Shell and check that the Shell path corresponds to the folder in which the **spamassassin.zip** file has been unzipped. If this is not the case, access it using the **cd** command.

   Enter **run_me.bat** then click **Enter** to start the installation and update process. The operation returns one of the following values in order to indicate the result of the update.

    * **0**: an update has been carried out.
    * **1**: No new update available.
    * **2**: no new update available.
    * **3**: update failed during prior verification.
    * **4** or more: an error has occurred.

1. To check that the SpamAssassin installation was successful, use the GTUBE test (Generic Test for Unsolicited Bulk Email) using the following procedure:

    1. Create a text file and save it under **C:\TestSpamMail.txt**.
    1. Insert the following content into the file:

       ```    
       Subject: Test Spam Mail (GTUBE)
       Message-ID: <1010101@example.net>
       Date: MM-DD-YY
       From: Sender <sender@example.net>
       To: Recipient <recipient@example.net>
       Precedence: junk
       MIME-Version: 1.0
       Content-Type: text/plain; charset=us-ascii
       Content-Transfer-Encoding: 7bit
       
       XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
       ```

    1. Double-click on the **portableShell.bat** file to display a Windows Shell then launch the following command (or "`<root>`" designates the created folder when unzipping the  **spamassassin.zip** file):

       ```    
        "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
       ```    
    
       The content of this test email triggers a 1,000 point score by SpamAssassin. This means it has been detected as undesirable and that the installation was successful and is fully functional.

### Integrating SpamAssassin into Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Edit the **`[INSTALL]/conf/serverConf.xml`** file. All the parameters available in the **serverConf.xml** are listed in this [section](../../installation/using/the-server-configuration-file.md).
1. Change the value of the **spamCheck** elements' **command** attribute in the **Web** node. To do this, run the following command:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >All paths must be absolute.

   Stop and start the **[!UICONTROL Adobe Campaign]** service.

1. To check the integration of SpamAssassin in Adobe Campaign use a GTBUE test (Generic Test for Unsolicited Bulk Email):

   Double-click on the **portableshell.bat** file. This triggers the display of a Windows Shell. Then run the following command:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   The content of this test email triggers 1,000 points assigned by SpamAssassin. This means it has been detected as undesirable and that integration in Adobe Campaign was successful and is fully functional.

1. Update SpamAssassin filtering and scoring rules

   For an initial update of filtering and scoring rules, start **portableShell.bat** and run the following command:

   ```
   sa-update --no-gpg
   ```

   To run an automatic update of filtering and scoring rules, use this same command in a scheduled system task:

   ```
   sa-update --no-gpg
   ```

## Installing on a Linux machine {#installing-on-a-linux-machine}

### Installation steps in Debian {#installation-steps-in-debian}

* If necessary, install Perl and SpamAssassin using the following command:

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* In the **serverConf.xml** file (available in `/usr/local/[INSTALL]/nl6/conf/`), change the **spamCheck** line as follows:

  ```
  <spamCheck command="perl
  /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
  ```

### Installation steps in RHEL/CentOS {#installation-steps-in-rhel-centos}

If necessary, install Perl and recover the packages using CPAN:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Updating filter rules {#updating-filter-rules}

Filter rules can be updated automatically using the **sa-update** tool. Refer to the official SpamAssassin website [http://spamassassin.apache.org/](http://spamassassin.apache.org/) for more information.

In Debian, updates take place automatically each day.

If this is not the case (for example when Debian is installed manually), create a script to automate rule updates.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Insert this script into **crontab** using the following command:

```
crontab-e
```

### Performance optimization {#performance-optimization}

To improve performances in Linux, edit the **/etc/spamassassin/local.cf** file and add the following line at the end of the file:

```
dns_available no
```
