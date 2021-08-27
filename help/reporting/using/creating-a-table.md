---
product: campaign
title: 建立資料表
description: 建立資料表
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 05f76bdf-6dcd-4360-9e72-0ba6a4dd0d5e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2495'
ht-degree: 1%

---

# 建立資料表{#creating-a-table}

![](../../assets/common.svg)

您可以新增表格至報表以顯示資料。 這可以是根據多維資料集測量建立的透視表、具有組的清單或包含值劃分的表。

![](assets/s_advuser_report_page_activity_05.png)

## 建立包含群組的清單 {#creating-a-list-with-group}

**[!UICONTROL List with group]**&#x200B;類型表可讓您對表格中的資料進行分組，並產生統計資料。 例如，您可以建立資料的總計和子總計。 每個群組都有其專屬的頁首、詳細資料和頁尾行。

>[!CAUTION]
>
>包含表格的&#x200B;**[!UICONTROL Page]**&#x200B;活動前面必須有&#x200B;**[!UICONTROL Query]**&#x200B;或&#x200B;**[!UICONTROL Script]**&#x200B;活動，以收集要在報表中分析的資料。 有關這些活動的詳細資訊，請參閱[收集資料以分析](../../reporting/using/collecting-data-to-analyze.md)和[指令碼活動](../../reporting/using/advanced-functionalities.md#script-activity)。

### 操作原則 {#operating-principle}

您可能需要同時分析數個資料類別。 具有群組的清單可讓您結合資料，並針對相同表格內的各種資料群組建立統計資料。 若要這麼做，您可以在表格中建立群組。

在下列範例中，群組會顯示資料庫中的所有促銷活動、傳送，以及每次傳送和每個促銷活動所傳送的訊息數。

它可讓您列出連結至促銷活動的促銷活動(**[!UICONTROL Label (Campaign)]**，傳遞清單(**[!UICONTROL Label]**)，並可讓您計算每次傳遞傳送的訊息數(**[!UICONTROL Processed)]**，然後再為每個促銷活動(**[!UICONTROL Sum(@processed)]**)加總。

![](assets/s_advuser_ergo_listgroup_005.png)

### 實施步驟 {#implementation-steps}

以下提供完整的實作範例：[使用案例：建立包含群組清單](#use-case--create-a-report-with-a-group-list)的報表。

請注意以下步驟，以建立「具有組的清單」類型表：

1. 前往報表圖表並放置&#x200B;**[!UICONTROL Query]**&#x200B;活動。 請參閱[收集資料以分析](../../reporting/using/collecting-data-to-analyze.md)。
1. 填寫源表，並選擇統計資訊將涉及的表的欄位。
1. 將&#x200B;**[!UICONTROL Page]**&#x200B;活動放入圖表中。 有關詳細資訊，請參閱[靜態元素](../../reporting/using/creating-a-new-report.md#static-elements)。
1. 將&#x200B;**[!UICONTROL List with group]**&#x200B;類型表插入頁中。
1. 指定資料路徑，或在查詢中選擇作為資料源的表。

   如果以後要恢復源表中的欄位，並將它們插入表的單元格中，則此步驟是必需的。

1. 建立表格及其內容。
1. 在&#x200B;**[!UICONTROL Preview]**&#x200B;標籤中顯示已完成的報表。 接著，您可以發佈報表，並視需要將其匯出為不同格式。 有關詳細資訊，請參閱[匯出報表](../../reporting/using/actions-on-reports.md#exporting-a-report)。

### 添加行和列 {#adding-lines-and-columns}

預設情況下，**[!UICONTROL List with group]**&#x200B;類型表包括頁眉、明細行和頁腳行。

組本身包括頁眉、詳細資訊和頁腳行。

* **標題行**:此行可讓您為表格的欄指定標題。

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **明細行**:此行包含統計值。

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **頁尾行**:此行可讓您顯示總值。

   ![](assets/s_advuser_ergo_listgroup_003.png)

您可以新增行和欄以符合您的需求。

組可以放置在表的任何行上，並包括其自己的頁眉、詳細資訊和頁腳行。

![](assets/s_advuser_ergo_listgroup_019.png)

**行和列**:要添加或刪除行或列，請轉到現有行或列，然後使用右鍵菜單。

![](assets/s_advuser_ergo_listgroup_006.png)

添加的行的性質取決於游標的位置。 例如，要添加標題行，請將游標放在標題上，然後按一下&#x200B;**[!UICONTROL Add > A line above/below]**。

![](assets/s_advuser_ergo_listgroup_006a.png)

欄的寬度可以透過&#x200B;**[!UICONTROL Column format]**&#x200B;項目修改。

**群組**:若要新增群組，請移至某一行，然後在下拉式功能表中選取相符項目。

![](assets/s_advuser_ergo_listgroup_007.png)

### 定義儲存格內容 {#defining-cell-content}

若要編輯表格的儲存格並定義其內容和格式，請移至儲存格，然後使用滑鼠右鍵功能表。

使用&#x200B;**[!UICONTROL Expression]**&#x200B;菜單條目選擇要顯示的值。

![](assets/s_advuser_ergo_listgroup_010.png)

* 要將要直接分析的值插入表中，請在可用欄位中選取它們。

   可用欄位清單與報表建構圖表中表格之前的查詢內容一致。

   ![](assets/s_advuser_ergo_listgroup_011.png)

* 輸入儲存格的標籤，例如標題。

   要執行此操作，請使用與在資料庫中插入欄位相同的過程，但不選擇表達式。 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入標籤。 會依原樣顯示。

* 計算匯總（平均值、總和等） 並在儲存格中顯示。

   若要這麼做，請使用&#x200B;**[!UICONTROL Aggregates]**&#x200B;功能表項目並選取所需的促銷活動。

   ![](assets/s_advuser_ergo_listgroup_008.png)

### 定義儲存格格式 {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

若要定義儲存格格式，**[!UICONTROL Cell format...]**&#x200B;功能表可讓您存取所選儲存格可用的所有格式選項。

這些選項可讓您個人化報表的最終轉譯，並更輕鬆地閱讀資訊。

將資料匯出至Excel時，請使用&#x200B;**[!UICONTROL Carriage return]**&#x200B;欄位：選取&#x200B;**[!UICONTROL Yes]**&#x200B;值以強制回車。 匯出時會保留此值。 有關詳細資訊，請參閱[匯出報表](../../reporting/using/actions-on-reports.md#exporting-a-report)。

**[!UICONTROL Cell format]**&#x200B;視窗可讓您存取下列索引標籤：

* **[!UICONTROL Value]**&#x200B;標籤
* **[!UICONTROL Borders]**&#x200B;標籤
* **[!UICONTROL Click]**&#x200B;標籤
* **[!UICONTROL Extra]**&#x200B;標籤

**[!UICONTROL Value]**&#x200B;索引標籤可讓您變更字型和各種值屬性，或根據其性質定義格式。

![](assets/s_advuser_ergo_listgroup_009.png)

格式會變更資料顯示：例如，**[!UICONTROL Number]**、**[!UICONTROL Monetary]**&#x200B;和&#x200B;**[!UICONTROL Percentage]**&#x200B;格式允許您對齊右側的數字並顯示小數點。

如何設定貨幣格式的範例：您可以指定值所表示的貨幣、選擇是否要分隔千位，以及以紅色顯示負值。 貨幣符號的位置取決於其設定檔中定義的運算子語言。

![](assets/s_advuser_ergo_listgroup_012.png)

日期的設定範例：您可以選擇是否顯示時間。

![](assets/s_advuser_ergo_listgroup_013.png)

**邊框**&#x200B;標籤可讓您在表格中的行和列中添加邊框。 將大型報表匯出至Excel時，新增邊框至儲存格可能會導致效能問題。

![](assets/s_advuser_ergo_listgroup_014.png)

如有必要，您可以在表格範本中定義邊框(**[!UICONTROL Administration > Configuration > Form rendering]**)。

在此情況下，您會使用下列語法：

在Web頁簽中：

```
 .tabular td {
 border: solid 1px #000000;
 }
```

在Excel索引標籤中：

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

**[!UICONTROL Click]**&#x200B;標籤可讓您定義使用者點按儲存格或表格內容時的動作。

在以下範例中，按一下儲存格中的值可讓您顯示報表的第二個頁面：其中會包含儲存格內傳送的資訊。

![](assets/s_advuser_ergo_listgroup_015.png)

**Extra**&#x200B;標籤可讓您將視覺化連結至資料，例如彩色標籤或值列。 當表格在圖表中顯示為圖例時，會使用彩色標籤。 如需詳細資訊，請參閱實作範例：[步驟5 — 建立第二頁](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## 使用案例：建立包含群組清單的報表 {#use-case--create-a-report-with-a-group-list}

在此範例中，我們將建立兩頁報表：第一個頁面會包含清單、每個促銷活動的傳送總數，以及傳送的訊息數量。 傳送名稱將可點按連結，且可讓您前往報表的第二頁，透過表格和圖表檢視所選傳送之每個電子郵件網域的傳送劃分。 在第二頁，表格將作為圖表的圖例。

![](assets/reporting_quick_start_report-final.png)

### 步驟1 — 建立報表 {#step-1---create-a-report}

建立與促銷活動結構&#x200B;**[!UICONTROL Campaigns (nms)]**&#x200B;相關的新報表。

![](assets/s_advuser_report_listgroup_001.png)

按一下&#x200B;**[!UICONTROL Save]**&#x200B;以建立報表。

前往圖表，並新增用於設計報表內容的第一個元件：第一個查詢和第一個頁面。

![](assets/reporting_quick_start_diagram.png)

### 步驟2 — 建立第一個查詢 {#step-2---create-the-first-query}

第一個查詢可讓您收集連結至每個促銷活動的傳遞。 目標是顯示連結至每個促銷活動之Adobe Campaign資料庫的各種傳送報表。

按兩下第一個查詢以進行編輯，然後套用下列步驟進行設定：

1. 首先，更改應用查詢源的架構：選擇&#x200B;**[!UICONTROL Deliveries (nms)]**&#x200B;架構。
1. 按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;連結並顯示進階欄位。

   ![](assets/reporting_quick_start_query-1.png)

1. 選取下列欄位：

   * 傳遞標籤，
   * 傳遞的主鍵，
   * 宣傳標籤，
   * 已處理傳送的指標，
   * 行銷活動連結的外鍵，
   * 錯誤率指示器。

   ![](assets/s_advuser_report_listgroup_002.png)

   將別名連結到每個欄位：建議您這麼做，以便從表格中選取資料，以新增至報表的第一頁。

   在此範例中，我們將使用下列別名：

   * 標籤：**@label**
   * 主鍵：**@deliveryId**
   * 標籤（促銷活動）:**@label1**
   * 已處理：**@processed**
   * 「促銷活動」（「id」欄位）連結的外鍵：**@operationId**
   * 錯誤率：**@errorRatio**


1. 按兩下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕以前往&#x200B;**[!UICONTROL Data filtering]**&#x200B;步驟。

   新增篩選條件，以僅收集連結至促銷活動的傳送。

   此篩選器的語法如下：&quot;Campaigns連結的外鍵大於0&quot;。

   ![](assets/reporting_quick_start_query_filter.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以儲存這些條件，然後按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以關閉查詢編輯器。

### 步驟3:建立第一頁 {#step-3--create-the-first-page}

在此步驟中，我們將設定報表的第一頁。 若要設定，請套用下列步驟：

1. 開啟&#x200B;**[!UICONTROL Page]**&#x200B;活動並輸入其標題，在此例中為&#x200B;**Deliveries**。

   ![](assets/s_advuser_report_listgroup_003.png)

1. 透過工具列插入含群組的清單並輸入其標籤，例如：每個促銷活動的傳送清單。

   ![](assets/s_advuser_report_listgroup_004.png)

1. 按一下&#x200B;**[!UICONTROL Table data XPath...]**&#x200B;連結並選取傳送連結，即`[query/delivery]`。

   ![](assets/s_advuser_report_listgroup_005.png)

1. 按一下&#x200B;**[!UICONTROL Data]**&#x200B;標籤並更改表的佈局：在右側新增三欄。

   ![](assets/s_advuser_report_listgroup_006.png)

1. 新增群組。

   ![](assets/s_advuser_report_listgroup_008.png)

   此群組可讓您將行銷活動和連結至行銷活動的傳送分組。

1. 在群組視窗中，參考&#39;Campaign&#39;連結&#x200B;**的**&#x200B;外鍵並關閉視窗。

   ![](assets/s_advuser_report_listgroup_007.png)

1. 編輯群組標題的第一個儲存格，並將促銷活動的&#x200B;**[!UICONTROL Label]**&#x200B;欄位插入為運算式。

   ![](assets/s_advuser_report_listgroup_009.png)

1. 編輯詳細資訊行的第二個儲存格，並選取傳送&#x200B;**[!UICONTROL Label]**。

   ![](assets/s_advuser_report_listgroup_011.png)

1. 編輯此儲存格的格式，並開啟&#x200B;**[!UICONTROL Click]**&#x200B;標籤。 設定適當的選項，讓使用者按一下傳送名稱時，就會在相同視窗中開啟。

   ![](assets/s_advuser_report_listgroup_0111.png)

   要執行此操作，請選擇&#x200B;**[!UICONTROL Next page]**&#x200B;類型操作，並選擇&#x200B;**[!UICONTROL In the same window]**&#x200B;作為開啟選項。

   ![](assets/s_advuser_report_listgroup_0112.png)

1. 在視窗的下方區段中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;並指定&#x200B;**`/vars/selectedDelivery`**&#x200B;路徑和&#x200B;**[!UICONTROL @deliveryId]**&#x200B;運算式，以符合傳送主要金鑰的別名，如先前建立的查詢所定義。 此公式可讓您存取選取的傳送。

   ![](assets/s_advuser_report_listgroup_010.png)

1. 編輯組頁尾行的第二個單元格，並輸入&#x200B;**[!UICONTROL Total per campaign]**&#x200B;作為標籤。

   ![](assets/s_advuser_report_listgroup_012.png)

1. 編輯組標題行的第三個單元格，並輸入&#x200B;**[!UICONTROL Number of messages sent]**&#x200B;作為標籤。

   ![](assets/s_advuser_report_listgroup_013.png)

   此資訊與欄標題一致。

1. 編輯詳細資訊行的第三個儲存格，並選取已處理的訊息指示器作為運算式。

   ![](assets/s_advuser_report_listgroup_014.png)

1. 編輯組頁尾行的第三個單元格，選擇已處理的傳送指示符，並將&#x200B;**[!UICONTROL Sum]**&#x200B;聚合應用到該指示符。

   ![](assets/s_advuser_report_listgroup_015.png)

1. 編輯詳細資訊行的第四個儲存格，並選取&#x200B;**錯誤傳送錯誤率**&#x200B;作為運算式。

   ![](assets/s_advuser_report_listgroup_016.png)

1. 選取此儲存格，以顯示代表傳送錯誤率的值列。

   要執行此操作，請訪問單元格格式，然後轉到&#x200B;**[!UICONTROL More]**&#x200B;頁簽。 在下拉式清單中選取&#x200B;**[!UICONTROL Value bar]**&#x200B;項目，然後選取&#x200B;**[!UICONTROL Hide the cell value]**&#x200B;選項。

   ![](assets/s_advuser_report_listgroup_023.png)

   您現在可以檢視報表的呈現。 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤並選取&#x200B;**[!UICONTROL Global]**&#x200B;選項：這會顯示連結至促銷活動之Adobe Campaign資料庫中所有傳送的清單。

   ![](assets/s_advuser_report_listgroup_025.png)

   建議您使用&#x200B;**[!UICONTROL Preview]**&#x200B;標籤，確認已正確選取並設定表格中的資料。 完成此操作後，您可以繼續格式化表格。

1. 將&#x200B;**[!UICONTROL Bold]**&#x200B;樣式套用至顯示每個促銷活動總計和已處理訊息總數的儲存格。

   ![](assets/s_advuser_report_listgroup_024.png)

1. 按一下群組標題行（顯示促銷活動名稱的行）的第一個儲存格，然後選取&#x200B;**[!UICONTROL Edit > Merge to right]**。

   ![](assets/s_advuser_report_listgroup_026.png)

   合併群組標題行的前兩個儲存格，將會重新對齊促銷活動標題和連結至該行銷活動的傳送清單。

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >建議您等到報表建置完成，再合併儲存格，因為合併是不可復原的。

### 步驟4 — 建立第二個查詢 {#step-4---create-the-second-query}

我們想新增第二個查詢和第二個頁面，以在報表的使用者點按時顯示傳送的詳細資料。 新增查詢前，請編輯您建立的頁面並啟用傳出轉變，以便將其連結至查詢。

1. 在&#x200B;**[!UICONTROL Page]**&#x200B;活動後新增查詢並編輯其結構：選擇&#x200B;**[!UICONTROL Recipient delivery logs]**&#x200B;架構。

   ![](assets/reporting_quick_start_query-2.png)

1. 編輯查詢並定義輸出欄。 若要顯示每個電子郵件網域的傳送數量，您必須：

   * 計算主要金鑰的總和，以計算傳送記錄檔的數量：

      ![](assets/reporting_quick_start_query-2_count.png)

   * 收集此欄位的收件者電子郵件網域和群組資訊：要執行此操作，請在「域名」列中選擇&#x200B;**[!UICONTROL Group]**&#x200B;選項。

   ![](assets/reporting_quick_start_query-2_filter.png)

   將以下別名連結到欄位：

   * count(primary key):**@count**
   * 電子郵件域（收件人）:**@domain**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. 按兩下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕：這會帶您前往&#x200B;**[!UICONTROL Data filtering]**&#x200B;步驟。

   新增篩選條件，以僅收集連結至所選傳送的資訊。

   語法如下：「傳送」連結的外鍵等於設定`$([vars/selectedDelivery])`的值

   ![](assets/s_advuser_report_listgroup_017.png)

1. 關閉查詢配置窗口，並在第二個查詢後添加頁到圖表。

### 步驟5 — 建立第二頁 {#step-5---create-the-second-page}

1. 編輯頁面並輸入其標籤：**電子郵件網域**。
1. 取消選中&#x200B;**[!UICONTROL Enable output transitions]**&#x200B;選項：這是報表的最後一頁，後面不會有其他活動。

   ![](assets/s_advuser_report_listgroup_028.png)

1. 使用右鍵功能表，新增群組的新清單，並將其呼叫給每個收件者&#x200B;**電子郵件網域。**
1. 按一下&#x200B;**[!UICONTROL Table data XPath...]**&#x200B;並選取&#x200B;**[!UICONTROL Recipient delivery logs]**&#x200B;連結。

   ![](assets/s_advuser_report_listgroup_029.png)

1. 在&#x200B;**[!UICONTROL Data]**&#x200B;標籤中，調整表格，如下所示：

   * 在右側新增兩欄。
   * 在詳細資訊行的第一個儲存格中，新增&#x200B;**[!UICONTROL rowNum()-1]**&#x200B;運算式以計算行數。 然後變更儲存格的格式：在&#x200B;**[!UICONTROL Extra]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL Color tab]**&#x200B;並按一下&#x200B;**[!UICONTROL Ok]**。

      ![](assets/s_advuser_report_listgroup_018.png)

      此設定可讓您將表格用作圖表的註解。

   * 在詳細資訊行的第二個儲存格中，新增&#x200B;**[!UICONTROL Email domain(Recipient)]**&#x200B;運算式。
   * 在詳細資訊行的第三個儲存格中，新增&#x200B;**[!UICONTROL count(primary key)]**&#x200B;運算式。

   ![](assets/s_advuser_report_listgroup_019.png)

1. 使用右鍵菜單將餅圖添加到頁中，並為其分配&#x200B;**電子郵件域**&#x200B;標籤。 如需詳細資訊，請參閱[圖表類型和變體](../../reporting/using/creating-a-chart.md#chart-types-and-variants)。
1. 按一下&#x200B;**[!UICONTROL Variants]**&#x200B;連結，取消選取&#x200B;**[!UICONTROL Display label]**&#x200B;和&#x200B;**[!UICONTROL Display caption]**&#x200B;選項。
1. 檢查是否未配置值排序。 如需詳細資訊，請參閱[本章節](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report)。

   ![](assets/s_advuser_report_listgroup_0191.png)

1. 在&#x200B;**[!UICONTROL Data]**&#x200B;標籤中，變更資料來源：從下拉式清單中選取&#x200B;**[!UICONTROL Context data]**。

   ![](assets/s_advuser_report_listgroup_020.png)

1. 然後按一下&#x200B;**[!UICONTROL Advanced settings]**&#x200B;並選取收件者傳送記錄檔的連結。

   ![](assets/s_advuser_report_listgroup_0201.png)

1. 在&#x200B;**[!UICONTROL Chart type]**&#x200B;區段中，選取&#x200B;**[!UICONTROL Email domain]**&#x200B;變數。
1. 然後新增要執行的計算：選取總和作為運算子。

   ![](assets/s_advuser_report_listgroup_0202.png)

1. 按一下&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕以選取計數將關注的欄位，然後關閉設定視窗。

   ![](assets/s_advuser_report_listgroup_030.png)

1. 儲存報表。

   您的頁面現在已設定完畢。

### 步驟6 — 檢視報表 {#step-6---viewing-the-report}

要查看此配置的結果，請按一下&#x200B;**[!UICONTROL Preview]**&#x200B;頁簽並選擇&#x200B;**[!UICONTROL Global]**&#x200B;選項。

報表的第一頁詳細說明資料庫中包含的所有傳送清單。

![](assets/s_advuser_report_listgroup_021.png)

如果您按一下其中一個傳送的連結，圖表會顯示此傳送的電子郵件網域劃分。 您現在位在報表的第二頁，可按一下適當的按鈕，返回上一頁。

![](assets/s_advuser_report_listgroup_022.png)

## 建立劃分或樞紐表格 {#creating-a-breakdown-or-pivot-table}

此類型的表格可讓您顯示根據資料庫中資料計算的統計資料。

這些類型的報表的設定與描述性分析精靈所使用的報表類似。 如需詳細資訊，請參閱[此頁面](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template)。

有關建立透視表的詳細資訊，請參閱[此部分](../../reporting/using/using-cubes-to-explore-data.md)。
