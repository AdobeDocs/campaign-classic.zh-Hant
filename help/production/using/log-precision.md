---
solution: Campaign Classic
product: campaign
title: 記錄精確度
description: 記錄精確度
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---


# 記錄精確度{#log-precision}

您可以將此程式套用至所有Adobe Campaign模組，以提高記錄精確度。

它涉及使用更高級別的日誌重新啟動進程。

>[!IMPORTANT]
>
>此過程取消此模組上正在進行的服務。

Adobe Campaign可以使用兩個記錄層級：

1. **Verbose**&#x200B;模式是標準級別之後的第一級。 以下命令將激活它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   檢查錯誤是否實際發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. **TraceFilter**&#x200B;模式，可讓您儲存最多的記錄檔。 它由以下命令激活：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用&#x200B;**tracefilter:***，則會激活所有日誌類型：ncm, rdr, nms, jst，計時， wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   >最有用的日誌類型有：**wdbc**（顯示所有SQL查詢）、**soap**（顯示所有SOAP調用）、**ldap**（驗證後顯示所有LDAP查詢）、**xtkquery**（顯示所有查詢的清單）。\
   >您可以個別使用（例如&#x200B;**tracefilter:soap,wdbc**）。 您也可以全部啟動，並選擇排除某些其他人：**-tracefilter:*,!soap**

   檢查錯誤是否實際發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>這些命令的日誌儲存在模組的日誌檔案中。

以下是Web模組的特有示例。 其他模組如上所示。

在發送此命令之前，請檢查是否不會影響正在進行的作業：

```
nlserver pdump -who
```

接著，在&#x200B;**TraceFilter**&#x200B;模式下關閉並重新啟動模組：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一個例子：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>**Tracefile**&#x200B;模式可讓您儲存記錄檔。 在上述範例中，記錄檔儲存在&#x200B;**var/`<instance-name>`/mta_debug.log**&#x200B;和&#x200B;**var/default/web_debug.log**&#x200B;檔案中。

>[!IMPORTANT]
>
>在Windows中，不要添加LD_PRELOAD選項。 以下命令即可：\
>nlserver web -tomcat -verbose -tracefilter:*

檢查問題是否再次出現，然後重新啟動模組：

```
nlserver restart web -tomcat -noconsole
```

檔案&#x200B;**/usr/local/neolane/nl6/var/default/log/web.log**&#x200B;中提供所有資訊。
