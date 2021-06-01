---
product: campaign
title: 電子郵件封存
description: 電子郵件封存
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 2%

---

# 電子郵件密件副本{#email-archiving}

您可以設定Adobe Campaign以保留從您的平台傳送的電子郵件副本。

不過，Adobe Campaign本身並不管理封存的檔案。 它確實可讓您將您選擇的訊息傳送至專用地址，以便使用外部系統處理和封存訊息。

要執行此操作，與已傳送電子郵件對應的.eml檔案會傳輸至遠端伺服器，例如SMTP電子郵件伺服器。 封存目的地是您必須指定的密件副本電子郵件地址（不會顯示給傳送收件者）。

## Recommendations和限制{#recommendations-and-limitations}

* 電子郵件密件副本功能為選用。 請檢查您的授權合約。
* 對於&#x200B;**托管和混合體系結構**，請聯繫您的客戶經理以激活它。 您選擇的密件副本電子郵件地址必須提供給Adobe團隊，由團隊為您進行配置。
* 若為&#x200B;**內部部署安裝**，請依照以下准則啟用它 — 請參閱[啟用電子郵件密件副本（內部部署）](#activating-email-archiving--on-premise-)和[設定電子郵件密件副本地址（內部部署）](#configuring-the-bcc-email-address--on-premise-)區段。
* 您只能使用一個密件副本電子郵件地址。
* 設定電子郵件密件副本後，請確定已在傳遞範本或透過&#x200B;**[!UICONTROL Email BCC]**&#x200B;選項的傳遞中啟用功能。 如需詳細資訊，請參閱[本節](../../delivery/using/sending-messages.md#archiving-emails)。
* 系統只會考慮成功傳送的電子郵件，不會考慮退信。
* 電子郵件封存系統已隨Adobe Campaign 17.2（版本編號8795）變更。 如果您已使用電子郵件封存，則必須手動升級至新的電子郵件密件副本系統。 如需詳細資訊，請參閱[移至新的電子郵件密件副本](#updated-email-archiving-system--bcc-)區段。

## 啟用電子郵件密件副本（內部部署）{#activating-email-archiving--on-premise-}

若要在內部部署Adobe Campaign時啟用BCC電子郵件封存，請遵循下列步驟。

### 本地資料夾{#local-folder}

若要啟用將已傳送電子郵件傳輸至密件副本電子郵件地址，必須先將已傳送電子郵件的確切原始副本儲存為.eml檔案，並儲存至本機資料夾。

必須在配置的&#x200B;**config-`<instance>`.xml**&#x200B;檔案中指定本地資料夾的路徑。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>實施項目的團隊應負責確保安全設定允許訪問通過&#x200B;**dataLogPath**&#x200B;參數定義的資料夾。

完整路徑如下：**`<datalogpath>  YYYY-MM-DDHHh`**。 日期和時間會根據MTA伺服器的時鐘(UTC)設定。 例如：

```
C:\emails\2018-12-02\13h
```

當電子郵件的狀態不是&#x200B;**[!UICONTROL Sent]**&#x200B;時，封存檔案名稱為&#x200B;**`<deliveryid>-<broadlogid>.eml`**。 狀態變更為&#x200B;**[!UICONTROL Sent]**&#x200B;後，檔案名稱就會變成&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**。 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中間來源補充例項中，BCC電子郵件的目錄位於中間來源補充伺服器上。
>
>若未傳送電子郵件的狀態，則deliveryID和broadlogID會來自中間來源伺服器。 狀態變更為&#x200B;**[!UICONTROL Sent]**&#x200B;後，這些ID即來自行銷伺服器。

### 參數 {#parameters}

定義本地資料夾路徑後，根據需要在&#x200B;**config-`<instance name>.xml`**&#x200B;檔案中添加和編輯以下元素。 預設值如下：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**:壓縮.eml檔案時使用的格式。可能的值包括：

   **0**:無壓縮（預設值）

   **1**:壓縮（.zip格式）

* **compressBatchSize**:.eml檔案新增至封存（.zip檔案）的數量。
* **archivingType**:要使用的歸檔策略。可能的值包括：

   **0**:已傳送電子郵件的原始副本會以.eml格式儲存至 **** dataLogPathfolder（預設值）。將&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**&#x200B;檔案的存檔副本保存到&#x200B;**dataLogPath/archives**&#x200B;資料夾。 已傳送的電子郵件檔案路徑變成&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**。

   **1**:已傳送電子郵件的原始副本會以.eml格式儲存至 **** dataLogPath資料夾，並透過SMTP傳送至密件副本電子郵件地址。將電子郵件副本發送到BCC地址後，存檔檔案名稱將變為&#x200B;**`<deliveryid>-<broadlogid>-sent-archived.eml`**，並將檔案移動到&#x200B;**dataLogPath/archives**&#x200B;資料夾。 已傳送和BCC封存的電子郵件檔案路徑則為&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**。

* **expirationDelay**:保留.eml檔案以進行歸檔的天數。延遲後，它們會自動移至&#x200B;**dataLogPath/archives**&#x200B;資料夾以進行壓縮。 依預設，.eml檔案會在兩天後過期。
* **purgeArchivesDelay**:dataLogPath/資料夾中保 **存的天`<archives>`** 數。在此期間後，將永久刪除這些檔案。 清除從MTA開始。 預設會每七天執行一次。
* **pollDelay**:正在檢查新傳入的已傳送電子郵件至dataLogPath資料夾的頻 **** 率（秒）。例如，如果此參數設定為60，則意味著每分鐘，歸檔過程都會通過&#x200B;**dataLogPath/`<date and time>`**&#x200B;資料夾中的.eml檔案，視需要應用清除，並在需要時將電子郵件副本發送到BCC地址和/或壓縮歸檔檔案。
* **acquireLimit**:根據pollDelay參數再次應用存檔進程之前一次處理的.eml檔 **** 案數。例如，如果您將&#x200B;**acquireLimit**&#x200B;參數設為100，而將&#x200B;**pollDelay**&#x200B;參數設為60，則每分鐘將處理100個.eml檔案。
* **smtpNbConnection**:與BCC電子郵件地址的SMTP連接數。

請務必根據電子郵件傳送的輸送量調整這些參數。 例如，在MTA每小時傳送30,000封電子郵件的設定中，您可以將&#x200B;**pollDelay**&#x200B;參數設為600，將&#x200B;**acquireLimit**&#x200B;參數設為5000，將&#x200B;**smtpNbConnection**&#x200B;參數設為2。 這表示使用2個SMTP連線時，每10分鐘會傳送5,000封電子郵件至密件副本地址。

## 配置BCC電子郵件地址（內部部署）{#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>基於隱私理由，BCC電子郵件必須由能夠安全地儲存個人識別資訊(PII)的封存系統處理。

在&#x200B;**config-`<instance name>.xml`**&#x200B;檔案中，使用以下參數定義要將儲存檔案傳輸到的SMTP電子郵件伺服器：

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
>此外，中繼會為所有電子郵件（包括未發送的電子郵件）指派&#x200B;**[!UICONTROL Sent]**&#x200B;狀態。 因此，會封存所有訊息。

## 移至新的電子郵件密件副本{#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>電子郵件封存系統(BCC)已隨Adobe Campaign 17.2（組建版本8795）變更。 如果您從舊版組建版本升級，且已使用電子郵件封存功能，則必須手動升級至新的電子郵件封存系統(BCC)。

要執行此操作，請對&#x200B;**`config-<instance>.xml`**&#x200B;檔案進行以下更改：

1. 從&#x200B;**`<archiving>`**&#x200B;節點中移除&#x200B;**zipPath**&#x200B;參數。
1. 視需要將&#x200B;**compressionFormat**&#x200B;參數設為&#x200B;**1**。
1. 將&#x200B;**archivingType**&#x200B;參數設定為&#x200B;**1**。

設定電子郵件密件副本後，請務必在傳送範本或傳送中選取&#x200B;**[!UICONTROL Email BCC]**&#x200B;選項。 如需詳細資訊，請參閱[本節](../../delivery/using/sending-messages.md#archiving-emails)。

## 電子郵件密件副本最佳實務{#best-practices}

* **密件副本地址郵箱**:請確定其接收容量足以封存MTA所傳送的所有電子郵件。
* **MTA共同化**:密件副本封存功能可在MTA層級運作。它可讓您複製MTA傳送的每封電子郵件。 由於MTA可在多個執行個體（例如開發、測試或生產）或甚至多個用戶端（在中間來源環境中）共同化，因此設定此功能會影響安全性：

   * 如果您與多個用戶端共用MTA，且其中一個用戶端已啟用此選項，則此用戶端將會存取共用相同MTA之其他用戶端的所有電子郵件。 若要避免這種情況，請對每個用戶端使用不同的MTA。
   * 如果您對單一用戶端在多個執行個體（開發、測試、生產）間使用相同的MTA，則從所有三個執行個體傳送的訊息將會由dataLogPath選項重複。

* **每個連線的電子郵件**:BCC電子郵件封存的運作方式是開啟連線，並嘗試透過該連線傳送所有電子郵件。Adobe建議您與內部技術聯絡人檢查指定連線上接受的電子郵件數量。 增加此數量可能會對BCC吞吐量產生很大影響。
* **密件副本傳送IP**:目前，不會透過一般MTA代理傳送密件副本電子郵件。而是會開啟從MTA伺服器到目的地電子郵件伺服器的直接連線。 這表示您可能需要根據電子郵件伺服器配置，將其他IP新增至網路上的允許清單。
