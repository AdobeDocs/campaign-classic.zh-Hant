---
solution: Campaign Classic
product: campaign
title: 促銷活動傳送設定
description: 瞭解如何設定促銷活動傳送設定
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
translation-type: tm+mt
source-git-commit: 401e1be234d52f04cbdf8dfa97f51ac227836cd5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 1%

---

# 設定傳送設定{#delivery-settings}

必須在&#x200B;**serverConf.xml**&#x200B;資料夾中設定傳送參數。

* **DNS配置**:指定傳送網域和DNS伺服器的IP位址（或主機），這些DNS伺服器用來回應MTA模組從此以後所做的MX類型DNS查 **`<dnsconfig>`** 詢。

   >[!NOTE]
   >
   >**nameServers**&#x200B;參數對於在Windows中安裝是必備的。 對於Linux中的安裝，它必須留空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

您也可以根據您的需求和設定執行下列設定：配置[SMTP中繼](#smtp-relay)，調整[MTA子進程數](#mta-child-processes)、[管理出站SMTP通信](#managing-outbound-smtp-traffic-with-affinities)。

## SMTP中繼{#smtp-relay}

MTA模組用作SMTP廣播（埠25）的本地郵件傳輸代理。

但是，如果安全策略要求，則可以將其替換為中繼伺服器。 在這種情況下，全局吞吐量將是中繼吞吐量(如果中繼伺服器吞吐量低於Adobe Campaign吞吐量)。

在這種情況下，通過在&#x200B;**`<relay>`**&#x200B;部分中配置SMTP伺服器來設定這些參數。 必須指定用於傳輸郵件及其關聯埠的SMTP伺服器的IP地址（或主機）（預設為25）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>此操作模式對傳送帶來嚴重限制，因為由於中繼伺服器的固有效能（延遲、頻寬……），它可大大降低吞吐量。 此外，限定同步傳送錯誤（通過分析SMTP通信量檢測到）的能力將受到限制，如果中繼伺服器不可用，則無法發送。

## MTA子進程{#mta-child-processes}

可以根據伺服器的CPU功率和可用網路資源來控制子進程數（預設情況下為maxSpareServers 2），以優化廣播效能。 此配置將在每台電腦的MTA配置的&#x200B;**`<master>`**&#x200B;部分中進行。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱[電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization)。

## 使用相關性{#managing-outbound-smtp-traffic-with-affinities}管理出站SMTP通信

>[!IMPORTANT]
>
>相關性設定必須在伺服器之間保持一致。 我們建議您與Adobe聯絡以進行親和性配置，因為所有執行MTA的應用程式伺服器上應複製組態變更。

您可以通過具有IP地址的相關性來改進出站SMTP通信。

若要這麼做，請套用下列步驟：

1. 在&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**`<ipaffinity>`**&#x200B;區段中輸入相關性。

   一個相似性可以有數個不同的名稱：若要分隔，請使用&#x200B;**;**&#x200B;字元。

   範例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   要查看相關參數，請參閱&#x200B;**serverConf.xml**&#x200B;檔案。

1. 若要在下拉式清單中啟用相似性選擇，您需要在&#x200B;**IPAffinity**&#x200B;列舉中新增相似性名稱。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >[本檔案](../../platform/using/managing-enumerations.md)中詳述了枚舉。

   然後，您可以選取要使用的相似性，如下所示：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您也可以參考[傳送伺服器組態](../../installation/using/email-deliverability.md#delivery-server-configuration)。

**相關主題**
* [技術電子郵件設定](email-deliverability.md)
* [搭配使用MX伺服器與Campaign](using-mx-servers.md)
* [設定電子郵件密件副本](email-archiving.md)
