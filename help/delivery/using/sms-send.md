---
product: campaign
title: 傳送、監視及追蹤簡訊
description: 了解如何在Campaign中傳送、監視及追蹤簡訊
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 3%

---

# 傳送、監視及追蹤SMS傳送{#sms-properties}

## 發送SMS消息{#sending-sms-messages}

若要核准您的訊息，並將其傳送給所建立傳送的收件者，請按一下&#x200B;**[!UICONTROL Send]**。

驗證和傳送傳遞的詳細程式會顯示在以下章節：

* [驗證傳遞](../../delivery/using/steps-validating-the-delivery.md)
* [傳送傳遞](../../delivery/using/steps-sending-the-delivery.md)

## 進階參數 {#advanced-parameters}

**[!UICONTROL Properties]**&#x200B;按鈕可提供進階傳送參數的存取權。 SMS傳送的特定參數位於&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤的&#x200B;**[!UICONTROL SMS parameters]**&#x200B;區段中。

可以使用以下選項：

* **寄件者地址**:可讓您使用字串以十一個字元為上限的英數字元，個人化傳送者的名稱。欄位不能只由數字組成。 您可以定義一個條件，以根據收件者的區域代碼顯示不同的名稱：

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >檢查您所在國家/地區有關編輯寄件者名稱的法律。 您也應洽詢運算子，確定它們是否提供此功能。

* **傳輸模式**:簡訊傳輸
* **優先順序**:指派給訊息的重要性層級。**[!UICONTROL Normal]** 預設會選取優先順序。向服務提供商詢問與&#x200B;**[!UICONTROL High]**&#x200B;優先順序一起發送的簡訊的成本。
* **應用程式類型**:選擇您要指派給SMS傳送的應用程式。預設會選取&#x200B;**[!UICONTROL Direct Marketing]**&#x200B;選項，這是最常用的選項。

**NetSize連接器的特定參數**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **對單一訊息使用數個簡訊**:這可讓您透過數個SMS訊息，傳送超過160個字元的訊息。

**SMPP連接器專用參數**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每條訊息的SMS最大數量**:此選項可讓您設定用於傳送訊息的SMS數量。如果數字設為0，您可以使用SMS來傳送訊息。 如果例項的SMS數量設為1或2，而訊息超過此臨界值，則不會傳送訊息。

## 監視和追蹤SMS {#monitoring-and-tracking-sms-deliveries}

傳送訊息後，您可以監控及追蹤您的傳送。 如需詳細資訊，請參閱下列區段。

* [監視傳遞](../../delivery/using/about-delivery-monitoring.md)
* [瞭解傳遞失敗](../../delivery/using/understanding-delivery-failures.md)
* [關於訊息追蹤](../../delivery/using/about-message-tracking.md)

## 處理傳入消息{#processing-inbound-messages}

**nlserver sms**&#x200B;模組定期查詢SMS路由器。 這可讓Adobe Campaign追蹤傳送進度，並處理狀態報表和收件者取消訂閱請求。

* **狀態報表**:檢視傳送記錄，以檢查訊息的狀態。

   >[!NOTE]
   >
   >每個傳送的SMS都會連結至其主要金鑰的外部帳戶。 以這種方式：
   >
   > * 已刪除外部SMS帳戶的狀態報表無法正確處理。
   > * SMS帳戶只能連結至單一外部帳戶，以確保狀態報表可歸屬於正確的帳戶


* **取消訂閱**:想要停止接收SMS傳送的收件者可傳回包含STOP字詞的訊息。如果您的提供者根據合約條款允許它，您可以透過&#x200B;**傳入SMS**&#x200B;工作流程活動擷取訊息，然後建立查詢以啟用&#x200B;**不再聯絡相關收件者的此收件者**&#x200B;選項。

   請參閱[工作流程](../../workflow/using/architecture.md)指南。

## InSMS架構{#insms-schema}

InSMS架構包含與傳入SMS相關的資訊。 可透過desc屬性取得這些欄位的說明。

* **訊息**:收到的簡訊內容。
* **來源**:訊息來源的行動電話號碼。
* **providerId**:SMSC（消息中心）返回的消息的標識符。
* **已建立**:日期傳入訊息已插入Adobe Campaign。
* **extAccount**:Adobe Campaign外部帳戶。

   >[!IMPORTANT]
   >
   >以下欄位是NetSize專用欄位。
   >
   >如果使用的運算子不是NetSize，則這些欄位被視為空。

* **別名**:傳入消息的別名。
* **分隔符**:別名和訊息內文之間的分隔符號。
* **messageDate**:由運算子提供的訊息日期。
* **receivalDate**:SMSC（報文中心）接收了來自操作員的日期消息。
* **deliveryDate**:由SMSC（訊息中心）傳送的日期訊息。
* **largeAccount**:連結至傳入SMS的客戶帳戶代碼
* **countryCode**:運算元國家/地區代碼。
* **operatorCode**:操作員網路代碼。
* **linkedSmsId**:Adobe Campaign識別碼(broadlogId)連結至傳出的SMS，其中此SMS為回應。

## 管理自動答復（美國法規）{#managing-automatic-replies--american-regulation-}

當訂閱者回覆透過Adobe Campaign傳送給他們的SMS訊息，並使用STOP、HELP或YES等關鍵字時，在美國市場上必須設定自動傳回的訊息。

例如，如果收件者傳送關鍵字STOP，則會自動收到確認訊息，指出他們已取消訂閱。

此類型訊息的寄件者名稱是通常用於傳送傳遞的簡短代碼。

>[!IMPORTANT]
>
>下列詳細過程僅對SMPP連接器有效，但擴展通用SMPP連接器除外。 有關詳細資訊，請參閱[建立SMPP外部帳戶](sms-set-up.md#creating-an-smpp-external-account)區段。
>
>這是美國運營商在美國開展營銷活動的認證過程的一部分。 這些對包含關鍵字的訂閱者SMS消息的回復必須在收到來自他們的消息後立即發回給訂閱者。

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

1. 對於&#x200B;**`<shortcode>`**&#x200B;標籤的&#x200B;**name**&#x200B;屬性，指定將顯示在郵件發件人名稱位置的短代碼。

   在每個&#x200B;**`<reply>`**&#x200B;標籤中，輸入包含關鍵字的&#x200B;**keyword**&#x200B;屬性，以及包含要為此關鍵字發送的消息的&#x200B;**text**&#x200B;屬性。

   >[!NOTE]
   >
   >每個關鍵字都必須以大寫字母寫入。

   如果您想要針對數個關鍵字傳送相同訊息，請複製對應的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成後，以名稱&#x200B;**smsAutoReply.xml**&#x200B;儲存此檔案。

   請注意，在Linux中，檔案名稱須區分大小寫。

1. 將此檔案複製到Adobe Campaign中與Web伺服器相同的&#x200B;**conf**&#x200B;目錄。

>[!IMPORTANT]
>
>這類自動訊息不會保留歷史記錄。 因此，傳送控制面板中不會顯示這些字元。 [瞭解更多](../../delivery/using/delivery-dashboard.md)。
>
>商業壓力規則沒有考慮這些報文。 [瞭解更多](../../campaign/using/pressure-rules.md)。
