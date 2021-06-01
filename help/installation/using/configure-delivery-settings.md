---
product: campaign
title: 促銷活動傳送設定設定
description: 了解如何配置Campaign傳送設定
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 3%

---

# 設定傳遞設定 {#delivery-settings}

傳送參數必須在&#x200B;**serverConf.xml**&#x200B;資料夾中設定。

* **DNS配置**:指定DNS伺服器的傳送網域和IP位址（或主機），這些DNS伺服器用於從此起回應MTA模組提出的MX類型DNS **`<dnsconfig>`** 查詢。

   >[!NOTE]
   >
   >**nameServers**&#x200B;參數對於在Windows中安裝是必要的。 在Linux中安裝時，必須將其保留為空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

您也可以根據需求和設定執行下列設定：配置[SMTP中繼](#smtp-relay)，調整[MTA子進程數](#mta-child-processes)、[管理出站SMTP通信](#managing-outbound-smtp-traffic-with-affinities)。

## SMTP中繼{#smtp-relay}

MTA模組充當SMTP廣播（埠25）的本機郵件傳輸代理。

但是，如果您的安全策略需要，則可以用中繼伺服器替換它。 在這種情況下，全局吞吐量將是中繼吞吐量(前提是中繼伺服器吞吐量低於Adobe Campaign吞吐量)。

在這種情況下，這些參數是通過在&#x200B;**`<relay>`**&#x200B;部分中配置SMTP伺服器來設定的。 必須指定用於傳輸郵件的SMTP伺服器的IP地址（或主機）及其關聯埠（預設為25）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>此操作模式意味著傳送受到嚴重限制，因為由於中繼伺服器的固有效能（延遲、頻寬……），它可以大大降低吞吐量。 此外，限定同步傳送錯誤（通過分析SMTP流量檢測到）的容量將受到限制，如果中繼伺服器不可用，則無法發送。

## MTA子進程{#mta-child-processes}

可以控制子進程（預設情況下為maxSpareServers 2）的數量，以根據伺服器的CPU功率和可用網路資源來優化廣播效能。 此配置將在每個單台電腦的MTA配置的&#x200B;**`<master>`**&#x200B;部分進行。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱[電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization)。

## 使用相關性{#managing-outbound-smtp-traffic-with-affinities}管理出站SMTP流量

>[!IMPORTANT]
>
>相關性設定必須在伺服器之間保持一致。 建議您聯絡Adobe以進行相關性設定，因為應在執行MTA的所有應用程式伺服器上複製設定變更。

您可以透過與IP位址的相似性來改善傳出SMTP流量。

若要這麼做，請套用下列步驟：

1. 在&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**`<ipaffinity>`**&#x200B;區段中輸入相關性。

   一個相關性可以有數個不同的名稱：若要分隔，請使用&#x200B;**;**&#x200B;字元。

   範例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   若要檢視相關參數，請參閱&#x200B;**serverConf.xml**&#x200B;檔案。

1. 若要在下拉式清單中啟用相關性選取，您需要在&#x200B;**IPAffinity**&#x200B;列舉中新增相關性名稱。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >[本文檔](../../platform/using/managing-enumerations.md)中詳細說明了枚舉。

   接著，您可以選取要使用的相關性，如下所示，針對類型：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您也可以參閱[傳送伺服器設定](../../installation/using/email-deliverability.md#delivery-server-configuration)。

**相關主題**
* [技術電子郵件設定](email-deliverability.md)
* [以 Campaign 使用 MX 伺服器](using-mx-servers.md)
* [設定電子郵件密件副本](email-archiving.md)
