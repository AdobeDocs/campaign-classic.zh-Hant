---
product: campaign
title: Campaign傳遞設定組態
description: 瞭解如何設定Campaign傳送設定
feature: Installation, Channel Configuration
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 5%

---

# 設定傳遞設定 {#delivery-settings}



必須在&#x200B;**serverConf.xml**&#x200B;資料夾中設定傳遞引數。

* **DNS設定**：指定傳遞網域和DNS伺服器的IP位址（或主機），這些伺服器是用來回應MTA模組從&#x200B;**`<dnsconfig>`**&#x200B;開始所發出的MX型別DNS查詢。

  >[!NOTE]
  >
  >**nameServers**&#x200B;引數對於Windows中的安裝是必要的。 在Linux中進行安裝時，必須將它保留為空白。

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

您也可以根據您的需求和設定進行下列設定：設定[SMTP轉送](#smtp-relay)、調整[MTA子處理序的數量](#mta-child-processes)、[管理輸出SMTP流量](#managing-outbound-smtp-traffic-with-affinities)。

## SMTP轉送 {#smtp-relay}

MTA模組會當作SMTP廣播（連線埠25）的原生郵件傳輸代理程式。

不過，如果您的安全性原則要求，可以透過轉送伺服器來取代它。 在這種情況下，全域輸送量將是轉送伺服器輸送量(前提是轉送伺服器輸送量低於Adobe Campaign輸送量)。

在此案例中，這些引數是透過在&#x200B;**`<relay>`**&#x200B;區段中設定SMTP伺服器來設定。 您必須指定用來傳輸郵件及其相關連線埠（預設為25）之SMTP伺服器的IP位址（或主機）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>此作業模式表示傳送受到嚴重限制，因為中繼伺服器的內在效能（延遲、頻寬……）會大幅降低輸送量。 此外，限定同步傳送錯誤（透過分析SMTP流量所偵測）的容量將會受到限制，而且如果無法使用轉送伺服器，將無法進行傳送。

## MTA子處理序 {#mta-child-processes}

您可以控制子處理序（預設為2）的數量，以根據伺服器的CPU效能和可用的網路資源來最佳化廣播效能。 此設定將在每台個別電腦上的MTA設定的&#x200B;**`<master>`**&#x200B;區段中進行。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱[電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization)。

## 使用相關性管理輸出SMTP流量 {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>伺服器之間的相似性設定必須保持一致。 建議您聯絡Adobe以進行相似性設定，因為應在執行MTA的所有應用程式伺服器上復寫設定變更。

您可以透過與IP位址的相似性來改善傳出SMTP流量。

若要這麼做，請套用下列步驟：

1. 在&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**`<ipaffinity>`**&#x200B;區段中輸入相關性。

   一個相似性可以有數個不同的名稱：若要分隔它們，請使用&#x200B;**；**&#x200B;字元。

   例如：

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   若要檢視相關引數，請參閱&#x200B;**serverConf.xml**&#x200B;檔案。

1. 若要在下拉式清單中啟用相似性選取，您必須在&#x200B;**IPAffinity**&#x200B;列舉中新增相似性名稱。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >列舉在[此檔案](../../platform/using/managing-enumerations.md)中有詳細說明。

   然後，您可以選取要使用的相似性，如下面的型別所示：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您也可以參考[傳遞伺服器組態](../../installation/using/email-deliverability.md#delivery-server-configuration)。

**相關主題**
* [技術電子郵件設定](email-deliverability.md)
* [以 Campaign 使用 MX 伺服器](using-mx-servers.md)
* [設定電子郵件密件副本](email-archiving.md)
