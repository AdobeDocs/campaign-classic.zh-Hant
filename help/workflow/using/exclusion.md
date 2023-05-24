---
product: campaign
title: 排除
description: 進一步瞭解排除工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 排除{#exclusion}



一個 **排除**-type活動會根據擷取一或多個其他目標的主要目標建立目標。

若要設定此活動，請輸入其標籤並選取主要收件者集：主要集的母體可讓您建構結果。 將排除主要集和至少一個登入活動共用的設定檔。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>有關設定和使用排除活動的詳細資訊，請參閱 [排除人口（排除）](targeting-data.md#excluding-a-population--exclusion-).

檢查 **[!UICONTROL Generate complement]** 選項（如果要利用剩餘母體）。 補碼將包含主要傳入母體減去傳出母體。 隨後會將其他輸出轉變新增至活動，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除範例 {#exclusion-examples}

下列範例會嘗試編譯18至30歲之間的收件者清單，但不包括巴黎居民。

1. 插入並開啟 **[!UICONTROL Exclusion]** -type活動。 第一個查詢會鎖定居住在巴黎的收件者。 第二個查詢會鎖定年齡在18至30歲之間的人。
1. 輸入主集。 主要集為 **18-30歲** 查詢。 將從最終結果中排除與第二個集合相關的元素。
1. 檢查 **[!UICONTROL Generate complement]** 選項（如果您想要利用排除後剩餘的資料）。 在此案例中，補充是由居住在巴黎的18至30歲收件者組成。
1. 核准排除設定，然後插入更新清單活動到結果。 您也可以視需要插入其他清單更新至補充。
1. 執行工作流程。 在此範例中，結果由18至30歲的收件者組成，但住在巴黎者會被排除並傳送至補充。

   ![](assets/exclusion_example.png)

## 輸入引數 {#input-parameters}

* tableName
* 綱要

每個傳入事件都必須指定由這些引數定義的目標。

## 輸出引數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值會識別排除所產生的目標。 **[!UICONTROL tableName]** 是記錄目標識別碼的資料表名稱， **[!UICONTROL schema]** 為母體的結構描述（通常為nms：recipient）和 **[!UICONTROL recCount]** 是表格中的元素數量。

與補碼關聯的轉變具有相同的引數。
