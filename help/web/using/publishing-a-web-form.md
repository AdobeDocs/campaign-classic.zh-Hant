---
product: campaign
title: 發佈網路表單
description: 發佈網路表單
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 1%

---

# 發佈網路表單{#publishing-a-web-form}



## 預先載入表單資料 {#pre-loading-the-form-data}

如果您想要透過Web表單更新儲存在資料庫中的設定檔，可以使用預先載入方塊。 預先載入方塊可讓您指定如何在資料庫中尋找要更新的記錄。

可以使用下列識別方法：

* **[!UICONTROL Adobe Campaign Encryption]**

  此加密方法使用加密的Adobe Campaign識別碼(ID)。 此方法僅適用於Adobe Campaign物件，且加密的ID只能由Adobe Campaign平台產生。

  使用此方法時，您必須新增&#x200B;**`<%=escapeUrl(recipient.cryptedId) %>`**&#x200B;引數，調整要傳送到電子郵件地址的表單URL。 如需詳細資訊，請參閱[透過電子郵件傳遞表單](#delivering-a-form-via-email)。

* **[!UICONTROL DES encryption]**

  ![](assets/s_ncs_admin_survey_preload_methods_001.png)

  此加密方法使用外部提供的識別碼(ID)，連結至Adobe Campaign和外部提供者共用的金鑰。 **[!UICONTROL Des key]**&#x200B;欄位可讓您輸入此加密金鑰。

* **[!UICONTROL List of fields]**

  此選項可讓您從表單目前內容的欄位中進行選擇，這些欄位將用於尋找資料庫中的對應設定檔。

  ![](assets/s_ncs_admin_survey_preload_methods_002.png)

  欄位可透過&#x200B;**[!UICONTROL Parameters]**&#x200B;索引標籤新增至表單屬性（請參閱[新增引數](defining-web-forms-properties.md#adding-parameters)）。 它們會放置在表單URL或輸入區域中。

  >[!CAUTION]
  >
  >所選欄位中的資料未加密。 不可以加密形式提供，因為如果選取&#x200B;**[!UICONTROL Field list]**&#x200B;選項，Adobe Campaign將無法將其解密。

  在以下範例中，設定檔預先載入是根據電子郵件地址。

  URL可包含未加密的電子郵件地址，在此情況下，使用者可直接存取他們相關的頁面。

  ![](assets/s_ncs_admin_survey_preload_methods_003.png)

  否則，系統會要求他們輸入密碼。

  ![](assets/s_ncs_admin_survey_preload_methods_004.png)

  >[!CAUTION]
  >
  >如果清單中指定了數個欄位，則&#x200B;**ALL FIELDS**&#x200B;的資料必須符合儲存在資料庫中的資料，才能更新設定檔。 否則，會建立新的設定檔。
  > 
  >此函式在Web應用程式中特別有用，但不建議用於公用表單。 選取的存取控制選項必須是「啟用存取控制」。

如果您不想更新設定檔，則必須選取&#x200B;**[!UICONTROL Skip preloading if no ID]**&#x200B;選項。 在這種情況下，在核准表單後，輸入的每個設定檔都將新增到資料庫。 例如，在網站上張貼表單時，會使用此選項。

**[!UICONTROL Auto-load data referenced in the form]**&#x200B;選項可讓您自動預先載入符合表單中輸入與合併欄位的資料。 不過，**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL Test]**&#x200B;活動中參考的資料並不相關。 如果未選取此選項，您必須使用&#x200B;**[!UICONTROL Load additional data]**&#x200B;選項定義欄位。

**[!UICONTROL Load additional data]**&#x200B;選項可讓您新增未用於表單頁面，但將預先載入的資訊。

例如，您可以預先載入收件者的性別，並透過測試方塊自動將其導向適當的頁面。

![](assets/s_ncs_admin_survey_preload_ex.png)

## 管理網路表單傳遞和追蹤 {#managing-web-forms-delivery-and-tracking}

建立、設定和發佈表單後，您就可以傳送表單並追蹤使用者回應。

### 表單的生命週期 {#life-cycle-of-a-form}

表單的生命週期有三個階段：

1. **正在編輯**

   這是初始設計階段。 建立新表單時，它處於編輯階段。 存取表單（僅供測試之用），則需要在其URL中使用引數&#x200B;**[!UICONTROL __uuid]**。 此URL可在&#x200B;**[!UICONTROL Preview]**&#x200B;子標籤中存取。 請參閱[表單URL引數](defining-web-forms-properties.md#form-url-parameters)。

   >[!CAUTION]
   >
   >只要正在編輯表單，其存取URL就是特殊的URL。

1. **擱置中的出版物**

   在某些情況下（例如當[透過封裝](#import-web-packages)匯入表單時），網頁表單可以具有&#x200B;**[!UICONTROL Pending publication]**&#x200B;狀態，直到其上線為止。

   >[!NOTE]
   >
   >對於技術網頁應用程式（可透過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Web applications]**&#x200B;功能表取得），具有&#x200B;**[!UICONTROL Pending publication]**&#x200B;狀態的表單會自動為[已發佈](#publishing-a-form)，且會取得&#x200B;**[!UICONTROL Online]**&#x200B;狀態。

1. **線上**

   設計階段完成後，即可交付表單。

   當表單的狀態為&#x200B;**[!UICONTROL Being edited]**&#x200B;或&#x200B;**[!UICONTROL Pending publication]**&#x200B;時，它必須是[已發佈](#publishing-a-form)，才能線上上並可透過瀏覽器中的網頁表單URL存取。

   發佈後，表單會一直有效，直到它過期為止。

   表單將為&#x200B;**[!UICONTROL Live]**，直到它過期為止。

   >[!CAUTION]
   >
   >若要傳遞，表單的URL不可包含&#x200B;**[!UICONTROL __uuid]**&#x200B;引數。

1. **已關閉**

   表單關閉後，傳送階段便會結束，表單會變成無法使用：使用者無法再存取表單。

   到期日可在表單屬性視窗中定義。 如需詳細資訊，請參閱[線上上提供表單](#making-a-form-available-online)。

表單的發佈狀態會顯示在表單清單中。

![](assets/s_ncs_admin_survey_status.png)

### 發佈表單 {#publishing-a-form}

若要變更表單的狀態，您必須將其發佈。 若要這麼做，請按一下網路表單清單上方的&#x200B;**[!UICONTROL Publication]**&#x200B;按鈕，然後在下拉式方塊中選取狀態。

![](assets/webapp_publish_webform.png)

### 線上上提供表單 {#making-a-form-available-online}

若要由使用者存取，該表單必須處於生產狀態並啟動（即在其有效期內）。 有效日期透過表單的&#x200B;**[!UICONTROL Properties]**&#x200B;連結輸入。

* 使用&#x200B;**[!UICONTROL Project]**&#x200B;區段中的欄位來輸入表單的開始和結束日期。

  ![](assets/webapp_availability_date.png)

* 按一下&#x200B;**[!UICONTROL Personalize the message displayed if the form is closed...]**&#x200B;連結以定義若使用者在表單無效時嘗試存取表單，則要顯示的錯誤訊息。

  請參閱表單](defining-web-forms-properties.md#accessibility-of-the-form)的[協助工具。

### 透過電子郵件傳遞表單 {#delivering-a-form-via-email}

當您透過電子郵件傳送邀請時，可以使用&#x200B;**[!UICONTROL Adobe Campaign Encryption]**&#x200B;選項進行資料協調。 若要這麼做，請前往傳送小幫手，新增下列引數，將連結調整為適合表單：

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

在此情況下，資料儲存的調解金鑰必須是收件者的加密識別碼。 如需詳細資訊，請參閱[預先載入表單資料](#pre-loading-the-form-data)。

在此情況下，您需要核取記錄方塊中的&#x200B;**[!UICONTROL Update the preloaded record]**&#x200B;選項。 如需詳細資訊，請參閱[儲存網路表單答案](web-forms-answers.md#saving-web-forms-answers)。

![](assets/s_ncs_admin_survey_save_box_option.png)

### 記錄回應 {#log-responses}

可在專用標籤中啟用回應追蹤，以監控網頁表單的影響。 若要這麼做，請按一下表單屬性視窗中的&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;連結，然後選取&#x200B;**[!UICONTROL Log responses]**&#x200B;選項。

![](assets/s_ncs_admin_survey_trace.png)

**[!UICONTROL Responses]**&#x200B;標籤可讓您檢視回應者的身分。

![](assets/s_ncs_admin_survey_trace_tab.png)

選取收件者並按一下&#x200B;**[!UICONTROL Detail...]**&#x200B;按鈕，以檢視提供的回應。

![](assets/s_ncs_admin_survey_trace_edit.png)

您可以處理查詢中提供的回應記錄，例如，在傳送提醒時僅針對非回應者，或僅向回應者提供特定通訊。

### 匯入Web表單套件 {#import-web-packages}

從執行個體匯出和匯入包含Web表單的套件至另一個執行個體時（例如，從預備到生產），新執行個體上的Web表單狀態可能會根據多個條件而改變。 以下列出不同案例。

在[本節](#life-cycle-of-a-form)中進一步瞭解網頁表單的不同狀態。

>[!NOTE]
>
>當您透過封裝匯出網頁表單時，表單狀態會顯示在結果封裝的內容中。

* 如果從第一個執行個體匯出時Web表單狀態為&#x200B;**[!UICONTROL Pending publication]**&#x200B;或&#x200B;**[!UICONTROL Online]**：

   * 網頁表單在新執行個體上匯入時取得&#x200B;**[!UICONTROL Pending publication]**&#x200B;狀態。

   * 如果新執行個體上已存在網頁表單，則會以新版本的表單取代，且會採用&#x200B;**[!UICONTROL Pending publication]**&#x200B;狀態，即使舊版本的表單為&#x200B;**[!UICONTROL Online]**&#x200B;亦然。

   * 無論表單存在與否，表單都必須是[已發佈](#publishing-a-form)，才能在新執行個體上變成&#x200B;**[!UICONTROL Online]**，並可在瀏覽器中透過網頁表單URL存取。

* 如果網頁表單在匯出時的狀態為&#x200B;**[!UICONTROL Being edited]**：

   * 如果網頁表單是匯入封裝的執行個體上的新表單，則網頁表單會取得&#x200B;**[!UICONTROL Being edited]**&#x200B;狀態。

   * 如果新執行個體上已存在網頁表單，則這是對現有表單的修改。 如果表單的舊版本是&#x200B;**[!UICONTROL Online]**，則舊版本會保持上線，直到表單的新版本在新執行個體上再次發佈[為](#publishing-a-form)為止。

  >[!NOTE]
  >
  >您可以使用&#x200B;**[!UICONTROL Preview]**&#x200B;索引標籤來檢查網頁表單的最新版本。

<!--For RN:
* Now, when a web form has the **Pending publication** status, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)
-->
