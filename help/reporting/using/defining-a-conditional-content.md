---
product: campaign
title: 定義條件式內容
description: 定義條件式內容
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 7%

---

# 定義條件式內容{#defining-a-conditional-content}



您可以設定顯示特定報表專案或頁面的條件。

若要讓特定專案成為條件專案，請調整其可見度設定。 如需詳細資訊，請參閱[條件專案顯示](#conditioning-item-display)。

若要以條件方式顯示一或多個頁面，請使用&#x200B;**[!UICONTROL Test]**&#x200B;型別活動。 如需詳細資訊，請參閱[條件頁面顯示](#conditioning-page-display)。

## 條件專案顯示 {#conditioning-item-display}

若要使顯示的部分報表成為條件式，您必須定義其可見性條件：如果不滿足這些條件，將不會顯示專案。

可視性條件可能取決於運運算元狀態、在報告頁面中選取或輸入的專案。

[此區段](../../web/using/form-rendering.md#defining-fields-conditional-display)中提供了顯示頁面上專案條件式顯示的範例。

在下列範例中，顯示條件取決於語言：

![](assets/reporting_display_condition.png)

## 條件頁面顯示 {#conditioning-page-display}

在報表的圖表中，**[!UICONTROL Test]**&#x200B;活動可讓您根據一或多個條件變更頁面順序。

本活動以下列操作原則為基礎：

1. 將&#x200B;**[!UICONTROL Test]**&#x200B;放入圖表並加以編輯。
1. 按一下「**[!UICONTROL Add]**」按鈕以建立各種可能的情況。

   ![](assets/reporting_test_sample.png)

   針對每種情況，都會將輸出轉換新增至&#x200B;**[!UICONTROL Test]**&#x200B;活動。

   ![](assets/reporting_test_transitions.png)

1. 選取&#x200B;**[!UICONTROL Enable default transition]**&#x200B;以新增轉變，以防其中一個設定的條件不符合。

   如需詳細資訊，請參閱[本章節](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

**[!UICONTROL Test]**&#x200B;活動可放置在圖表開頭，以根據執行個體的內容或運運算元設定檔來設定顯示的條件。
