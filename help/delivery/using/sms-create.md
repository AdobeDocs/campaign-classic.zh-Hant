---
product: campaign
title: 使用Campaign建立簡訊
description: 瞭解如何使用Campaign建立簡訊
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: SMS
role: User
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# 建立簡訊傳遞 {#creating-a-sms-delivery}

## 選取傳遞管道 {#selecting-the-delivery-channel}

若要建立新的SMS傳送，請遵循下列步驟：

>[!NOTE]
>
>有關傳遞建立的全域概念，請參見 [本節](steps-about-delivery-creation-steps.md).

1. 例如，從「傳遞」控制面板建立新傳遞。
1. 選取傳遞範本 **傳送至行動裝置(SMPP)** 您先前建立的。 有關詳細資訊，請參閱 [變更傳遞範本](sms-set-up.md#changing-the-delivery-template) 區段。

   ![](assets/s_user_mobile_wizard.png)

1. 使用標籤、程式碼和說明來識別您的傳遞。 如需詳細資訊，請參閱[本章節](steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 按一下 **[!UICONTROL Continue]** 以確認此資訊並顯示訊息組態視窗。

## 定義簡訊內容 {#defining-the-sms-content}

若要建立SMS的內容，請遵循下列步驟：

1. 請在以下位置輸入訊息的內容： **[!UICONTROL Text content]** 區段。 工具列按鈕可讓您匯入、儲存或搜尋內容。 最後一個按鈕用於插入個人化欄位。

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   個人化欄位的使用方式顯示在中 [關於個人化](about-personalization.md) 區段。

1. 按一下 **[!UICONTROL Preview]** 在頁面底部，檢視訊息的呈現及其個人化。 若要啟動預覽，請使用 **[!UICONTROL Test personalization]** 按鈕。 您可以從定義的目標中選取收件者或選擇其他收件者。

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   您可以核准SMS訊息。 您也可以在內容編輯器右側顯示的行動電話熒幕上檢視SMS的內容。 按一下熒幕，然後使用滑鼠捲動內容。

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 按一下 **[!UICONTROL Data loaded]** 檢視收件者相關資訊的連結。

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >若使用Latin-1 (ISO-8859-1)字碼頁，SMS訊息的長度上限為160個字元。 如果訊息是以Unicode撰寫，則不可超過70個字元。 某些特殊字元可能會影響訊息長度。 如需訊息長度的詳細資訊，請參閱 [簡訊字母音譯](#about-character-transliteration) 區段。
   >
   >當出現個人化欄位或條件內容欄位時，訊息的大小會因收件者而異。 進行個人化時，必須評估訊息的長度。
   >
   >當您啟動分析時，會檢查訊息的長度，並在溢位事件中顯示警告。

1. 如果您使用NetSize聯結器或SMPP聯結器，則可以個人化傳送寄件者的名稱。 有關詳細資訊，請參閱 [進階引數](#advanced-parameters) 區段。

## 選取目標母體 {#selecting-the-target-population}

選擇傳送的目標母體時的詳細程式會顯示在中 [本節](steps-defining-the-target-population.md).

有關個人化欄位使用的詳細資訊，請參閱 [本節](about-personalization.md).

有關包含種子清單的詳細資訊，請參閱 [此頁面](about-seed-addresses.md).
