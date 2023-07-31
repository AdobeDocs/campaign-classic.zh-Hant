---
product: campaign
title: 記錄檔精確度
description: 記錄檔精確度
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 4%

---

# 記錄檔精確度{#log-precision}



您可以將此程式套用至所有Adobe Campaign模組，以提高記錄精確度。

這涉及使用更高層級的記錄來重新啟動流程。

>[!IMPORTANT]
>
>此程式會取消此模組上正在進行的服務。

Adobe Campaign可以使用兩個記錄層級進行操作：

1. 此 **詳細資訊** 模式是標準層級之後的第一個層級。 下列指令會啟動它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   檢查錯誤是否確實發生，然後以正常方式重新啟動程式：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. 此 **TraceFilter** 模式，可讓您儲存最大數量的記錄。 它透過下列命令啟動：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用 **tracefilter：&#42;**，所有記錄型別都會啟動： ncm、rdr、nms、jst、timing、wdbc、ldap、soap、xtk、xtkquery、session、xtkwriter、網路、pop3、inmail\
   >最有用的記錄型別包括： **wdbc** （顯示所有SQL查詢）、 **soap** （顯示所有SOAP呼叫）、 **ldap** （在驗證後顯示所有LDAP查詢）， **xtkquery** （顯示所有querydef清單）。\
   >您可以分別使用它們(**tracefilter：soap，wdbc** 例如)。 您也可以全部啟用這些變數，並選擇排除某些其他變數： **-tracefilter：&#42;，！soap**

   檢查錯誤是否確實發生，然後以正常方式重新啟動程式：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>這些命令的記錄會儲存在模組的記錄檔中。

以下是Web模組專屬的範例。 其他模組會如上所述運作。

在傳送此命令之前，請檢查進行中的工作是否不會受到影響：

```
nlserver pdump -who
```

接著，關閉並重新啟動模組 **TraceFilter** 模式：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一個範例：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>此 **追蹤檔** 模式可讓您儲存記錄。 在上述範例中，記錄檔會儲存在 **var/`<instance-name>`/mta_debug.log** 和 **var/default/web_debug.log** 檔案。

>[!IMPORTANT]
>
>在Windows中，請勿新增LD_PRELOAD選項。 下列指令就足夠了：\
>nlserver web -tomcat -verbose -tracefilter：&#42;

檢查問題是否再次發生，然後重新啟動模組：

```
nlserver restart web -tomcat -noconsole
```

檔案中有所有資訊 **/usr/local/neolane/nl6/var/default/log/web.log**.
