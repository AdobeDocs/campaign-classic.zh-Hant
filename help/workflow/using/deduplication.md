---
product: campaign
title: 去重複化
description: 深入瞭解重複資料刪除工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 38add4fe-6238-45de-863e-895ebca189b7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 9%

---

# 去重複化{#deduplication}



重複資料刪除會從入站活動的結果中刪除重複專案。 可在電子郵件地址、電話號碼或其他欄位上執行重複資料刪除。

此 **[!UICONTROL Deduplication]** 活動用於從資料集中移除重複列。 例如，下列記錄可能會被視為重複，因為它們有相同的電子郵件地址和相同的行動和/或住家電話。

| 上次修改日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
-----|------------|-----------|-------|--------------|------
| 02/03/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |
| 05/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 07/22/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

此 **[!UICONTROL Deduplication]** 在識別重複專案後，活動可保留整列作為唯一記錄。 例如，在上述使用案例中，如果活動設定為僅保留具有最舊記錄的記錄 **[!UICONTROL Date]**，結果會是：

| 日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
-----|----------|------------|-------|--------------|------
| 02/03/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

選取的主要記錄將結轉資料，不會將欄位資料與重複列中的其他相關資料進行任何合併。

補充：

| 日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
-----|------------|-----------|-------|--------------|------
| 05/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 07/22/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

## 最佳實務 {#best-practices}

在重複資料刪除期間，會個別處理傳入資料流。 例如，如果在查詢1的結果中以及在查詢2的結果中找到收件者A，則不會進行重複資料刪除。

此問題需要透過以下方式解決：

* 建立 **聯集** 活動以統一每個傳入流量。
* 建立 **重複資料刪除** 活動之後 **聯集** 活動。

![](assets/dedup_bonnepratique.png)

## 設定 {#configuration}

若要設定重複資料刪除，請輸入其標籤、方法和重複資料刪除條件，以及有關結果的選項。

1. 按一下 **[!UICONTROL Edit configuration...]** 定義重複資料刪除模式的連結。

   ![](assets/s_user_segmentation_dedup_param.png)

1. 選取此活動的目標型別（預設情況下，重複資料刪除會連結至收件者）以及要使用的條件，即允許您識別重複專案的相同值欄位。

   >[!NOTE]
   >
   >如果您使用外部資料作為輸入（例如來自外部檔案），請務必選取 **[!UICONTROL Temporary schema]** 選項。
   >
   >在下一步中， **[!UICONTROL Other]** 選項可讓您選取要使用的條件：

   ![](assets/s_user_segmentation_dedup_param2.png)

1. 在下一步中， **[!UICONTROL Other]** 選項可讓您選取在值相同的情況下要使用的准則。

   ![](assets/s_user_segmentation_dedup_param3.png)

1. 從下拉式清單中，選取要使用的重複資料刪除方法，然後輸入要保留的重複專案數。

   ![](assets/s_user_segmentation_dedup_param4.png)

   可以使用下列方法：

   * **[!UICONTROL Choose for me]**：隨機選取要保留在重複項目外的記錄。
   * **[!UICONTROL Following a list of values]**：可讓您定義一或多個欄位的值優先順序。若要定義值，請選取欄位或建立運算式，然後將值新增至適當的資料表中。若要定義新欄位，請按一下值清單上方的 **[!UICONTROL Add]** 按鈕。

     ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**：您可以保留所選運算式的值不為空白的記錄作為優先順序。

     ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**：可讓您保留具有指定運算式之最低（或最高）值的記錄。

     ![](assets/s_user_segmentation_dedup_param7.png)

   >[!NOTE]
   >
   >此 **[!UICONTROL Merge]** 功能，可透過 **[!UICONTROL Advanced parameters]** 連結，可讓您設定一組規則，以便將欄位或欄位群組合併為單一結果資料記錄。 有關詳細資訊，請參閱 [將欄位合併為單一記錄](#merging-fields-into-single-record).

1. 按一下 **[!UICONTROL Finish]** 以核准所選的重複資料刪除方法。

   視窗的中間區段會摘要列出定義的組態。

   在活動編輯器視窗的下半部，您可以修改圖形物件出站轉變的標籤，並輸入與活動結果相關聯的區段代碼。 此程式碼稍後可當作鎖定目標條件使用。

   ![](assets/s_user_segmentation_dedup_param8.png)

1. 檢查 **[!UICONTROL Generate complement]** 選項，以利用剩餘母體。 補充包含所有重複專案。 隨後會將其他轉變新增至活動，如下所示：

   ![](assets/s_user_segmentation_dedup_param9.png)

## 範例：在傳遞之前識別重複專案 {#example--identify-the-duplicates-before-a-delivery}

在以下範例中，重複資料刪除與三個查詢的聯合有關。

工作流程的目的是透過排除重複專案來定義傳遞的目標，以避免將其多次傳送給相同的收件者。

已識別的重複專案也會整合到專用的重複專案清單中，以便視需要重複使用。

![](assets/deduplication_example.png)

1. 新增並連結工作流程運作所需的各種活動，如上所示。

   聯合活動是用來將三個查詢「統一」成一個單一轉變。 因此，重複資料刪除不適用於個別查詢，但適用於整個查詢。 有關本主題的詳細資訊，請參閱 [最佳實務](#best-practices).

1. 開啟重複資料刪除活動，然後按一下 **[!UICONTROL Edit configuration...]** 定義重複資料刪除模式的連結。
1. 在新視窗中，選取 **[!UICONTROL Database schema]**.
1. 選取 **收件者** 做為定位和篩選維度。
1. 選取的ID欄位 **[!UICONTROL Email]** 重複，只傳送一次傳遞至每個電子郵件地址，然後按一下 **[!UICONTROL Next]**.

   如果您希望複製ID以特定欄位為基礎，請選取 **[!UICONTROL Other]** 以存取可用欄位清單。

1. 選擇時，在識別多個收件者的相同電子郵件地址時，只保留一個專案。
1. 選取 **[!UICONTROL Choose for me]** 重複資料刪除模式，以便隨機選擇在識別重複專案時儲存的記錄，然後按一下 **[!UICONTROL Finish]**.

執行工作流程時，會從結果（以及傳遞）中排除所有識別為重複的收件者，並將其新增至重複專案清單。 此清單可再次使用，而不需要重新識別重複專案。

## 將欄位合併到單一資料記錄中 {#merging-fields-into-single-record}

此 **[!UICONTROL Merge]** 功能可讓您設定重複資料刪除的一組規則，以定義要合併成單一結果資料記錄的欄位或欄位群組。

例如，如果有一組重複記錄，您可以選擇保留最舊的電話號碼或最新的名稱。

運用此功能的使用案例可在以下取得： [本節](deduplication-merge.md).

要執行此操作，請依照下列步驟執行：

1. 在 **[!UICONTROL Deduplication method]** 選取步驟，按一下 **[!UICONTROL Advanced Parameters]** 連結。

   ![](assets/dedup1.png)

1. 選取 **[!UICONTROL Merge records]** 選項以啟動功能。

   如果您想要在每個合併條件中將多個資料欄位分組，請啟動 **[!UICONTROL Use several record merging criteria]** 選項。

   ![](assets/dedup2.png)

1. 啟動功能後， **[!UICONTROL Merge]** 索引標籤已新增至 **[!UICONTROL Deduplication]** 活動。 它可讓您定義要合併的欄位群組及其相關規則。

   如需詳細資訊，請參閱中的專用使用案例。 [本節](deduplication-merge.md).

   ![](assets/dedup3.png)

## 輸入引數 {#input-parameters}

* tableName
* 綱要

每個傳入事件都必須指定由這些引數定義的目標。

## 輸出引數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值可識別重複資料刪除所產生的目標。 **[!UICONTROL tableName]** 是儲存目標識別碼的表格名稱， **[!UICONTROL schema]** 是母體的綱要（通常是nms：recipient）和 **[!UICONTROL recCount]** 是表格中的元素數。

與補充關聯的轉變有相同的引數。
