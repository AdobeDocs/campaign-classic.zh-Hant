---
solution: Campaign Classic
product: campaign
title: 配置
description: 配置
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

---


# 設定{#configuration}

## 更改syslogd監聽埠{#changing-the-syslogd-listening-port}

預設情況下， **syslogd**&#x200B;監聽埠為666(udp)。 如有必要，可使用環境變數對其進行更改。

在設定此變數後，所有Adobe Campaign模組都會考量此變數。

### 在Linux {#in-linux}中

編輯&#x200B;**customer.sh**&#x200B;檔案並新增下列行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows {#in-windows}中

您需要使用&#x200B;**localhost**&#x200B;值建立&#x200B;**TRACE_ADDR.**&#x200B;環境變數：**`<listening port="" />`**。

>[!IMPORTANT]
>
>我們建議您在建立此環境變數後，執行一些測試，以確保您的平台運作正常。

## 配置安全區{#configuring-security-zones}

每個運算子都必須連結至區域才能登入例項，且運算子IP必須包含在安全區域中定義的位址或位址集中。 技術區配置在Adobe Campaign伺服器的配置檔案中執行。 必須在控制台（**[!UICONTROL Administration > Access management > Operators]**&#x200B;節點）中定義操作員與安全區的連結。

>[!NOTE]
>
>有關配置安全區的詳細資訊，請參閱[本節](../../installation/using/security-zones.md)。
