---
title: 查詢傳送資訊
description: 瞭解如何查詢傳送資訊
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 查詢傳送資訊 {#querying-delivery-information}

## 特定傳送的點按次數 {#number-of-clicks-for-a-specific-delivery}

在此範例中，我們希望恢復特定傳送的點按次數。 由於收件者追蹤記錄在指定的時段內，因此會記錄這些點按。 收件者是透過其電子郵件地址識別。 此查詢使用 **[!UICONTROL Recipient tracking logs]** 表。

* 需要選擇哪個表？

   收件者記錄追蹤表格(**[!UICONTROL nms:trackingLogRcp]**)

* 要為輸出列選擇的欄位？

   主鍵（含計數）和電子郵件

* 將根據哪些標準篩選資訊？

   傳送標籤的特定期間和元素

要執行此示例，請應用以下步驟：

1. 開啟並 **[!UICONTROL Generic query editor]** 選擇方 **[!UICONTROL Recipient tracking logs]** 案。

   ![](assets/query_editor_tracklog_05.png)

1. 在該窗 **[!UICONTROL Data to extract]** 口中，我們要建立聚合來收集資訊。 若要這麼做，請新增主要金鑰(位於主要元素 **[!UICONTROL Recipient tracking logs]** 上方):追蹤記錄計數會在此欄位上執 **[!UICONTROL Primary key]** 行。 編輯的運算式為 **[!UICONTROL x=count(primary key)]**。 它會將各種追蹤記錄的總和連結至單一電子郵件地址。

   操作步驟：

   * 按一下 **[!UICONTROL Add]** 欄位右側的圖 **[!UICONTROL Output columns]** 示。 在窗口 **[!UICONTROL Formula type]** 中，選擇選 **[!UICONTROL Edit the formula using an expression]** 項並按一下 **[!UICONTROL Next]**。 在窗口 **[!UICONTROL Field to select]** 中，按一下 **[!UICONTROL Advanced selection]**。

      ![](assets/query_editor_tracklog_06.png)

   * 在窗口 **[!UICONTROL Formula type]** 中，對集合函式運行進程。 此程式將是主鍵計數。

      在節 **[!UICONTROL Process on an aggregate function]** 中選 **[!UICONTROL Aggregate]** 擇並按一下 **[!UICONTROL Count]**。

      ![](assets/query_editor_nveau_18.png)

      按一下 **[!UICONTROL Next]**.

   * 選擇字 **[!UICONTROL Primary key (@id)]** 段。 輸 **[!UICONTROL count (primary key)]** 出列已配置。

      ![](assets/query_editor_nveau_19.png)

1. 選擇要在輸出列中顯示的其它欄位。 在列中 **[!UICONTROL Available fields]** ，開啟節 **[!UICONTROL Recipient]** 點並選擇 **[!UICONTROL Email]**。 核取方 **[!UICONTROL Group]** 塊以依 **[!UICONTROL Yes]** 電子郵件位址分組追蹤記錄：此群組會將每個記錄連結至其收件者。

   ![](assets/query_editor_nveau_20.png)

1. 設定欄排序，讓最活躍的收件者（具有最多的追蹤記錄）會先顯示。 檢 **[!UICONTROL Yes]** 入欄 **[!UICONTROL Descending sort]** 中。

   ![](assets/query_editor_nveau_64.png)

1. 然後，您必須篩選您感興趣的記錄檔，即2週以下且與銷售相關的交貨記錄檔。

   操作步驟：

   * 設定資料篩選。 若要這麼做，請選取， **[!UICONTROL Filter conditions]** 然後按一下 **[!UICONTROL Next]**。

      ![](assets/query_editor_nveau_22.png)

   * 在特定傳送的指定期間內恢復追蹤記錄檔。 需要三種篩選條件：兩個日期條件，將搜索期間設定在當前日期前2週和當前日期前2週之間；以及另一個條件，以限制搜尋至特定的傳送。

      在視 **[!UICONTROL Target element]** 窗中，設定將追蹤記錄納入其中的開始日期。 按一下 **[!UICONTROL Add]**. 顯示條件行。 按一下 **[!UICONTROL Expression]** 函式以編輯 **[!UICONTROL Edit expression]** 欄。 在窗口 **[!UICONTROL Field to select]** 中，選擇 **[!UICONTROL Date (@logDate)]**。

      ![](assets/query_editor_nveau_23.png)

      選擇運算 **[!UICONTROL greater than]** 符。 在列中 **[!UICONTROL Value]** ，按一下 **[!UICONTROL Edit expression]**，然後在窗口 **[!UICONTROL Formula type]** 中選擇 **[!UICONTROL Process on dates]**。 最後，在 **[!UICONTROL Current date minus n days]**&#x200B;中輸入&quot;15&quot;。

      按一下 **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_24.png)

   * 若要選取追蹤記錄搜尋結束日期，請按一下以建立第二個條件 **[!UICONTROL Add]**。 在欄中， **[!UICONTROL Expression]** 再次選 **[!UICONTROL Date (@logDate)]** 擇。

      選擇運算 **[!UICONTROL less than]** 符。 在欄中 **[!UICONTROL Value]** 按一下 **[!UICONTROL Edit expression]**。 對於日期處理，請轉至 **[!UICONTROL Formula type]** 窗口，在中輸入&quot;1&quot; **[!UICONTROL Current date minus n days]**。

      按一下 **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_65.png)

      現在，我們要設定第三個篩選條件，即我們查詢所關注的傳送標籤。

   * 按一下函 **[!UICONTROL Add]** 數以建立另一個篩選條件。 在欄中 **[!UICONTROL Expression]** 按一下 **[!UICONTROL Edit expression]**。 在窗口 **[!UICONTROL Field to select]** 中，在節 **[!UICONTROL Label]** 點中選 **[!UICONTROL Delivery]** 擇。

      按一下 **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_66.png)

      尋找包含&quot;sales&quot;字詞的傳送。 由於您不記得其確切標籤，因此可以選擇運 **[!UICONTROL contains]** 算元並在欄中輸入「sales」 **[!UICONTROL Value]** 。

      ![](assets/query_editor_nveau_25.png)

1. 按一 **[!UICONTROL Next]** 下，直到您到達視 **[!UICONTROL Data preview]** 窗：這裡不需要格式設定。
1. 在視窗 **[!UICONTROL Data preview]** 中，按一 **[!UICONTROL Start the preview of the data]** 下以查看每個傳送收件者的追蹤記錄檔數。

   結果會以遞減順序顯示。

   ![](assets/query_editor_tracklog_04.png)

   此傳送的使用者記錄檔數目上限為6。 5位不同的使用者開啟傳送電子郵件，或按一下電子郵件中的其中一個連結。

## 未開啟任何傳送的收件者 {#recipients-who-did-not-open-any-delivery}

在此範例中，我們想篩選過去7天內未開啟電子郵件的收件者。

若要建立此範例，請套用下列步驟：

1. 在工作流程中拖 **[!UICONTROL Query]** 放活動並開啟活動。
1. 按一 **[!UICONTROL Edit query]** 下並將定位和篩選維度設為 **[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 選取 **[!UICONTROL Filtering conditions]** ，然後按一 **[!UICONTROL Next]**&#x200B;下。
1. Click the **[!UICONTROL Add]** button and select **[!UICONTROL Tracking logs]**.
1. 將表達 **[!UICONTROL Operator]** 式的 **[!UICONTROL Tracking logs]** 設定為 **[!UICONTROL Do not exist such as]**。

   ![](assets/query_open_1.png)

1. 新增另一個運算式。 在類 **[!UICONTROL Type]** 別中選 **[!UICONTROL URL]** 擇。
1. 然後，將其 **[!UICONTROL Operator]** 設定為 **[!UICONTROL equal to]** ，其 **[!UICONTROL Value]** 為 **[!UICONTROL Open]**。

   ![](assets/query_open_2.png)

1. 添加另一個表達式並選擇 **[!UICONTROL Date]**。 **[!UICONTROL Operator]** 應設為 **[!UICONTROL on or after]**。

   ![](assets/query_open_3.png)

1. 若要將值設定為最近7天，請按一 **[!UICONTROL Edit expression]** 下欄位中的按 **[!UICONTROL Value]** 鈕。
1. 在類 **[!UICONTROL Function]** 別中，選 **[!UICONTROL Current date minus n days]** 取並新增您要定位的天數。 這裡，我們想鎖定過去7天。

   ![](assets/query_open_4.png)

您的對外轉換將包含過去7天內未開啟電子郵件的收件者。

相反地，如果您想要篩選至少開啟一封電子郵件的收件者，您的查詢應如下所示。 請注意，在本例中，應 **[!UICONTROL Filtering dimension]** 將其設定為 **[!UICONTROL Tracking logs (Recipients)]**。

![](assets/query_open_5.png)

## 已開啟傳送的收件者 {#recipients-who-have-opened-a-delivery}

下列範例說明如何定位在過去2週內開啟傳送的描述檔：

1. 若要定位已開啟傳送的描述檔，您必須使用追蹤記錄檔。 它們儲存在連結表中：首先，在欄位的下拉式清單中選取此表格， **[!UICONTROL Filtering dimension]** 如下所示：

   ![](assets/s_advuser_query_sample1.0.png)

1. 關於篩選條件，請按 **[!UICONTROL Edit expression]** 一下追蹤記錄檔子樹結構中顯示的准則圖示。 選擇字 **[!UICONTROL Date]** 段。

   ![](assets/s_advuser_query_sample1.1.png)

   按一 **[!UICONTROL Finish]** 下以確認選擇。

   若要僅復原不到兩週的追蹤記錄檔，請選取運算 **[!UICONTROL Greater than]** 元。

   ![](assets/s_advuser_query_sample1.4.png)

   然後，單 **[!UICONTROL Edit expression]** 擊列中的 **[!UICONTROL Value]** 表徵圖以定義要應用的計算公式。 選擇公 **[!UICONTROL Current date minus n days]** 式，然後在相關欄位中輸入15。

   ![](assets/s_advuser_query_sample1.5.png)

   按一下公 **[!UICONTROL Finish]** 式窗口的按鈕。 在篩選視窗中，按一下標 **[!UICONTROL Preview]** 簽以檢查定位條件。

   ![](assets/s_advuser_query_sample1.6.png)

## 篩選傳送後收件者的行為 {#filtering-recipients--behavior-folllowing-a-delivery}

在工作流程中， **[!UICONTROL Query]** 和方 **[!UICONTROL Split]** 塊可讓您選取先前傳送後的行為。 此選擇是透過篩選器 **[!UICONTROL Delivery recipient]** 進行。

* 範例目標

   在傳送工作流程中，有數種方式可追蹤第一次電子郵件通訊。 此類操作涉及使用該 **[!UICONTROL Split]** 框。

* 內容

   酒店會寄送「夏季運動優惠」。 交貨四天後，另外兩件交貨送出。 其中一項是「水上運動優惠」，另一項是首次「夏季運動優惠」的後續活動。

   「Watersports選件」傳送給在第一次傳送時按一下「watersports」連結的收件者。 這些點按顯示收件者對主題感興趣。 將它們引向類似的報價是明智的。 不過，未點選「夏季運動優惠」的收件者將會再次收到相同的內容。

下列步驟將示範如何透過整合兩 **[!UICONTROL Split]** 種不同的行為來設定方塊：

1. 將方塊 **[!UICONTROL Split]** 插入工作流程。 此方塊會將第一個交貨的收件者劃分為下一個兩個交貨。 劃分會根據第一個傳送期間連結至收件者行為的篩選條件進行。

   ![](assets/query_editor_ex_09.png)

1. 開啟 **[!UICONTROL Split]** 盒子。 在標籤 **[!UICONTROL General]** 中，輸入標籤：例 **如，根據行為** 分割。

   ![](assets/query_editor_ex_04.png)

1. 在頁籤 **[!UICONTROL Subsets]** 中，定義第一個拆分分支。 例如，輸入此 **分支的** 「已點按」標籤。
1. 選擇選 **[!UICONTROL Add a filtering condition on the incoming population]** 項。 按一下 **[!UICONTROL Edit]**.
1. 在視窗 **[!UICONTROL Targeting and filtering dimension]** 中，按兩下篩選 **[!UICONTROL Recipients of a delivery]** 器。

   ![](assets/query_editor_ex_05.png)

1. 在窗口 **[!UICONTROL Target element]** 中，選擇要應用於此分支的行為： **[!UICONTROL Recipients having clicked (email)]**。

   在下方，選擇 **[!UICONTROL Delivery specified by the transition]** 選項。 這項功能會自動復原第一次傳送期間鎖定的人員。

   這是「水上運動優惠」。

   ![](assets/query_editor_ex_08.png)

1. 定義第二個分支。 此分支會包含後續電子郵件，其內容與第一次傳送的內容相同。 前往標籤 **[!UICONTROL Subsets]** 並按一下 **[!UICONTROL Add]** 以建立它。

   ![](assets/query_editor_ex_06.png)

1. 將顯示另一個子頁籤。 將其命名為「**Did not click**」。
1. 按一下 **[!UICONTROL Add a filtering condition for the incoming population]**. 然後按一 **[!UICONTROL Edit...]**&#x200B;下。

   ![](assets/query_editor_ex_07.png)

1. 在視 **[!UICONTROL Delivery recipients]** 窗中按一 **[!UICONTROL Targeting and filtering dimension]** 下。
1. 在窗口 **[!UICONTROL Target element]** 中，選擇行 **[!UICONTROL Recipients who did not click (email)]** 為。 選擇 **[!UICONTROL Delivery specified by the transition]** 最後一個分支的選項。

   現在 **[!UICONTROL Split]** 已完全配置該框。

   ![](assets/query_editor_ex_03.png)

以下是依預設設定的各種元件清單：

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

   ![](assets/query_editor_ex_02.png)
