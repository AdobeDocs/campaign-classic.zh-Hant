---
title: 對數精度
seo-title: 對數精度
description: 對數精度
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# 對數精度{#log-precision}

您可以將此程式套用至所有Adobe Campaign模組，以提高記錄精確度。

它涉及使用更高級別的日誌重新啟動進程。

>[!CAUTION]
>
>此過程取消此模組上正在進行的服務。

Adobe Campaign可以使用兩個記錄層級：

1. Verbose **模式** 是標準級別之後的第一級。 以下命令將激活它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   檢查錯誤是否實際發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. TraceFilter **** 模式，可讓您儲存最多的記錄檔。 它由以下命令激活：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用 **tracefilter:***，則會激活所有日誌類型：ncm, rdr, nms, jst，計時， wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   最有用的日誌類型有： **wdbc** （顯示所有SQL查詢）、 **soap** （顯示所有SOAP調用）、 **ldap** （驗證後顯示所有LDAP查詢）、 **** xtkqueryJosk（顯示所有查詢def的清單）。\
   您可以個別使用(**例如tracefilter:soap** 、wdbc)。 您也可以全部啟動，並選擇排除某些其他人： **tracefilter:*,!soap**

   檢查錯誤是否實際發生，然後以正常方式重新啟動進程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!CAUTION]
這些命令的日誌儲存在模組的日誌檔案中。

以下是Web模組的特有示例。 其他模組如上所示。

在發送此命令之前，請檢查是否不會影響正在進行的作業。

```
nlserver pdump -who
```

接著，在 **TraceFilter模式下關閉並重新啟** 動模組。

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一個例子：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
追蹤 **檔案** 模式可讓您儲存記錄檔。 在上述範例中，記錄檔會儲存在 **var/`<instance-name>`/mta_debug.log** 和 **var/default/web_debug.log** 檔案中。

>[!CAUTION]
在Windows中，不要添加LD_PRELOAD選項。 以下命令即可：\
nlserver web -tomcat -verbose -tracefilter:*

檢查問題是否再次出現，然後重新啟動模組：

```
nlserver restart web -tomcat -noconsole
```

檔案/usr/local/neolane/nl6/var/default/log/web.log中提供所有資 **訊**。
