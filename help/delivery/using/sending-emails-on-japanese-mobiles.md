---
product: campaign
title: 使用Adobe Campaign Classic在日本的行動裝置上傳送電子郵件
description: 瞭解如何設定、設計和傳送將在日文行動裝置上閱讀的電子郵件
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email, Email Design
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 403227736e2e8c606204e9324d0afb5b71be62a5
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---

# 在日文的行動裝置上傳送電子郵件 {#sending-emails-on-japanese-mobiles}



## 日文行動裝置的電子郵件格式 {#email-formats-for-japanese-mobiles}

Adobe Campaign會針對行動裝置上的電子郵件管理三種特定的日文格式： **裝飾郵件** （DoCoMo手機）， **裝飾郵件** （軟銀手機）及 **裝飾郵件** （KDDI AU手機）。 這些格式會施加特定的編碼、結構和大小限制。 進一步瞭解中的限制和建議 [本節](#limitations-and-recommendations).

為了讓收件者能夠正確接收這些格式之一的訊息，我們建議選取 **[!UICONTROL Deco-mail (DoCoMo)]**， **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 在對應設定檔中：

![](assets/deco-mail_03.png)

不過，如果您將 **[!UICONTROL Email format]** 選項為 **[!UICONTROL Unknown]**， **[!UICONTROL HTML]** 或 **[!UICONTROL Text]**，Adobe Campaign會自動偵測（傳送電子郵件時）要使用的日文格式，以便正確顯示訊息。

此自動偵測系統以「 」中定義的預先定義網域清單為基礎 **[!UICONTROL Management of Email Formats]** 郵件規則集。 有關管理電子郵件格式的詳細資訊，請參閱 [此頁面](../../installation/using/email-deliverability.md#managing-email-formats).

## 限制和建議 {#limitations-and-recommendations}

某些限制適用於傳送電子郵件，這些電子郵件將在日本供應商(Softbank、DoCoMo、KDDI AU)營運的行動裝置上讀取。

因此，您必須：

* 僅以JPEG或GIF格式使用影像
* 建立包含嚴格低於10,000位元組之文字和HTML區段的傳遞（針對KDDI AU和DoCoMo）
* 使用總大小（編碼前）小於100 KB的影像
* 每則訊息請勿使用超過20個影像
* 使用縮減大小的HTML格式（每個運運算元可用的標籤數量有限）

>[!NOTE]
>
>建立訊息時，必須考慮每個運運算元的特定限制。 請參閱他們的產品檔案。


## 測試電子郵件內容 {#testing-the-email-content}

### 預覽訊息 {#previewing-the-message}

Adobe Campaign可讓您檢查您的訊息格式是否適合傳送至日文行動裝置。

定義內容並輸入電子郵件主旨後，您可以在建立訊息時檢查顯示和格式設定。

在 **[!UICONTROL Preview]** 內容編輯視窗的索引標籤，按一下 **[!UICONTROL More... > Deco-mail diagnostic]** 可讓您：

* 檢查HTML內容標籤是否符合日文格式限制
* 檢查訊息中的影像數量是否未超過格式的限制（20個影像）
* 檢查郵件大小總計（小於100kB）

   ![](assets/deco-mail_06.png)

### 執行型別規則 {#running-typology-rule}

除了預覽診斷之外，傳送證明或傳遞時還會進行第二次檢查：特定型別規則、 **[!UICONTROL Deco-mail check]**，會在分析期間啟動。

>[!IMPORTANT]
>
>只有當至少有一個收件者設定為接收電子郵件時，才會執行此型別規則 **[!UICONTROL Deco-mail (DoCoMo)]**， **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 格式。

此型別規則可讓您確保傳送遵守 [格式限制](#limitations-and-recommendations) 由日文運運算元定義，尤其是關於電子郵件的總大小、HTML和文字區段的大小、訊息中的影像數量以及HTML內容中的標籤。

### 傳送校樣 {#sending-proofs}

您可以傳送校樣以測試您的傳遞。 傳送證明時，如果您使用替代地址，請輸入與使用之設定檔的電子郵件格式對應的地址。

例如，如果事先定義了設定檔的電子郵件格式，則可以使用test@softbank.ne.jp來取代設定檔的位址 **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## 傳送訊息 {#sending-messages}

若要使用Campaign以日文電子郵件格式傳送電子郵件給收件者，有兩個選項可供使用：

* 建立兩個傳遞：一個僅供日文收件者使用，另一個僅供其他收件者使用 — 請參閱 [本節](#designing-a-specific-delivery-for-japanese-formats).
* 建立單一傳遞，Adobe Campaign會自動偵測要使用的格式 — 請參閱 [本節](#designing-a-delivery-for-all-formats).

### 設計日文格式的特定傳遞 {#designing-a-specific-delivery-for-japanese-formats}

您可以建立包含兩個傳遞的工作流程：一個要在日文行動裝置上讀取，另一個用於具有標準電子郵件格式的收件者。

若要這麼做，請使用 **[!UICONTROL Split]** 活動，並將日文電子郵件格式（裝飾郵件、裝飾郵件和裝飾郵件）定義為篩選條件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 為所有格式設計傳遞 {#designing-a-delivery-for-all-formats}

當Adobe Campaign根據網域動態管理格式時(具有定義為 **[!UICONTROL Unknown]**， **[!UICONTROL HTML]** 或 **[!UICONTROL Text]** )，則可以將相同的傳遞傳送給所有收件者。

訊息連絡人會在日文的行動裝置上正確顯示給使用者，就像標準收件者一樣。

>[!IMPORTANT]
>
>請務必遵守與每個日文電子郵件格式（裝飾郵件、裝飾郵件和裝飾郵件）相關的特殊功能。 有關限制的詳細資訊，請參閱 [本節](#limitations-and-recommendations).
