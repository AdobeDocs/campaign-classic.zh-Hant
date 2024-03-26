---
product: campaign
title: 其他設定
description: 設定
feature: Monitoring, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 5%

---

# 設定{#configuration}



## 變更syslogd接聽連線埠 {#changing-the-syslogd-listening-port}

根據預設， **syslogd** 接聽連線埠是666 (udp)。 如有需要，您可以使用環境變數加以變更。

設定後，所有Adobe Campaign模組都會考量此變數。

### 在Linux中 {#in-linux}

編輯 **customer.sh** 並新增下列行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows中 {#in-windows}

您需要建立 **TRACE_ADDR** 環境變數搭配 **localhost** 值： **`<listening port="" />`**.

>[!IMPORTANT]
>
>我們建議您在建立此環境變數後，執行一些測試來確保您的平台正常運作。

## 設定安全區域 {#configuring-security-zones}

每個運運算元都必須連結到區域才能登入執行個體，而且運運算元IP必須包含在安全性區域中定義的位址或位址集中。 技術區域設定是在Adobe Campaign伺服器的設定檔案中執行。 必須在主控台中定義運運算元連結至安全性區域( **[!UICONTROL Administration > Access management > Operators]** 節點)。

>[!NOTE]
>
>有關設定安全性區域的詳細資訊，請參閱 [本節](../../installation/using/security-zones.md).
