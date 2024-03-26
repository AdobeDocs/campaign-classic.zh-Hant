---
product: campaign
title: 變更維度
description: 變更維度
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 4%

---

# 變更維度{#change-dimension}



變更維度活動可讓您在目標建構週期中變更目標維度。 座標軸移動取決於資料範本和輸入維度。 例如，這可讓您從「合約」維度切換至「客戶」維度。

您也可以使用此活動來定義新目標的其他欄。

您可以定義重複資料刪除的條件。

## 設定模式 {#configuration-mode}

若要設定變更維度活動，請套用下列步驟：

1. 透過以下方式選取新的目標維度 **[!UICONTROL Change dimension]** 欄位。

   ![](assets/s_user_change_dimension_param1.png)

1. 在尺寸變更期間，您可以保留所有元素或選取要保留在輸出中的元素。 在下列範例中，最大值為 重複專案數設為2。

   ![](assets/s_user_change_dimension_limit.png)

   當您選擇只保留一個記錄時，會在工作結構描述中顯示集合：此集合代表最終結果中未鎖定目標的所有記錄（因為只保留一個記錄）。 如同其他所有集合，這個集合可讓您計算彙總或復原欄中的資訊。

   例如，如果您變更 **[!UICONTROL Customers]** 的維度 **[!UICONTROL Recipients]** 維度時，將可以鎖定特定商店的客戶，同時新增購買的次數。

1. 如果您選擇不保留所有這些資訊，您可以設定重複管理模式。

   ![](assets/s_user_change_dimension_param2.png)

   藍色箭頭可讓您定義重複的處理優先順序。

   在上述範例中，收件者會先在其電子郵件地址上刪除重複專案，然後視需要在其帳號上刪除重複專案。

1. 此 **[!UICONTROL Result]** 索引標籤可讓您新增其他資訊。

   例如，您可以使用根據郵遞區號復原縣 **子字串** type函式。 操作步驟：

   * 按一下 **[!UICONTROL Add data...]** 連結並選取 **[!UICONTROL Data linked to the filtering dimension]**.

     ![](assets/wf_change-dimension_sample_01.png)

     >[!NOTE]
     >
     >有關建立和管理其他欄的資訊，請參閱 [新增資料](query.md#adding-data).

   * 選取上一個目標維度（在軸切換前），並選取 **[!UICONTROL Zip Code]** 在收件者的 **[!UICONTROL Location]** 子樹，然後按一下 **[!UICONTROL Edit expression]**.

     ![](assets/wf_change-dimension_sample_02.png)

   * 按一下 **[!UICONTROL Advanced selection]** 並選擇 **[!UICONTROL Edit the formula using an expression]**.

     ![](assets/wf_change-dimension_sample_03.png)

   * 使用清單中提供的函式並指定要執行的計算。

     ![](assets/wf_change-dimension_sample_04.png)

   * 最後，輸入您剛建立之欄的標籤。

     ![](assets/wf_change-dimension_sample_05.png)

1. 執行工作流程以檢視此設定的結果。 比較變更維度活動前後表格中的資料，並比較工作流程表格的結構，如下列範例所示：

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
