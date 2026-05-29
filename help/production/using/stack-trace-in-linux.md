---
product: campaign
title: Linux 中的堆疊追蹤
description: Linux 中的堆疊追蹤
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
TQID: https://experienceleague.adobe.com/djAlzlskJf-rVq57J-fS5hG1HdeMSSvskl9jByDYS9I
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 149
ht-degree: 21%

---

# Linux 中的堆疊追蹤{#stack-trace-in-linux}



**棧疊追蹤**&#x200B;代表包含在&#x200B;**核心**&#x200B;型別檔案中的追蹤。 這個檔案會在發生電腦錯誤時產生。 它可以識別錯誤的來源。

>[!NOTE]
>
>* **core**&#x200B;檔案名稱為&#x200B;**core.`<num>`**。
>* **gdb — 電腦上必須安裝GNU Debugger**。
>

Adobe Campaign技術支援可要求您提供此&#x200B;**棧疊追蹤**。 若要取得，請在Linux中輸入下列命令：

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

Adobe Campaign技術支援可能會要求您使用特定的可執行檔（由我們提供）執行此命令。

在此情況下，只要將&#x200B;**nlserver**&#x200B;取代為Adobe Campaign提供的可執行檔來執行下列命令即可：

```
gdb nlserver <coreFile>
```

例如：

```
gdb nlserver.1823 <coreFile>
```
