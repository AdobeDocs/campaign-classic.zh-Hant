---
product: campaign
title: 開始使用意見調查
description: 開始進行活動調查
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# 開始使用意見調查{#about-surveys}

![](../../assets/v7-only.svg)

Adobe Campaign包含一個圖形模組，用於定義和發佈Web應用程式。 它用於建立頁面，如外聯網上的編輯表單或通知表單，包括來自資料庫的資料以及表、圖表、輸入表單等。 使用此功能可以設計和發佈網頁，用戶可以在其中查找或輸入資訊。

可選 **調查** 外接程式允許您建立新類型的Web應用程式以建立和管理聯機調查表，如添加或修改配置檔案資訊的表單、訂閱或取消訂閱資訊服務或競爭條目表單。 一旦收集了答案，它們就會儲存在資料庫或本地變數中。 通過對問卷的回答可以動態地擴展資料模型。 您可以即時查看結果，過濾響應，並使用專用圖表分析它們。

本章詳細介紹如何建立和管理 **調查**、欄位和頁面管理、儲存模式和記錄。

瞭解如何在 [此頁](getting-started-with-surveys.md)。

>[!NOTE]
>
>* 有關建立標準Web表單的詳細步驟，請參見 [此文檔](../../web/using/about-web-forms.md)。
>
>* Web應用程式管理在 [此文檔](../../web/using/about-web-applications.md)。 有關詳細資訊，請參閱本章。


## 功能範圍 {#campaign-surveys-scope}

在Adobe Campaign，使用 [Web應用程式](../../web/using/about-web-forms.md) 至：

* 建立多頁表單，
* 使用整合的翻譯工具管理多語言表單，
* 管理圖形介面、多列頁面佈局、
* 添加個性化並定義欄位位置，
* 根據答案顯示調查欄位的條件，
* 條件頁顯示，
* 在批准前檢查資訊，具體取決於預期的資料類型（數字、電子郵件地址、日期等） 和強制欄位，
* 發送電子郵件邀請/通知，
* 個性化錯誤和結束頁，
* 在表單中添加影像、視頻、超文本連結、驗證碼等

可選的調查建立模組提供了用戶友好的UI和以下附加功能：

* 資料庫的動態擴展：建立不屬於初始資料模型的答案。 [了解更多](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 分數管理。 [了解更多](../../surveys/using/managing-answers.md#score-management)。
* 隨機顯示問題。 [了解更多](../../surveys/using/building-a-survey.md#adding-questions)。
* 即時跟蹤答案。 [了解更多](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)。
* 生成專用報告。 [了解更多](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)。


## 實施步驟 {#surveys-implementation-steps}

應用以下步驟建立並交付調查並處理其結果：

1. 建立調查的頁面及其內容（輸入欄位、下拉清單、問題等）。
1. 定義應如何保存答案。 可以插入資料預載入步驟，以便用資料庫中已有的資料預載入表單。 也可以添加test框。
1. 發佈，然後將調查發送給收件人（例如，在遞送或網站中包含連結）。
1. 監視響應並查看報告。

有關配置和排序這些步驟的詳細資訊，請參閱 [此文檔](../../web/using/about-web-forms.md)。 本章僅詳細介紹特定於調查的配置。

>[!CAUTION]
>
>出於隱私原因，我們建議對所有外部資源使用HTTPS。

## 設定 {#settings}

預設情況下，在 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign樹的節點。

設定儲存在以下資料夾中：

* **[!UICONTROL Administration > Configuration > Form rendering]**:包含Web表單演示（應用程式和調查）的呈現模板。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含窗體模板。 要建立表單，需要從模板開始。

>[!NOTE]
>
>設定詳細資訊可在 [此文檔](../../web/using/about-web-forms.md)。
