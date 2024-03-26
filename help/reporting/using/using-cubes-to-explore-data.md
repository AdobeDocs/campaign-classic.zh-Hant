---
product: campaign
title: 使用 cubes 來探索資料
description: 使用 cubes 來探索資料
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Reporting, Monitoring
hide: true
hidefromtoc: true
exl-id: 32696bbf-1415-4214-837f-5437fdb8b4d4
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 2%

---

# 使用 cubes 來探索資料{#using-cubes-to-explore-data}



Marketing Analytics可讓您更輕鬆地建立報表，以及透過多維度資料集從資料庫識別和選取資料。 這可讓您：

* 根據立方體建立報告。 本流程的詳細資訊如下： [探索報表中的資料](#exploring-the-data-in-a-report).
* 收集資料庫中的資料，並將其分組到清單中，例如識別及建立目標及傳遞。 有關詳細資訊，請參閱 [建立目標母體](#building-a-target-population).
* 在報表中插入樞紐分析表，參照其中現有的立方結構。 有關詳細資訊，請參閱 [在報表中插入樞紐分析表](#inserting-a-pivot-table-into-a-report).

>[!NOTE]
>
>需要Marketing Analytics才能建立或修改立方體。 有關詳細資訊，請參閱 [關於立方體](../../reporting/using/ac-cubes.md).

## 探索報表中的資料 {#exploring-the-data-in-a-report}

### 步驟1 — 根據立方體建立報表 {#step-1---creating-a-report-based-on-a-cube}

若要根據立方結構建立報表，請按一下 **[!UICONTROL Create]** 中的按鈕 **[!UICONTROL Reports]** 頁簽並選取您要使用的立方結構。

本流程的詳細資訊如下： [根據立方體建立報告](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube).

### 步驟2 — 選取行和欄 {#step-2---selecting-lines-and-columns}

預設顯示會顯示立方結構的前兩個維度（在此例中是年齡和城市）。

此 **[!UICONTROL Add]** 每個軸上的按鈕可讓您新增維度。

![](assets/s_advuser_cube_in_report_03.png)

1. 選取要在表格的行和欄中顯示的尺寸。 若要這麼做，請拖放可用的維度，如下所示：
1. 從清單中選取要新增至表格的維度：

   ![](assets/s_advuser_cube_in_report_04.png)

1. 然後選取此尺寸的引數。

   ![](assets/s_advuser_cube_in_report_04b.png)

   引數取決於所選尺寸的資料型別。

   例如，日期有數個層級可供使用。 有關詳細資訊，請參閱 [顯示量值](../../reporting/using/concepts-and-methodology.md#displaying-measures).

   此案例中提供下列選項：

   ![](assets/s_advuser_cube_in_report_config2.png)

   您可以：

   * 載入時展開資料：預設會在每次更新報表時顯示值（預設值：否）。
   * 在行尾顯示總計：當資料以欄顯示時，附加選項可讓您在行尾顯示總計：在表格中新增欄（預設值：是）。
   * 套用排序：欄的值可依值、標籤或量值（預設值：依值）排序。
   * 以遞增(a-z、0-9)或遞減(z-a、9-0)順序顯示值。
   * 變更載入時顯示的欄數（預設為： 200）。

1. 按一下 **[!UICONTROL Ok]** 確認：將維度新增至現有維度。

   表格上方的黃色橫幅顯示您已進行變更：按一下 **[!UICONTROL Save]** 按鈕以儲存它們。

   ![](assets/s_advuser_cube_in_report_04c.png)

### 步驟3 — 設定要顯示的測量 {#step-3---configuring-the-measures-to-display}

直線和欄位就位後，指示您要顯示的量測及其顯示模式。

依預設，只顯示一個量值。 若要新增或設定測量：

1. 按一下 **[!UICONTROL Measures]** 按鈕。

   ![](assets/s_advuser_cube_in_report_05.png)

1. 此 **[!UICONTROL Use a measure]** 按鈕可讓您選取現有的測量之一。

   ![](assets/s_advuser_cube_in_report_08.png)

   選取您要顯示的資訊和格式型別。 選項清單視已設定的測量型別而定。

   ![](assets/s_advuser_cube_in_report_09.png)

   整體測量組態也可透過 **[!UICONTROL Edit the configuration of the pivot table]** 圖示來識別。

   ![](assets/s_advuser_cube_in_report_config_02.png)

   然後，您可以選擇是否要顯示測量標籤。 有關詳細資訊，請參閱 [設定顯示](../../reporting/using/concepts-and-methodology.md#configuring-the-display).

1. 可以使用現有測量來建置新測量。 若要這麼做，請按一下 **[!UICONTROL Create a measure]** 並加以設定。

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   可用的測量型別如下：

   * 測量的組合：此型別的測量可讓您使用現有的測量來建立新的測量：

     可用的運運算元包括：和、差、乘和速率。

   * 比例：此測量型別可讓您計算針對指定維度測量的記錄數。 您可以根據維度或子維度來計算比例性。
   * 變化：此測量可讓您計算某個層級值的變化。
   * 標準差：此型別的測量可讓您計算每一儲存格群組內與平均值比較的偏差。 例如，您可以比較所有現有區段的購買量。

   建立的測量會新增至報表。

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   建立測量之後，您可以編輯它，並視需要變更其組態。 若要這麼做，請按一下 **[!UICONTROL Measures]** 按鈕，然後移至要編輯之測量的標籤。

   然後按一下 **[!UICONTROL Edit the dynamic measure]** 以存取設定功能表。

## 建立目標母體 {#building-a-target-population}

使用立方體建置報表可讓您從表格收集資料並將其儲存在清單中。

若要這麼做，請將它們新增至購物車並處理其內容。

若要將母體群組至清單，請套用下列步驟：

1. 按一下包含要收集之母體的儲存格加以選取，然後按一下 **[!UICONTROL Add to cart]** 圖示。

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   收集各種設定檔所需的時間

1. 按一下 **[!UICONTROL Show cart]** 按鈕以在執行匯出之前檢視其內容。

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. 此 **[!UICONTROL Export]** 按鈕可讓您將購物車中的專案分組到清單中。

   您需要指定清單的名稱和要執行的匯出型別。

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   按一下 **[!UICONTROL Start]** 以執行匯出。

1. 匯出完成後，訊息會確認其執行以及已處理的記錄數。

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   您可以儲存購物車的內容或將其清空。

   相關清單可透過以下方式存取： **[!UICONTROL Profiles and targets]** 標籤。

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## 在報表中插入樞紐分析表 {#inserting-a-pivot-table-into-a-report}

若要建立表格並探索立方結構中的資料，請套用下列步驟：

1. 建立具有單一頁面的新報表，並在其中插入樞紐分析表。 如需詳細資訊，請參閱[此頁面](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)。

   ![](assets/s_advuser_cube_in_report_01.png)

1. 在 **[!UICONTROL Data]** 頁簽中，選取立方結構以處理其所包含的維度，並顯示計算的計量。

   ![](assets/s_advuser_cube_in_report_02.png)

   這可讓您建立要顯示的報表。 有關詳細資訊，請參閱 [步驟2 — 選取行和欄](#step-2---selecting-lines-and-columns).
