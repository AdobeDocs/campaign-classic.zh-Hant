---
product: campaign
title: 定義條件式內容
description: 定義條件式內容
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---

# 定義條件式內容{#defining-a-conditional-content}

![](../../assets/common.svg)

您可以限制特定報表項目或頁面的顯示。

若要將特定項目設為條件式，請調整其可見度設定。 有關詳細資訊，請參閱 [調節項顯示](#conditioning-item-display).

若要讓一或多個頁面的顯示成為條件，請使用 **[!UICONTROL Test]** 類型活動。 有關詳細資訊，請參閱 [調整頁面顯示](#conditioning-page-display).

## 調節項顯示 {#conditioning-item-display}

若要讓報表的部分顯示成為條件式，需要定義其可見性條件：如果不符合這些條件，則不會顯示項目。

可見性條件可能取決於運算子狀態，取決於在報表頁面中選取或輸入的項目。

顯示頁面上項目有條件顯示的範例，位於 [本節](../../web/using/form-rendering.md#defining-fields-conditional-display).

在下列範例中，顯示條件取決於語言：

![](assets/reporting_display_condition.png)

## 調整頁面顯示 {#conditioning-page-display}

在報表的圖表中， **[!UICONTROL Test]** 活動可讓您根據一或多個條件來變更頁面順序。

此活動以下列操作原則為基礎：

1. 放置 **[!UICONTROL Test]** 並加以編輯。
1. 按一下 **[!UICONTROL Add]** 按鈕以建立各種可能的案例。

   ![](assets/reporting_test_sample.png)

   對於每種情況，都會將輸出轉變新增至 **[!UICONTROL Test]** 活動。

   ![](assets/reporting_test_transitions.png)

1. 選取 **[!UICONTROL Enable default transition]** 若要新增轉變，若未符合其中一個已設定的條件。

   如需詳細資訊，請參閱[本章節](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

A **[!UICONTROL Test]** 活動可放置在圖表的開頭，以根據上下文或運算子設定檔來調整顯示。
