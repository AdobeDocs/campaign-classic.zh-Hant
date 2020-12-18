---
solution: Campaign Classic
product: campaign
title: 使用彙總
description: 瞭解如何使用匯總
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---


# 使用彙總{#using-aggregates}

此使用案例詳細資訊如何自動識別最後新增至資料庫的收件者。

使用以下流程，將資料庫中收件人的建立日期與上次使用匯總建立收件人的已知日期進行比較。 也會選取在同一天建立的所有收件者。

要對收件者執行&#x200B;**建立日期= max（建立日期）**&#x200B;類型篩選器，您必須運行工作流以遵循以下步驟：

1. 使用基本查詢檢索資料庫收件人。 有關此步驟的詳細資訊，請參閱[建立查詢](../../workflow/using/query.md#creating-a-query)。
1. 使用從&#x200B;**max（建立日期）**&#x200B;聚合函式生成的結果計算收件人建立的最後已知日期。
1. 將每個收件者連結至匯總函式，會產生相同的架構。
1. 透過編輯的結構，使用匯整篩選收件者。

![](assets/datamanagement_usecase_1.png)

## 步驟1:計算聚合結果{#step-1--calculating-the-aggregate-result}

1. 建立查詢。 在此，目標是計算資料庫中所有收件人的最後一個已知建立日期。 因此，查詢不包含篩選器。
1. 選取 **[!UICONTROL Add data]**。
1. 在開啟的窗口中，選擇&#x200B;**[!UICONTROL Data linked to the filtering dimension]** ，然後選擇&#x200B;**[!UICONTROL Filtering dimension data]**。
1. 在&#x200B;**[!UICONTROL Data to add]**&#x200B;窗口中，添加一列，該列計算收件人表中&#x200B;**建立日期**&#x200B;欄位的最大值。 您可以使用運算式編輯器，或直接在&#x200B;**[!UICONTROL Expression]**&#x200B;欄的欄位中輸入&#x200B;**max(@created)**。 然後按一下&#x200B;**[!UICONTROL Finish]**&#x200B;按鈕。

   ![](assets/datamanagement_usecase_2.png)

1. 按一下 **[!UICONTROL Edit additional data]**，之後 **[!UICONTROL Advanced parameters...]**。核取 **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** 選項。

   此選項可確保不會因此顯示所有收件者，而且不會保留明確新增的資料。 在此例中，它是指收件者最後建立的日期。

   保留 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 選項為已核取狀態。

## 步驟2:連結收件人和聚合函式結果{#step-2--linking-the-recipients-and-the-aggregation-function-result}

要將處理收件人的查詢連結到執行聚合函式計算的查詢，必須使用方案編輯活動。

1. 將收件者查詢定義為主集。
1. 在&#x200B;**[!UICONTROL Links]**&#x200B;標籤中，新增新連結並在視窗中輸入以下開啟的資訊：

   * 選擇與聚合相關的臨時方案。 此架構的資料將添加到主集的成員中。
   * 選擇&#x200B;**[!UICONTROL Use a simple join]**&#x200B;將聚合結果連結到主集的每個收件人。
   * 最後，指定連結為&#x200B;**[!UICONTROL Type 11 simple link]**。

   ![](assets/datamanagement_usecase_3.png)

因此，聚合結果與每個接收者連結。

## 步驟3:使用匯總篩選收件者。{#step-3--filtering-recipients-using-the-aggregate-}

建立連結後，匯整結果和收件者會組成相同的暫時架構。 因此，可以在方案上建立篩選器，以比較收件人的建立日期和由聚集函式表示的最後已知建立日期。 此篩選器是使用分割活動來執行。

1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，選擇&#x200B;**Recipients**&#x200B;作為目標維，選擇&#x200B;**Edit schema**&#x200B;作為篩選維（以篩選入站轉換模式活動）。
1. 在&#x200B;**[!UICONTROL subsets]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]** ，然後按一下&#x200B;**[!UICONTROL Edit...]**。
1. 使用運算式編輯器，在收件者的建立日期與由匯總計算的建立日期之間新增等式標準。

   資料庫中的日期類型欄位通常保存為毫秒。 因此，您必須將這些內容延長整天，以避免擷取僅在毫秒內建立的收件者。

   若要這麼做，請使用運算式編輯器中提供的&#x200B;**ToDate**&#x200B;函式，將日期和小時轉換為簡單日期。

   因此，要用於條件的表達式為：

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`，其中expr####與聚合函式查詢中指定的聚合相關。

   ![](assets/datamanagement_usecase_4.png)

因此，分割活動的結果與與上次已知建立日期建立的同一天建立的收件人有關。

然後，您可以新增其他活動，例如清單更新或傳送，以豐富您的工作流程。
