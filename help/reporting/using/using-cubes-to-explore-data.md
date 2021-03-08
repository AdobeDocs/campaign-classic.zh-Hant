---
solution: Campaign Classic
product: campaign
title: 使用立方體來探索資料
description: 使用立方體來探索資料
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 2%

---


# 使用立方體來探索資料{#using-cubes-to-explore-data}

行銷分析可讓您更輕鬆地建立報表，並透過立方體從資料庫識別和選取資料。 這可讓您：

* 根據立方建立報表。 此過程在以下位置詳細說明：[探索報表中的資料](#exploring-the-data-in-a-report)。
* 收集資料庫中的資料，並將其分組至清單中，例如識別並建立目標和傳送。 有關詳細資訊，請參閱[構建目標人口](#building-a-target-population)。
* 將透視表插入報表中，引用報表中的現有立方。 有關詳細資訊，請參閱[將透視表插入報告](#inserting-a-pivot-table-into-a-report)。

>[!NOTE]
>
>建立或修改立方是必要的行銷分析。 有關詳細資訊，請參閱[關於立方](../../reporting/using/about-cubes.md)。

## 探索報表{#exploring-the-data-in-a-report}中的資料

### 步驟1 —— 基於立方{#step-1---creating-a-report-based-on-a-cube}建立報告

要建立基於立方的報表，請按一下&#x200B;**[!UICONTROL Reports]**&#x200B;頁籤中的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕，然後選擇要使用的立方。

此過程在以下位置詳細說明：[建立以立方](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube)為基礎的報表。

### 步驟2 —— 選擇行和列{#step-2---selecting-lines-and-columns}

預設顯示顯示立方的前兩個維（在本例中為年齡和城市）。

每個軸上的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕可讓您新增尺寸。

![](assets/s_advuser_cube_in_report_03.png)

1. 選擇要在表格的行和列中顯示的維。 若要這麼做，請拖放可用的維度，如下所示：
1. 從清單中選擇要添加到表的維：

   ![](assets/s_advuser_cube_in_report_04.png)

1. 然後選擇此尺寸的參數。

   ![](assets/s_advuser_cube_in_report_04b.png)

   參數取決於所選維的資料類型。

   例如，對於日期，可以使用數個層級。 有關詳細資訊，請參閱[顯示度量](../../reporting/using/concepts-and-methodology.md#displaying-measures)。

   本例提供下列選項：

   ![](assets/s_advuser_cube_in_report_config2.png)

   您可以：

   * 在載入期間展開資料：每次更新報表時，預設會顯示值(預設值：否)。
   * 在行尾顯示總計：當資料以欄顯示時，另一個選項可讓您在行尾顯示總計：將一列添加到表中(預設值：是)。
   * 套用排序：可以根據值、標籤或度量(預設值：值)。
   * 以遞增(a-z, 0-9)或遞減(z-a, 9-0)順序顯示值。
   * 變更載入時要顯示的欄數(預設為：200)。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;確認：維將添加到現有維。

   表格上方的黃色橫幅顯示您已進行變更：按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕保存它們。

   ![](assets/s_advuser_cube_in_report_04c.png)

### 步驟3 —— 將測量配置為顯示{#step-3---configuring-the-measures-to-display}

在行和列就位後，指定要顯示的測量及其顯示模式。

預設情況下，只顯示一個度量。 要添加或配置度量：

1. 按一下 **[!UICONTROL Measures]** 按鈕。

   ![](assets/s_advuser_cube_in_report_05.png)

1. 使用&#x200B;**[!UICONTROL Use a measure]**&#x200B;按鈕可以選擇一個現有測量。

   ![](assets/s_advuser_cube_in_report_08.png)

   選擇要顯示的資訊和格式類型。 選項清單取決於已配置的測量類型。

   ![](assets/s_advuser_cube_in_report_09.png)

   也可透過標題中的&#x200B;**[!UICONTROL Edit the configuration of the pivot table]**&#x200B;圖示使用整體測量設定。

   ![](assets/s_advuser_cube_in_report_config_02.png)

   然後，您可以選擇是否顯示度量標籤。 有關詳細資訊，請參閱[配置顯示](../../reporting/using/concepts-and-methodology.md#configuring-the-display)。

1. 有可能使用現有的措施來建立新的措施。 若要這麼做，請按一下&#x200B;**[!UICONTROL Create a measure]**&#x200B;並加以設定。

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   可用的測量類型如下：

   * 措施組合：此類型的度量使您能夠使用現有度量構建新度量：

      可用的運算子包括：和、差、乘和速率。

   * 比例：這種測量類型使您能夠計算為給定尺寸測量的記錄數。 您可以根據維度或子維度計算比例。
   * 變化：此度量可讓您計算層級值的變化。
   * 標準差：此類型的測量可讓您計算每組儲存格內與平均值的偏差。 例如，您可以比較所有現有區段的購買量。

   建立的度量將添加到報告中。

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   建立度量後，可以對其進行編輯，並根據需要更改其配置。 要執行此操作，請按一下&#x200B;**[!UICONTROL Measures]**&#x200B;按鈕，然後轉到要編輯的度量的頁籤。

   然後按一下&#x200B;**[!UICONTROL Edit the dynamic measure]**&#x200B;以存取設定功能表。

## 建立目標人口{#building-a-target-population}

使用立方建立報表可讓您從表格收集資料並儲存在清單中。

若要這麼做，請將它們新增至購物車並處理其內容。

要將人口分組到清單中，請應用以下步驟：

1. 按一下包含要收集之人口族群的儲存格以選取它們，然後按一下&#x200B;**[!UICONTROL Add to cart]**&#x200B;圖示。

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   若要收集各種描述檔，請視需要多次這麼做

1. 在執行匯出之前，按一下&#x200B;**[!UICONTROL Show cart]**&#x200B;按鈕以檢視其內容。

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. **[!UICONTROL Export]**&#x200B;按鈕可讓您將購物車中的項目群組至清單。

   您需要指定清單的名稱和要執行的匯出類型。

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   按一下&#x200B;**[!UICONTROL Start]**&#x200B;以運行導出。

1. 匯出完成後，訊息會確認其執行以及已處理的記錄數。

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   您可以儲存購物車的內容或將其空白。

   相關清單可通過&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;頁籤訪問。

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## 將透視表插入報表{#inserting-a-pivot-table-into-a-report}

要建立表並瀏覽立方中的資料，請應用以下步驟：

1. 使用單一頁面建立新報表，並將樞紐表插入報表。 有關詳細資訊，請參見[此頁面](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)。

   ![](assets/s_advuser_cube_in_report_01.png)

1. 在頁的&#x200B;**[!UICONTROL Data]**&#x200B;頁籤中，選擇立方以處理它包含的維並顯示計算度量。

   ![](assets/s_advuser_cube_in_report_02.png)

   這可讓您建立要顯示的報表。 有關詳細資訊，請參閱[步驟2 —— 選擇行和列](#step-2---selecting-lines-and-columns)。

