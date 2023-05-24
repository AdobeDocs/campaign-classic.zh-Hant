---
product: campaign
title: Campaign傳遞設定組態
description: 瞭解如何設定Campaign傳遞設定
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



傳遞引數必須設定在 **serverConf.xml** 資料夾。

* **DNS設定**：指定傳遞網域和DNS伺服器的IP位址（或主機），用於回應MTA模組從進行的MX型別DNS查詢。 **`<dnsconfig>`** 從上往下。

   >[!NOTE]
   >
   >此 **nameServer** 引數對於Windows中的安裝是必要的。 若是在Linux中進行安裝，則必須保留空白。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

您也可以根據您的需求和設定進行以下設定：設定 [SMTP轉送](#smtp-relay)，調整數量 [MTA子處理序](#mta-child-processes)， [管理輸出SMTP流量](#managing-outbound-smtp-traffic-with-affinities).

## SMTP轉送 {#smtp-relay}

MTA模組會當作SMTP廣播（連線埠25）的原生郵件傳輸代理程式。

不過，如果您的安全性原則需要，可以透過轉送伺服器來取代它。 在這種情況下，全域輸送量將是轉送量(前提是轉送伺服器輸送量低於Adobe Campaign輸送量)。

在此情況下，這些引數的設定方式為透過以下專案中的SMTP伺服器進行： **`<relay>`** 區段。 您必須指定用來傳輸郵件及其相關連線埠（預設為25）之SMTP伺服器的IP位址（或主機）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>此作業模式表示傳送作業受到嚴重限制，因為中繼伺服器的固有效能（延遲、頻寬……）會大幅降低輸送量。 此外，限定同步傳送錯誤（透過分析SMTP流量所偵測）的容量將會受到限制，而且如果無法使用轉送伺服器，將無法進行傳送。

## MTA子處理序 {#mta-child-processes}

您可以控制子處理序（預設為2）的數量，以便根據伺服器的CPU效能和可用的網路資源來最佳化廣播效能。 此設定將在 **`<master>`** 每部電腦上MTA設定的區段。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱 [電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization).

## 使用相關性管理輸出SMTP流量 {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>伺服器之間的相似性設定必須一致。 建議您聯絡Adobe以取得相似性設定，因為應在執行MTA的所有應用程式伺服器上復寫設定變更。

您可以透過與IP位址的相似性來改善輸出SMTP流量。

若要這麼做，請套用下列步驟：

1. 輸入相關性，在 **`<ipaffinity>`** 部分 **serverConf.xml** 檔案。

   一個相似性可以有多種不同的名稱：若要加以分隔，請使用 **；** 字元。

   範例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   若要檢視相關引數，請參閱 **serverConf.xml** 檔案。

1. 若要在下拉式清單中啟用相關性選擇，您必須在以下專案新增相關性名稱： **IPAffinity** 分項清單。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >詳細列舉請參閱 [本檔案](../../platform/using/managing-enumerations.md).

   然後您可以選取要使用的相似性，如下面的型別所示：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您也可以參閱 [傳遞伺服器設定](../../installation/using/email-deliverability.md#delivery-server-configuration).

**相關主題**
* [技術電子郵件設定](email-deliverability.md)
* [以 Campaign 使用 MX 伺服器](using-mx-servers.md)
* [設定電子郵件密件副本](email-archiving.md)
