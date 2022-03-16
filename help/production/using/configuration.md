---
product: campaign
title: 其他配置
description: 設定
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# 設定{#configuration}

![](../../assets/v7-only.svg)

## 更改syslogd偵聽埠 {#changing-the-syslogd-listening-port}

預設情況下， **syslog** 偵聽埠為666(udp)。 如有必要，可使用環境變數更改它。

配置後，所有Adobe Campaign模組都會考慮此變數。

### 在Linux中 {#in-linux}

編輯 **customer.sh** 並添加以下行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows中 {#in-windows}

您需要建立 **TRACE_ADDR。** 環境變數 **本地主機** 值： **`<listening port="" />`**。

>[!IMPORTANT]
>
>我們建議運行一些test，以確保在建立此環境變數後您的平台工作正常。

## 配置安全區域 {#configuring-security-zones}

每個操作員需要連結到區域才能登錄到實例，並且必須將操作員IP包括在安全區域中定義的地址或地址集中。 在Adobe Campaign伺服器的配置檔案中執行技術區域配置。 必須在控制台中定義操作員與安全區域的連結( **[!UICONTROL Administration > Access management > Operators]** 節點)。

>[!NOTE]
>
>有關配置安全區域的詳細資訊，請參閱 [此部分](../../installation/using/security-zones.md)。
