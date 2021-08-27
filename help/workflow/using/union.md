---
product: campaign
title: 聯合
description: 深入了解Union工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# 聯合{#union}

![](../../assets/common.svg)

聯合會將單一目標中數個入站活動的結果分組。 目標建立時會收到所有結果：因此，必須完成所有先前的活動才能執行聯合。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有關配置和使用聯合活動的詳細資訊，請參閱[組合多個目標（聯合）](targeting-data.md#combining-several-targets--union-)。

## 聯合範例 {#union-example}

在以下範例中，已結合兩個查詢的結果以更新清單。 這兩個查詢會鎖定收件者。 因此，結果是以相同表格為基礎。

1. 在兩個查詢後和清單的更新類型活動前插入&#x200B;**[!UICONTROL Union]** -type活動，然後開啟它。
1. 您可以輸入標籤。
1. 選取&#x200B;**[!UICONTROL Keys only]**&#x200B;調解方法，因為在此範例中，查詢產生的母體包含一致的資料。
1. 如果已為查詢新增其他資料，您可以決定僅保留已共用的資料。
1. 如果要限制最終母體的大小，請核取&#x200B;**[!UICONTROL Limit size of generated population]**&#x200B;方塊。

   輸入最大收件者人數，並選取母體將優先順序排列的查詢，以指定此最終編號。

1. 核准聯合活動，然後設定清單更新活動（請參閱[清單更新](list-update.md)）。
1. 開始工作流程. 將顯示結果數，並建立或更新清單更新活動中定義的清單。 此清單包含查詢的收件者集合，如果適用，則包含上一步定義的數字。

   ![](assets/union_example.png)

## 輸入參數 {#input-parameters}

* tableName
* 綱要

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值識別聯合後產生的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是母體（通常為nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素數。
