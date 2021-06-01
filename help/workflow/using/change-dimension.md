---
product: campaign
title: 變更維度
description: 變更維度
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# 變更維度{#change-dimension}

變更維度活動可讓您在目標建構週期期間變更目標維度。 軸移取決於資料範本和輸入維度。 例如，這可讓您從「合約」維度切換至「用戶端」維度。

您也可以使用此活動來定義新目標的其他欄。

可以定義重複資料刪除標準。

## 配置模式{#configuration-mode}

若要設定變更維度活動，請套用下列步驟：

1. 透過&#x200B;**[!UICONTROL Change dimension]**&#x200B;欄位選取新的目標維度。

   ![](assets/s_user_change_dimension_param1.png)

1. 在尺寸更改期間，您可以保留所有元素或選擇要保留在輸出中的元素。 在下列範例中，最大值為。 重複項目數設為2。

   ![](assets/s_user_change_dimension_limit.png)

   當您選擇僅保留一條記錄時，工作架構中會顯示一個集合：此集合表示在最終結果中不會定位的所有記錄（因為只保留一個記錄）。 與所有其他集合一樣，此集合可讓您計算欄中的匯總或復原資訊。

   例如，如果您將&#x200B;**[!UICONTROL Customers]**&#x200B;維度變更為&#x200B;**[!UICONTROL Recipients]**&#x200B;維度，則可在新增購買次數時鎖定特定商店的客戶。

1. 如果您選擇不保留所有這些資訊，則可以配置重複管理模式。

   ![](assets/s_user_change_dimension_param2.png)

   藍色箭頭可讓您定義重複的處理優先順序。

   在上述範例中，收件者的電子郵件地址會先刪除重複項目，然後視需要刪除其帳號。

1. **[!UICONTROL Result]**&#x200B;標籤可讓您新增其他資訊。

   例如，您可以使用&#x200B;**Substring**&#x200B;類型函式，根據郵遞區號來復原縣。 操作步驟：

   * 按一下&#x200B;**[!UICONTROL Add data...]**&#x200B;連結並選取&#x200B;**[!UICONTROL Data linked to the filtering dimension]**。

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >有關建立和管理其他列的資訊，請參閱[Adding data](../../workflow/using/query.md#adding-data)。

   * 選取先前的目標維度（軸切換前），並在收件者的&#x200B;**[!UICONTROL Location]**&#x200B;子樹中選取&#x200B;**[!UICONTROL Zip Code]**，然後按一下&#x200B;**[!UICONTROL Edit expression]**。

      ![](assets/wf_change-dimension_sample_02.png)

   * 按一下&#x200B;**[!UICONTROL Advanced selection]**&#x200B;並選擇&#x200B;**[!UICONTROL Edit the formula using an expression]**。

      ![](assets/wf_change-dimension_sample_03.png)

   * 使用清單中提供的函式並指定要執行的計算。

      ![](assets/wf_change-dimension_sample_04.png)

   * 最後，輸入剛建立的列的標籤。

      ![](assets/wf_change-dimension_sample_05.png)

1. 執行工作流以查看此配置的結果。 比較變更維度活動前後表格中的資料，並比較工作流程表格的結構，如下列範例所示：

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
