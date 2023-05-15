---
product: campaign
title: 電子郵件封存
description: 電子郵件封存
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 5%

---

# 設定電子郵件密件副本 {#email-archiving}



您可以設定Adobe Campaign以保留從您的平台傳送的電子郵件副本。

不過，Adobe Campaign本身並不管理封存的檔案。 它確實可讓您將您選擇的訊息傳送至專用地址，以便使用外部系統處理和封存訊息。

要執行此操作，與已傳送電子郵件對應的.eml檔案會傳輸至遠端伺服器，例如SMTP電子郵件伺服器。 封存目的地是您必須指定的密件副本電子郵件地址（不會顯示給傳送收件者）。

## Recommendations和限制 {#recommendations-and-limitations}

* 電子郵件密件副本功能為選用。 請檢查您的授權合約。
* 針對 **托管和混合體系結構**，請連絡您的帳戶管理員以啟用它。 您選擇的密件副本電子郵件地址必須提供給Adobe團隊，由團隊為您進行配置。
* 針對 **內部部署安裝**，請依照下列准則啟用 — 請參閱 [啟用電子郵件密件副本（內部部署）](#activating-email-archiving--on-premise-) 和 [設定BCC電子郵件地址（內部部署）](#configuring-the-bcc-email-address--on-premise-) 區段。
* 您只能使用一個密件副本電子郵件地址。
* 設定電子郵件密件副本後，請確定已在傳遞範本或透過 **[!UICONTROL Email BCC]** 選項。 如需詳細資訊，請參閱[本節](../../delivery/using/sending-messages.md#archiving-emails)。
* 系統只會考慮成功傳送的電子郵件，不會考慮退信。
* 電子郵件封存系統已隨Adobe Campaign 17.2（版本編號8795）變更。 如果您已使用電子郵件封存，則必須手動升級至新的電子郵件密件副本系統。 如需詳細資訊，請參閱 [移至新的電子郵件密件副本](#updated-email-archiving-system--bcc-) 區段。

## 啟用電子郵件密件副本（內部部署） {#activating-email-archiving--on-premise-}

[!BADGE 內部部署與混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}


若要在內部部署Adobe Campaign時啟用BCC電子郵件封存，請遵循下列步驟。

### 本機資料夾 {#local-folder}

若要啟用將已傳送電子郵件傳輸至密件副本電子郵件地址，必須先將已傳送電子郵件的確切原始副本儲存為.eml檔案，並儲存至本機資料夾。

必須在 **config-`<instance>`.xml** 檔案中。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>實施專案的團隊應負責確保安全設定可允許存取透過 **dataLogPath** 參數。

完整路徑如下： **`<datalogpath>  YYYY-MM-DDHHh`**. 日期和時間會根據MTA伺服器的時鐘(UTC)設定。 例如：

```
C:\emails\2018-12-02\13h
```

存檔檔案名為 **`<deliveryid>-<broadlogid>.eml`** 當電子郵件的狀態不是 **[!UICONTROL Sent]**. 狀態變更為 **[!UICONTROL Sent]**，檔案名稱就會變成 **`<deliveryid>-<broadlogid>-sent.eml`**. 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中間來源補充例項中，BCC電子郵件的目錄位於中間來源補充伺服器上。
>
>若未傳送電子郵件的狀態，則deliveryID和broadlogID會來自中間來源伺服器。 狀態變更為 **[!UICONTROL Sent]**，這些ID來自行銷伺服器。

### 參數 {#parameters}

定義本機資料夾路徑後，視需要在 **config-`<instance name>.xml`** 檔案。 預設值如下：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**:壓縮.eml檔案時使用的格式。 可能的值包括：

   **0**:無壓縮（預設值）

   **1**:壓縮（.zip格式）

* **compressBatchSize**:.eml檔案新增至封存（.zip檔案）的數量。
* **archivingType**:要使用的歸檔策略。 可能的值包括：

   **0**:已傳送電子郵件的原始副本會以.eml格式儲存至 **dataLogPath** 資料夾（預設值）。 的存檔副本 **`<deliveryid>-<broadlogid>-sent.eml`** 檔案會儲存至 **dataLogPath/archives** 檔案夾。 傳送的電子郵件檔案路徑會變成 **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**:已傳送電子郵件的原始副本會以.eml格式儲存至 **dataLogPath** 資料夾，並透過SMTP傳送至BCC電子郵件地址。 將電子郵件副本發送到密件副本地址後，歸檔檔案名稱將變為 **`<deliveryid>-<broadlogid>-sent-archived.eml`** 檔案會移至 **dataLogPath/archives** 檔案夾。 然後會傳送已傳送和BCC封存的電子郵件檔案路徑 **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**:保留.eml檔案以進行歸檔的天數。 延遲後，系統會自動將其移至 **dataLogPath/archives** 資料夾進行壓縮。 依預設，.eml檔案會在兩天後過期。
* **purgeArchivesDelay**:封存於 **dataLogPath/`<archives>`** 檔案夾。 在此期間後，將永久刪除這些檔案。 清除從MTA開始。 預設會每七天執行一次。
* **pollDelay**:檢查新傳入已傳送電子郵件的頻率（以秒為單位） **dataLogPath** 檔案夾。 例如，如果此參數設為60，這表示每分鐘，封存程式都會在 **dataLogPath/`<date and time>`** 資料夾、視需要套用清除，並將電子郵件副本傳送至密件副本地址及/或視需要壓縮封存的檔案。
* **acquireLimit**:在根據 **pollDelay** 參數。 例如，若您設定 **acquireLimit** 參數設為100，而 **pollDelay** 參數設為60，每分鐘會處理100.eml檔案。
* **smtpNbConnection**:與BCC電子郵件地址的SMTP連接數。

請務必根據電子郵件傳送的輸送量調整這些參數。 例如，在MTA每小時傳送30,000封電子郵件的設定中，您可以設定 **pollDelay** 參數為600, **acquireLimit** 參數為5000和 **smtpNbConnection** 參數。 這表示使用2個SMTP連線時，每10分鐘會傳送5,000封電子郵件至密件副本地址。

## 設定BCC電子郵件地址（內部部署） {#configuring-the-bcc-email-address--on-premise-}

[!BADGE 內部部署與混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}


>[!IMPORTANT]
>
>基於隱私理由，BCC電子郵件必須由能夠安全地儲存個人識別資訊(PII)的封存系統處理。

在 **config-`<instance name>.xml`** 檔案中，請使用以下參數來定義要將儲存檔案傳輸到的SMTP電子郵件伺服器：

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**:封存目標目的地
* **smtpEnableTLS**:使用安全SMTP連線（TLS/SSL通訊協定）
* **smtpRelayAddress**:使用的中繼地址
* **smtpRelayPort**:使用中繼埠

>[!NOTE]
>
>如果您使用SMTP中繼，則在封存程式中不會考慮中繼對電子郵件所做的變更。
>
>此外，中繼器 **[!UICONTROL Sent]** 狀態至所有電子郵件，包括未傳送的電子郵件。 因此，會封存所有訊息。

## 移至新的電子郵件密件副本 {#updated-email-archiving-system--bcc-}

[!BADGE 內部部署與混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}



>[!IMPORTANT]
>
>電子郵件封存系統(BCC)已隨Adobe Campaign 17.2（組建版本8795）變更。 如果您從舊版組建版本升級，且已使用電子郵件封存功能，則必須手動升級至新的電子郵件封存系統(BCC)。

若要這麼做，請對 **`config-<instance>.xml`** 檔案：

1. 移除 **zipPath** 參數 **`<archiving>`** 節點。
1. 設定 **compressionFormat** 參數 **1** 如有需要。
1. 設定 **archivingType** 參數 **1**.

設定電子郵件密件副本後，請務必選取 **[!UICONTROL Email BCC]** 選項（在傳遞範本或傳遞中）。 如需詳細資訊，請參閱[本節](../../delivery/using/sending-messages.md#archiving-emails)。

## 電子郵件密件副本最佳作法 {#best-practices}

* **密件副本地址郵箱**:請確定其接收容量足以封存MTA所傳送的所有電子郵件。
* **MTA集區**:密件副本封存功能可在MTA層級運作。 它可讓您複製MTA傳送的每封電子郵件。 由於MTA可以匯集於多個執行個體（例如開發、測試或生產），甚至可匯集於多個用戶端（在中間來源環境中），因此設定此功能會影響安全性：

   * 如果您與多個用戶端共用MTA，且其中一個用戶端已啟用此選項，則此用戶端將會存取共用相同MTA之其他用戶端的所有電子郵件。 若要避免這種情況，請對每個用戶端使用不同的MTA。
   * 如果您對單一用戶端在多個執行個體（開發、測試、生產）間使用相同的MTA，則從所有三個執行個體傳送的訊息將會由dataLogPath選項重複。

* **每個連線的電子郵件數**:BCC電子郵件封存的運作方式是開啟連線，並嘗試透過該連線傳送所有電子郵件。 Adobe建議您與內部技術聯絡人檢查指定連線上接受的電子郵件數量。 增加此數量可能會對BCC吞吐量產生很大影響。
* **密件副本傳送IP**:目前，不會透過一般MTA代理傳送密件副本電子郵件。 而是會開啟從MTA伺服器到目的地電子郵件伺服器的直接連線。 這表示您可能需要根據電子郵件伺服器配置，將其他IP新增至網路上的允許清單。

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