---
product: campaign
title: 去重複化
description: 瞭解有關重複資料消除工作流活動的詳細資訊
feature: Workflows, Targeting Activity
exl-id: 38add4fe-6238-45de-863e-895ebca189b7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 10%

---

# 去重複化{#deduplication}

![](../../assets/v7-only.svg)

重複資料消除從入站活動的結果中刪除重複項。 可以對電子郵件地址、電話號碼或其他欄位執行重複資料消除。

的 **[!UICONTROL Deduplication]** 活動用於從資料集中刪除重複行。 例如，以下記錄可被視為重複，因為它們具有相同的電子郵件地址和相同的行動電話和/或家庭電話。

| 上次修改日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
-----|------------|-----------|-------|--------------|------
| 02/03/2020 | 鮑勃 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 888-888-8888 |
| 05/19/2020 | 羅伯特 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 07/22/2020 | 鮑比 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

的 **[!UICONTROL Deduplication]** 活動能夠在標識重複項後將整個行保留為唯一記錄。 例如，在上述使用情形中，如果將活動配置為僅保留具有最舊記錄的記錄 **[!UICONTROL Date]**&#x200B;結果是：

| 日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
-----|----------|------------|-------|--------------|------
| 02/03/2020 | 鮑勃 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

所選主記錄將繼承資料，而不將欄位資料與重複行中的其他相關資料合併。

補充：

| 日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
-----|------------|-----------|-------|--------------|------
| 05/19/2020 | 羅伯特 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 07/22/2020 | 鮑比 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

## 最佳實務 {#best-practices}

在重複資料消除期間，入站流將單獨處理。 如果在查詢1的結果和查詢2的結果中都找到實例收件人A，則不會消除重複。

這一問題需要處理如下：

* 建立 **聯合** 活動以統一每個入站流。
* 建立 **重複資料消除** 活動 **聯合** 的子菜單。

![](assets/dedup_bonnepratique.png)

## 設定 {#configuration}

要配置重複資料消除，請輸入其標籤、方法、重複資料消除標準以及與結果相關的選項。

1. 按一下 **[!UICONTROL Edit configuration...]** 連結以定義重複資料消除模式。

   ![](assets/s_user_segmentation_dedup_param.png)

1. 選擇此活動的目標類型（預設情況下，重複資料消除連結到收件人）和要使用的標準，即相同值允許您標識重複項的欄位。

   >[!NOTE]
   >
   >如果使用外部資料作為輸入，例如從外部檔案中，請確保選擇 **[!UICONTROL Temporary schema]** 的雙曲餘切值。
   >
   >在下一步中， **[!UICONTROL Other]** 選項，可以選擇要使用的標準或標準：

   ![](assets/s_user_segmentation_dedup_param2.png)

1. 在下一步中， **[!UICONTROL Other]** 選項，可選擇在具有相同值時使用的標準或標準。

   ![](assets/s_user_segmentation_dedup_param3.png)

1. 從下拉清單中，選擇要使用的重複資料消除方法，並輸入要保留的重複項數。

   ![](assets/s_user_segmentation_dedup_param4.png)

   以下方法可用：

   * **[!UICONTROL Choose for me]**：隨機選取要保留在重複項目外的記錄。
   * **[!UICONTROL Following a list of values]**：可讓您定義一或多個欄位的值優先順序。若要定義值，請選取欄位或建立運算式，然後將值新增至適當的資料表中。若要定義新欄位，請按一下值清單上方的 **[!UICONTROL Add]** 按鈕。

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**：您可以保留所選運算式的值不為空白的記錄作為優先順序。

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**:允許您使用給定表達式的最低（或最高）值保留記錄。

      ![](assets/s_user_segmentation_dedup_param7.png)
   >[!NOTE]
   >
   >的 **[!UICONTROL Merge]** 功能，可通過 **[!UICONTROL Advanced parameters]** 連結，允許您配置一組規則，以便將一個欄位或一組欄位合併到單個生成的資料記錄中。 有關此的詳細資訊，請參閱 [將欄位合併到單個記錄](#merging-fields-into-single-record)。

1. 按一下 **[!UICONTROL Finish]** 以批准選定的重複資料消除方法。

   窗口的中間部分匯總了定義的配置。

   在活動編輯器窗口的下半部分，您可以修改圖形對象出站轉換的標籤，並輸入與活動結果關聯的段代碼。 此代碼稍後可用作目標標準。

   ![](assets/s_user_segmentation_dedup_param8.png)

1. 檢查 **[!UICONTROL Generate complement]** 的雙曲餘切值。 補碼包含所有重複項。 然後，將向活動添加一個附加的轉換，如下所示：

   ![](assets/s_user_segmentation_dedup_param9.png)

## 示例：在交貨前確定重複項 {#example--identify-the-duplicates-before-a-delivery}

在以下示例中，重複資料消除涉及三個查詢的合併。

工作流的目的是通過排除重複項來定義傳遞的目標，以避免將其多次發送到同一收件人。

所識別的重複項也將整合到專用的重複項清單中，如有必要，這些重複項清單可重複使用。

![](assets/deduplication_example.png)

1. 添加並連結工作流運行所需的各種活動，如上所示。

   此處使用聯合活動將三個查詢「統一」為一個轉換。 因此，重複資料刪除不會單獨用於每個查詢，而會用於整個查詢。 有關此主題的詳細資訊，請參閱 [最佳做法](#best-practices)。

1. 開啟重複資料消除活動，然後按一下 **[!UICONTROL Edit configuration...]** 連結以定義重複資料消除模式。
1. 在新窗口中，選擇 **[!UICONTROL Database schema]**。
1. 選擇 **收件人** 作為目標和篩選維。
1. 為 **[!UICONTROL Email]** 重複，以僅向每個電子郵件地址發送一次傳遞，然後按一下 **[!UICONTROL Next]**。

   如果希望將重複ID基於特定欄位，請選擇 **[!UICONTROL Other]** 的子菜單。

1. 當為多個收件人標識了同一電子郵件地址時，選擇只保留一個條目。
1. 選擇 **[!UICONTROL Choose for me]** 重複資料消除模式，以便隨機選擇在發現重複項時保存的記錄，然後按一下 **[!UICONTROL Finish]**。

運行工作流時，所有標識為重複項的收件人都將從結果中排除（因此也將從中排除傳遞），並添加到重複項清單中。 此清單可以再次使用，而不必重新標識重複項。

## 將欄位合併到單個資料記錄 {#merging-fields-into-single-record}

的 **[!UICONTROL Merge]** 功能允許您為重複資料消除配置一組規則，以定義要合併到單個結果資料記錄中的欄位或欄位組。

例如，對於一組重複的記錄，您可以選擇保留最舊的電話號碼或最近的名稱。

利用此功能的使用案例在中提供 [此部分](deduplication-merge.md)。

要執行此操作，請依照下列步驟執行：

1. 在 **[!UICONTROL Deduplication method]** 選擇步驟，按一下 **[!UICONTROL Advanced Parameters]** 的子菜單。

   ![](assets/dedup1.png)

1. 選擇 **[!UICONTROL Merge records]** 頁籤

   如果要在每個合併條件中對多個資料欄位進行分組，請激活 **[!UICONTROL Use several record merging criteria]** 的雙曲餘切值。

   ![](assets/dedup2.png)

1. 激活功能後， **[!UICONTROL Merge]** 頁籤 **[!UICONTROL Deduplication]** 的子菜單。 它允許您定義要合併的欄位組及其關聯規則。

   有關詳情，請參閱中提供的專用用例 [此部分](deduplication-merge.md)。

   ![](assets/dedup3.png)

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這組三個值標識了由重複資料消除生成的目標。 **[!UICONTROL tableName]** 是保存目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補碼相關聯的過渡具有相同的參數。
