---
product: campaign
title: 記錄檔精確度
description: 記錄檔精確度
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 2%

---

# 記錄檔精確度{#log-precision}



您可以將此程式套用至所有Adobe Campaign模組，以提高記錄精確度。

這涉及使用更高層級的記錄來重新啟動流程。

>[!IMPORTANT]
>
>此程式會取消此模組上正在進行的服務。

Adobe Campaign可以使用兩個記錄層級進行操作：

1. **詳細資訊**&#x200B;模式是標準層級之後的第一個層級。 下列指令會啟動它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   檢查錯誤是否確實發生，然後以正常方式重新啟動程式：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. **TraceFilter**&#x200B;模式可讓您儲存最多記錄數。 它透過下列命令啟動：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用&#x200B;**tracefilter：&#42;**，則會啟動所有記錄型別： ncm、rdr、nms、jst、timing、wdbc、ldap、soap、xtk、xtkquery、session、xtkwriter、網路、pop3、inmail\
   最有用的記錄型別是： **wdbc** （顯示所有SQL查詢）、**soap** (顯示所有SOAP呼叫)、**ldap** （驗證後顯示所有LDAP查詢）、**xtkquery** （顯示所有querydef的清單）。\
   您可以個別使用它們（例如&#x200B;**tracefilter：soap，wdbc**）。 您也可以全部啟用它們，並選擇排除某些其他專案： **-tracefilter：&#42;，！soap**

   檢查錯誤是否確實發生，然後以正常方式重新啟動程式：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
這些命令的記錄會儲存在模組的記錄檔中。

以下是Web模組專屬的範例。 其他模組會如上所述運作。

在傳送此命令之前，請檢查進行中的工作是否不會受到影響：

```
nlserver pdump -who
```

接著，在&#x200B;**TraceFilter**&#x200B;模式中關閉並重新啟動模組：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一個範例：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
**追蹤檔**&#x200B;模式可讓您儲存記錄。 在上述範例中，記錄檔儲存在&#x200B;**var/`<instance-name>`/mta_debug.log**&#x200B;和&#x200B;**var/default/web_debug.log**&#x200B;檔案中。

>[!IMPORTANT]
>
在Windows中，請勿新增LD_PRELOAD選項。 下列指令就足夠了：\
nlserver web -tomcat -verbose -tracefilter：&#42;

檢查問題是否再次發生，然後重新啟動模組：

```
nlserver restart web -tomcat -noconsole
```

所有資訊都可在檔案&#x200B;**/usr/local/neolane/nl6/var/default/log/web.log**&#x200B;中取得。
