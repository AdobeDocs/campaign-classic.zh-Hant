---
product: campaign
title: 發佈網路表單
description: 發佈網路表單
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 2%

---

# 發佈網路表單{#publishing-a-web-form}

## 預先載入表單資料{#pre-loading-the-form-data}

如果您想要透過Web表單更新儲存在資料庫中的設定檔，可以使用預先載入方塊。 預載框允許您指明如何查找要在資料庫中更新的記錄。

可採用下列識別方法：

* **[!UICONTROL Adobe Campaign Encryption]**

   此加密方法使用加密的Adobe Campaign識別碼(ID)。 此方法僅適用於Adobe Campaign物件，且加密的ID只能由Adobe Campaign平台產生。

   使用此方法時，您需要借由新增&#x200B;**`<%=escapeUrl(recipient.cryptedId) %>`**&#x200B;參數來調整表單的URL以傳遞至電子郵件地址。 如需詳細資訊，請參閱[透過電子郵件傳送表單](#delivering-a-form-via-email)。

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   此加密方法使用外部提供的識別碼(ID)，連結至Adobe Campaign和外部提供者共用的金鑰。 **[!UICONTROL Des key]**&#x200B;欄位允許您輸入此加密密鑰。

* **[!UICONTROL List of fields]**

   此選項可讓您從表單目前內容的欄位中進行選擇，這些欄位將用於在資料庫中尋找對應的設定檔。

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   欄位可透過&#x200B;**[!UICONTROL Parameters]**&#x200B;標籤新增至表單屬性（請參閱[新增參數](../../web/using/defining-web-forms-properties.md#adding-parameters)）。 它們會放在表單URL或輸入區域中。

   >[!CAUTION]
   >
   >所選欄位中的資料未加密。 不得以加密的形式提供，因為如果選取&#x200B;**[!UICONTROL Field list]**&#x200B;選項，Adobe Campaign將無法解密。

   在下列範例中，設定檔預先載入是根據電子郵件地址。

   URL可包含未加密的電子郵件地址，在此情況下，使用者可直接存取與其相關的頁面。

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   否則，將要求他們輸入密碼。

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >如果清單中指定了多個欄位，**ALL FIELDS**&#x200B;的資料必須與資料庫中儲存的資料匹配，才能更新配置檔案。 否則，會建立新的設定檔。
   > 
   >此函式對Web應用程式特別有用，但不建議用於公開表單。 選定的訪問控制選項必須是「啟用訪問控制」。

如果您不想更新配置檔案，則必須選擇&#x200B;**[!UICONTROL Skip preloading if no ID]**&#x200B;選項。 在這種情況下，在批准表單後，輸入的每個配置檔案都將添加到資料庫中。 例如，表單張貼至網站時，會使用此選項。

**[!UICONTROL Auto-load data referenced in the form]**&#x200B;選項可讓您自動預先載入與表單中輸入和合併欄位相符的資料。 但是，**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL Test]**&#x200B;活動中引用的資料並不相關。 如果未選取此選項，則需使用&#x200B;**[!UICONTROL Load additional data]**&#x200B;選項定義欄位。

**[!UICONTROL Load additional data]**&#x200B;選項可讓您新增未在表單頁面中使用，但仍會預先載入的資訊。

例如，您可以預先載入收件者的性別，並透過測試方塊自動將其導向至適當的頁面。

![](assets/s_ncs_admin_survey_preload_ex.png)

## 管理網路表單傳送和追蹤{#managing-web-forms-delivery-and-tracking}

建立、設定和發佈表單後，您就可以傳送表單並追蹤使用者回應。

### 表單的生命週期{#life-cycle-of-a-form}

一種形式的生命週期有三個階段：

1. **正在編輯的表單**

   這是初步設計階段。 建立新表單時，該表單處於編輯階段。 存取表單（僅用於測試用途），然後需要在其URL中使用參數&#x200B;**[!UICONTROL __uuid]**。 此URL可在&#x200B;**[!UICONTROL Preview]**&#x200B;子索引標籤中存取。 請參閱[表單URL參數](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

   >[!CAUTION]
   >
   >只要正在編輯表單，其存取URL就是特殊URL。

1. **線上表單**

   設計階段完成後，即可傳送表單。 首先，它需要發佈。 有關詳細資訊，請參閱[發佈表單](#publishing-a-form)。

   表單會是&#x200B;**[!UICONTROL Live]**，直到過期為止。

   >[!CAUTION]
   >
   >要傳送，調查的URL不得包含&#x200B;**[!UICONTROL __uuid]**&#x200B;參數。

1. **表單不可用**

   表單關閉後，傳送階段就會結束，表單將無法使用：使用者無法再存取。

   到期日可在表單屬性視窗中定義。 有關詳細資訊，請參閱[讓表單可線上使用](#making-a-form-available-online)

表單的發佈狀態會顯示在表單清單中。

![](assets/s_ncs_admin_survey_status.png)

### 發佈表單{#publishing-a-form}

若要變更表單的狀態，您必須發佈它。 要執行此操作，請按一下Web表單清單上方的&#x200B;**[!UICONTROL Publication]**&#x200B;按鈕，然後在下拉式方塊中選取狀態。

![](assets/webapp_publish_webform.png)

### 使表單聯機可用{#making-a-form-available-online}

若要供使用者存取，表單必須在生產環境中並開始，即在有效期內。 有效日期是透過表單的&#x200B;**[!UICONTROL Properties]**&#x200B;連結輸入。

* 使用&#x200B;**[!UICONTROL Project]**&#x200B;區段中的欄位輸入表單的開始日期和結束日期。

   ![](assets/webapp_availability_date.png)

* 按一下&#x200B;**[!UICONTROL Personalize the message displayed if the form is closed...]**&#x200B;連結，定義當使用者嘗試存取表單無效時要顯示的錯誤訊息。

   請參閱[表單的可及性](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form)。

### 透過電子郵件{#delivering-a-form-via-email}傳送表單

透過電子郵件傳送邀請時，您可以使用&#x200B;**[!UICONTROL Adobe Campaign Encryption]**&#x200B;選項進行資料協調。 若要這麼做，請前往傳送精靈，並新增下列參數以調整表單的連結：

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

在此情況下，資料儲存的調解金鑰必須是收件者的加密識別碼。 如需詳細資訊，請參閱[預先載入表單資料](#pre-loading-the-form-data)。

在此情況下，您需要核取記錄方塊中的&#x200B;**[!UICONTROL Update the preloaded record]**&#x200B;選項。 有關詳細資訊，請參閱[儲存網路表單回答](../../web/using/web-forms-answers.md#saving-web-forms-answers)。

![](assets/s_ncs_admin_survey_save_box_option.png)

### 日誌響應{#log-responses}

您可以在專用索引標籤中啟動回應追蹤，以監控網路表單的影響。 要執行此操作，請按一下表單屬性窗口中的&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;連結，並選擇&#x200B;**[!UICONTROL Log responses]**&#x200B;選項。

![](assets/s_ncs_admin_survey_trace.png)

**[!UICONTROL Responses]**&#x200B;標籤可讓您檢視回應者的身分。

![](assets/s_ncs_admin_survey_trace_tab.png)

選取收件者，然後按一下&#x200B;**[!UICONTROL Detail...]**&#x200B;按鈕以檢視所提供的回應。

![](assets/s_ncs_admin_survey_trace_edit.png)

您可以處理查詢中提供的回應記錄，例如在傳送提醒時僅鎖定非回應者，或僅向回應者提供特定通訊。

>[!NOTE]
>
>若要完整追蹤提供的回應，請匯出回應並檢視或建立專用報表，請使用選用的&#x200B;**Survey**&#x200B;模組。 如需詳細資訊，請參閱[本章節](../../web/using/about-surveys.md)。
