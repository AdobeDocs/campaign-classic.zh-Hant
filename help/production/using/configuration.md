---
product: campaign
title: 其他設定
description: 設定
feature: Monitoring, Configuration
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 1%

---

# 設定{#configuration}



## 變更syslogd接聽連線埠 {#changing-the-syslogd-listening-port}

依預設，**syslogd**&#x200B;接聽連線埠是666 (udp)。 如有需要，您可以使用環境變數加以變更。

設定後，所有Adobe Campaign模組都會考量此變數。

### 在Linux中 {#in-linux}

編輯&#x200B;**customer.sh**&#x200B;檔案並新增下列行：

```sql
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows中 {#in-windows}

您必須建立具有&#x200B;**localhost**&#x200B;值： **`<listening port="" />`**&#x200B;的&#x200B;**TRACE_ADDR**&#x200B;環境變數。

>[!IMPORTANT]
>
>我們建議您在建立此環境變數後，執行一些測試來確保您的平台正常運作。

## 設定安全區域 {#configuring-security-zones}

每個運運算元都必須連結到區域才能登入執行個體，而且運運算元IP必須包含在安全性區域中定義的位址或位址集中。 技術區域設定是在Adobe Campaign伺服器的設定檔案中執行。 必須在主控台（ **[!UICONTROL Administration > Access management > Operators]**&#x200B;節點）中定義運運算元連結至安全性區域。

>[!NOTE]
>
>如需設定安全性區域的詳細資訊，請參閱[本節](../../installation/using/security-zones.md)。
