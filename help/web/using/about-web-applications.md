---
title: 關於Web應用程式
seo-title: 關於Web應用程式
description: 關於Web應用程式
seo-description: null
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 61c7681535dc08e1d705d7d239e96c603bbad339

---


# 關於Web應用程式{#about-web-applications}

Adobe Campaign可讓您建立和發佈動態互動式網頁應用程式，其中包含資料庫的資料和符合連線使用者權限的內容。 您可以建立頁面，如外部網上的編輯表單，或通知表單，包括來自資料庫的資料，以及表、圖表、輸入表單等。 此功能可讓您設計並張貼網頁，讓使用者可在其中查閱或輸入資訊。

這可以是包含預先載入Adobe Campaign資料庫中資訊之資料的訂閱表單，如下所示：

![](assets/webapp_form_sample.png)

本章概述如何管理Web應用程式。

>[!CAUTION]
>
>基於隱私權原因，我們建議對所有外部資源使用HTTPS。

## Web應用程式範圍 {#web-application-scope}

Adobe Campaign中的網頁應用程式可讓您存取下列功能：

* 建立多頁表單。 For more on this, refer to this [page](../../web/using/about-web-forms.md).
* 使用整合的翻譯工具管理多語言調查。 For more on this, refer to this [page](../../web/using/translating-a-web-application.md).
* 圖形頁面管理介面，多欄頁面版面。 For more on this, refer to this [page](../../web/using/designing-a-web-application.md).
* 呈現個人化和現場位置。 For more on this, refer to this [page](../../web/using/editing-content.md#adding-personalization-content).
* 根據答案有條件顯示調查欄位。 For more on this, refer to this [page](../../web/using/form-rendering.md#defining-fields-conditional-display).
* 隨機顯示問題。 For more on this, refer to this [page](../../web/using/building-a-survey.md#adding-questions).
* 條件式頁面顯示。 For more on this, refer to this [page](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).
* 驗證前檢查資訊，視預期的資料類型（編號、電子郵件位址、日期等）而定和必填欄位。 For more on this, refer to this [page](../../web/using/form-rendering.md#defining-control-settings).
* 電子郵件邀請或通知。 For more on this, refer to this [page](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).
* 錯誤和結束訊息的個人化。 For more on this, refer to this [page](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page).
* 影像、視訊、超文字連結、驗證碼等的使用。 For more on this, refer to this [page](../../web/using/editing-content.md).
* 即時監控回應。 For more on this, refer to this [page](../../web/using/publish--track-and-use-collected-data.md#response-tracking).

選用的 **Survey** 建立模組提供下列額外功能：

* 資料庫的動態擴展：建立未包含在初始資料範本中的回應。 For more on this, refer to this [page](../../web/using/managing-answers.md#storing-collected-answers).
* 產生專用報表。 For more on this, refer to this [page](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

與Web應用程式相比，調查具有簡化的圖形介面，並減少編輯控制項的數量。

>[!NOTE]
>
>本節將詳述 [調查](../../web/using/about-surveys.md)。
>
>Adobe Campaign中Web表格的整體功能在本節 [中詳述](../../web/using/about-web-forms.md)。

## Web應用程式實作 {#web-application-implementation}

若要建立和張貼Web應用程式，您必須：

1. 建立內容（欄位、清單、表格、圖形等）。

   您也可以檢視詳細說明表單可用欄位的章節：這些欄位也適用於Web應用程式。 本頁提供此 [資訊](../../web/using/adding-fields-to-a-web-form.md)。

1. 根據需要，您可以添加預載、測試和保存步驟，並配置訪問控制系統（主要在外聯網出版物的框架內）。
1. 發佈網路應用程式，以便在外部網路或Adobe Campaign中提供。

## Web應用程式初始設定 {#web-application-initial-configuration}

Web應用程式是透過與標籤 **[!UICONTROL Web Applications]** 中的連結 **[!UICONTROL Campaigns]** 建立 **[!UICONTROL Profiles and targets]** 的。

Web應用程式會儲存在Adobe **[!UICONTROL Resources > Online > Web Applications]** Campaign樹狀結構的節點中。 配置在以下資料夾中劃分：

* **[!UICONTROL Administration > Configuration > Form renderings]**:包含Web表單簡報（應用程式和調查）的轉換範本。 範本可讓您產生表單。 它也使用CSS樣式表。 此樣式表可以在模板級別過載。 有關詳細資訊，請參見[此頁面](../../web/using/form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表單範本。 若要建立表單或Web應用程式，您必須從範本開始。

## 網頁應用程式範本 {#web-application-templates}

依預設，Adobe Campaign會針對每個可用的網頁應用程式提供一個範本。

>[!NOTE]
>
>您可以將現有的Web應用程式轉換為範本。 若要這麼做，請選取表格並按一下滑鼠右鍵。 Select **[!UICONTROL Actions > Save as template...]**.

您可以透過Adobe Campaign樹狀結 **[!UICONTROL Resources > Templates > Web Application templates]** 構的節點建立新範本。

建立精靈可讓您選取要啟用的選項，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的應用程式取決於您的選項和模組。 請檢查您的授權合約。

