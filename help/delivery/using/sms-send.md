---
product: campaign
title: 發送、監視和跟蹤SMS
description: 瞭解如何在活動中發送、監控和跟蹤簡訊
feature: SMS
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 3%

---

# 發送、監視和跟蹤SMS遞送{#sms-properties}

![](../../assets/common.svg)

## 發送SMS消息 {#sending-sms-messages}

要批准您的郵件並將其發送到正在建立的傳遞的收件人，請按一下 **[!UICONTROL Send]**。

驗證和發送交貨時的詳細過程在以下各節中介紹：

* [驗證傳遞](steps-validating-the-delivery.md)
* [傳送傳遞](steps-sending-the-delivery.md)

## 高級參數 {#advanced-parameters}

的 **[!UICONTROL Properties]** 按鈕可訪問高級傳遞參數。 特定於SMS遞送的參數位於 **[!UICONTROL SMS parameters]** 的下界 **[!UICONTROL Delivery]** 頁籤。

可以使用以下選項：

* **發件人地址**:允許您使用一串字母數字字元（最多11個字元）來個性化遞送發件人的名稱。 欄位不能只由數字組成。 您可以定義一個條件來顯示，例如，根據收件人的區號顯示不同的名稱：

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >檢查您所在國家/地區有關編輯發件人姓名的法律。 您還應詢問運營商是否提供此功能。

* **傳輸模式**:簡訊發送
* **優先順序**:分配給消息的重要級別。 **[!UICONTROL Normal]** 預設情況下，優先順序處於選中狀態。 向服務提供商咨詢隨之發送的SMS的成本 **[!UICONTROL High]** 優先順序。
* **應用程式類型**:選擇要分配給SMS傳遞的應用程式。 的 **[!UICONTROL Direct Marketing]** 選項。

**特定於NetSize連接器的參數**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **對單條消息使用多條SMS**:這允許您通過多個SMS消息發送長達160個字元的消息。

**SMPP連接器特有的參數**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每條消息的最大SMS數**:此選項允許您設定用於發送消息的SMS數。 如果數字設定為0，則可以使用SMS來傳遞消息。 如果SMS的數量設定為1或2（例如），並且消息超過此閾值，則不會發送該消息。

## 監視和跟蹤SMS {#monitoring-and-tracking-sms-deliveries}

發送消息後，您可以監視和跟蹤交貨。 如需詳細資訊，請參閱下列區段。

* [監視傳遞](about-delivery-monitoring.md)
* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [關於訊息追蹤](about-message-tracking.md)

## 處理入站消息 {#processing-inbound-messages}

的 **nlserver sms** 模組定期查詢SMS路由器。 這使Adobe Campaign能夠跟蹤交貨進度並處理狀態報告和收件人取消訂閱請求。

* **狀態報告**:查看傳遞日誌以檢查郵件的狀態。

   >[!NOTE]
   >
   >發送的每條SMS都連結到其主鍵的外部帳戶。 這樣：
   >
   > * 未正確處理來自已刪除外部SMS帳戶的狀態報告。
   > * SMS帳戶只能連結到單個外部帳戶，以確保狀態報告歸屬於正確的帳戶


* **取消訂閱**:希望停止接收SMS遞送的收件人可以返回包含STOP一詞的消息。 如果您的提供商根據合同條款允許它訪問，您可以通過 **入站SMS** 工作流活動，然後建立查詢以啟用 **不再聯繫此收件人** 的子菜單。

   請參閱 [工作流](../../workflow/using/architecture.md) 的子菜單。

## InSMS架構 {#insms-schema}

InSMS架構包含與傳入的SMS相關的資訊。 通過desc屬性可獲得這些欄位的說明。

* **消息**:收到的簡訊內容。
* **來源**:消息源處的移動號碼。
* **提供程式ID**:SMSC（消息中心）返回的消息的標識符。
* **建立**:日期傳入消息插入Adobe Campaign。
* **ext帳戶**:Adobe Campaign外部帳戶。

   >[!IMPORTANT]
   >
   >以下欄位特定於NetSize。
   >
   >如果使用的運算子不是NetSize，則這些欄位被視為空。

* **別名**:傳入消息的別名。
* **分離器**:別名和消息正文之間的分隔符。
* **消息日期**:由運算子提供的消息日期。
* **接收日期**:SMSC（消息中心）接收來自操作員的日期消息。
* **交貨日期**:SMSC（消息中心）發送的日期消息。
* **大型帳戶**:連結到傳入SMS的客戶帳戶代碼
* **國家代碼**:操作員國家/地區代碼。
* **運算子代碼**:操作員網路代碼。
* **連結的SmsId**:Adobe Campaign標識符(broadlogId)連結到傳出SMS，其中此SMS是響應。

## 管理自動答復（美國法規） {#managing-automatic-replies--american-regulation-}

當訂閱者回復通過Adobe Campaign發送給他們的SMS消息，並且使用STOP 、 HELP或YES等關鍵字時，在美國市場，有必要配置自動返回的消息。

例如，如果收件人發送關鍵字STOP ，則他們會自動收到確認消息，指出他們已取消訂閱。

此類郵件的發件人名稱是通常用於發送遞送的簡短代碼。

>[!IMPORTANT]
>
>以下詳細過程僅對SMPP連接器有效，擴展通用SMPP連接器除外。 有關詳細資訊，請參閱 [建立SMPP外部帳戶](sms-set-up.md#creating-an-smpp-external-account) 的子菜單。
>
>它是美國運營商在美國開展營銷活動的認證過程的一部分。 這些對包含關鍵字的訂戶SMS消息的回復必須在收到來自它們的消息後立即發回給訂戶。

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

1. 對於 **名稱** 屬性 **`<shortcode>`** 標籤，指定將顯示在消息發件人名稱位置的短代碼。

   每個 **`<reply>`** 標籤，輸入 **關鍵字** 帶關鍵字的屬性和 **文本** 屬性。

   >[!NOTE]
   >
   >每個關鍵字必須用大寫字母寫。

   如果要為多個關鍵字發送相同的消息，請複製相應的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成後，以名稱保存此檔案 **sms自動回復.xml**。

   請注意，在Linux中，檔案名區分大小寫。

1. 將此檔案複製到 **會議** 目錄，位於Web伺服器的同一位置。

>[!IMPORTANT]
>
>這類自動消息不會保留歷史記錄。 因此，它們不會出現在交貨儀表板中。 [了解更多](delivery-dashboard.md)。
>
>這些資訊在商業壓力規則中沒有考慮。 [了解更多](../../campaign-opt/using/pressure-rules.md)。
