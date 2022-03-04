---
product: campaign
title: 開始使用網路應用程式
description: 建立和共用動態Web應用程式、登錄頁和調查
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 20%

---

# 開始使用網路應用程式{#about-web-applications}

![](../../assets/common.svg)

Adobe Campaign允許您建立和發佈動態和互動式Web應用程式，其中包含來自資料庫的資料和適合連接用戶權限的內容。

您可以建立頁面，如外聯網上的編輯表單，或通知表單，包括來自資料庫的資料，以及表、圖表、輸入表單等。 此功能允許您設計和發佈網頁，用戶可以在其中查找或輸入資訊。

這可以是一個訂閱表，其中包含預載了Adobe Campaign資料庫中所含資訊的資料，如下所示：

![](assets/webapp_form_sample.png)

本章概述了如何管理Web應用程式。

>[!NOTE]
>
>請參閱 [安全和隱私檢查表](https://helpx.adobe.com/tw/campaign/kb/acc-security.html) 瞭解如何優化Web應用程式的安全性。

>[!CAUTION]
>
>出於隱私原因，我們建議對所有外部資源使用HTTPS。

## Web應用程式範圍 {#web-application-scope}

Adobe Campaign的Web應用程式可訪問以下功能：

* 多頁表單建立。 如需關於此項目的詳細資訊，請參閱此[頁面](about-web-forms.md)。
* 使用整合翻譯工具進行多語言調查管理。 如需關於此項目的詳細資訊，請參閱此[頁面](translating-a-web-application.md)。
* 圖形頁面管理介面，多列頁面佈局。 如需關於此項目的詳細資訊，請參閱此[頁面](designing-a-web-application.md)。
* 呈現個性化和欄位位置。 如需關於此項目的詳細資訊，請參閱此[頁面](editing-content.md#adding-personalization-content)。
* 根據答案有條件顯示調查欄位。 如需關於此項目的詳細資訊，請參閱此[頁面](form-rendering.md#defining-fields-conditional-display)。
* 隨機顯示問題。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/building-a-survey.md#adding-questions)。
* 條件頁顯示。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-page-sequencing.md#conditional-page-display)。
* 驗證前的資訊檢查取決於預期的資料類型（編號、電子郵件地址、日期等） 和強制欄位。 如需關於此項目的詳細資訊，請參閱此[頁面](form-rendering.md#defining-control-settings)。
* 電子郵件邀請或通知。 如需關於此項目的詳細資訊，請參閱此[頁面](publishing-a-web-form.md#delivering-a-form-via-email)。
* 錯誤和結束消息的個性化。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-properties.md#setting-up-an-error-page)。
* 使用影像、視頻、超文本連結、驗證碼等 如需關於此項目的詳細資訊，請參閱此[頁面](editing-content.md)。
* 即時監控響應。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)。

可選 **調查** 建立模組提供了以下附加功能：

* 資料庫的動態擴展：建立初始資料模板中未包括的響應。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 生成專用報告。 如需關於此項目的詳細資訊，請參閱此[頁面](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

與Web應用程式相比，調查具有簡化的圖形介面和減少的編輯控制。

>[!NOTE]
>
>調查詳見 [此部分](../../surveys/using/about-surveys.md)。
>
>Adobe Campaign網表的總體功能詳見 [此部分](about-web-forms.md)。

## Web應用程式實現 {#web-application-implementation}

要建立和發佈Web應用程式，必須：

1. 建立內容（欄位、清單、表格、圖形等）。

   您還可以查看詳細列出表單可用欄位的部分：所有這些欄位也可用於Web應用程式。 此資訊可在 [此頁](adding-fields-to-a-web-form.md)。

1. 根據需要，您可以添加預載入、test和保存步驟，並配置訪問控制系統（主要在外聯網發佈的框架內）。
1. 發佈Web應用程式，使其在外聯網或Adobe Campaign上可用。

## Web應用程式初始配置 {#web-application-initial-configuration}

通過 **[!UICONTROL Web Applications]** 連結 **[!UICONTROL Campaigns]** 和 **[!UICONTROL Profiles and targets]** 頁籤。

Web應用程式儲存在 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign樹的節點。 配置在以下資料夾中細分：

* **[!UICONTROL Administration > Configuration > Form renderings]**:包含Web表單演示文稿（應用程式和調查）的呈現模板。 該模板使您能夠生成表單。 它還使用CSS樣式表。 此樣式表可以在模板級別重載。 如需詳細資訊，請參閱[此頁面](form-rendering.md#selecting-the-form-rendering-template)。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含窗體模板。 要建立表單或Web應用程式，必須從模板開始。

## Web應用程式模板 {#web-application-templates}

預設情況下，Adobe Campaign為每個可用Web應用程式提供一個模板。

>[!NOTE]
>
>可以將現有Web應用程式轉換為模板。 要執行此操作，請選擇窗體並按一下右鍵。 選取 **[!UICONTROL Actions > Save as template...]**。

您可以通過 **[!UICONTROL Resources > Templates > Web Application templates]** Adobe Campaign樹的節點。

建立嚮導允許您選擇要啟用的選項，如下所示。

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>可用的應用程式取決於您的選項和模組。 請檢查您的授權合約。
