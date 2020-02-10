---
title: 發佈Web表格
seo-title: 發佈Web表格
description: 發佈Web表格
seo-description: null
page-status-flag: never-activated
uuid: 37222829-1d56-438c-a4ca-878925debcb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: f4322902-c72d-4443-9c30-09add4c615a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 發佈Web表格{#publishing-a-web-form}

## 預先載入表單資料 {#pre-loading-the-form-data}

如果希望通過Web表單更新儲存在資料庫中的配置檔案，可使用預載框。 通過預載入框，可以指明如何查找要在資料庫中更新的記錄。

可採用下列識別方法：

* **[!UICONTROL Adobe Campaign Encryption]**

   此加密方法使用加密的Adobe Campaign識別碼(ID)。 此方法僅適用於Adobe Campaign物件，且加密的ID只能由Adobe Campaign平台產生。

   使用此方法時，您需要調整表單的URL，以新增參數來傳送至電子郵件 **`<%=escapeUrl(recipient.cryptedId) %>`** 地址。 如需詳細資訊，請參閱「透 [過電子郵件傳送表格」](#delivering-a-form-via-email)。

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   此加密方法使用外部提供的識別碼(ID)，此識別碼會連結至Adobe Campaign和外部提供者共用的金鑰。 欄位 **[!UICONTROL Des key]** 可讓您輸入此加密金鑰。

* **[!UICONTROL List of fields]**

   此選項可讓您從表單目前內容中的欄位中選擇，這些欄位將用於在資料庫中尋找對應的描述檔。

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   欄位可透過標籤新增至表單屬 **[!UICONTROL Parameters]** 性(請參 [閱新增參數](../../web/using/defining-web-forms-properties.md#adding-parameters))。 它們以URL或輸入區域的形式放置。

   >[!CAUTION]
   >
   >選取欄位中的資料不會加密。 它不得以加密的形式提供，因為如果選取該選項，Adobe Campaign將無法 **[!UICONTROL Field list]** 解密。

   在下列範例中，描述檔預先載入是以電子郵件地址為基礎。

   URL可包含未加密的電子郵件地址，在此情況下，使用者可直接存取其相關頁面。

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   否則，系統會要求他們輸入密碼。

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >如果在清單中指定了多個欄位，則 **ALL FIELDS** （所有欄位）的資料必須與資料庫中儲存的資料匹配，以便更新配置檔案。 否則，將建立新配置檔案。
   > 
   >此函式對Web應用程式特別有用，但不建議用於公開表單。 選定的訪問控制選項必須是「啟用訪問控制」。

如 **[!UICONTROL Skip preloading if identification is empty]** 果您不想更新配置式，則必須選擇該選項。 在這種情況下，在批准表單後，輸入的每個配置檔案都將添加到資料庫中。 例如，當表單張貼在網站上時，就會使用這個選項。

選 **[!UICONTROL Auto-load data referenced in the form]** 項可讓您自動預先載入符合表單中輸入和合併欄位的資料。 但是，與活動中參 **[!UICONTROL Script]** 考的 **[!UICONTROL Test]** 資料並不相關。 如果未選取此選項，您必須使用選項來定義欄 **[!UICONTROL Load additional data]** 位。

選 **[!UICONTROL Load additional data]** 項可讓您新增未用於表單頁面但仍會預先載入的資訊。

例如，您可以預先載入收件者的性別，並透過測試方塊自動將其導向至適當的頁面。

![](assets/s_ncs_admin_survey_preload_ex.png)

## 管理Web表單傳送和追蹤 {#managing-web-forms-delivery-and-tracking}

建立、設定和發佈表單後，您就可以傳送並追蹤使用者回應。

### 表單的生命週期 {#life-cycle-of-a-form}

表單生命週期有三個階段：

1. **正在編輯的表單**

   這是初始設計階段。 建立新表單時，它正處於編輯階段。 存取表單（僅供測試之用）時，會要求 **[!UICONTROL __uuid]** 在其URL中使用參數。 此URL可在子標籤 **[!UICONTROL Preview]** 中存取。 請參 [閱表單URL參數](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

   >[!CAUTION]
   >
   >只要正在編輯表單，其存取URL就是特殊的URL。

1. **線上表單**

   設計階段完成後，就可傳送表格。 首先，它需要發佈。 如需詳細資訊，請參閱「發 [布表格」](#publishing-a-form)。

   表單將一直到 **[!UICONTROL Live]** 過期為止。

   >[!CAUTION]
   >
   >若要傳送，調查的URL不得包含參 **[!UICONTROL __uuid]** 數。

1. **表單無法使用**

   表單關閉後，傳送階段即告結束，表單將無法使用：使用者無法再存取。

   到期日可在表單屬性視窗中定義。 有關詳情，請參閱「 [Making a form available online（聯機提供表單）」](#making-a-form-available-online)

表單的發佈狀態顯示在表單清單中。

![](assets/s_ncs_admin_survey_status.png)

### 發佈表格 {#publishing-a-form}

若要變更表單的狀態，您必須發佈表單。 若要這麼做，請按一 **[!UICONTROL Publication]** 下Web表格清單上方的按鈕，然後在下拉式方塊中選取狀態。

![](assets/webapp_publish_webform.png)

### 線上提供表單 {#making-a-form-available-online}

若要讓使用者存取，表單必須在生產中並開始，即在有效期內。 有效日期是透過表單 **[!UICONTROL Properties]** 的連結輸入。

* 使用區段中的 **[!UICONTROL Project]** 欄位輸入表單的開始和結束日期。

   ![](assets/webapp_availability_date.png)

* 按一 **[!UICONTROL Personalize the message displayed if the form is closed...]** 下連結，以定義當使用者嘗試存取表單無效時要顯示的錯誤訊息。

   請參 [閱表單的協助功能](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form)。

### 透過電子郵件傳送表格 {#delivering-a-form-via-email}

當您透過電子郵件傳送邀請時，可以使用資 **[!UICONTROL Adobe Campaign Encryption]** 料協調選項。 若要這麼做，請前往傳送精靈，並新增下列參數，將連結調整為表格：

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

在這種情況下，資料儲存的協調密鑰必須是收件人的加密標識符。 如需詳細資訊，請參 [閱預先載入表單資料](#pre-loading-the-form-data)。

在這種情況下，您必須勾選記 **[!UICONTROL Update the preloaded record]** 錄方塊中的選項。 如需詳細資訊，請參閱「儲 [存Web表格答案」](../../web/using/web-forms-answers.md#saving-web-forms-answers)。

![](assets/s_ncs_admin_survey_save_box_option.png)

### 記錄回應 {#log-responses}

您可以在專用標籤中啟動回應追蹤，以監控Web表單的影響。 要執行此操作，請按一下表 **[!UICONTROL Advanced parameters...]** 單屬性窗口中的連結，然後選擇 **[!UICONTROL Log responses]** 選項。

![](assets/s_ncs_admin_survey_trace.png)

此標 **[!UICONTROL Responses]** 簽可讓您檢視回應者的身分。

![](assets/s_ncs_admin_survey_trace_tab.png)

選取收件者，然後按一下按 **[!UICONTROL Detail...]** 鈕以檢視所提供的回應。

![](assets/s_ncs_admin_survey_trace_edit.png)

您可以處理查詢中提供的回應記錄，例如，在傳送提醒時僅鎖定非回應者，或僅向回應者提供特定的通訊。

>[!NOTE]
>
>如需完整追蹤提供的回應，請匯出回應並檢視或建立專屬報表，請使用選用的「調查」 **模組** 。 如需詳細資訊，請參閱[本小節](../../web/using/about-surveys.md)。

