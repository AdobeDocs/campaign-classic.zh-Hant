---
product: campaign
title: 開始使用意見調查
description: 開始使用Campaign調查
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# 開始使用意見調查{#about-surveys}

Adobe Campaign包含圖形模組，可定義及發佈Web應用程式。 它用於建立頁面，如外聯網上的編輯表單或通知表單，包括資料庫中的資料，包括表、圖表、輸入表單等。 使用此功能來設計和發佈用戶可以查找或輸入資訊的網頁。

可選的&#x200B;**Survey**&#x200B;附加元件可讓您建立新類型的Web應用程式，以建立和管理線上調查表，例如添加或修改配置檔案資訊的表單、訂閱或取消訂閱資訊服務或競爭參加表單。 收集到答案後，答案會儲存在資料庫或本機變數中。 資料模型可通過對問卷的回答動態擴展。 您可以即時檢視結果、篩選回應，並使用專用圖表加以分析。

本章詳細說明如何建立和管理&#x200B;**調查**、欄位和頁面管理、儲存模式和記錄。

[!DNL :bulb:] 在本頁面中了解如何建立您的第 [一個調查](getting-started-with-surveys.md)。

>[!NOTE]
>
>* 有關建立標準Web表單的詳細步驟，請參見[本文檔](../../web/using/about-web-forms.md)。
   >
   >
* 在[本文檔](../../web/using/about-web-applications.md)中詳細介紹了Web應用程式管理。 如需詳細資訊，請參閱本章。


## 功能範圍 {#campaign-surveys-scope}

在Adobe Campaign中，使用[Web應用程式](../../web/using/about-web-forms.md)以：

* 建立多頁表單，
* 使用整合的翻譯工具管理多語言表單，
* 管理圖形介面、多列頁面佈局、
* 新增個人化和定義欄位位置，
* 根據答案顯示調查欄位的條件，
* 條件頁面顯示、
* 視預期的資料類型（號碼、電子郵件地址、日期等）而定，在核准前檢查資訊 和必填欄位，
* 傳送電子郵件邀請/通知，
* 個人化錯誤和結束頁面，
* 在表單中新增影像、影片、超文字連結、驗證碼等

選用的調查建立模組提供方便使用的UI，以及下列其他功能：

* 資料庫的動態擴展：建立不屬於初始資料模型的答案。 [深入瞭解](../../surveys/using/managing-answers.md#storing-collected-answers)。
* 分數管理。 [深入瞭解](../../surveys/using/managing-answers.md#score-management)。
* 隨機顯示問題。 [深入瞭解](../../surveys/using/building-a-survey.md#adding-questions)。
* 即時追蹤答案。 [深入瞭解](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)。
* 產生專用報表。 [深入瞭解](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)。


## 實施步驟 {#surveys-implementation-steps}

套用下列步驟來建立和傳送調查並處理其結果：

1. 建立調查的頁面及其內容（輸入欄位、下拉式清單、問題等）。
1. 定義應如何儲存答案。 可以插入資料預載入步驟，以便使用資料庫中已有的資料預先載入表單。 您也可以新增測試方塊。
1. 發佈，然後將調查傳送給收件者（例如在傳遞或網站中包含連結）。
1. 監視回應並檢視報表。

有關配置和排序這些步驟的詳細資訊，請參閱[本文檔](../../web/using/about-web-forms.md)。 本章僅詳細說明調查的特定設定。

>[!CAUTION]
>
>基於隱私權考量，我們建議對所有外部資源使用HTTPS。

## 設定 {#settings}

依預設，調查可在Adobe Campaign樹的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;節點中使用。

設定會儲存在下列資料夾中：

* **[!UICONTROL Administration > Configuration > Form rendering]**:包含用於Web表單演示（應用程式和調查）的呈現模板。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表單範本。若要建立表單，您必須從範本開始。

>[!NOTE]
>
>在[本文檔](../../web/using/about-web-forms.md)中提供了設定詳細資訊。
