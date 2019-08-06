---
title: Stack trace in Linux
seo-title: Stack trace in Linux
description: Stack trace in Linux
seo-description: 
page-status-flag: never-activated
uuid: 86494bbd-474c-4a95-9465-bb712d85f1e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 61d614ea-c872-4aaa-ab01-bc648c81b5a6
index: y
internal: n
snippet: y
---

# Stack trace in Linux{#stack-trace-in-linux}

A **stack trace** represents a trace contained in a **core** type file. This file is generated in the event of a machine error. It can identify the origin of the error.

>[!NOTE]
>
>* A **core** file is named **core. `<num>`**.
>* **gdb - The GNU Debugger** must be installed on the machine.
>

Adobe Campaign technical support can ask you for this **stack trace**. To obtain it, enter the following commands in Linux:

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

Adobe Campaign technical support might ask you to run this command using a specific executable (to be supplied by us).

In this case, simply run the following command by replacing **nlserver** with the executable provided by Adobe Campaign:

```
gdb nlserver <coreFile>
```

For example:

```
gdb nlserver.1823 <coreFile>
```

