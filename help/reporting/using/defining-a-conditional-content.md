---
title: 定義條件式內容
seo-title: 定義條件式內容
description: 定義條件式內容
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 定義條件式內容{#defining-a-conditional-content}

您可以限制特定報表項目或頁面的顯示。

若要讓特定項目成為條件，請調整其可見度設定。 有關詳細資訊，請參閱「 [Conditioning（調節）」項目顯示](#conditioning-item-display)。

若要讓一或多個頁面以條件顯示，請使用文字 **[!UICONTROL Test]** 活動。 For more on this, refer to [Conditioning page display](#conditioning-page-display).

## 調節項目顯示器 {#conditioning-item-display}

若要讓部分報表的顯示為條件式，您必須定義其可見性條件：如果未符合這些條件，則不會顯示項目。

可見性條件可能取決於運算子狀態，取決於在報告頁面中選擇或輸入的項目。

本節提供範例，說明頁面上項目的條件 [顯示](../../web/using/form-rendering.md#defining-fields-conditional-display)。

在下列範例中，顯示條件取決於語言：

![](assets/reporting_display_condition.png)

## 調整頁面顯示器 {#conditioning-page-display}

在報表的圖表中，活動 **[!UICONTROL Test]** 可讓您根據一或多個條件變更頁面順序。

本活動以下列操作原則為基礎：

1. 將圖表 **[!UICONTROL Test]** 中置入並加以編輯。
1. 按一下 **[!UICONTROL Add]** 按鈕以建立各種可能的案例。

   ![](assets/reporting_test_sample.png)

   對於每種情況，都會向活動添加輸出 **[!UICONTROL Test]** 轉變。

   ![](assets/reporting_test_transitions.png)

1. 選取 **[!UICONTROL Enable default transition]** 要新增轉場的項目，以防其中一個設定的條件不符合。

   如需詳細資訊，請參閱[本小節](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

可 **[!UICONTROL Test]** 以在圖表的開頭放置活動，以根據上下文或運算子配置檔案來調整顯示。
