---
product: campaign
title: 開始使用網路應用程式
description: 建立和共用動態網頁應用程式、登陸頁面和調查
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 20%

---

# 開始使用網路應用程式{#about-web-applications}



Adobe Campaign可讓您使用來自資料庫的資料，以及根據連線使用者的許可權而改寫的內容，建立及發佈動態和互動式Web應用程式。

您可以建立頁面，例如外部網路上的編輯表單，或通知表單，其中包含來自資料庫的資料，以及表格、圖表、輸入表單等。 此功能可讓您設計和張貼網頁，讓使用者在其中查閱或輸入資訊。

這可以是訂閱表單，其中包含已預先載入Adobe Campaign資料庫所含資訊的資料，如下所示：

![](assets/webapp_form_sample.png)

本章提供如何管理Web應用程式的概觀。

>[!NOTE]
>
>請參閱 [安全性與隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html) 以瞭解如何最佳化Web應用程式的安全性。

>[!CAUTION]
>
>基於隱私權理由，我們建議對所有外部資源使用HTTPS。

## Web應用程式範圍 {#web-application-scope}

Adobe Campaign中的網頁應用程式可存取下列功能：

* 建立多頁表單。 如需關於此項目的詳細資訊，請參閱此[頁面](about-web-forms.md)。
* 使用整合式翻譯工具進行多語言調查管理。 如需關於此項目的詳細資訊，請參閱此[頁面](translating-a-web-application.md)。
* 圖形化頁面管理介面，多欄頁面配置。 如需關於此項目的詳細資訊，請參閱此[頁面](designing-a-web-application.md)。
* 呈現個人化和欄位位置。 如需關於此項目的詳細資訊，請參閱此[頁面](editing-content.md#adding-personalization-content)。
* 根據答案有條件地顯示調查欄位。 如需關於此項目的詳細資訊，請參閱此[頁面](form-rendering.md#defining-fields-conditional-display)。
* 隨機顯示問題。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/building-a-survey.md#adding-questions)。
* 條件式頁面顯示。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-page-sequencing.md#conditional-page-display)。
* 根據預期的資料型別（編號、電子郵件地址、日期等），在驗證之前檢查資訊 和必填欄位。 如需關於此項目的詳細資訊，請參閱此[頁面](form-rendering.md#defining-control-settings)。
* 電子郵件邀請或通知。 如需關於此項目的詳細資訊，請參閱此[頁面](publishing-a-web-form.md#delivering-a-form-via-email)。
* 個人化錯誤和結束訊息。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-properties.md#setting-up-an-error-page)。
* 使用影像、影片、超文字連結、驗證碼等。 如需關於此項目的詳細資訊，請參閱此[頁面](editing-content.md)。
* 即時監控回應。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking)。

選填 **調查** 建立模組提供下列附加功能：

* 資料庫的動態擴充：建立未包含在初始資料範本中的回應。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 產生專用報表。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys)。

相較於Web應用程式，調查具有簡化的圖形介面，且編輯控制項數目減少。

>[!NOTE]
>
>有關調查的詳情，請參閱 [本節](../../surveys/using/about-surveys.md).
>
>Adobe Campaign中網路表單的整體功能詳見 [本節](about-web-forms.md).

## Web應用程式實施 {#web-application-implementation}

若要建立並張貼Web應用程式，您必須：

1. 建立內容（欄位、清單、表格、圖形等）。

   您也可以檢視詳細說明表單可用欄位的區段：所有這些欄位也適用於Web應用程式。 此資訊可在以下位置取得： [此頁面](adding-fields-to-a-web-form.md).

1. 您可以視需要新增預先載入、測試和儲存步驟，以及設定存取控制系統（主要在外聯網發佈的架構中）。
1. 發佈Web應用程式，使其可在外部網路或Adobe Campaign中使用。

## Web應用程式初始設定 {#web-application-initial-configuration}

網路應用程式是透過以下方式建立： **[!UICONTROL Web Applications]** 中的連結 **[!UICONTROL Campaigns]** 和 **[!UICONTROL Profiles and targets]** 索引標籤。

網頁應用程式儲存在 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign樹的節點。 設定分為以下資料夾：

* **[!UICONTROL Administration > Configuration > Form renderings]**：包含網頁表單簡報（應用程式和調查）的轉譯範本。 範本可讓您產生表單。 它也使用CSS樣式表。 可在範本層級多載此樣式表。 如需詳細資訊，請參閱[此頁面](form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**：包含表單範本。 若要建立表單或Web應用程式，您必須從範本開始。

## 網頁應用程式範本 {#web-application-templates}

依預設，Adobe Campaign會為每個可用的Web應用程式提供一個範本。

>[!NOTE]
>
>您可以將現有的Web應用程式轉換成範本。 要執行此操作，請選取表單並按一下滑鼠右鍵。 選取 **[!UICONTROL Actions > Save as template...]**。

您可以透過建立新範本 **[!UICONTROL Resources > Templates > Web Application templates]** Adobe Campaign樹的節點。

建立精靈可讓您選取要啟用的選項，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的應用程式取決於您的選項和模組。 請檢查您的授權合約。
