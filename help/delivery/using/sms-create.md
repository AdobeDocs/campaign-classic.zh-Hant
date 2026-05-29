---
product: campaign
title: 使用Campaign建立簡訊
description: 瞭解如何使用Campaign建立簡訊
feature: SMS
role: User
hide: true
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
TQID: https://experienceleague.adobe.com/ENt9cwc7OjXcMr5tbkg2f3BxpPBNtVytVTw70NQZPyI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 465
ht-degree: 3%

---

# 建立簡訊傳送 {#creating-a-sms-delivery}

## 選取傳遞管道 {#selecting-the-delivery-channel}

若要建立新的SMS傳送，請遵循下列步驟：

>[!NOTE]
>
>在[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant){target="_blank"}中介紹了傳遞建立的全域概念。

1. 例如，從「傳遞」控制面板建立新傳遞。
1. 選取您先前建立的傳遞範本&#x200B;**傳送至行動裝置(SMPP)**。 如需詳細資訊，請參閱[變更傳遞範本](sms-set-up.md#changing-the-delivery-template)區段。

   ![](assets/s_user_mobile_wizard.png)

1. 使用標籤、程式碼和說明來識別您的傳遞。 如需詳細資訊，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#create-the-delivery){target="_blank"}中的本節。
1. 按一下&#x200B;**[!UICONTROL Continue]**&#x200B;以確認此資訊並顯示訊息設定視窗。

## 定義簡訊內容 {#defining-the-sms-content}

若要建立SMS的內容，請遵循下列步驟：

1. 在助理員的&#x200B;**[!UICONTROL Text content]**&#x200B;區段中輸入訊息的內容。 工具列按鈕可讓您匯入、儲存或搜尋內容。 最後一個按鈕用於插入個人化欄位。

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   個人化欄位的使用顯示在[關於個人化](about-personalization.md)區段。

1. 按一下頁面底部的&#x200B;**[!UICONTROL Preview]**&#x200B;以檢視訊息的呈現及其個人化。 若要啟動預覽，請使用工具列中的&#x200B;**[!UICONTROL Test personalization]**&#x200B;按鈕選取收件者。 您可以從定義的目標中選取收件者或選擇其他收件者。

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   您可以核准SMS訊息。 您也可以在內容編輯器右側顯示的行動電話熒幕上檢視SMS的內容。 按一下熒幕，然後使用滑鼠捲動內容。

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 按一下&#x200B;**[!UICONTROL Data loaded]**&#x200B;連結以檢視收件者的相關資訊。

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >若使用Latin-1 (ISO-8859-1)字碼頁，SMS訊息的長度上限為160個字元。 如果訊息是以Unicode撰寫，則不可超過70個字元。 某些特殊字元可能會影響訊息長度。 如需訊息長度的詳細資訊，請參閱[簡訊字母音譯](#about-character-transliteration)區段。
   >
   >當出現個人化欄位或條件內容欄位時，訊息的大小會因收件者而異。 進行個人化時，必須評估訊息的長度。
   >
   >當您啟動分析時，會檢查訊息的長度，並在溢位事件中顯示警告。

1. 如果您使用NetSize聯結器或SMPP聯結器，則可以個人化傳送寄件者的名稱。 如需詳細資訊，請參閱[進階引數](#advanced-parameters)區段。

## 選取目標母體 {#selecting-the-target-population}

選取傳遞的目標母體時的詳細程式會顯示在[本節](steps-defining-the-target-population.md)中。

如需使用個人化欄位的詳細資訊，請參閱[本區段](about-personalization.md)。

如需包含種子清單的詳細資訊，請參閱[此頁面](about-seed-addresses.md)。
