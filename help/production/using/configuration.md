---
product: campaign
title: 其他配置
description: 設定
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# 設定{#configuration}



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
