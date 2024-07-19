---
product: campaign
title: 開始使用意見調查
description: 開始使用Campaign調查
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 8e5a328bee7701adfedec6a533cc21b4ce548187
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 3%

---

# 開始使用意見調查{#about-surveys}

Adobe Campaign包含圖形模組，可定義及發佈網頁應用程式。 這可用來建立頁面，例如外部網路上的編輯表單，或通知表單（包含來自資料庫的資料，以及表格、圖表、輸入表單等）。 使用此功能來設計和張貼網頁，讓使用者可以在其中查閱或輸入資訊。

>[!AVAILABILITY]
>
>調查管理不適用於企業(FFDA)部署內容中的Campaign v8。 深入瞭解[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}。


選用的&#x200B;**調查**&#x200B;附加元件可讓您建立新型別的Web應用程式，以建立和管理線上問卷，例如新增或修改設定檔資訊、訂閱或取消訂閱資訊服務或競爭專案表單的表單。 收集到答案後，就會儲存在資料庫或本機變數中。 資料模型可透過調查問卷的答案動態擴展。 您可以即時檢視結果、篩選回應，並使用專用圖表加以分析。

本章詳細說明如何建立和管理&#x200B;**調查**、欄位和頁面管理、儲存模式和記錄。

在[此頁面](getting-started-with-surveys.md)中瞭解如何建立您的第一個調查。

>[!NOTE]
>
>* 建立標準Web表單的詳細步驟可在[此檔案](../../web/using/about-web-forms.md)中取得。
>
>* 在[此檔案](../../web/using/about-web-applications.md)中詳細說明Web應用程式管理。 如需詳細資訊，請參閱本章。

## 功能範圍 {#campaign-surveys-scope}

在Adobe Campaign中，使用[網頁應用程式](../../web/using/about-web-forms.md)來：

* 建立多頁表單，
* 使用整合的翻譯工具管理多語言表單，
* 管理圖形介面、多欄頁面配置、
* 新增個人化並定義欄位位置
* 根據答案之調查欄位的條件顯示，
* 條件頁面顯示，
* 根據預期的資料型別（數字、電子郵件地址、日期等），在核准前檢查資訊 和必填欄位，
* 傳送電子郵件邀請/通知，
* 個人化錯誤和結束頁面，
* 在表單中新增影像、影片、超文字連結、驗證碼等

選用的調查建立模組提供使用者易記的UI和以下附加功能：

* 資料庫的動態擴充：建立不屬於初始資料模型的回答。 [了解更多](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 分數管理。 [了解更多](../../surveys/using/managing-answers.md#score-management)。
* 隨機顯示問題。 [了解更多](../../surveys/using/building-a-survey.md#adding-questions)。
* 即時追蹤答案。 [了解更多](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking)。
* 產生專用報表。 [了解更多](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys)。


## 實施步驟 {#surveys-implementation-steps}

套用下列步驟來建立和傳遞調查並處理其結果：

1. 建立調查的頁面及其內容（輸入欄位、下拉式清單、問題等）。
1. 定義應如何儲存答案。 可以插入資料預先載入步驟，以便使用資料庫中已存在的資料預先載入表單。 您也可以新增測試方塊。
1. Publish，然後將調查傳送給收件者（例如將連結納入傳送或網站）。
1. 監視回應並檢視報表。

如需設定和排序這些步驟的詳細資訊，請參閱[本檔案](../../web/using/about-web-forms.md)。 本章僅會詳細說明調查的特定設定。

>[!CAUTION]
>
>基於隱私權理由，我們建議對所有外部資源使用HTTPS。

## 設定 {#settings}

依預設，調查可在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;節點中使用。

設定會儲存在下列資料夾中：

* **[!UICONTROL Administration > Configuration > Form rendering]**：包含Web表單簡報（應用程式和調查）的轉譯範本。
* **[!UICONTROL Resources > Templates > Web application templates]**：包含表單範本。 若要建立表單，您必須先使用範本。

>[!NOTE]
>
>[此檔案](../../web/using/about-web-forms.md)中有設定詳細資料。
