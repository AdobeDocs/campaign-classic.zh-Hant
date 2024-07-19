---
product: campaign
title: 傳送、監控和追蹤簡訊
description: 瞭解如何在Campaign傳送、監控和追蹤簡訊
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 3%

---

# 傳送、監控和追蹤簡訊傳遞{#sms-properties}

## 傳送簡訊訊息 {#sending-sms-messages}

若要核准您的郵件並傳送給所建立傳遞的收件者，請按一下&#x200B;**[!UICONTROL Send]**。

驗證和傳送傳送時的詳細程式會顯示在下列章節中：

* [驗證傳遞](steps-validating-the-delivery.md)
* [傳送傳遞](steps-sending-the-delivery.md)

## 高級參數 {#advanced-parameters}

**[!UICONTROL Properties]**&#x200B;按鈕可讓您存取進階傳遞引數。 簡訊傳遞的特定引數位於&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤的&#x200B;**[!UICONTROL SMS parameters]**&#x200B;區段。

可以使用以下選項：

* **寄件者地址**：可讓您使用限製為11個字元的英數字元字串，個人化傳送寄件者的名稱。 欄位不可僅由數字組成。 您可以定義要顯示的條件，例如根據收件者的區碼顯示不同的名稱：

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >檢查您所在國家/地區有關編輯寄件者名稱的法律。 您也應洽詢您的操作員，瞭解他們是否提供此功能。

* **傳輸模式**：由SMS傳送訊息。
* **優先順序**：指派給訊息的重要等級。 預設會選取&#x200B;**[!UICONTROL Normal]**&#x200B;優先順序。 詢問您的服務提供者有關以&#x200B;**[!UICONTROL High]**&#x200B;優先順序傳送的SMS費用。
* **應用程式型別**：選擇您要指派給SMS傳遞的應用程式。 預設會選取&#x200B;**[!UICONTROL Direct Marketing]**&#x200B;選項，並且是最常用的選項。

**NetSize聯結器專屬的引數**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **單一訊息使用數個SMS**：這可讓您透過數個SMS訊息傳送長度超過160個字元的訊息。

**SMPP聯結器專屬的引數**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每則訊息的SMS數目上限**：此選項可讓您設定用於傳送訊息的SMS數目。 如果數字設為0，您可以使用簡訊傳送訊息。 舉例來說，如果SMS數量設為1或2，而訊息超過此臨界值，則不會傳送。

## 監視和追蹤簡訊 {#monitoring-and-tracking-sms-deliveries}

傳送訊息後，您可以監視和追蹤您的傳遞。 如需詳細資訊，請參閱下列區段。

* [監視傳遞](about-delivery-monitoring.md)
* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [關於訊息追蹤](about-message-tracking.md)

## 處理傳入訊息 {#processing-inbound-messages}

**nlserver sms**&#x200B;模組會定期查詢SMS路由器。 這可讓Adobe Campaign追蹤傳遞進度，並處理狀態報表和收件者取消訂閱請求。

* **狀態報告**：檢視傳遞記錄檔以檢查訊息的狀態。

  >[!NOTE]
  >
  >每封傳送的簡訊都會連結至其主索引鍵的外部帳戶。 以此方式：
  >
  > * 來自已刪除外部SMS帳戶的狀態報表無法正確處理。
  > * SMS帳戶只能連結至單一外部帳戶，以確保狀態報表已歸因到正確的帳戶

* **取消訂閱**：希望停止接收簡訊傳遞的收件者可以傳回包含STOP字樣的訊息。 如果您的提供者根據合約條款允許，您可以透過&#x200B;**傳入簡訊**&#x200B;工作流程活動擷取訊息，然後建立查詢以啟用相關收件者的&#x200B;**不再連絡此收件者**&#x200B;選項。

  請參閱[工作流程](../../workflow/using/architecture.md)指南。

## InSMS結構描述 {#insms-schema}

InSMS結構描述包含與傳入SMS相關的資訊。 這些欄位的說明可透過desc屬性取得。

* **訊息**：已接收SMS的內容。
* **來源**：訊息來源的行動電話號碼。
* **providerId**： SMSC （訊息中心）傳回的訊息識別碼。
* **已建立**：將傳入訊息插入Adobe Campaign的日期。
* **extAccount**： Adobe Campaign外部帳戶。

  >[!IMPORTANT]
  >
  >下列欄位是NetSize專屬欄位。
  >
  >如果使用的運運算元不是NetSize，則這些欄位會視為空白。

* **別名**：傳入訊息的別名。
* **分隔符號**：郵件別名和內文之間的分隔符號。
* **messageDate**：操作員提供的訊息日期。
* **receivalDate**： SMSC （訊息中心）收到來自操作員的訊息日期。
* **deliveryDate**：由SMSC （訊息中心）傳送的日期訊息。
* **largeAccount**：連結到傳入SMS的客戶帳戶代碼。
* **國家/地區代碼**：運運算元國家/地區代碼。
* **operatorCode**：操作員網路代碼。
* **linkedSmsId**：連結至傳出SMS的Adobe Campaign識別碼(broadlogId)，其中此SMS為回應。

## 管理自動回覆（美國法規） {#managing-automatic-replies--american-regulation-}

當訂閱者回覆透過Adobe Campaign傳送給他們的簡訊訊息，並使用關鍵字（例如STOP、HELP或YES）時，在美國市場，必須設定自動傳回的訊息。

例如，如果收件者傳送關鍵字STOP，他們會自動收到一則確認訊息，指出他們已取消訂閱。

此類訊息的寄件者名稱是用來傳送傳遞的簡短代碼。

>[!IMPORTANT]
>
>以下詳細程式僅對SMPP聯結器有效，擴展通用SMPP聯結器除外。 如需詳細資訊，請參閱[建立SMPP外部帳戶](sms-set-up.md#creating-an-smpp-external-account)區段。
>
>它構成美國營運商針對美國行銷活動所執行的認證程式的一部分。 這些對訂閱者SMS訊息的回覆（包含關鍵字）必須在收到訂閱者的訊息後立即傳回給訂閱者。

1. 建立此型別的XML檔案：

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

1. 針對&#x200B;**`<shortcode>`**&#x200B;標籤的&#x200B;**name**&#x200B;屬性，指定將顯示在郵件寄件者名稱位置的簡短代碼。

   在每個&#x200B;**`<reply>`**&#x200B;標籤中，輸入具有關鍵字的&#x200B;**關鍵字**&#x200B;屬性，以及包含您要為此關鍵字傳送之訊息的&#x200B;**文字**&#x200B;屬性。

   >[!NOTE]
   >
   >每個關鍵字都必須以大寫字母書寫。

   如果要為多個關鍵字傳送相同的訊息，請複製對應的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成之後，以名稱&#x200B;**smsAutoReply.xml**&#x200B;儲存此檔案。

   請注意，檔案名稱在Linux中區分大小寫。

1. 將此檔案複製到Adobe Campaign中的&#x200B;**conf**&#x200B;目錄中，與Web伺服器位於相同位置。

>[!IMPORTANT]
>
>這些型別的自動訊息不會保留歷史記錄。 因此，它們不會出現在傳送控制面板中。 [了解更多](delivery-dashboard.md)。
>
>商業壓力規則不會考慮這些訊息。 [了解更多](../../campaign-opt/using/pressure-rules.md)。
