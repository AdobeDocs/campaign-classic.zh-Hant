---
solution: Campaign Classic
product: campaign
title: 使用Adobe Campaign Classic在日文行動裝置上傳送電子郵件
description: 瞭解如何設定、設計和傳送將在日文行動裝置上閱讀的電子郵件。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: fe4262a1da011cb155651c5e786f19188139cff1
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# 在日文手機上傳送電子郵件{#sending-emails-on-japanese-mobiles}

## 日文行動裝置的電子郵件格式{#email-formats-for-japanese-mobiles}

Adobe Campaign管理三種特定的日文格式，用於行動裝置上的電子郵件：**Deco-mail**(DoCoMo mo mobiles)、**Decore Mail**(Softbank mobiles)和&#x200B;**Decoring Mail**(KDDI AU mobiles)。 這些格式會加上特定的編碼、結構和大小限制。 進一步瞭解[本節](#limitations-and-recommendations)中的限制和建議。

為了讓收件者能夠正確接收以下格式的訊息，建議在對應的設定檔中選取&#x200B;**[!UICONTROL Deco-mail (DoCoMo)]**、**[!UICONTROL Decore Mail (Softbank)]**&#x200B;或&#x200B;**[!UICONTROL Decoration Mail (KDDI AU)]**:

![](assets/deco-mail_03.png)

不過，如果您將&#x200B;**[!UICONTROL Email format]**&#x200B;選項保留為&#x200B;**[!UICONTROL Unknown]**、**[!UICONTROL HTML]**&#x200B;或&#x200B;**[!UICONTROL Text]**,Adobe Campaign會自動偵測（傳送電子郵件時）要使用的日文格式，以正確顯示訊息。

此自動檢測系統基於&#x200B;**[!UICONTROL Management of Email Formats]**&#x200B;郵件規則集中定義的預定義域清單。 有關管理電子郵件格式的詳細資訊，請參閱[本頁](../../installation/using/email-deliverability.md#managing-email-formats)。

## 限制與建議{#limitations-and-recommendations}

傳送電子郵件時，會受到若干限制，這些電子郵件會在日本供應商(Softbank、DoCoMo、KDDI AU)所營運的行動裝置上讀取。

因此，您必須：

* 僅使用JPEG或GIF格式的影像
* 建立文字和HTML區段的傳送，其欄位嚴格低於10 000位元組（適用於KDDI AU和DoCoMo）
* 使用總大小（編碼前）低於100 KB的影像
* 每則訊息不要使用超過20個影像
* 使用精簡的HTML格式（每個運算子可使用有限數目的標籤）

>[!NOTE]
>
>建立訊息時，應考量到每個運算子的特定限制。 請參閱:
>
>* 如需DoCoMo，請參閱[本頁](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* 對於KDDI AU，請參閱[此頁](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* 如需Softbank，請參閱[本頁](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## 測試電子郵件內容{#testing-the-email-content}

### 預覽訊息{#previewing-the-message}

Adobe Campaign可讓您檢查訊息格式是否適合傳送至日文行動裝置。

定義內容並輸入電子郵件主旨後，您就可以在建立訊息時檢查顯示和格式。

在內容編輯窗口的&#x200B;**[!UICONTROL Preview]**&#x200B;頁籤中，按一下&#x200B;**[!UICONTROL More... > Deco-mail diagnostic]**&#x200B;可以：

* 檢查HTML內容標籤是否符合日文格式限制
* 檢查訊息中的影像數量是否未超過格式（20張影像）所設定的限制
* 檢查消息大小總計（小於100kB）

   ![](assets/deco-mail_06.png)

### 運行類型學規則{#running-typology-rule}

除了預覽診斷外，在傳送校樣或傳送時進行第二檢查：分析期間會啟動特定的排版規則&#x200B;**[!UICONTROL Deco-mail check]**。

>[!IMPORTANT]
>
>只有當至少一個收件者被配置為接收&#x200B;**[!UICONTROL Deco-mail (DoCoMo)]**、**[!UICONTROL Decore Mail (Softbank)]**&#x200B;或&#x200B;**[!UICONTROL Decoration Mail (KDDI AU)]**&#x200B;格式的電子郵件時，才執行此排版規則。

此排版規則可讓您確定傳送符合日文運算子所定義的[格式限制](#limitations-and-recommendations)，尤其是與電子郵件的總大小、HTML和文字區段的大小、訊息中的影像數量，以及HTML內容中的標籤有關。

### 傳送校樣 {#sending-proofs}

您可以傳送校樣來測試傳送。 當您傳送證明時，如果您使用替代地址，請輸入與所用描述檔電子郵件格式對應的地址。

例如，如果此描述檔的電子郵件格式是預先在&#x200B;**[!UICONTROL Decore Mail (Softbank)]**&#x200B;中定義的，您可以將描述檔的位址取代為test@softbank.ne.jp。

![](assets/deco-mail_05.png)

## 傳送訊息 {#sending-messages}

若要使用Campaign以日文電子郵件格式傳送電子郵件給收件者，有兩種選項可能：

* 建立兩個傳送：一個僅供日文收件人使用，另一個為其他收件人使用——請參閱[本節](#designing-a-specific-delivery-for-japanese-formats)。
* 建立單一傳送，Adobe Campaign會自動偵測要使用的格式——請參閱[本節](#designing-a-delivery-for-all-formats)。

### 針對日文格式設計特定的傳送內容{#designing-a-specific-delivery-for-japanese-formats}

您可以建立包含兩個傳送的工作流程：一個要在日文行動裝置上閱讀，另一個要在標準電子郵件格式的收件者閱讀。

若要這麼做，請使用工作流程中的&#x200B;**[!UICONTROL Split]**&#x200B;活動，並將日文電子郵件格式（Deco-mail、Decoring Mail和Decore Mail）定義為篩選條件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 設計所有格式的傳送{#designing-a-delivery-for-all-formats}

當Adobe Campaign根據網域動態管理格式（電子郵件格式定義為&#x200B;**[!UICONTROL Unknown]**、**[!UICONTROL HTML]**&#x200B;或&#x200B;**[!UICONTROL Text]**&#x200B;的描述檔）時，您可以傳送相同的傳送給所有收件者。

訊息連絡人會正確顯示給日文行動裝置上的使用者，就像標準收件者一樣。

>[!IMPORTANT]
>
>請務必遵守與每種日文電子郵件格式（裝飾郵件、裝飾郵件和廣告郵件）相關的特殊功能。 有關限制的詳細資訊，請參閱[本節](#limitations-and-recommendations)。
