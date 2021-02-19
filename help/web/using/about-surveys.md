---
solution: Campaign Classic
product: campaign
title: 開始使用意見調查
description: 開始使用Campaign調查
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---


# 開始使用意見調查{#about-surveys}

Adobe Campaign包含一個圖形模組，可用來定義和發佈網頁應用程式。 它用於建立頁，如外聯網上的編輯表單，或通知表單，包括來自資料庫的資料以及表、圖表、輸入表單等。 這項功能可讓您設計和張貼網頁，讓使用者可在其中查閱或輸入資訊。

選用的&#x200B;**Survey**&#x200B;模組可讓您建立新類型的Web應用程式，以建立和管理線上問卷，例如新增或修改描述檔資訊的表單、訂閱或取消訂閱資訊服務或競賽參賽表單。 收集答案後，答案會儲存在資料庫或本機變數中。 通過對問卷的回答，可以動態地擴展資料模型。 您可以即時檢視結果、篩選回應，並使用專用圖表來分析。

本章詳細說明建立和管理&#x200B;**調查**、欄位和頁面管理、儲存模式和記錄的方法。

建立標準Web表單的步驟在[本節](../../web/using/about-web-forms.md)中有詳細說明。

Web應用程式管理在[本節](../../web/using/about-web-applications.md)中有詳細說明。 有關詳細資訊，請參閱本章。

>[!CAUTION]
>
>基於隱私權原因，我們建議對所有外部資源使用HTTPS。

## 功能範圍{#campaign-surveys-scope}

在Adobe Campaign中，Web應用程式一般可讓您存取下列功能：

* 建立多頁表單、
* 使用整合的翻譯工具管理多語言調查、
* 圖形頁面管理介面，多欄頁面版面，
* 呈現個人化和現場位置，
* 根據答案有條件顯示調查欄位、
* 條件式頁面顯示、
* 核准前先檢查資訊，視預期資料類型（編號、電子郵件地址、日期等）而定 和必填欄位，
* 電子郵件邀請／通知、
* 將錯誤和結束訊息個人化，
* 影像、視訊、超文字連結、驗證碼等的使用。

>[!NOTE]
>
>連結至Web表單的所有組態詳見[本節](../../web/using/about-web-forms.md)。 有關使用Adobe Campaign的概念和網頁表單功能的詳細資訊，請參閱本檔案。

選用的調查建立模組(**Survey**)提供下列額外功能：

* 資料庫的動態擴展：建立不屬於初始資料模型的答案。 有關詳細資訊，請參閱[儲存收集的答案](../../web/using/managing-answers.md#storing-collected-answers)。
* 分數管理。 如需詳細資訊，請參閱[分數管理](../../web/using/managing-answers.md#score-management)。
* 隨機顯示問題。 有關詳細資訊，請參閱[添加問題](../../web/using/building-a-survey.md#adding-questions)。
* 即時追蹤答案。 如需詳細資訊，請參閱[回應追蹤](../../web/using/publish--track-and-use-collected-data.md#response-tracking)。
* 產生專用報表。 如需詳細資訊，請參閱調查的[報表](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

與Web應用程式相比，調查具有簡化的圖形介面，並減少編輯控制項的數量。

## 調查實施步驟{#surveys-implementation-steps}

套用下列步驟來建立和傳送調查並處理其結果：

1. 建立調查的頁面及其內容（輸入欄位、下拉式清單、問題等）。
1. 定義應如何儲存答案。

   可以插入資料預載入步驟，以便用資料庫中已有的資料預載入表單。 您也可以新增測試方塊。

1. 發佈，然後將調查傳送給收件者（例如，將連結加入傳送或網站中）。
1. 監控回應並檢視報表。

有關配置和排序這些步驟的詳細資訊，請參閱[本節](../../web/using/about-web-forms.md)。 本章僅詳述調查的特定設定。

## 調查設定{#surveys-configuration}

調查會儲存在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;節點中。 配置位於以下資料夾中：

* **[!UICONTROL Administration > Configuration > Form rendering]**:包含Web表單簡報（應用程式和調查）的轉換範本。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表單範本。若要建立表格，您必須從範本開始。

>[!NOTE]
>
>[本節](../../web/using/about-web-forms.md)中提供了配置資訊。

