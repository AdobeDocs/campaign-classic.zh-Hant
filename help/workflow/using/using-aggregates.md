---
product: campaign
title: 使用彙總
description: 了解如何使用匯總
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 12b173e9-5068-4d45-9e1e-2aecc9866e9c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---

# 使用彙總{#using-aggregates}

![](../../assets/common.svg)

此使用案例詳細說明了如何自動識別上次新增至資料庫的收件者。

使用以下過程，將資料庫中收件人的建立日期與上次使用匯總建立收件人的已知日期進行比較。 也會選取在同一天建立的所有收件者。

執行 **建立日期=最大值（建立日期）** 對收件者輸入篩選，您必須執行工作流程以遵循下列步驟：

1. 使用基本查詢檢索資料庫收件人。 如需此步驟的詳細資訊，請參閱 [建立查詢](query.md#creating-a-query).
1. 使用從 **最大值（建立日期）** 聚合函式。
1. 將每個收件者連結至匯總函式會產生相同的架構。
1. 透過編輯的結構，使用匯總來篩選收件者。

![](assets/datamanagement_usecase_1.png)

## 步驟1:計算匯總結果 {#step-1--calculating-the-aggregate-result}

1. 建立查詢。 在此，目標是從資料庫中的所有收件者中計算最後已知的建立日期。 因此，查詢不包含篩選器。
1. 選取 **[!UICONTROL Add data]**。
1. 在開啟的視窗中，選取 **[!UICONTROL Data linked to the filtering dimension]** then **[!UICONTROL Filtering dimension data]**.
1. 在 **[!UICONTROL Data to add]** 窗口中，添加計算 **建立日期** 欄位。 您可以使用運算式編輯器或輸入 **max(@created)** 直接放入 **[!UICONTROL Expression]** 欄。 然後按一下 **[!UICONTROL Finish]** 按鈕。

   ![](assets/datamanagement_usecase_2.png)

1. 按一下 **[!UICONTROL Edit additional data]**，之後 **[!UICONTROL Advanced parameters...]**。核取 **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** 選項。

   此選項可確保不會因此顯示所有收件者，也不會保留明確新增的資料。 在此案例中，它是指收件者的最後建立日期。

   保留 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 選項為已核取狀態。

## 步驟2:連結收件者和匯總函式結果 {#step-2--linking-the-recipients-and-the-aggregation-function-result}

要將處理收件者的查詢連結到執行匯總函式計算的查詢，必須使用架構編輯活動。

1. 將收件者的查詢定義為主要集。
1. 在 **[!UICONTROL Links]** 頁簽，添加新連結並在窗口中輸入以下開啟的資訊：

   * 選擇與聚合相關的臨時架構。 此架構的資料將新增至主集的成員。
   * 選擇 **[!UICONTROL Use a simple join]** 將匯總結果連結到主集的每個收件人。
   * 最後，指定連結為 **[!UICONTROL Type 11 simple link]**.

   ![](assets/datamanagement_usecase_3.png)

因此，聚合結果將連結到每個收件人。

## 步驟3:使用匯總來篩選收件者。 {#step-3--filtering-recipients-using-the-aggregate-}

建立連結後，匯總結果和收件者會組成相同暫時結構的一部分。 因此，可以在架構上建立篩選器，以比較收件者的建立日期和最後已知的建立日期，由匯總函式表示。 此篩選器是使用分割活動執行。

1. 在 **[!UICONTROL General]** 索引標籤，選取 **收件者** 作為目標維度，而 **編輯結構** 作為篩選維度（以篩選入站轉變結構活動）。
1. 在 **[!UICONTROL subsets]** 索引標籤，選取 **[!UICONTROL Add a filtering condition on the inbound population]** 然後按一下 **[!UICONTROL Edit...]**.
1. 使用運算式編輯器，在收件者的建立日期與匯總計算的建立日期之間新增相等標準。

   資料庫中的日期類型欄位通常會以毫秒為單位儲存。 因此，您必須將這些檔案延長一天，以避免僅擷取以毫秒為單位建立的收件者。

   若要這麼做，請使用 **ToDate** 函式，可在運算式編輯器中使用，將日期和小時轉換為簡單日期。

   因此，要用於條件的運算式為：

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`，其中expr###與聚合函式查詢中指定的聚合相關。

   ![](assets/datamanagement_usecase_4.png)

因此，分割活動的結果與在上次已知建立日期的同一天建立的收件者有關。

然後，您可以新增其他活動，例如清單更新或傳送，以豐富您的工作流程。
