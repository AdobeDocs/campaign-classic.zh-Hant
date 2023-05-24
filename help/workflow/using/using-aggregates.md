---
product: campaign
title: 使用彙總
description: 瞭解如何使用彙總
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 12b173e9-5068-4d45-9e1e-2aecc9866e9c
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---

# 使用彙總{#using-aggregates}



此使用案例詳細說明如何自動識別新增至資料庫的最後一位收件者。

使用下列程式，將資料庫中收件者的建立日期與使用彙總建立收件者的最後已知日期進行比較。 也會選取當天建立的所有收件者。

執行 **建立日期=上限（建立日期）** 在收件者上輸入篩選器，您必須執行工作流程才能遵循下列步驟：

1. 使用基本查詢擷取資料庫收件者。 如需此步驟的詳細資訊，請參閱 [建立查詢](query.md#creating-a-query).
1. 使用產生的結果計算上次建立收件者的已知日期。 **最大（建立日期）** 彙總函式。
1. 將每個收件者連結至彙總函式會產生相同的結構描述。
1. 透過已編輯的結構描述使用彙總來篩選收件者。

![](assets/datamanagement_usecase_1.png)

## 步驟1：計算彙總結果 {#step-1--calculating-the-aggregate-result}

1. 建立查詢。 在此處，目標是計算資料庫中所有收件者的最後已知建立日期。 因此，查詢不包含篩選器。
1. 選取 **[!UICONTROL Add data]**。
1. 在開啟的視窗中，選取 **[!UICONTROL Data linked to the filtering dimension]** 則 **[!UICONTROL Filtering dimension data]**.
1. 在 **[!UICONTROL Data to add]** 視窗，新增一個欄以計算 **建立日期** 收件者表格中的欄位。 您可以使用運算式編輯器或輸入 **max(@created)** 直接放入中的欄位 **[!UICONTROL Expression]** 欄。 然後按一下 **[!UICONTROL Finish]** 按鈕。

   ![](assets/datamanagement_usecase_2.png)

1. 按一下 **[!UICONTROL Edit additional data]**，之後 **[!UICONTROL Advanced parameters...]**。核取 **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** 選項。

   此選項可確保不會顯示所有收件者，且不會保留明確新增的資料。 在此案例中，該日期是指上次建立收件者的日期。

   保留 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 選項為已核取狀態。

## 步驟2：連結收件者和彙總函式結果 {#step-2--linking-the-recipients-and-the-aggregation-function-result}

若要將處理收件者的查詢連結至執行彙總函式計算的查詢，您必須使用結構描述編輯活動。

1. 將收件者的查詢定義為主集。
1. 在 **[!UICONTROL Links]** 標籤，新增連結，並在開啟的視窗中輸入資訊，如下所示：

   * 選取與彙總相關的暫存結構描述。 此結構描述的資料將新增至主要集的成員。
   * 選取 **[!UICONTROL Use a simple join]** 將彙總結果連結至主集的每個收件者。
   * 最後，指定連結為 **[!UICONTROL Type 11 simple link]**.

   ![](assets/datamanagement_usecase_3.png)

因此，彙總結果會連結至每個收件者。

## 步驟3：使用彙總篩選收件者。 {#step-3--filtering-recipients-using-the-aggregate-}

建立連結後，彙總結果和收件者會成為相同臨時結構描述的一部分。 因此，可以在結構描述上建立篩選，以比較收件者的建立日期與最後已知建立日期（以彙總函式表示）。 使用分割活動執行此篩選。

1. 在 **[!UICONTROL General]** 索引標籤，選取 **收件者** 作為目標維度和 **編輯結構描述** 作為篩選維度（以篩選入站轉變結構描述活動）。
1. 在 **[!UICONTROL subsets]** 索引標籤，選取 **[!UICONTROL Add a filtering condition on the inbound population]** 然後按一下 **[!UICONTROL Edit...]**.
1. 使用運算式編輯器，在收件者的建立日期與彙總計算的建立日期之間新增相等條件。

   資料庫中的日期型別欄位通常會儲存到毫秒。 因此，您必須將這些延長一整天，以避免擷取僅建立該毫秒的收件者。

   若要這麼做，請使用 **ToDate** 函式，可在運算式編輯器中取得，可將日期和時數轉換為簡單日期。

   因此，用於條件的運算式為：

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**： `toDate([datemax/expr####])`，其中expr####與彙總函式查詢中指定的彙總有關。

   ![](assets/datamanagement_usecase_4.png)

因此，分割活動的結果會與最後一個已知建立日期當天建立的收件者相關。

然後，您可以新增其他活動（例如清單更新或傳遞）以豐富您的工作流程。
