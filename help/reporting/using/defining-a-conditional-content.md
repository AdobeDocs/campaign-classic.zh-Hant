---
solution: Campaign Classic
product: campaign
title: 定義條件式內容
description: 定義條件式內容
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---


# 定義條件式內容{#defining-a-conditional-content}

您可以限制特定報表項目或頁面的顯示。

若要讓特定項目成為條件，請調整其可見度設定。 有關詳細資訊，請參閱[Conditioning item display](#conditioning-item-display)。

若要讓一或多個頁面以條件顯示，請使用&#x200B;**[!UICONTROL Test]**&#x200B;類型活動。 有關詳細資訊，請參閱[Conditioning page display](#conditioning-page-display)。

## 調節項目顯示{#conditioning-item-display}

若要讓部分報表的顯示為條件式，您必須定義其可見性條件：如果未符合這些條件，則不會顯示項目。

可見性條件可能取決於運算子狀態，取決於在報告頁面中選擇或輸入的項目。

[本節](../../web/using/form-rendering.md#defining-fields-conditional-display)提供顯示頁面上項目條件顯示的範例。

在下列範例中，顯示條件取決於語言：

![](assets/reporting_display_condition.png)

## 調整頁面顯示{#conditioning-page-display}

在報表的圖表中，**[!UICONTROL Test]**&#x200B;活動可讓您根據一或多個條件變更頁面順序。

本活動以下列操作原則為基礎：

1. 將&#x200B;**[!UICONTROL Test]**&#x200B;置於圖表中並加以編輯。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕可建立各種可能的情況。

   ![](assets/reporting_test_sample.png)

   對於每種情況，都會向&#x200B;**[!UICONTROL Test]**&#x200B;活動添加一個輸出轉變。

   ![](assets/reporting_test_transitions.png)

1. 選擇&#x200B;**[!UICONTROL Enable default transition]**&#x200B;以添加過渡，以防其中一個配置的條件不符合。

   如需詳細資訊，請參閱[本章節](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

**[!UICONTROL Test]**&#x200B;活動可放置在圖表的開頭，以根據上下文或運算子描述檔來調整顯示。
