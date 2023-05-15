---
product: campaign
title: 使用Adobe Campaign Classic在日文行動裝置上傳送電子郵件
description: 了解如何設定、設計和傳送將在日文行動裝置上閱讀的電子郵件
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email, Email Design
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 在日文行動裝置上傳送電子郵件 {#sending-emails-on-japanese-mobiles}



## 日文行動裝置的電子郵件格式 {#email-formats-for-japanese-mobiles}

Adobe Campaign管理行動裝置上電子郵件的三種特定日文格式： **裝飾郵件** （DoCoMo行動裝置）, **Decore Mail** （軟體銀行移動）和 **裝飾郵件** （KDDI AU行動裝置）。 這些格式會施加特定的編碼、結構和大小限制。 進一步了解 [本節](#limitations-and-recommendations).

為了讓收件者正確接收其中一種格式的訊息，我們建議選取 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 在對應的設定檔中：

![](assets/deco-mail_03.png)

不過，如果您離開 **[!UICONTROL Email format]** 選項 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 或 **[!UICONTROL Text]**,Adobe Campaign會自動偵測（傳送電子郵件時）要使用的日文格式，以便正確顯示訊息。

此自動偵測系統以 **[!UICONTROL Management of Email Formats]** 郵件規則集。 有關管理電子郵件格式的詳細資訊，請參閱 [本頁](../../installation/using/email-deliverability.md#managing-email-formats).

## 限制和建議 {#limitations-and-recommendations}

對於發送將在由日本提供商（軟體銀行、 DoCoMo、KDDI AU）運營的移動設備上讀取的電子郵件，應使用一定數量的限制。

因此，您必須：

* 僅使用JPEG或GIF格式的影像
* 建立包含嚴格低於10 000位元組的文本和HTML段的傳送（對於KDDI AU和DoCoMo）
* 使用大小總計（編碼前）低於100 KB的影像
* 每則訊息不要使用超過20個影像
* 使用縮小的HTML格式（每個運算子可使用有限數量的標籤）

>[!NOTE]
>
>建立訊息時，應考量每個運算子的特定限制。 請參閱:
>
>* 若為DoCoMo，請參閱 [本頁](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* 對於KDDI AU，請參閱 [本頁](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* 有關軟體庫，請參閱 [本頁](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## 測試電子郵件內容 {#testing-the-email-content}

### 預覽訊息 {#previewing-the-message}

Adobe Campaign可讓您檢查訊息格式是否適合傳送至日文行動裝置。

定義內容並輸入電子郵件主旨後，您就可以在建立訊息時檢查顯示和格式。

在 **[!UICONTROL Preview]** 頁簽，按一下 **[!UICONTROL More... > Deco-mail diagnostic]** 可讓您：

* 檢查HTML內容標籤是否符合日文格式限制
* 檢查訊息中的影像數量是否未超過格式（20個影像）所設定的限制
* 檢查總郵件大小（小於100kB）

   ![](assets/deco-mail_06.png)

### 執行類型規則 {#running-typology-rule}

除了預覽診斷外，在傳送校樣或傳送時還會執行第二次檢查：特定的類型規則， **[!UICONTROL Deco-mail check]**，會在分析期間啟動。

>[!IMPORTANT]
>
>只有當至少有一個收件者設定為在 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 格式。

此類型規則可讓您確定傳送符合 [格式約束](#limitations-and-recommendations) 由日文運算子定義，尤其是與電子郵件的總大小、HTML和文字區段的大小、訊息中的影像數量，以及HTML內容中的標籤相關。

### 傳送校樣 {#sending-proofs}

您可以傳送校樣以測試傳遞。 傳送校樣時，如果您使用替代地址，請輸入與所用設定檔的電子郵件格式相對應的地址。

例如，如果此設定檔的電子郵件格式是在預先定義的，您可以以test@softbank.ne.jp取代設定檔的位址 **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## 傳送訊息 {#sending-messages}

若要使用Campaign以日文電子郵件格式傳送電子郵件給收件者，可以使用兩個選項：

* 建立兩個傳送：一個僅適用於日文收件者，另一個則適用於其他收件者 — 請參閱 [本節](#designing-a-specific-delivery-for-japanese-formats).
* 建立單一傳送，Adobe Campaign會自動偵測要使用的格式 — 請參閱 [本節](#designing-a-delivery-for-all-formats).

### 為日文格式設計特定的傳送 {#designing-a-specific-delivery-for-japanese-formats}

您可以建立包含兩個傳送的工作流程：一個在日文行動裝置上讀取，另一個在標準電子郵件格式的收件者閱讀。

若要這麼做，請使用 **[!UICONTROL Split]** 活動，並將日文電子郵件格式（裝飾郵件、裝飾郵件和轉寄郵件）定義為篩選條件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 設計所有格式的傳送 {#designing-a-delivery-for-all-formats}

當Adobe Campaign根據網域(具有定義為 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 或 **[!UICONTROL Text]** )，您可以將相同的傳遞傳送給所有收件者。

訊息連絡人將正確顯示給日文行動裝置上的使用者，正如標準收件者。

>[!IMPORTANT]
>
>請務必遵守與每個日文電子郵件格式（裝飾郵件、裝飾郵件和Decore Mail）相關的特殊功能。 有關限制的詳細資訊，請參閱 [本節](#limitations-and-recommendations).
