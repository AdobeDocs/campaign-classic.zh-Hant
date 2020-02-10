---
title: 報表動作
seo-title: 報表動作
description: 報表動作
seo-description: null
page-status-flag: never-activated
uuid: 7f9d99ab-ce19-46dd-bbf0-79de348d38fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 3b9c138e-8f7f-4ee1-9baa-328848d01d3a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# 報表動作{#actions-on-reports}

當您檢視報表時，工具列可讓您執行特定數目的動作。 以下是詳細說明。

![](assets/s_ncs_advuser_report_wizard_2.png)

例如，工具列可讓您匯出、列印、封存或在網頁瀏覽器中顯示報表。

![](assets/s_ncs_advuser_report_wizard_04.png)

## 匯出報表 {#exporting-a-report}

從下拉式清單中，選取您要將報表匯出至的格式。 （.xls、.pdf或。ods）。

![](assets/s_ncs_advuser_report_wizard_06.png)

當報表包含數個頁面時，您必須對每個頁面重複此作業。

您可以設定報表，以匯出為PDF、Excel或OpenOffice格式。 開啟Adobe Campaign瀏覽器並選取相關報表。

匯出選項可透過報 **[!UICONTROL Page]** 表的活動在標籤中存 **[!UICONTROL Advanced]** 取。

變更和的設 **[!UICONTROL Paper]** 定 **[!UICONTROL Margins]** 以符合您的需求。 您也可以僅授權匯出PDF格式的頁面。 若要這麼做，請取消勾選 **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** 選項。

![](assets/s_ncs_advuser_report_wizard_021.png)

### 匯出至Microsoft Excel {#exporting-into-microsoft-excel}

對於 **[!UICONTROL List with group]** 要匯出至Excel的類型報表，會套用下列建議和限制：

* 這些報表不得包含任何空行。

   ![](assets/export_limitations_remove_empty_line.png)

* 清單的圖例必須隱藏。

   ![](assets/export_limitations_hide_label.png)

* 報表不必使用在儲存格層級定義的特定格式。 最好使用 **[!UICONTROL Form rendering]** 定義表中單元格的格式。 您可 **[!UICONTROL Form rendering]** 以透過存取 **[!UICONTROL Administration > Configuration > Form rendering]**。
* 我們不建議插入HTML內容。
* 如果報表包含數個表格、圖表等。 類型元素，它們將導出到另一個下方。
* 您可以強制儲存格中的歸位符號：此設定將保留在Excel中。 有關詳細資訊，請參閱此定 [義單元格格式](../../reporting/using/creating-a-table.md#defining-cell-format)。

### 推遲出口 {#postpone-the-export}

您可以延遲匯出報表，例如等候非同步呼叫。 要執行此操作，請在頁面的初始化指令碼中輸入以下參數：

```
document.nl_waitBeforeRender = true;
```

若要啟動匯出並開始轉換為PDF，請使用 **document.nl_renderToPdf()函式，毋需任何參數** 。

### 記憶體分配 {#memory-allocation}

匯出某些大型報表時，可能會發生記憶體分配錯誤。

在某些情況下， **serverConf.xml設定檔中指示之JavaScript的預設值** maxMB **(代管例項的SKMS** )會設 **** 定為64 MB。 如果您在匯出報表時遇到記憶體不足的錯誤，建議將此數字增加為512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

要應用對配置所做的更改，需 **要重新啟動nlserver** 服務。

要瞭解有關serverConf.xml **檔案的更多資訊** ，請參 [閱本節](../../production/using/configuration-principle.md)。

要瞭解有關nlserver服務的更 **多資訊** ，請參閱 [本節](../../production/using/administration.md)。

## 列印報表 {#printing-a-report}

您可以列印報表：要執行此操作，請按一下打印機表徵圖：這將開啟對話框。

為獲得更好的結果，請編輯Internet explorer打印選項並選擇 **[!UICONTROL Print background colors and images]**。

![](assets/s_ncs_advuser_report_print_options.png)

## 建立報表封存 {#creating-report-archives}

封存報表可讓您建立不同時段的報表檢視，例如顯示指定時段的統計資料。

若要建立封存，請開啟相關報表，然後按一下適當的圖示。

![](assets/s_ncs_advuser_report_wizard_07.png)

若要顯示或隱藏現有封存，請按一下顯示／隱藏圖示。

![](assets/s_ncs_advuser_report_history_06.png)

封存日期會顯示在顯示／隱藏圖示下。 按一下封存以檢視。

![](assets/s_ncs_advuser_report_history_04.png)

可以刪除報表封存。 若要這麼做，請前往儲存報表的Adobe Campaign節點。 按一下 **[!UICONTROL Archives]** 標籤，選取您要刪除的標籤，然後按一下 **[!UICONTROL Delete]**。

![](assets/s_ncs_advuser_report_history_01.png)

