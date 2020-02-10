---
title: 配置
seo-title: 配置
description: 配置
seo-description: null
page-status-flag: never-activated
uuid: 4316d4b2-0964-4e25-9e4f-f2378f044c85
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 12f13b8d-afc3-4b55-a31b-080d31f84fc9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# 配置{#configuration}

## 更改syslogd監聽埠 {#changing-the-syslogd-listening-port}

預設情況下， **syslogd** 監聽埠為666(udp)。 如有必要，可使用環境變數對其進行更改。

設定此變數後，所有Adobe Campaign模組都會考慮此變數。

### 在Linux中 {#in-linux}

編輯 **customer.sh** 檔案並新增下列行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows中 {#in-windows}

您需要使用 **localhost值建立TRACE_ADDR** . **environment變數** : **`<listening port="" />`**。

>[!CAUTION]
>
>我們建議您在建立此環境變數後，執行一些測試，以確保您的平台運作正常。

## 配置安全區 {#configuring-security-zones}

每個運算子都必須連結至區域才能登入例項，且運算子IP必須包含在安全區域中定義的位址或位址集中。 技術區組態是在Adobe Campaign伺服器的組態檔中執行。 必須在控制台（節點）中定義操作員與安全區 **[!UICONTROL Administration > Access management > Operators]** 的連結。

>[!NOTE]
>
>有關配置安全區的詳細資訊，請參 [閱本節](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

