---
product: campaign
title: 用日本手機發送電子郵件，Adobe Campaign Classic
description: 瞭解如何配置、設計和發送將在日文手機上閱讀的電子郵件
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 在日本手機上發送電子郵件 {#sending-emails-on-japanese-mobiles}

![](../../assets/common.svg)

## 日本手機的電子郵件格式 {#email-formats-for-japanese-mobiles}

Adobe Campaign為手機上的電子郵件管理三種特定的日文格式： **Deco郵件** （DoCoMo手機）, **迪克雷郵件** （軟銀手機） **裝飾郵件** （KDDI AU手機）。 這些格式施加了特定的編碼、結構和大小約束。 瞭解有關中的限制和建議的更多資訊 [此部分](#limitations-and-recommendations)。

為了讓收件人正確接收這些格式之一的郵件，我們建議選擇 **[!UICONTROL Deco-mail (DoCoMo)]**。 **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 在相應的配置檔案中：

![](assets/deco-mail_03.png)

但是，如果你離開 **[!UICONTROL Email format]** 選項 **[!UICONTROL Unknown]**。 **[!UICONTROL HTML]** 或 **[!UICONTROL Text]**,Adobe Campaign將自動檢測（在發送電子郵件時）要使用的日文格式，以便正確顯示消息。

此自動檢測系統基於在 **[!UICONTROL Management of Email Formats]** 郵件規則集。 有關管理電子郵件格式的詳細資訊，請參閱 [此頁](../../installation/using/email-deliverability.md#managing-email-formats)。

## 限制和建議 {#limitations-and-recommendations}

發送電子郵件時，應使用一定數量的限制，這些電子郵件將在日本提供商（軟銀、DoCoMo、KDDI AU）運營的移動設備上讀取。

因此，您必須：

* 僅使用JPEG或GIF格式的影像
* 建立文本和HTML部分嚴格低於10 000位元組（對於KDDI AU和DoCoMo）的傳遞
* 使用總大小（編碼前）低於100 KB的影像
* 每封郵件使用的映像不超過20個
* 使用縮減大小的HTML格式（每個運算子可用的標籤數量有限）

>[!NOTE]
>
>建立郵件時，將考慮每個運算子的特定限制。 請參閱:
>
>* 有關DoCoMo，請參閱 [此頁](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* 有關KDDI AU，請參閱 [此頁](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* 有關軟銀，請參閱 [此頁](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## Test電子郵件內容 {#testing-the-email-content}

### 預覽消息 {#previewing-the-message}

Adobe Campaign允許您檢查您的消息格式是否適合發送到日文手機。

定義內容並輸入電子郵件主題後，可以在建立郵件時檢查顯示和格式。

在 **[!UICONTROL Preview]** 頁籤，按一下 **[!UICONTROL More... > Deco-mail diagnostic]** 允許您：

* 檢查HTML內容標籤是否符合日文格式限制
* 檢查郵件中的影像數是否未超過格式所規定的限制（20個影像）
* 檢查總消息大小（小於100kB）

   ![](assets/deco-mail_06.png)

### 運行類型規則 {#running-typology-rule}

除預覽診斷外，在發送證明或遞送時執行第二檢查：具體的分類規則， **[!UICONTROL Deco-mail check]**，在分析過程中啟動。

>[!IMPORTANT]
>
>僅當至少一個收件人配置為在以下位置接收電子郵件時，才執行此類型規則 **[!UICONTROL Deco-mail (DoCoMo)]**。 **[!UICONTROL Decore Mail (Softbank)]** 或 **[!UICONTROL Decoration Mail (KDDI AU)]** 的子菜單。

此類型規則允許您確保傳遞 [格式約束](#limitations-and-recommendations) 由日語運算子定義，特別是與電子郵件的總大小、HTML和文本節的大小、消息中的影像數以及HTML內容中的標籤有關。

### 傳送校樣 {#sending-proofs}

你可以發送校樣來test你的交貨。 當您發送證明時，如果您使用的是替代地址，請輸入與使用的配置檔案的電子郵件格式對應的地址。

例如，如果此配置檔案的電子郵件格式是在上預先定義的，則可以將配置檔案的地址替換為test@softbank.ne.jp **[!UICONTROL Decore Mail (Softbank)]**。

![](assets/deco-mail_05.png)

## 傳送訊息 {#sending-messages}

要使用「促銷活動」向具有日文電子郵件格式的收件人發送電子郵件，可以選擇以下兩個選項：

* 建立兩個交貨：一個僅用於日文收件人，另一個用於其他收件人 — 請參閱 [此部分](#designing-a-specific-delivery-for-japanese-formats)。
* 建立單個交貨，Adobe Campaign將自動檢測要使用的格式 — 請參閱 [此部分](#designing-a-delivery-for-all-formats)。

### 為日文格式設計特定的交付 {#designing-a-specific-delivery-for-japanese-formats}

您可以建立包含兩個交貨的工作流：一個在日文手機上閱讀，另一個在標準電子郵件格式的收件人上閱讀。

要執行此操作，請使用 **[!UICONTROL Split]** 中的活動，並將日文電子郵件格式（Deco-mail、Decoration Mail和Decore Mail）定義為篩選條件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 設計所有格式的交付 {#designing-a-delivery-for-all-formats}

當Adobe Campaign根據域動態管理格式(具有定義為 **[!UICONTROL Unknown]**。 **[!UICONTROL HTML]** 或 **[!UICONTROL Text]** )，您可以向所有收件人發送相同的遞送。

消息聯繫人將正確顯示給日文手機上的用戶，就像標準接收者一樣。

>[!IMPORTANT]
>
>確保遵守與每種日文電子郵件格式（Deco-mail、Decoration Mail和Decore Mail）相關的特殊功能。 有關限制的詳細資訊，請參閱 [此部分](#limitations-and-recommendations)。
