---
product: campaign
title: Linux 中的堆疊追蹤
description: Linux 中的堆疊追蹤
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---

# Linux 中的堆疊追蹤{#stack-trace-in-linux}

**堆棧跟蹤**&#x200B;表示&#x200B;**core**&#x200B;類型檔案中包含的跟蹤。 系統會在發生電腦錯誤時產生此檔案。 它可識別錯誤的來源。

>[!NOTE]
>
>* **core**&#x200B;檔案的名稱為&#x200B;**core.`<num>`**。
>* **gdb — 必須** 在電腦上安裝GNU調試程式。

>



Adobe Campaign技術支援可要求您提供此&#x200B;**堆疊追蹤**。 要獲取，請在Linux中輸入以下命令：

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

Adobe Campaign技術支援可能會要求您使用特定執行檔（由我們提供）執行此命令。

在此情況下，只需將&#x200B;**nlserver**&#x200B;替換為Adobe Campaign提供的執行檔，即可運行以下命令：

```
gdb nlserver <coreFile>
```

例如：

```
gdb nlserver.1823 <coreFile>
```
