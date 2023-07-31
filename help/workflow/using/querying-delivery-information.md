---
product: campaign
title: 查詢傳遞資訊
description: 瞭解如何查詢傳遞資訊
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: b699b064-1287-41c9-8d94-1c1aa2c145ab
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 1%

---

# 查詢傳遞資訊 {#querying-delivery-information}



## 特定傳送的點按次數 {#number-of-clicks-for-a-specific-delivery}

在此範例中，我們想要復原特定傳送的點按次數。 這些點按會被記錄下來，這要歸功於指定時段內的收件者追蹤記錄。 收件者可透過其電子郵件地址識別。 此查詢使用 **[!UICONTROL Recipient tracking logs]** 表格。

* 需要選取哪個表格？

  收件者記錄追蹤表格(**[!UICONTROL nms:trackingLogRcp]**)

* 要為輸出欄選取的欄位？

  主索引鍵（含計數）和電子郵件

* 會根據哪些條件篩選資訊？

  傳遞標籤的特定期間和元素

若要執行此範例，請套用下列步驟：

1. 開啟 **[!UICONTROL Generic query editor]** 並選取 **[!UICONTROL Recipient tracking logs]** 綱要。

   ![](assets/query_editor_tracklog_05.png)

1. 在 **[!UICONTROL Data to extract]** 視窗中，我們要建立彙總以收集資訊。 若要這麼做，請新增主索引鍵（位於主索引鍵上方） **[!UICONTROL Recipient tracking logs]** 元素)：對此執行追蹤記錄計數 **[!UICONTROL Primary key]** 欄位。 編輯的運算式將為 **[!UICONTROL x=count(primary key)]**. 它會將各種追蹤記錄的總和連結至單一電子郵件地址。

   操作步驟：

   * 按一下 **[!UICONTROL Add]** 圖示右側 **[!UICONTROL Output columns]** 欄位。 在 **[!UICONTROL Formula type]** 視窗，選取 **[!UICONTROL Edit the formula using an expression]** 選項並按一下 **[!UICONTROL Next]**. 在 **[!UICONTROL Field to select]** 視窗，按一下 **[!UICONTROL Advanced selection]**.

     ![](assets/query_editor_tracklog_06.png)

   * 在 **[!UICONTROL Formula type]** 視窗，對彙總函式執行程式。 此程式將會是主鍵計數。

     選取 **[!UICONTROL Process on an aggregate function]** 在 **[!UICONTROL Aggregate]** 區段並按一下 **[!UICONTROL Count]**.

     ![](assets/query_editor_nveau_18.png)

     按一下&#x200B;**[!UICONTROL Next]**。

   * 選取 **[!UICONTROL Primary key (@id)]** 欄位。 此 **[!UICONTROL count (primary key)]** 輸出欄已設定。

     ![](assets/query_editor_nveau_19.png)

1. 選取要顯示在輸出欄中的其他欄位。 在 **[!UICONTROL Available fields]** 欄，開啟 **[!UICONTROL Recipient]** 節點並選擇 **[!UICONTROL Email]**. 檢查 **[!UICONTROL Group]** 方塊至 **[!UICONTROL Yes]** 若要依電子郵件地址將追蹤記錄分組：此群組會將每個記錄連結至其收件者。

   ![](assets/query_editor_nveau_20.png)

1. 設定欄排序，以便最先顯示最活躍的收件者（具有最多的追蹤記錄）。 檢查 **[!UICONTROL Yes]** 在 **[!UICONTROL Descending sort]** 欄。

   ![](assets/query_editor_nveau_64.png)

1. 接著，您必須篩選出您感興趣的記錄，亦即兩週以內以及與銷售相關傳送的記錄。

   操作步驟：

   * 設定資料篩選。 要執行此操作，請選取 **[!UICONTROL Filter conditions]** 然後按一下 **[!UICONTROL Next]**.

     ![](assets/query_editor_nveau_22.png)

   * 在特定期間內復原特定傳送的追蹤記錄。 需要三個篩選條件：兩個日期條件，可設定目前日期前2週與目前日期前一天之間的搜尋期間；另一個條件，可限制搜尋至特定傳遞。

     在 **[!UICONTROL Target element]** 視窗，設定開始將追蹤記錄納入考量的日期。 按一下 **[!UICONTROL Add]**。會顯示條件行。 編輯 **[!UICONTROL Expression]** 欄，按一下 **[!UICONTROL Edit expression]** 函式。 在 **[!UICONTROL Field to select]** 視窗，選擇 **[!UICONTROL Date (@logDate)]**.

     ![](assets/query_editor_nveau_23.png)

     選取 **[!UICONTROL greater than]** 運運算元。 在 **[!UICONTROL Value]** 欄，按一下 **[!UICONTROL Edit expression]**，以及 **[!UICONTROL Formula type]** 視窗，選取 **[!UICONTROL Process on dates]**. 最後，在 **[!UICONTROL Current date minus n days]**，輸入「15」。

     按一下&#x200B;**[!UICONTROL Finish]**。

     ![](assets/query_editor_nveau_24.png)

   * 若要選取追蹤記錄搜尋結束日期，請按一下「 」以建立第二個條件 **[!UICONTROL Add]**. 在 **[!UICONTROL Expression]** 欄，選擇 **[!UICONTROL Date (@logDate)]** 再來一次。

     選取 **[!UICONTROL less than]** 運運算元。 在 **[!UICONTROL Value]** 欄，按一下 **[!UICONTROL Edit expression]**. 若要處理日期，請前往 **[!UICONTROL Formula type]** 視窗中，輸入「1」 **[!UICONTROL Current date minus n days]**.

     按一下&#x200B;**[!UICONTROL Finish]**。

     ![](assets/query_editor_nveau_65.png)

     現在，我們要設定第三個篩選條件，即查詢關注的傳送標籤。

   * 按一下 **[!UICONTROL Add]** 函式，以建立另一個篩選條件。 在 **[!UICONTROL Expression]** 欄，按一下 **[!UICONTROL Edit expression]**. 在 **[!UICONTROL Field to select]** 視窗，選擇 **[!UICONTROL Label]** 在 **[!UICONTROL Delivery]** 節點。

     按一下&#x200B;**[!UICONTROL Finish]**。

     ![](assets/query_editor_nveau_66.png)

     尋找包含「sales」字樣的傳遞。 由於您不記得確切的標籤，因此您可以選擇 **[!UICONTROL contains]** 運運算元並輸入「sales」，在 **[!UICONTROL Value]** 欄。

     ![](assets/query_editor_nveau_25.png)

1. 按一下 **[!UICONTROL Next]** 直到您進入 **[!UICONTROL Data preview]** 視窗：這裡不需要格式設定。
1. 在 **[!UICONTROL Data preview]** 視窗，按一下 **[!UICONTROL Start the preview of the data]** 以檢視每個傳遞收件者的追蹤記錄數量。

   結果會以遞減順序顯示。

   ![](assets/query_editor_tracklog_04.png)

   此傳遞的使用者最大記錄數為6。 5名不同使用者開啟了傳遞電子郵件，或按一下電子郵件中的連結。

## 未開啟任何傳遞的收件者 {#recipients-who-did-not-open-any-delivery}

在此範例中，我們要篩選過去7天內未開啟電子郵件的收件者。

若要建立此範例，請套用下列步驟：

1. 拖放 **[!UICONTROL Query]** 活動並開啟活動。
1. 按一下 **[!UICONTROL Edit query]** 並將目標和篩選維度設為 **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. 選取 **[!UICONTROL Filtering conditions]** 然後按一下 **[!UICONTROL Next]**.
1. 按一下 **[!UICONTROL Add]** 按鈕並選取 **[!UICONTROL Tracking logs]**.
1. 設定 **[!UICONTROL Operator]** 的 **[!UICONTROL Tracking logs]** 運算式至 **[!UICONTROL Do not exist such as]**.

   ![](assets/query_open_1.png)

1. 新增另一個運算式。 選取 **[!UICONTROL Type]** 在 **[!UICONTROL URL]** 類別。
1. 然後，設定其 **[!UICONTROL Operator]** 至 **[!UICONTROL equal to]** 及其 **[!UICONTROL Value]** 至 **[!UICONTROL Open]**.

   ![](assets/query_open_2.png)

1. 新增其他運算式並選取 **[!UICONTROL Date]**. **[!UICONTROL Operator]** 應設為 **[!UICONTROL on or after]**.

   ![](assets/query_open_3.png)

1. 若要設定最近7天的值，請按一下 **[!UICONTROL Edit expression]** 中的按鈕 **[!UICONTROL Value]** 欄位。
1. 在 **[!UICONTROL Function]** 類別，選取 **[!UICONTROL Current date minus n days]** 並新增您想要鎖定的天數。 在此處，我們想要鎖定過去7天。

   ![](assets/query_open_4.png)

您的出站轉變將包含過去7天內未開啟電子郵件的收件者。

如果相反地，您想要篩選至少開啟一封電子郵件的收件者，則您的查詢應如下所示。 請注意，在此案例中， **[!UICONTROL Filtering dimension]** 應設為 **[!UICONTROL Tracking logs (Recipients)]**.

![](assets/query_open_5.png)

## 已開啟傳遞的收件者 {#recipients-who-have-opened-a-delivery}

以下範例說明如何定位過去2週內開啟傳送的設定檔：

1. 若要將已開啟傳送的設定檔設為目標，您需要使用追蹤記錄。 它們儲存在連結表格中：一開始可在的下拉式清單中選取此表格 **[!UICONTROL Filtering dimension]** 欄位，如下所示：

   ![](assets/s_advuser_query_sample1.0.png)

1. 關於篩選條件，請按一下 **[!UICONTROL Edit expression]** 圖示中顯示的追蹤記錄之子樹狀結構中的條件圖示。 選取 **[!UICONTROL Date]** 欄位。

   ![](assets/s_advuser_query_sample1.1.png)

   按一下 **[!UICONTROL Finish]** 以確認選取。

   若只要復原兩週前的追蹤記錄，請選取 **[!UICONTROL Greater than]** 運運算元。

   ![](assets/s_advuser_query_sample1.4.png)

   然後按一下 **[!UICONTROL Edit expression]** 圖示於 **[!UICONTROL Value]** 欄，以定義要套用的計算公式。 選取 **[!UICONTROL Current date minus n days]** 公式，並在相關欄位中輸入15。

   ![](assets/s_advuser_query_sample1.5.png)

   按一下 **[!UICONTROL Finish]** 公式視窗的按鈕。 在篩選視窗中，按一下 **[!UICONTROL Preview]** 標籤以檢查鎖定目標條件。

   ![](assets/s_advuser_query_sample1.6.png)

## 篩選傳遞後的收件者行為 {#filtering-recipients--behavior-folllowing-a-delivery}

在工作流程中， **[!UICONTROL Query]** 和 **[!UICONTROL Split]** 方塊可讓您選取先前傳送後的行為。 此選取是透過 **[!UICONTROL Delivery recipient]** 篩選。

* 範例的目標

  在傳遞工作流程中，有數種方式可追蹤第一個電子郵件通訊。 這類作業涉及使用 **[!UICONTROL Split]** 方塊。

* 內容

  已傳送「夏季運動選件」傳遞。 在傳送後四天，會傳送其他兩個傳送。 其中一個是「水上運動優惠方案」，另一個是第一個「夏季運動優惠方案」的後續專案。

  「水上運動選件」傳送會傳送給在第一次傳送中按一下「水上運動」連結的收件者。 這些點按可顯示收件者對主題感興趣。 引導他們接受類似優惠方案是有意義的。 不過，未點選「夏季體育選件」的收件者將再次收到相同的內容。

下列步驟說明如何設定 **[!UICONTROL Split]** 方塊中，整合兩種不同的行為：

1. 插入 **[!UICONTROL Split]** 方塊放入工作流程中。 此方塊會將第一個傳遞的收件者劃分為接下來的兩個傳遞。 在首次傳遞期間，根據連結至收件者行為的篩選條件會發生劃分。

   ![](assets/query_editor_ex_09.png)

1. 開啟 **[!UICONTROL Split]** 方塊。 在 **[!UICONTROL General]** 標籤，輸入標籤： **根據行為分割** 例如。

   ![](assets/query_editor_ex_04.png)

1. 在 **[!UICONTROL Subsets]** 標籤，定義第一個分割分支。 例如，輸入 **已點按** 此分支的標籤。
1. 選取 **[!UICONTROL Add a filtering condition on the incoming population]** 選項。 按一下&#x200B;**[!UICONTROL Edit]**。
1. 在 **[!UICONTROL Targeting and filtering dimension]** 視窗，按兩下 **[!UICONTROL Recipients of a delivery]** 篩選。

   ![](assets/query_editor_ex_05.png)

1. 在 **[!UICONTROL Target element]** 視窗，選取您要套用至此分支的行為： **[!UICONTROL Recipients having clicked (email)]**.

   在下方，選取 **[!UICONTROL Delivery specified by the transition]** 選項。 此功能會自動在首次傳遞期間復原目標人員。

   這是「水上運動選件」傳遞。

   ![](assets/query_editor_ex_08.png)

1. 定義第二個分支。 此分支將包含後續電子郵件，其內容與第一次傳遞的內容相同。 前往 **[!UICONTROL Subsets]** 標籤並按一下 **[!UICONTROL Add]** 以建立它。

   ![](assets/query_editor_ex_06.png)

1. 另一個子標籤隨即顯示。 將其命名為&quot;**未點按**「。
1. 按一下 **[!UICONTROL Add a filtering condition for the incoming population]**。然後按一下 **[!UICONTROL Edit...]**。

   ![](assets/query_editor_ex_07.png)

1. 按一下 **[!UICONTROL Delivery recipients]** 在 **[!UICONTROL Targeting and filtering dimension]** 視窗。
1. 在 **[!UICONTROL Target element]** 視窗，選取 **[!UICONTROL Recipients who did not click (email)]** 行為。 選取 **[!UICONTROL Delivery specified by the transition]** 選項，如最後一個分支所示。

   此 **[!UICONTROL Split]** 方塊現在已完整設定。

   ![](assets/query_editor_ex_03.png)

以下是預設設定的各種元件清單：

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

  ![](assets/query_editor_ex_02.png)
