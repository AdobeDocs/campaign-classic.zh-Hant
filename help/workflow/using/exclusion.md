---
product: campaign
title: 排除
description: 瞭解有關排除工作流活動的詳細資訊
feature: Workflows, Targeting Activity
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 排除{#exclusion}

![](../../assets/v7-only.svg)

安 **排除**-type活動基於從中提取一個或多個其他目標的主目標建立目標。

要配置此活動，請輸入其標籤並選擇主收件人集：主集的總量允許您構造結果。 將排除由主集共用的配置檔案和至少一個輸入活動。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有關配置和使用排除活動的詳細資訊，請參閱 [排除人口（排除）](targeting-data.md#excluding-a-population--exclusion-)。

檢查 **[!UICONTROL Generate complement]** 的雙曲餘切值。 補編將包含主要的外來人口減去即將出來的人口。 然後，將向活動添加附加輸出轉換，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除示例 {#exclusion-examples}

以下示例試圖匯編一份18至30歲的受助者名單，但不包括巴黎居民。

1. 插入並開啟 **[!UICONTROL Exclusion]** -type查詢後的活動。 第一個查詢針對的是生活在巴黎的收件人。 第二個查詢針對18至30歲的人。
1. 輸入主集。 這裡，主集是 **18歲~30歲** 的子菜單。 與第二組相關的元素將從最終結果中排除。
1. 檢查 **[!UICONTROL Generate complement]** 選項。 在這種情況下，補編由居住在巴黎的18至30歲受助者組成。
1. 批准排除配置，然後將更新清單活動插入結果。 如有必要，您還可以向補碼插入附加清單更新。
1. 執行工作流。 在本例中，結果由18至30歲的受助者組成，但居住在巴黎的受助者被排除，並被送至補編。

   ![](assets/exclusion_example.png)

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這組三個值標識了排除所導致的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補碼相關聯的過渡具有相同的參數。
