---
product: campaign
title: 開始使用意見調查
description: 開始使用Campaign調查
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---

# 開始使用意見調查{#about-surveys}

Adobe Campaign包含圖形模組，可定義及發佈Web應用程式。 它用於建立頁面，如外聯網上的編輯表單或通知表單，包括資料庫中的資料，包括表、圖表、輸入表單等。 此功能可讓您設計和發佈網頁，讓使用者可在其中查詢或輸入資訊。

可選的&#x200B;**Survey**&#x200B;模組允許您建立新類型的Web應用程式，以建立和管理線上調查表，例如添加或修改配置檔案資訊的表單、訂閱或取消訂閱資訊服務或競爭參加表單。 收集到答案後，答案會儲存在資料庫或本機變數中。 資料模型可通過對問卷的回答動態擴展。 您可以即時檢視結果、篩選回應，並使用專用圖表加以分析。

本章詳細說明建立和管理&#x200B;**調查**、欄位和頁面管理、儲存模式和記錄的方法。

在[本節](../../web/using/about-web-forms.md)中詳細說明建立標準Web表單的步驟。

在[本節](../../web/using/about-web-applications.md)中詳細介紹Web應用程式管理。 如需詳細資訊，請參閱本章。

>[!CAUTION]
>
>基於隱私權考量，我們建議對所有外部資源使用HTTPS。

## 功能範圍{#campaign-surveys-scope}

在Adobe Campaign中，一般Web應用程式可讓您存取下列功能：

* 建立多頁表單，
* 使用整合的翻譯工具管理多語言調查，
* 圖形化頁面管理介面，多欄頁面配置，
* 呈現個人化和欄位位置，
* 根據答案有條件地顯示調查欄位，
* 條件式頁面顯示，
* 視預期的資料類型（號碼、電子郵件地址、日期等）而定，在核准前檢查資訊 和必填欄位，
* 電子郵件邀請/通知，
* 錯誤和結束訊息的個人化，
* 影像、影片、超文字連結、驗證碼等的使用。

>[!NOTE]
>
>連結到Web表單的所有配置在[本部分](../../web/using/about-web-forms.md)中有詳細說明。 如需使用Adobe Campaign的概念和網頁表單功能的詳細資訊，請參閱本檔案。

選用的調查建立模組(**Survey**)提供下列其他功能：

* 資料庫的動態擴展：建立不屬於初始資料模型的答案。 有關詳細資訊，請參閱[儲存收集的答案](../../web/using/managing-answers.md#storing-collected-answers)。
* 分數管理。 有關詳細資訊，請參閱[分數管理](../../web/using/managing-answers.md#score-management)。
* 隨機顯示問題。 有關詳細資訊，請參閱[新增問題](../../web/using/building-a-survey.md#adding-questions)。
* 即時追蹤答案。 如需詳細資訊，請參閱[回應追蹤](../../web/using/publish--track-and-use-collected-data.md#response-tracking)。
* 產生專用報表。 如需詳細資訊，請參閱[調查報表](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys)。

與Web應用程式相比，調查具有簡化的圖形介面，編輯控制項的數量減少。

## 調查實施步驟{#surveys-implementation-steps}

套用下列步驟來建立和傳送調查並處理其結果：

1. 建立調查的頁面及其內容（輸入欄位、下拉式清單、問題等）。
1. 定義應如何儲存答案。

   可以插入資料預載入步驟，以便使用資料庫中已有的資料預先載入表單。 您也可以新增測試方塊。

1. 發佈，然後將調查傳送給收件者（例如在傳遞或網站中包含連結）。
1. 監視回應並檢視報表。

有關配置和排序這些步驟的詳細資訊，請參閱[此部分](../../web/using/about-web-forms.md)。 本章僅詳細說明調查的特定設定。

## 調查設定{#surveys-configuration}

調查會儲存在Adobe Campaign樹的&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;節點中。 配置位於以下資料夾中：

* **[!UICONTROL Administration > Configuration > Form rendering]**:包含用於Web表單演示（應用程式和調查）的呈現模板。
* **[!UICONTROL Resources > Templates > Web application templates]**:包含表單範本。若要建立表單，您必須從範本開始。

>[!NOTE]
>
>[此部分](../../web/using/about-web-forms.md)中提供配置資訊。
