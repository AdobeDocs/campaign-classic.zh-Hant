---
product: campaign
title: 聯合
description: 瞭解有關聯合工作流活動的詳細資訊
feature: Workflows, Targeting Activity
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# 聯合{#union}

![](../../assets/common.svg)

聯合將單個目標中多個入站活動的結果分組。 建立目標時會收到所有結果：因此，必須完成所有以前的活動才能執行工會。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有關配置和使用聯合活動的詳細資訊，請參閱 [合併多個目標（聯合）](targeting-data.md#combining-several-targets--union-)。

## 聯合示例 {#union-example}

在以下示例中，已合併兩個查詢的結果以更新清單。 這兩個查詢針對收件人。 因此，結果基於同一表。

1. 插入 **[!UICONTROL Union]** -type活動在兩個查詢後直接在清單的update-type活動前開啟。
1. 您可以輸入標籤。
1. 選擇 **[!UICONTROL Keys only]** 協調方法，因為在本示例中，由查詢產生的填充包含一致的資料。
1. 如果為查詢添加了其他資料，則可以決定只保留共用的資料。
1. 如果希望限制最終人口的大小，請檢查 **[!UICONTROL Limit size of generated population]** 框。

   通過輸入最大收件人數和選擇其填充將優先的查詢來指定此最終編號。

1. 批准聯合活動，然後配置清單更新活動(請參閱 [清單更新](list-update.md))。
1. 開始工作流程. 顯示結果數，並建立或更新清單更新活動中定義的清單。 此清單包含查詢和上一步定義的數字的收件人集。

   ![](assets/union_example.png)

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這組三個值標識了聯合產生的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。
