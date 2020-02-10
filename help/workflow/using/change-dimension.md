---
title: 變更維度
seo-title: 變更維度
description: 變更維度
seo-description: null
page-status-flag: never-activated
uuid: 6cb309c0-4096-47ce-b1d4-37a3ddafaaa1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 61583062-2349-4ab3-a3bf-310d21894f34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 變更維度{#change-dimension}

變更維度活動可讓您在目標建構週期中變更目標維度。 軸偏移取決於資料模板和輸入維。 例如，這可讓您從「合約」維度切換至「客戶」維度。

您也可以使用此活動來定義新目標的其他列。

可以定義重複資料消除標準。

## 配置模式 {#configuration-mode}

要配置更改維活動，請應用以下步驟：

1. 透過欄位選取新的定位 **[!UICONTROL Change dimension]** 維度。

   ![](assets/s_user_change_dimension_param1.png)

1. 在尺寸更改期間，您可以保留所有元素或選擇要保留在輸出中的元素。 在下例中，最大值。 重複項數設為2。

   ![](assets/s_user_change_dimension_limit.png)

   當您選擇只保留一個記錄時，系列會顯示在工作結構中：此集合代表所有不會在最終結果中定位的記錄（因為只保留一個記錄）。 和其他所有系列一樣，此系列可讓您計算欄中的匯總或復原資訊。

   例如，如果您將維 **[!UICONTROL Customers]** 度變更為維 **[!UICONTROL Recipients]** 度，則可定位特定商店的客戶，同時新增購買次數。

1. 如果您選擇不保留所有這些資訊，則可以配置複製管理模式。

   ![](assets/s_user_change_dimension_param2.png)

   藍色箭頭可讓您定義重複的處理優先順序。

   在上述範例中，收件者會先在其電子郵件地址上進行去重複化，然後視需要在其帳號上進行去重複化。

1. 此標 **[!UICONTROL Result]** 簽可讓您新增其他資訊。

   例如，您可以使用子字串類型函式，根據郵遞區號來 **復原郡** 。 操作步驟：

   * 按一下連 **[!UICONTROL Add data...]** 結並選取 **[!UICONTROL Data linked to the filtering dimension]**。

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >有關建立和管理附加列的資訊，請參閱添 [加資料](../../workflow/using/query.md#adding-data)。

   * 選取先前的定位維度（軸切換前），並在收件 **[!UICONTROL Zip Code]** 者的子樹狀結構中 **[!UICONTROL Location]** 選取，然後按一下 **[!UICONTROL Edit expression]**。

      ![](assets/wf_change-dimension_sample_02.png)

   * 按一 **[!UICONTROL Advanced selection]** 下並選擇 **[!UICONTROL Edit the formula using an expression]**。

      ![](assets/wf_change-dimension_sample_03.png)

   * 使用清單中提供的函式，並指定要執行的計算。

      ![](assets/wf_change-dimension_sample_04.png)

   * 最後，輸入您剛建立的列的標籤。

      ![](assets/wf_change-dimension_sample_05.png)

1. 執行工作流以查看此配置的結果。 比較變更維活動前後表格中的資料，並比較工作流表的結構，如下列範例所示：

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

