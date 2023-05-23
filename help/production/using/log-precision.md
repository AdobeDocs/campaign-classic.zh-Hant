---
product: campaign
title: 記錄檔精確度
description: 記錄檔精確度
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# 記錄檔精確度{#log-precision}



您可以將此過程應用於所有Adobe Campaign模組，以提高日誌精度。

它涉及使用更高級別的日誌重新啟動進程。

>[!IMPORTANT]
>
>此過程取消此模組上正在進行的服務。

Adobe Campaign可以使用兩級日誌：

1. 的 **詳細** 模式是標準級別之後的第一個級別。 以下命令將激活它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   檢查錯誤是否確實發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. 的 **跟蹤篩選器** 模式，用於保存最大數量的日誌。 它由以下命令激活：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用 **跟蹤過濾器：&#42;**，所有日誌類型都已激活：ncm, rdr nms, jst，計時， wdbc, ldap, soap, xtkquery，會話， xtkwriter，網路， pop3, inmail\
   >最有用的日誌類型有： **wdbc** （顯示所有SQL查詢）, **肥皂** （顯示所有SOAP調用）, **LDAP** （在驗證後顯示所有LDAP查詢）, **xtkquery** （顯示所有querydef的清單）。\
   >您可以單獨使用它們(**跟蹤過濾器：soap,wdbc** 例如)。 您還可以全部激活它們，並選擇排除某些其他項： **-tracefilter:&#42;,soap**

   檢查錯誤是否確實發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>這些命令的日誌儲存在模組的日誌檔案中。

下面是Web模組的一個示例。 其它模組如上所示。

在發送此命令之前，請檢查是否不會影響任何正在進行的作業：

```
nlserver pdump -who
```

接下來，關閉並重新啟動 **跟蹤篩選器** 模式：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一個例子：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>的 **特拉塞菲萊** 模式可保存日誌。 在上面的示例中，日誌保存在 **var/`<instance-name>`/mta_debug.log** 和 **var/default/web_debug.log** 的子菜單。

>[!IMPORTANT]
>
>在Windows中，不要添加LD_PRELOAD選項。 以下命令已滿足：\
>nlserver web -tomcat -verbose -tracefilter:&#42;

檢查問題是否再次出現，然後重新啟動模組：

```
nlserver restart web -tomcat -noconsole
```

檔案中提供了所有資訊 **/usr/local/neolane/nl6/var/default/log/web.log**。
