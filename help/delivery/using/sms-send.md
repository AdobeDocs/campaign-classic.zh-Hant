---
solution: Campaign Classic
product: campaign
title: 傳送、監控及追蹤簡訊
description: 瞭解如何在Campaign中傳送、監控及追蹤SMS
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 2%

---


# 傳送、監控及追蹤SMS傳送{#sms-properties}

## 傳送SMS訊息{#sending-sms-messages}

若要核准訊息並傳送給所建立之傳送的收件者，請按一下&#x200B;**[!UICONTROL Send]**。

驗證和傳送傳送時的詳細程式會列於以下各節：

* [驗證傳送](../../delivery/using/steps-validating-the-delivery.md)
* [傳送傳送](../../delivery/using/steps-sending-the-delivery.md)

## 高級參數 {#advanced-parameters}

**[!UICONTROL Properties]**&#x200B;按鈕可讓您存取進階傳送參數。 SMS傳送的特定參數位於&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤的&#x200B;**[!UICONTROL SMS parameters]**&#x200B;區段中。

可以使用以下選項：

* **發件人地址**:可讓您使用字母數字字元字串（以十一個字元為限），個人化傳送者的名稱。該欄位不能只由數字組成。 您可以定義條件，例如根據收件者的區域代碼顯示不同的名稱：

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >檢查您所在國家／地區有關編輯傳送者名稱的法律。 您也應洽詢您的營運商，看他們是否提供此功能。

* **傳輸模式**:通過SMS進行消息傳輸。
* **優先順序**:指派給訊息的重要程度。**[!UICONTROL Normal]** 優先順序預設為選取。請洽詢您的服務供應商有關以&#x200B;**[!UICONTROL High]**&#x200B;優先順序傳送之簡訊的成本。
* **應用程式類型**:選擇您要指派給SMS傳送的應用程式。預設會選取&#x200B;**[!UICONTROL Direct Marketing]**&#x200B;選項，是最常用的選項。

**NetSize連接器的特定參數**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **針對單一訊息使用數種簡訊**:這可讓您透過數條簡訊傳送超過160個字元的訊息。

**SMPP連接器的特定參數**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每則訊息的SMS最大數量**:此選項可讓您設定用來傳送訊息的SMS數目。如果數字設為0，您可以使用SMS來傳送訊息。 例如，如果SMS的數目設為1或2，而訊息超過此臨界值，則不會傳送。

## 監視和跟蹤SMS {#monitoring-and-tracking-sms-deliveries}

傳送訊息後，您可以監控及追蹤傳送內容。 如需詳細資訊，請參閱下列區段。

* [監控傳送](../../delivery/using/about-delivery-monitoring.md)
* [瞭解交付失敗](../../delivery/using/understanding-delivery-failures.md)
* [關於訊息追蹤](../../delivery/using/about-message-tracking.md)

## 處理入站消息{#processing-inbound-messages}

**nlserver sms**&#x200B;模組以定期間隔查詢SMS路由器。 這可讓Adobe Campaign追蹤傳送進度，並處理狀態報告和收件者取消訂閱的要求。

* **狀態報告**:檢視傳送記錄，以檢查訊息的狀態。

   >[!NOTE]
   >
   >每個傳送的簡訊都會連結至其主要金鑰的外部帳戶。 這樣：
   >
   > * 已刪除外部SMS帳戶的狀態報告無法正確處理。
   > * SMS帳戶只能連結至單一外部帳戶，以確保狀態報表歸屬於正確的帳戶


* **取消訂閱**:希望停止接收SMS傳送的收件者可傳回包含STOP字詞的訊息。如果您的提供者根據合約條款允許留言，您可以透過&#x200B;**傳入SMS**&#x200B;工作流程活動擷取訊息，然後建立查詢以啟用&#x200B;**不再為相關收件者連絡此收件者**&#x200B;選項。

   請參閱[Workflows](../../workflow/using/architecture.md)指南。

## InSMS架構{#insms-schema}

InSMS架構包含與傳入SMS相關的資訊。 這些欄位的說明可透過desc屬性取得。

* **訊息**:收到的簡訊內容。
* **來源**:訊息來源的行動電話號碼。
* **providerId**:SMSC（消息中心）返回的消息的標識符。
* **已建立**:日期傳入消息被插入Adobe Campaign。
* **extAccount**:Adobe Campaign外部帳戶。

   >[!IMPORTANT]
   >
   >以下欄位是NetSize專用的。
   >
   >如果使用中的運算子不是NetSize，則這些欄位會視為空白。

* **別名**:傳入消息的別名。
* **分隔符**:別名和消息正文之間的分隔符。
* **messageDate**:運算子提供的訊息日期。
* **receivalDate**:SMSC（消息中心）收到來自操作員的日期消息。
* **deliveryDate**:由SMSC（消息中心）發送的日期消息。
* **largeAccount**:連結至傳入SMS的客戶帳戶代碼。
* **countryCode**:營運商國家／地區代碼。
* **operatorCode**:營運商網路程式碼。
* **linkedSmsId**:Adobe Campaign識別碼(broadlogId)，連結至傳出的SMS，而此SMS是回應。

## 管理自動回覆（美國法規）{#managing-automatic-replies--american-regulation-}

當訂閱者回覆透過Adobe Campaign傳送給他們的SMS訊息，並使用STOP、HELP或YES等關鍵字時，在美國市場，必須設定自動傳回的訊息。

例如，如果收件者傳送關鍵字STOP，他們會自動收到確認訊息，指出他們已取消訂閱。

此類型訊息的傳送者名稱是用來傳送傳送訊息的簡短代碼。

>[!IMPORTANT]
>
>以下詳細過程僅對SMPP連接器有效，擴展的通用SMPP連接器除外。 有關詳細資訊，請參閱[建立SMPP外部帳戶](sms-set-up.md#creating-an-smpp-external-account)部分。
>
>它是美國營運商在美國進行行銷宣傳的認證程式的一部分。 這些對包含關鍵字的訂戶SMS消息的回覆必須在收到來自他們的消息後立即傳回給訂戶。

1. 建立此類型的XML檔案：

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. 對於&#x200B;**`<shortcode>`**&#x200B;標籤的&#x200B;**name**&#x200B;屬性，指定將顯示在消息發送者名稱位置的短代碼。

   在每個&#x200B;**`<reply>`**&#x200B;標籤中，輸入包含關鍵字的&#x200B;**keyword**&#x200B;屬性，以及包含您要為此關鍵字傳送訊息的&#x200B;**text**&#x200B;屬性。

   >[!NOTE]
   >
   >每個關鍵字都必須以大寫字母寫入。

   如果您想要傳送多個關鍵字的相同訊息，請複製對應的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成後，請以&#x200B;**smsAutoReply.xml**&#x200B;的名稱儲存此檔案。

   請注意，在Linux中，檔案名稱區分大小寫。

1. 將此檔案複製到Adobe Campaign的&#x200B;**conf**&#x200B;目錄，與Web伺服器位於同一位置。

>[!IMPORTANT]
>
>這類自動訊息不會保留歷史記錄。 因此，它們不會出現在傳送控制面板中。 [進一步瞭解](../../delivery/using/delivery-dashboard.md)。
>
>商業壓力規則沒有考慮這些資訊。 [進一步瞭解](../../campaign/using/pressure-rules.md)。
