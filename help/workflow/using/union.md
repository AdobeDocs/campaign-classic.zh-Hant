---
solution: Campaign Classic
product: campaign
title: 聯集
description: 進一步瞭解Union工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---


# 聯集{#union}

聯合將單個目標中多個入站活動的結果分組。 目標建立時會收到所有結果：因此，必須完成所有先前活動，工會才能執行。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有關配置和使用聯合活動的詳細資訊，請參閱[組合多個目標（聯合）](../../workflow/using/targeting-data.md#combining-several-targets--union-)。

## 聯合示例{#union-example}

在下列範例中，已結合兩個查詢的結果以更新清單。 這兩個查詢會針對收件者。 因此，結果基於同一表。

1. 在兩個查詢後直接插入&#x200B;**[!UICONTROL Union]** -type活動，然後在清單的更新類型活動前將其開啟。
1. 您可以輸入標籤。
1. 選擇&#x200B;**[!UICONTROL Keys only]**&#x200B;協調方法，因為在此示例中，查詢生成的人口包含一致的資料。
1. 如果您已新增查詢的其他資料，您可以決定只保留已共用的資料。
1. 如果希望限制最終人口的大小，請選中&#x200B;**[!UICONTROL Limit size of generated population]**&#x200B;框。

   輸入最大收件者數，並選取人口優先的查詢，以指定此最終編號。

1. 批准聯合活動，然後配置清單更新活動（請參閱[清單更新](../../workflow/using/list-update.md)）。
1. 啟動工作流程。將顯示結果數，並建立或更新清單更新活動中定義的清單。 此清單包含兩個查詢的收件者集，或（如果適用）在上一步驟中定義的數字。

   ![](assets/union_example.png)

## 輸入參數{#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

## 輸出參數{#output-parameters}

* tableName
* 架構
* recCount

這組三個值用於標識聯合所生成的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。
