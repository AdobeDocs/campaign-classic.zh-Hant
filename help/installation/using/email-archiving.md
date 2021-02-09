---
solution: Campaign Classic
product: campaign
title: 電子郵件封存
description: 電子郵件封存
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 5fa848d86f951cb9dc40eb7981abea29c1092291
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 2%

---


# 電子郵件密件副本{#email-archiving}

您可以設定Adobe Campaign，以保留從您的平台傳送的電子郵件副本。

但是，Adobe Campaign本身並不管理已封存的檔案。 它確實可讓您將您選擇的訊息傳送至專用位址，以便使用外部系統處理及封存。

為此，將與已發送電子郵件對應的。eml檔案傳輸到遠程伺服器，如SMTP電子郵件伺服器。 封存目標是您必須指定的密件副本電子郵件地址（對傳送收件者不可見）。

## 建議與限制{#recommendations-and-limitations}

* 電子郵件密件副本功能是可選的。 請檢查您的授權合約。
* 對於&#x200B;**代管和混合式架構**，請連絡您的客戶經理以啟動它。 您選擇的密件副本電子郵件地址必須提供給將為您設定的Adobe團隊。
* 對於&#x200B;**內部部署安裝**，請遵循以下指導來激活它——請參閱[啟用電子郵件密件副本（內部部署）](#activating-email-archiving--on-premise-)和[配置密件副本電子郵件地址（內部部署）](#configuring-the-bcc-email-address--on-premise-)章節。
* 您只能使用一個密件副本電子郵件地址。
* 在設定電子郵件密件副本後，請務必在傳送範本或透過&#x200B;**[!UICONTROL Email BCC]**&#x200B;選項傳送時啟用此功能。 如需詳細資訊，請參閱[本節](../../delivery/using/sending-messages.md#archiving-emails)。
* 只有成功傳送的電子郵件才會納入考量，但彈回數則不會納入考量。
* 電子郵件封存系統已隨Adobe Campaign 17.2(build 8795)而變更。 如果您已使用電子郵件封存，則必須手動升級至新的電子郵件密件副本系統。 有關詳細資訊，請參閱[移至新的電子郵件密件副本](#updated-email-archiving-system--bcc-)部分。

## 啟用電子郵件密件副本（內部部署）{#activating-email-archiving--on-premise-}

若要在內部部署Adobe Campaign時啟用密件副本電子郵件封存，請遵循下列步驟。

### 本地資料夾{#local-folder}

若要啟用將傳送的電子郵件傳輸至密件副本電子郵件地址，必須先將已傳送電子郵件的原始副本儲存為。eml檔案至本機資料夾。

必須在配置的&#x200B;**config-`<instance>`.xml**&#x200B;檔案中指定本地資料夾的路徑。 例如：

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>實施項目的團隊有責任確保安全設定允許訪問通過&#x200B;**dataLogPath**&#x200B;參數定義的資料夾。

完整路徑如下：**`<datalogpath>  YYYY-MM-DDHHh`**。 日期和時間會根據MTA伺服器的時鐘(UTC)來設定。 例如：

```
C:\emails\2018-12-02\13h
```

當電子郵件狀態不是&#x200B;**[!UICONTROL Sent]**&#x200B;時，封存檔案的名稱為&#x200B;**`<deliveryid>-<broadlogid>.eml`**。 狀態變更為&#x200B;**[!UICONTROL Sent]**&#x200B;後，檔案名稱會變成&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**。 例如：

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>在中間採購實例中，密件副本電子郵件的目錄位於中間採購伺服器上。
>
>當未傳送電子郵件狀態時，deliveryID和broadlogID會來自中間採購伺服器。 狀態變更為&#x200B;**[!UICONTROL Sent]**&#x200B;後，這些ID會來自行銷伺服器。

### 參數 {#parameters}

定義本機資料夾路徑後，視需要在&#x200B;**config-`<instance name>.xml`**&#x200B;檔案中新增及編輯下列元素。 以下是預設值：

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**:壓縮。eml檔案時使用的格式。可能的值包括：

   **0**:無壓縮（預設值）

   **1**:壓縮（.zip格式）

* **compressBatchSize**:已新增至封存（.zip檔案）的。eml檔案數。
* **archivingType**:歸檔策略。可能的值包括：

   **0**:已傳送電子郵件的原始副本會以。eml格式儲存至 **** dataLogPath資料夾（預設值）。將&#x200B;**`<deliveryid>-<broadlogid>-sent.eml`**&#x200B;檔案的存檔副本保存到&#x200B;**dataLogPath/archives**&#x200B;資料夾。 傳送的電子郵件檔案路徑變成&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**。

   **1**:已發送電子郵件的原始副本以。eml格式保存到 **** dataLogPath資料夾，並通過SMTP發送到密件副本電子郵件地址。將電子郵件副本發送到BCC地址後，歸檔檔案名將變為&#x200B;**`<deliveryid>-<broadlogid>-sent-archived.eml`** ，並將檔案移動到&#x200B;**dataLogPath/archives**&#x200B;資料夾。 然後，已發送和密件副本歸檔的電子郵件檔案路徑為&#x200B;**`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**。

* **expirationDelay**:保存要存檔的。eml檔案的天數。延遲後，它們會自動移至&#x200B;**dataLogPath/archives**&#x200B;資料夾以進行壓縮。 依預設，.eml檔案會在兩天後到期。
* **purgeArchivesDelay**:dataLogPath/資料夾中保存封 **存的天`<archives>`** 數。在此期間後，會永久刪除這些項目。 清除從MTA啟動開始。 依預設，每七天執行一次。
* **pollDelay**:正在檢查新傳入的電子郵件的頻率（以秒為單位），以找出 **** dataLogPath資料夾。例如，如果此參數設定為60，則表示每分鐘，歸檔過程都會通過&#x200B;**dataLogPath/`<date and time>`**&#x200B;資料夾內的。eml檔案，根據需要應用清除，並將電子郵件副本發送到BCC地址和／或在需要時壓縮歸檔檔案。
* **acquireLimit**:根據pollDelay參數，再次套用封存程式之前一次處理的。eml檔案 **** 數。例如，如果您將&#x200B;**acquireLimit**&#x200B;參數設為100，而將&#x200B;**pollDelay**&#x200B;參數設為60，則每分鐘將處理100個。eml檔案。
* **smtpNbConnection**:到密件副本電子郵件地址的SMTP連接數。

請務必根據電子郵件傳送的吞吐量來調整這些參數。 例如，在MTA每小時傳送30,000封電子郵件的組態中，您可將&#x200B;**pollDelay**&#x200B;參數設定為600，將&#x200B;**acquireLimit**&#x200B;參數設定為5000，將&#x200B;**smtpNbConnection**&#x200B;參數設定為2... 這意味著，使用2個SMTP連接，每10分鐘將發送5,000封電子郵件到密件副本地址。

## 配置密件副本電子郵件地址（內部部署）{#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>出於隱私原因，密件副本電子郵件必須由能夠安全地儲存個人識別資訊(PII)的歸檔系統處理。

在&#x200B;**config-`<instance name>.xml`**&#x200B;檔案中，使用以下參數定義要將儲存檔案傳輸到的SMTP電子郵件伺服器：

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**:歸檔目標目標目標目標
* **smtpEnableTLS**:使用安全的SMTP連接（TLS/SSL協定）
* **smtpRelayAddress**:中繼地址
* **smtpRelayPort**:中繼埠

>[!NOTE]
>
>如果使用SMTP中繼，則在歸檔過程中不會考慮中繼對電子郵件所做的更改。
>
>此外，中繼會為所有電子郵件（包括未發送的電子郵件）分配&#x200B;**[!UICONTROL Sent]**&#x200B;狀態。 因此，將存檔所有消息。

## 移至新的電子郵件密件副本{#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>電子郵件封存系統(BCC)已隨Adobe Campaign 17.2(build 8795)變更。 如果您正在從舊版本升級，並且已使用電子郵件存檔功能，則必須手動升級到新的電子郵件存檔系統(BCC)。

若要這麼做，請對&#x200B;**`config-<instance>.xml`**&#x200B;檔案進行下列變更：

1. 從&#x200B;**`<archiving>`**&#x200B;節點中刪除&#x200B;**zipPath**&#x200B;參數。
1. 視需要將&#x200B;**compressionFormat**&#x200B;參數設為&#x200B;**1**。
1. 將&#x200B;**archivingType**&#x200B;參數設為&#x200B;**1**。

在設定電子郵件密件副本後，請務必在傳送範本或傳送中選取&#x200B;**[!UICONTROL Email BCC]**&#x200B;選項。 如需詳細資訊，請參閱[本節](../../delivery/using/sending-messages.md#archiving-emails)。

## 電子郵件密件副本最佳實踐{#best-practices}

* **密件副本地址郵箱**:請確定它有足夠的接收能力來封存MTA傳送的所有電子郵件。
* **MTA共同化**:密件副本封存功能可在MTA層級運作。它可讓您複製MTA傳送的每封電子郵件。 由於MTA可以跨多個例項（例如開發、測試或prod）或甚至跨多個用戶端（在中部採購環境中）共同化，因此設定此功能會影響安全性：

   * 如果您與多個用戶端共用MTA，且其中一個用戶端已啟用此選項，此用戶端將會存取其他共用相同MTA之用戶端的所有電子郵件。 為避免這種情況，請針對每個用戶端使用不同的MTA。
   * 如果您針對單一用戶端在多個執行個體（開發、測試、prod）上使用相同的MTA，則dataLogPath選項會複製從這三個執行個體傳送的訊息。

* **每個連線的電子郵件**:密件副本電子郵件封存的運作方式是開啟連線並嘗試透過該連線傳送所有電子郵件。Adobe建議與您的內部技術聯絡人確認特定連線上接受的電子郵件數。 增加此數量對BCC吞吐量有很大影響。
* **密件副本發送IP**:目前，密件副本電子郵件不會透過一般的MTA Proxy傳送。而是從MTA伺服器開啟直接連線至目標電子郵件伺服器。 這表示，根據您的電子郵件伺服器配置，您可能需要將其他IP添加到網路上的allowlist。

