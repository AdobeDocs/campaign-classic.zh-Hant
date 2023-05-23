---
product: campaign
title: 其他配置
description: 設定
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# 設定{#configuration}



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
