---
product: campaign
title: 設定
description: 設定
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

---

# 設定{#configuration}

![](../../assets/v7-only.svg)

## 更改syslogd監聽埠 {#changing-the-syslogd-listening-port}

依預設， **syslogd** 偵聽埠為666(udp)。 您可以視需要使用環境變數加以變更。

設定後，所有Adobe Campaign模組都會考量此變數。

### 在Linux {#in-linux}

編輯 **customer.sh** 並新增下列行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows {#in-windows}

您需要建立 **TRACE_ADDR。** 環境變數搭配 **localhost** 值： **`<listening port="" />`**.

>[!IMPORTANT]
>
>建議您執行一些測試，以在您建立此環境變數後確定您的平台運作正常。

## 配置安全區域 {#configuring-security-zones}

每個運算子都需要連結到區域才能登錄到實例，並且運算子IP必須包含在安全區域中定義的地址或地址集中。 技術區配置在Adobe Campaign伺服器的配置檔案中執行。 必須將運算子連結至安全區域，必須在主控台中定義( **[!UICONTROL Administration > Access management > Operators]** 節點)。

>[!NOTE]
>
>有關配置安全區域的詳細資訊，請參閱 [本節](../../installation/using/security-zones.md).
