---
product: campaign
title: 市場活動交付設定配置
description: 瞭解如何配置市場活動交付設定
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# 設定傳遞設定 {#delivery-settings}



必須在 **serverConf.xml** 的子菜單。

* **DNS配置**:指定傳遞域和DNS伺服器的IP地址（或主機），這些DNS伺服器用於響應MTA模組從 **`<dnsconfig>`** 向前。

   >[!NOTE]
   >
   >的 **名稱伺服器** 參數對於在Windows中安裝是必不可少的。 對於Linux中的安裝，它必須為空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

您還可以根據您的需要和設定執行以下配置：配置 [SMTP中繼](#smtp-relay)，調整 [MTA子進程](#mta-child-processes)。 [管理出站SMTP通信](#managing-outbound-smtp-traffic-with-affinities)。

## SMTP中繼 {#smtp-relay}

MTA模組充當SMTP廣播（埠25）的本機郵件傳輸代理。

但是，如果安全策略需要，可以將其替換為中繼伺服器。 在這種情況下，全局吞吐量將是中繼吞吐量(前提是中繼伺服器吞吐量低於Adobe Campaign吞吐量)。

在這種情況下，通過在 **`<relay>`** 的子菜單。 必須指定用於傳輸郵件的SMTP伺服器及其關聯埠（預設為25）的IP地址（或主機）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>此操作模式對傳輸造成嚴重限制，因為它由於中繼伺服器固有效能（延遲、頻寬……）而可以大大降低吞吐量。 此外，限定同步傳送錯誤（通過分析SMTP通信量檢測到）的容量將受到限制，如果中繼伺服器不可用，則無法發送。

## MTA子進程 {#mta-child-processes}

可以根據伺服器的CPU功率和可用網路資源控制子進程數（預設情況下為2），以優化廣播效能。 此配置將在 **`<master>`** MTA配置的部分。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱 [電子郵件發送優化](../../installation/using/email-deliverability.md#email-sending-optimization)。

## 管理具有關聯的出站SMTP通信 {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>關聯配置需要從一個伺服器到另一個伺服器保持一致。 我們建議您與Adobe聯繫以進行關聯配置，因為應在運行MTA的所有應用程式伺服器上複製配置更改。

您可以通過與IP地址的關聯來改進出站SMTP通信。

若要這麼做，請套用下列步驟：

1. 在 **`<ipaffinity>`** 的下界 **serverConf.xml** 的子菜單。

   一個關聯可以有多個不同的名稱：分離，使用 **;** 字元。

   範例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   要查看相關參數，請參閱 **serverConf.xml** 的子菜單。

1. 要在下拉清單中啟用地緣選擇，您需要在 **IPAfinity** 枚舉。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >枚舉詳細資訊 [此文檔](../../platform/using/managing-enumerations.md)。

   然後，可以選擇要使用的關聯，如下所示：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您還可以參考 [傳遞伺服器配置](../../installation/using/email-deliverability.md#delivery-server-configuration)。

**相關主題**
* [技術電子郵件設定](email-deliverability.md)
* [以 Campaign 使用 MX 伺服器](using-mx-servers.md)
* [設定電子郵件密件副本](email-archiving.md)
