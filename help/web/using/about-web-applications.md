---
product: campaign
title: 開始使用網路應用程式
description: 建立和共用動態網頁應用程式、登錄頁面和調查
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 20%

---

# 開始使用網路應用程式{#about-web-applications}

![](../../assets/common.svg)

Adobe Campaign可讓您使用資料庫中的資料和符合連線使用者權限的內容，來建立和發佈動態和互動式Web應用程式。

您可以建立頁面，如外聯網上的編輯表單，或包括資料庫中的資料的通知表單，包括表格、圖表、輸入表單等。 此功能可讓您設計和發佈網頁，讓使用者可在其中查詢或輸入資訊。

這可以是訂閱表單，其中包含已預先載入Adobe Campaign資料庫所含資訊的資料，如下所示：

![](assets/webapp_form_sample.png)

本章概述如何管理Web應用程式。

>[!NOTE]
>
>請參閱 [安全性與隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html) 了解如何最佳化網頁應用程式的安全性。

>[!CAUTION]
>
>基於隱私權考量，我們建議對所有外部資源使用HTTPS。

## Web應用程式範圍 {#web-application-scope}

Adobe Campaign中的Web應用程式可存取下列功能：

* 建立多頁表單。 如需關於此項目的詳細資訊，請參閱此[頁面](about-web-forms.md)。
* 使用整合的翻譯工具管理多語言調查。 如需關於此項目的詳細資訊，請參閱此[頁面](translating-a-web-application.md)。
* 圖形化頁面管理介面，多欄頁面配置。 如需關於此項目的詳細資訊，請參閱此[頁面](designing-a-web-application.md)。
* 轉譯個人化和欄位位置。 如需關於此項目的詳細資訊，請參閱此[頁面](editing-content.md#adding-personalization-content)。
* 根據答案有條件顯示調查欄位。 如需關於此項目的詳細資訊，請參閱此[頁面](form-rendering.md#defining-fields-conditional-display)。
* 隨機顯示問題。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/building-a-survey.md#adding-questions)。
* 條件式頁面顯示。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-page-sequencing.md#conditional-page-display)。
* 驗證前的資訊檢查取決於預期的資料類型（號碼、電子郵件地址、日期等） 和必填欄位。 如需關於此項目的詳細資訊，請參閱此[頁面](form-rendering.md#defining-control-settings)。
* 電子郵件邀請或通知。 如需關於此項目的詳細資訊，請參閱此[頁面](publishing-a-web-form.md#delivering-a-form-via-email)。
* 錯誤和結束訊息的個人化。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-properties.md#setting-up-an-error-page)。
* 影像、影片、超文字連結、驗證碼等的使用。 如需關於此項目的詳細資訊，請參閱此[頁面](editing-content.md)。
* 即時監控回應。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)。

選填 **調查** 建立模組提供下列其他功能：

* 資料庫的動態擴展：建立不包含在初始資料範本中的回應。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 產生專用報表。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

與Web應用程式相比，調查具有簡化的圖形介面，編輯控制項的數量減少。

>[!NOTE]
>
>調查在 [本節](../../surveys/using/about-surveys.md).
>
>Adobe Campaign中網路表單的整體功能於 [本節](about-web-forms.md).

## Web應用程式實作 {#web-application-implementation}

要建立和發佈Web應用程式，您必須：

1. 建立內容（欄位、清單、表格、圖形等）。

   您也可以檢視區段，其中詳細說明表單的可用欄位：這些欄位也適用於Web應用程式。 此資訊可在 [本頁](adding-fields-to-a-web-form.md).

1. 根據需要，您可以添加預載、測試和保存步驟，並配置訪問控制系統（主要在外聯網發佈的框架內）。
1. 發佈Web應用程式，以便在外聯網或Adobe Campaign上提供。

## Web應用程式初始配置 {#web-application-initial-configuration}

Web應用程式是透過 **[!UICONTROL Web Applications]** 連結 **[!UICONTROL Campaigns]** 和 **[!UICONTROL Profiles and targets]** 頁簽。

Web應用程式儲存在 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign樹的節點。 設定在下列資料夾中劃分：

* **[!UICONTROL Administration > Configuration > Form renderings]**:包含用於Web表單演示（應用程式和調查）的呈現模板。 範本可讓您產生表單。 它也使用CSS樣式表。 在模板級別，此樣式表可以超載。 如需詳細資訊，請參閱[此頁面](form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表單範本。 要建立表單或Web應用程式，必須從模板開始。

## 網頁應用程式範本 {#web-application-templates}

依預設，Adobe Campaign會為每個可用的Web應用程式提供一個範本。

>[!NOTE]
>
>您可以將現有的Web應用程式轉換為範本。 要執行此操作，請選取表單並按一下右鍵。 選取 **[!UICONTROL Actions > Save as template...]**。

您可以透過 **[!UICONTROL Resources > Templates > Web Application templates]** Adobe Campaign樹的節點。

建立精靈可讓您選取要啟用的選項，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的應用程式取決於您的選項和模組。 請檢查您的授權合約。
