---
product: campaign
title: 使用Campaign建立簡訊
description: 了解如何使用Campaign建立簡訊
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 2%

---

# 建立簡訊傳遞 {#creating-a-sms-delivery}

![](../../assets/common.svg)

## 選取傳送通道 {#selecting-the-delivery-channel}

若要建立新的簡訊傳送，請遵循下列步驟：

>[!NOTE]
>
>傳遞建立的全域概念，在 [本節](steps-about-delivery-creation-steps.md).

1. 建立新傳送，例如從傳送控制面板。
1. 選取傳送範本 **傳送至行動裝置(SMPP)** 你之前建立的。 有關詳細資訊，請參閱 [變更傳遞範本](sms-set-up.md#changing-the-delivery-template) 區段。

   ![](assets/s_user_mobile_wizard.png)

1. 使用標籤、程式碼和說明來識別您的傳送。 如需詳細資訊，請參閱[本章節](steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 按一下 **[!UICONTROL Continue]** 確認此資訊並顯示消息配置窗口。

## 定義SMS內容 {#defining-the-sms-content}

若要建立簡訊內容，請遵循下列步驟：

1. 在 **[!UICONTROL Text content]** 的子句。 工具列按鈕可讓您匯入、儲存或搜尋內容。 最後一個按鈕用於插入個人化欄位。

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   個人化欄位的使用會顯示在 [關於個人化](about-personalization.md) 區段。

1. 按一下 **[!UICONTROL Preview]** 位於頁面底部，以檢視呈現訊息及其個人化內容。 若要啟動預覽，請使用 **[!UICONTROL Test personalization]** 按鈕。 您可以從定義的目標中選擇收件者，或選擇其他收件者。

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   您可以核准SMS訊息。 您也可以在內容編輯器右側顯示的行動電話畫面上檢視SMS內容。 按一下畫面，然後使用滑鼠捲動內容。

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 按一下 **[!UICONTROL Data loaded]** 連結以檢視收件者的相關資訊。

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >如果使用Latin-1(ISO-8859-1)代碼頁，SMS訊息的長度限制為160個字元。 如果訊息以Unicode寫入，則不得超過70個字元。 某些特殊字元會影響訊息長度。 如需訊息長度的詳細資訊，請參閱 [SMS字母音譯](#about-character-transliteration) 區段。
   >
   >當個人化欄位或條件式內容欄位存在時，訊息的大小會因收件者而異。 執行個人化時，必須評估訊息的長度。
   >
   >啟動分析時，會檢查消息的長度，並在溢出事件中顯示警告。

1. 如果您使用NetSize連接器或SMPP連接器，則可以個人化傳送者的名稱。 有關詳細資訊，請參閱 [進階參數](#advanced-parameters) 區段。

## 選取目標母體 {#selecting-the-target-population}

選取傳送的目標母體時的詳細程式會顯示在 [本節](steps-defining-the-target-population.md).

有關個人化欄位使用的詳細資訊，請參閱 [本節](about-personalization.md).

有關包含種子清單的詳細資訊，請參閱 [本頁](about-seed-addresses.md).
