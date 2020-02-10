---
title: 聯合
seo-title: 聯合
description: 聯合
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 聯合{#union}

聯合將單個目標中多個入站活動的結果分組。 目標建立時會收到所有結果：因此，必須完成所有先前活動，工會才能執行。

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>有關配置和使用聯合活動的詳細資訊，請參 [閱組合多個目標（聯合）](../../workflow/using/targeting-data.md#combining-several-targets--union-)。

## Union範例 {#union-example}

在下列範例中，已結合兩個查詢的結果以更新清單。 這兩個查詢會針對收件者。 因此，結果基於同一表。

1. 在兩個 **[!UICONTROL Union]** 查詢後直接插入-type活動，然後在清單的更新類型活動前直接將其開啟。
1. 您可以輸入標籤。
1. 選擇協 **[!UICONTROL Keys only]** 調方法，因為在本示例中，由查詢生成的人口包含一致的資料。
1. 如果您已為查詢新增其他資料，您可以決定只保留已共用的資料。
1. 如果希望限制最終人口的大小，請選中該 **[!UICONTROL Limit size of generated population]** 框。

   輸入最大收件者數，並選取人口優先的查詢，以指定此最終編號。

1. 批准聯合活動，然後配置清單更新活動(請參 [閱清單更新](../../workflow/using/list-update.md))。
1. 啟動工作流程。 將顯示結果數，並建立或更新清單更新活動中定義的清單。 此清單包含兩個查詢的收件者集，或（如果適用）在上一步驟中定義的數字。

   ![](assets/union_example.png)

## 輸入參數 {#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這組三個值用於標識聯合所生成的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。
