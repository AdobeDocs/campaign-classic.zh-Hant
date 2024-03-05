---
product: campaign
title: 發佈網路表單
description: 發佈網路表單
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: 8bb839bd0118010ac8e3e4bde88f6f3972786ed0
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 1%

---

# 發佈網路表單{#publishing-a-web-form}



## 預先載入表單資料 {#pre-loading-the-form-data}

如果您想要透過Web表單更新儲存在資料庫中的設定檔，可以使用預先載入方塊。 預先載入方塊可讓您指定如何在資料庫中尋找要更新的記錄。

可以使用下列識別方法：

* **[!UICONTROL Adobe Campaign Encryption]**

  此加密方法使用加密的Adobe Campaign識別碼(ID)。 此方法僅適用於Adobe Campaign物件，且加密的ID只能由Adobe Campaign平台產生。

  使用此方法時，您需要透過新增 **`<%=escapeUrl(recipient.cryptedId) %>`** 引數。 有關詳細資訊，請參閱 [透過電子郵件傳遞表單](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

  ![](assets/s_ncs_admin_survey_preload_methods_001.png)

  此加密方法使用外部提供的識別碼(ID)，連結至Adobe Campaign和外部提供者共用的金鑰。 此 **[!UICONTROL Des key]** 欄位可讓您輸入此加密金鑰。

* **[!UICONTROL List of fields]**

  此選項可讓您從表單目前內容的欄位中進行選擇，這些欄位將用於尋找資料庫中的對應設定檔。

  ![](assets/s_ncs_admin_survey_preload_methods_002.png)

  欄位可透過 **[!UICONTROL Parameters]** 索引標籤(請參閱 [新增引數](defining-web-forms-properties.md#adding-parameters))。 它們會放置在表單URL或輸入區域中。

  >[!CAUTION]
  >
  >所選欄位中的資料未加密。 不可以加密形式提供，因為Adobe Campaign無法將其解密，如果 **[!UICONTROL Field list]** 已選取選項。

  在以下範例中，設定檔預先載入是根據電子郵件地址。

  URL可包含未加密的電子郵件地址，在此情況下，使用者可直接存取他們相關的頁面。

  ![](assets/s_ncs_admin_survey_preload_methods_003.png)

  否則，系統會要求他們輸入密碼。

  ![](assets/s_ncs_admin_survey_preload_methods_004.png)

  >[!CAUTION]
  >
  >如果清單中指定了數個欄位，則資料屬於 **所有欄位** 必須符合儲存在資料庫中的資料，才能更新設定檔。 否則，會建立新的設定檔。
  > 
  >此函式在Web應用程式中特別有用，但不建議用於公用表單。 選取的存取控制選項必須是「啟用存取控制」。

此 **[!UICONTROL Skip preloading if no ID]** 如果您不想更新設定檔，則必須選取選項。 在這種情況下，在核准表單後，輸入的每個設定檔都將新增到資料庫。 例如，在網站上張貼表單時，會使用此選項。

此 **[!UICONTROL Auto-load data referenced in the form]** 選項可讓您自動預先載入與表單中輸入及合併欄位相符的資料。 不過，資料引用自 **[!UICONTROL Script]** 和 **[!UICONTROL Test]** 活動無關。 如果未選取此選項，您需要使用 **[!UICONTROL Load additional data]** 選項。

此 **[!UICONTROL Load additional data]** 選項可讓您新增未在表單頁面中使用，但將預先載入的資訊。

例如，您可以預先載入收件者的性別，並透過測試方塊自動將其導向適當的頁面。

![](assets/s_ncs_admin_survey_preload_ex.png)

## 管理網路表單傳遞和追蹤 {#managing-web-forms-delivery-and-tracking}

建立、設定和發佈表單後，您就可以傳送表單並追蹤使用者回應。

### 表單的生命週期 {#life-cycle-of-a-form}

表單的生命週期有三個階段：

1. **正在編輯**

   這是初始設計階段。 建立新表單時，它處於編輯階段。 存取表單僅供測試之用，因此需要引數 **[!UICONTROL __uuid]** 用於其URL中。 此URL的存取方式為 **[!UICONTROL Preview]** 子標籤。 另請參閱 [表單URL引數](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >只要正在編輯表單，其存取URL就是特殊的URL。

1. **待處理的出版物**

   在某些情況下(例如 [透過封裝匯入表單](#import-web-packages))，網路表單可以 **[!UICONTROL Pending publication]** 狀態直到其上線為止。

   >[!NOTE]
   >
   >對於技術網頁應用程式(可透過 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Web applications]** 功能表)，包含 **[!UICONTROL Pending publication]** 狀態為自動 [已發佈](#publishing-a-form) 並取得 **[!UICONTROL Online]** 狀態。

1. **線上**

   設計階段完成後，即可交付表單。

   當表單具有 **[!UICONTROL Being edited]** 或 **[!UICONTROL Pending publication]** 狀態，它必須 [已發佈](#publishing-a-form) 線上並可透過瀏覽器中的網路表單URL存取。

   發佈後，表單會一直有效，直到它過期為止。

   表單將會 **[!UICONTROL Live]** 直到它過期為止。

   >[!CAUTION]
   >
   >若要傳遞，表單的URL不可包含 **[!UICONTROL __uuid]** 引數。

1. **已關閉**

   表單關閉後，傳送階段便會結束，表單會變成無法使用：使用者無法再存取表單。

   到期日可在表單屬性視窗中定義。 有關詳細資訊，請參閱 [線上上提供表單](#making-a-form-available-online).

表單的發佈狀態會顯示在表單清單中。

![](assets/s_ncs_admin_survey_status.png)

### 發佈表單 {#publishing-a-form}

若要變更表單的狀態，您必須將其發佈。 若要這麼做，請按一下 **[!UICONTROL Publication]** 按鈕，然後在下拉式方塊中選取狀態。

![](assets/webapp_publish_webform.png)

### 線上上提供表單 {#making-a-form-available-online}

若要由使用者存取，該表單必須處於生產狀態並啟動（即在其有效期內）。 有效日期是透過 **[!UICONTROL Properties]** 表單的連結。

* 使用中的欄位 **[!UICONTROL Project]** 區段來輸入表單的開始和結束日期。

  ![](assets/webapp_availability_date.png)

* 按一下 **[!UICONTROL Personalize the message displayed if the form is closed...]** 定義使用者在表單無效時嘗試存取表單時所顯示錯誤訊息的連結。

  另請參閱 [表單的協助工具](defining-web-forms-properties.md#accessibility-of-the-form).

### 透過電子郵件傳遞表單 {#delivering-a-form-via-email}

當您透過電子郵件傳送邀請時，可以使用 **[!UICONTROL Adobe Campaign Encryption]** 資料協調的選項。 若要這麼做，請前往傳送精靈，並新增下列引數，將連結調整為適合表單：

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

在此情況下，資料儲存的調解金鑰必須是收件者的加密識別碼。 有關詳細資訊，請參閱 [預先載入表單資料](#pre-loading-the-form-data).

在此情況下，您需要檢查 **[!UICONTROL Update the preloaded record]** 選項。 有關詳細資訊，請參閱 [儲存網路表單答案](web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### 記錄回應 {#log-responses}

可在專用標籤中啟用回應追蹤，以監控網頁表單的影響。 若要這麼做，請按一下 **[!UICONTROL Advanced parameters...]** 在表單屬性視窗中連結，然後選取 **[!UICONTROL Log responses]** 選項。

![](assets/s_ncs_admin_survey_trace.png)

此 **[!UICONTROL Responses]** 標籤可讓您檢視回應者的身分。

![](assets/s_ncs_admin_survey_trace_tab.png)

選取收件者並按一下 **[!UICONTROL Detail...]** 按鈕以檢視提供的回應。

![](assets/s_ncs_admin_survey_trace_edit.png)

您可以處理查詢中提供的回應記錄，例如，在傳送提醒時僅針對非回應者，或僅向回應者提供特定通訊。

### 匯入Web表單套件 {#import-web-packages}

從執行個體匯出和匯入包含Web表單的套件至另一個執行個體時（例如，從預備到生產），新執行個體上的Web表單狀態可能會根據多個條件而改變。 以下列出不同案例。

瞭解更多關於網路表單的不同狀態，在 [本節](#life-cycle-of-a-form).

>[!NOTE]
>
>當您透過封裝匯出網頁表單時，表單狀態會顯示在結果封裝的內容中。

* 如果網頁表單狀態為 **[!UICONTROL Pending publication]** 或 **[!UICONTROL Online]** 從第一個執行個體匯出時：

   * 網頁表單取得 **[!UICONTROL Pending publication]** 在新執行個體匯入時的狀態。

   * 如果新執行個體上已存在網頁表單，則會以新版本的表單取代，並採用 **[!UICONTROL Pending publication]** 狀態，即使表單的舊版本為 **[!UICONTROL Online]**.

   * 無論表單存在與否，表單都必須 [已發佈](#publishing-a-form) 成為 **[!UICONTROL Online]** ，並可透過瀏覽器中的網路表單URL存取。

* 如果網頁表單狀態為 **[!UICONTROL Being edited]** 匯出時：

   * 如果網頁表單是匯入套件所在執行個體上的新表單，則網頁表單會取得 **[!UICONTROL Being edited]** 狀態。

   * 如果新執行個體上已存在網頁表單，則這是對現有表單的修改。 如果表單的舊版本為 **[!UICONTROL Online]**，舊版本會保持上線，直到新版本的表單成為 [已發佈](#publishing-a-form) 在新執行個體上再次進行。

  >[!NOTE]
  >
  >您可以使用以下網址檢視網頁表單的最新版本： **[!UICONTROL Preview]** 標籤。

<!--For RN:
* Now, when a web form has the **Pending publication** status, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)
-->
