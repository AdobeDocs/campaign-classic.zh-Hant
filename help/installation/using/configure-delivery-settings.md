---
product: campaign
title: 促銷活動傳送設定設定
description: 了解如何配置Campaign傳送設定
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# 設定傳遞設定 {#delivery-settings}



傳送參數必須在 **serverConf.xml** 檔案夾。

* **DNS配置**:指定用於回應MTA模組從 **`<dnsconfig>`** 向前。

   >[!NOTE]
   >
   >此 **nameServers** 參數是在Windows中安裝的必要參數。 在Linux中安裝時，必須將其保留為空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

您也可以根據需求和設定執行下列設定：設定 [SMTP中繼](#smtp-relay)，調整 [MTA子進程](#mta-child-processes), [管理出站SMTP流量](#managing-outbound-smtp-traffic-with-affinities).

## SMTP中繼 {#smtp-relay}

MTA模組充當SMTP廣播（埠25）的本機郵件傳輸代理。

但是，如果您的安全策略需要，則可以用中繼伺服器替換它。 在這種情況下，全局吞吐量將是中繼吞吐量(前提是中繼伺服器吞吐量低於Adobe Campaign吞吐量)。

在此情況下，這些參數的設定方式為在 **`<relay>`** 區段。 必須指定用於傳輸郵件的SMTP伺服器的IP地址（或主機）及其關聯埠（預設為25）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>此操作模式意味著傳送受到嚴重限制，因為由於中繼伺服器的固有效能（延遲、頻寬……），它可以大大降低吞吐量。 此外，限定同步傳送錯誤（通過分析SMTP流量檢測到）的容量將受到限制，如果中繼伺服器不可用，則無法發送。

## MTA子進程 {#mta-child-processes}

可以控制子進程（預設情況下為maxSpareServers 2）的數量，以根據伺服器的CPU功率和可用網路資源來優化廣播效能。 此設定將在 **`<master>`** MTA設定的區段。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱 [電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization).

## 使用相關性管理傳出SMTP流量 {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>相關性設定必須在伺服器之間保持一致。 建議您聯絡Adobe以進行相關性設定，因為應在執行MTA的所有應用程式伺服器上複製設定變更。

您可以透過與IP位址的相似性來改善傳出SMTP流量。

若要這麼做，請套用下列步驟：

1. 在 **`<ipaffinity>`** 區段 **serverConf.xml** 檔案。

   一個相關性可以有數個不同的名稱：若要加以區隔，請使用 **;** 字元。

   範例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   若要檢視相關參數，請參閱 **serverConf.xml** 檔案。

1. 若要在下拉式清單中啟用相關性選取，您必須在 **IPAffinity** 枚舉。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >列舉在 [此文檔](../../platform/using/managing-enumerations.md).

   接著，您可以選取要使用的相關性，如下所示，針對類型：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您也可以參閱 [傳送伺服器設定](../../installation/using/email-deliverability.md#delivery-server-configuration).

**相關主題**
* [技術電子郵件設定](email-deliverability.md)
* [以 Campaign 使用 MX 伺服器](using-mx-servers.md)
* [設定電子郵件密件副本](email-archiving.md)
