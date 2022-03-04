---
product: campaign
title: 定義條件式內容
description: 定義條件式內容
feature: Reporting
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---

# 定義條件式內容{#defining-a-conditional-content}

![](../../assets/common.svg)

您可以限制特定報表項或頁面的顯示。

要使特定項目成為條件，請調整其可見性設定。 有關此內容的詳細資訊，請參閱 [條件項顯示](#conditioning-item-display)。

要使一個或多個頁面的顯示成為條件，請使用 **[!UICONTROL Test]** 鍵入活動。 有關此內容的詳細資訊，請參閱 [條件頁顯示](#conditioning-page-display)。

## 條件項顯示 {#conditioning-item-display}

要使報告的部分顯示為條件，需要定義其可見性條件：如果未滿足這些要求，則不顯示項目。

可視性條件可能取決於操作員狀態，取決於在報告頁中選擇或輸入的項。

中提供了顯示頁面上項的條件顯示的示例 [此部分](../../web/using/form-rendering.md#defining-fields-conditional-display)。

在以下示例中，顯示條件取決於語言：

![](assets/reporting_display_condition.png)

## 條件頁顯示 {#conditioning-page-display}

在報表的圖表中， **[!UICONTROL Test]** 活動允許您根據一個或多個條件更改頁序。

本活動基於以下操作原則：

1. 放置a **[!UICONTROL Test]** 編輯。
1. 按一下 **[!UICONTROL Add]** 按鈕，將選定控制項在Tab鍵次序中下移一個位置。

   ![](assets/reporting_test_sample.png)

   對於每種情況，將輸出轉換添加到 **[!UICONTROL Test]** 的子菜單。

   ![](assets/reporting_test_transitions.png)

1. 選擇 **[!UICONTROL Enable default transition]** 添加過渡時，如果未滿足配置的條件之一，請執行此操作。

   如需詳細資訊，請參閱[本章節](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

A **[!UICONTROL Test]** 活動可放置在圖表的開頭，以根據上下文或運算子配置檔案（例如）來限制顯示。
