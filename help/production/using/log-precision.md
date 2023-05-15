---
product: campaign
title: 記錄檔精確度
description: 記錄檔精確度
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# 記錄檔精確度{#log-precision}



您可以將此程式套用至所有Adobe Campaign模組，以提高記錄精度。

它涉及重新啟動具有較高級別日誌的進程。

>[!IMPORTANT]
>
>此過程取消此模組上正在進行的服務。

Adobe Campaign可以使用兩個層級的記錄檔：

1. 此 **詳細** mode是標準層級之後的第一層。 以下命令將激活它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   檢查錯誤是否確實發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. 此 **TraceFilter** 模式，可讓您儲存最多的記錄檔。 它通過以下命令激活：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用 **追蹤篩選器：&#42;**，則所有記錄類型都會啟用：ncm, rdr, nms, jst，計時， wdbc, ldap, soap, xtk, xtkquery，會話， xtkwriter，網路， pop3, inmail\
   >最實用的記錄檔類型為： **wdbc** （顯示所有SQL查詢）, **皂** （顯示所有SOAP呼叫）, **ldap** （驗證後顯示所有LDAP查詢）, **xtkquery** （顯示所有查詢的清單）。\
   >您可以個別使用(**tracefilter:soap,wdbc** 例如)。 您也可以全部啟用，並選擇排除某些其他項目： **-tracefilter:&#42;,!soap**

   檢查錯誤是否確實發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>這些命令的日誌儲存在模組的日誌檔案中。

以下是Web模組的特定範例。 其他模組則如上所述運作。

在發送此命令之前，請檢查是否不會影響正在進行的作業：

```
nlserver pdump -who
```

接下來，關閉並重新啟動 **TraceFilter** 模式：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一個例子：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>此 **Tracefile** 模式可讓您儲存記錄檔。 在上述範例中，記錄檔會儲存在 **var/`<instance-name>`/mta_debug.log** 和 **var/default/web_debug.log** 檔案。

>[!IMPORTANT]
>
>在Windows中，不要添加LD_PRELOAD選項。 以下命令就足：\
>nlserver web -tomcat -verbose -tracefilter:&#42;

檢查問題是否再次發生，然後重新啟動模組：

```
nlserver restart web -tomcat -noconsole
```

檔案中提供所有資訊 **/usr/local/neolane/nl6/var/default/log/web.log**.
