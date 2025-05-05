---
product: campaign
title: 電子郵件封存
description: 電子郵件封存
feature: Installation, Instance Settings, Email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 2%

---

# 設定電子郵件密件副本 {#email-archiving}



您可以設定Adobe Campaign以保留從您的平台傳送的電子郵件副本。

不過，Adobe Campaign本身不會管理封存的檔案。 它可讓您選擇的訊息傳送至專用地址，您可在其中使用外部系統處理和封存訊息。

為此，會將與已傳送電子郵件相對應的.eml檔案傳輸到遠端伺服器，例如SMTP電子郵件伺服器。 封存目的地是您必須指定的密件副本電子郵件地址（傳送收件者無法看到）。

## Recommendations和限制 {#recommendations-and-limitations}

* 電子郵件密件副本功能為選用。 請檢查您的授權合約。
* 若為&#x200B;**託管和混合式架構**，請連絡您的帳戶管理員以啟用它。 您必須將您選擇的密件副本電子郵件地址提供給會為您設定該地址的Adobe團隊。
* 若為&#x200B;**內部部署安裝**，請遵循下列准則加以啟用 — 請參閱[啟用電子郵件密件副本（內部部署）](#activating-email-archiving--on-premise-)與[設定密件副本電子郵件地址（內部部署）](#configuring-the-bcc-email-address--on-premise-)區段。
* 您只能使用一個密件副本電子郵件地址。
* 設定電子郵件密件副本後，請確定在傳遞範本中或透過&#x200B;**[!UICONTROL Email BCC]**&#x200B;選項在傳遞中啟用該功能。 如需詳細資訊，請參閱[本節](../../delivery/using/sending-messages.md#archiving-emails)。
* 只考慮成功傳送的電子郵件，不考慮跳出。
* 電子郵件封存系統隨Adobe Campaign 17.2 （版本編號8795）而變更。 如果您已在使用電子郵件封存，則必須手動升級至新的電子郵件密件副本系統。 如需詳細資訊，請參閱[移至新的電子郵件密件副本](#updated-email-archiving-system--bcc-)區段。

## 啟用電子郵件密件副本（內部部署） {#activating-email-archiving--on-premise-}

[!BADGE 內部部署與混合式]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}


若要在內部部署Adobe Campaign時啟用密件副本電子郵件封存，請遵循下列步驟。

### 本機資料夾 {#local-folder}

若要將已傳送電子郵件傳輸至密件副本電子郵件地址，必須先將已傳送電子郵件的精確原始副本儲存為.eml檔案至本機資料夾。

本機資料夾的路徑必須在組態的&#x200B;**config-`<instance>`.xml**&#x200B;檔案中指定。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>實作專案的團隊有責任確保安全性設定允許存取透過&#x200B;**dataLogPath**&#x200B;引數定義的資料夾。

完整路徑如下： **`<datalogpath>  YYYY-MM-DDHHh`**。 日期和時間會根據MTA伺服器的時鐘(UTC)設定。 例如：

```
C:\emails\2018-12-02\13h
```

當電子郵件的狀態不是&#x200B;**[!UICONTROL Sent]**&#x200B;時，封存檔案名稱為&#x200B;**`<deliveryid>-<broadlogid>.eml`**。 一旦狀態變更為&#x200B;**[!UICONTROL Sent]**，檔案名稱就會變成&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**。 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中間來源執行個體中，密件副本電子郵件的目錄位於中間來源伺服器上。
>
>當電子郵件的狀態未傳送時，deliveryID和broadlogID會來自中間來源伺服器。 一旦狀態變更為&#x200B;**[!UICONTROL Sent]**，這些ID就會來自行銷伺服器。

### 參數 {#parameters}

定義本機資料夾路徑後，視需要在&#x200B;**config-`<instance name>.xml`**&#x200B;檔案中新增並編輯下列元素。 以下是預設值：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**：壓縮.eml檔案時使用的格式。 可能的值包括：

  **0**：無壓縮（預設值）

  **1**：壓縮（.zip格式）

* **compressBatchSize**：新增至封存檔的.eml檔案數目（.zip檔案）。


* **archivingType**：要使用的封存策略。 唯一可能的值為&#x200B;**1**。 已傳送電子郵件的原始復本會以.eml格式儲存至&#x200B;**dataLogPath**&#x200B;資料夾，並透過SMTP傳送至密件副本電子郵件地址。 將電子郵件復本傳送至密件副本位址後，封存檔案名稱會變成&#x200B;**`<deliveryid>-<broadlogid>-sent-archived.eml`**，且檔案會移至&#x200B;**dataLogPath/封存**&#x200B;資料夾。 已傳送及密件副本封存的電子郵件檔案路徑為&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**。

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**： .eml檔案保留存檔的天數。 延遲之後，它們會自動移至&#x200B;**dataLogPath/archives**&#x200B;資料夾進行壓縮。 根據預設，.eml檔案會在兩天後過期。
* **purgeArchivesDelay**： **dataLogPath/`<archives>`**&#x200B;資料夾中保留的封存天數。 在這段期間後，它們將會永久刪除。 清除作業會在MTA啟動時開始。 預設會每七天執行一次。
* **pollDelay**：檢查新傳入已傳送電子郵件至&#x200B;**dataLogPath**&#x200B;資料夾的頻率（秒）。 例如，如果此引數設為60，表示封存程式每分鐘都會處理&#x200B;**dataLogPath/`<date and time>`**&#x200B;資料夾內的.eml檔案、視需要套用清除，並視需要傳送電子郵件復本至BCC位址及/或壓縮封存的檔案。
* **acquireLimit**：在根據&#x200B;**pollDelay**&#x200B;引數再次套用封存程式之前，一次處理的.eml檔案數目。 例如，如果您將&#x200B;**acquireLimit**&#x200B;引數設為100，而&#x200B;**pollDelay**&#x200B;引數設為60，則每分鐘將處理100個.eml檔案。
* **smtpNbConnection**：與BCC電子郵件地址的SMTP連線數目。

請務必根據電子郵件傳送吞吐量調整這些引數。 例如，在MTA每小時傳送30,000封電子郵件的設定中，您可以將&#x200B;**pollDelay**&#x200B;引數設為600，**acquireLimit**&#x200B;引數設為5000，並將&#x200B;**smtpNbConnection**&#x200B;引數設為2。 這表示若使用2個SMTP連線，每10分鐘會傳送5,000封電子郵件至BCC位址。

## 設定密件副本電子郵件地址（內部部署） {#configuring-the-bcc-email-address--on-premise-}

[!BADGE 內部部署與混合式]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}


>[!IMPORTANT]
>
>基於隱私權理由，密件副本電子郵件必須由能夠安全儲存個人識別資訊(PII)的封存系統處理。

在&#x200B;**config-`<instance name>.xml`**&#x200B;檔案中，使用下列引數來定義儲存的檔案將傳輸到的SMTP電子郵件伺服器：

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**：封存目標目的地
* **smtpEnableTLS**：使用安全的SMTP連線（TLS/SSL通訊協定）
* **smtpRelayAddress**：要使用的轉送位址
* **smtpRelayPort**：要使用的轉送連線埠

>[!NOTE]
>
>如果您使用SMTP轉送，在封存程式中不會考慮轉送對電子郵件所做的變更。
>
>此外，轉送會將&#x200B;**[!UICONTROL Sent]**&#x200B;狀態指派給所有電子郵件，包括未傳送的電子郵件。 因此，所有訊息都會被封存。

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## 電子郵件密件副本最佳實務 {#best-practices}

* **密件副本位址信箱**：請確定它有足夠的接收容量來封存MTA所傳送的所有電子郵件。
* **MTA集區**： BCC封存功能可在MTA層級運作。 它可讓您複製MTA傳送的每封電子郵件。 由於MTA可以跨多個執行個體（例如開發、測試或生產）或甚至跨多個客戶（在中間來源環境中）進行集區，因此設定此功能會影響安全性：

   * 如果您與多個使用者端共用MTA，且其中一個已啟用此選項，則此使用者端將存取共用相同MTA的其他使用者端的所有電子郵件。 若要避免這種情況，請對每個使用者端使用不同的MTA。
   * 如果您針對單一使用者端在多個執行個體（開發、測試、生產）中使用相同的MTA，則從所有三個執行個體傳送的訊息將由dataLogPath選項複製。

* **每個連線的電子郵件**： BCC電子郵件封存的運作方式是開啟連線，並嘗試透過該連線傳送所有電子郵件。 Adobe建議您與內部技術連絡人確認指定的連線可接受的電子郵件數量。 增加此數目可能會對BCC輸送量產生重大影響。
* **BCC傳送IP**：目前，BCC電子郵件不會透過一般MTA代理程式傳送。 而是會開啟從MTA伺服器到目的地電子郵件伺服器的直接連線。 這表示根據您的電子郵件伺服器設定，您可能需要將其他IP新增到您網路上的允許清單。

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->