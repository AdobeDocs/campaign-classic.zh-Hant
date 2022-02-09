---
product: campaign
title: 使用分析報告
description: 使用分析報告
exl-id: d133efec-33e1-4711-a90f-e40385059386
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 1%

---

# 使用分析報告{#processing-a-report}

![](../../assets/common.svg)

## 保存分析報告 {#saving-an-analysis-report}

如果您具有相應權限，則可以保存從模板建立的分析報告，或以Excel、PDF或OpenOffice格式將其導出。

要保存報告，請按一下 **[!UICONTROL Save]** 給報告貼個標籤。

選擇 **[!UICONTROL Also save data]** 如果希望建立報表的歷史記錄，並在保存時查看報表的值。 有關此內容的詳細資訊，請參閱 [存檔分析報告](#archiving-analysis-reports)。

的 **[!UICONTROL Share this report]** 選項允許其他運算子訪問報告。

![](assets/s_ncs_user_report_wizard_010.png)

保存後，可以重新使用此報告生成其他分析報告：

![](assets/s_ncs_user_report_wizard_08a.png)

要更改此報表，請編輯 **[!UICONTROL Administration > Configuration > Adobe Campaign tree reports]** 「Adobe Campaign」樹的節點（或操作員具有編輯權限的第一個「報告」類型資料夾）。 有關此內容的詳細資訊，請參閱 [配置描述性分析報告的佈局](#configuring-the-layout-of-a-descriptive-analysis-report)。

## 分析報告其他設定 {#analysis-report-additional-settings}

保存描述性分析報告後，可以編輯其屬性並訪問其他選項。

![](assets/s_ncs_user_report_wizard_08b.png)

這些選項與標準報告相同，並在 [此頁](../../reporting/using/properties-of-the-report.md)。

## 配置描述性分析報告的佈局 {#configuring-the-layout-of-a-descriptive-analysis-report}

您可以個性化描述性分析的圖表和表中的資料顯示和佈局。 所有選項都可通過Adobe Campaign樹訪問， **[!UICONTROL Edit]** 頁籤。

### 分析報表顯示模式 {#analysis-report-display-mode}

使用 **[!UICONTROL qualitative distribution]** 預設情況下，模板、表和圖表顯示模式將被選中。 如果只需要一種顯示模式，請取消選中相應的框。 這意味著只有選中的顯示模式的頁籤才可用。

![](assets/s_ncs_advuser_report_display_01.png)

要更改報表的架構，請按一下 **[!UICONTROL Select the link]** 並從資料庫中選擇另一個表。

![](assets/s_ncs_advuser_report_display_02.png)

### 分析報告顯示設定 {#analysis-report-display-settings}

可以隱藏或顯示統計資訊和小計，也可以選擇統計資訊的方向。

![](assets/s_ncs_advuser_report_display_05.png)

建立統計資訊時，可以個性化其標籤。

![](assets/s_ncs_advuser_report_display_06.png)

其名稱將顯示在報告中。

![](assets/s_ncs_advuser_report_display_07.png)

但是，如果取消選中標籤和小計顯示選項，則這些選項在報告中將不可見。 當將滑鼠懸停在表的單元格上時，該名稱將出現在工具提示中。

![](assets/s_ncs_advuser_report_display_08.png)

預設情況下，統計資訊會聯機顯示。 要更改方向，請從下拉清單中選擇相應的選項。

![](assets/s_ncs_advuser_report_wizard_035a.png)

在以下示例中，統計資訊顯示在列中。

![](assets/s_ncs_advuser_report_wizard_035.png)

### 分析報表資料佈局 {#analysis-report-data-layout}

可以直接在描述性分析表中個性化資料佈局。 為此，請按一下右鍵要使用的變數。 從下拉菜單中選擇可用選項：

* **[!UICONTROL Pivot]** 的子菜單。
* **[!UICONTROL Up]** / **[!UICONTROL Down]** 換行中的變數。
* **[!UICONTROL Move to the right]** / **[!UICONTROL Move to the left]** 以替換列中的變數。
* **[!UICONTROL Turn]** 來反轉變數軸。
* **[!UICONTROL Sort from A to Z]** 將變數值排序為「低」。
* **[!UICONTROL Sort from Z to A]** 將變數值從高到低排序。

   ![](assets/s_ncs_advuser_report_wizard_016.png)

要返回到初始顯示，請刷新視圖。

### 分析報表圖表選項 {#analysis-report-chart-options}

可以個性化圖表中資料的顯示。 要執行此操作，請按一下 **[!UICONTROL Variables...]** 在圖表類型選擇階段中可用的連結。

![](assets/s_ncs_advuser_report_wizard_3c.png)

可以使用以下選項：

* 窗口的上部部分允許您修改圖表顯示區域。
* 預設情況下，標籤會顯示在圖表中。 你可以通過取消檢查 **[!UICONTROL Show values]** 的雙曲餘切值。
* 的 **[!UICONTROL Accumulate values]** 選項，可將值從一個系列添加到另一個系列。
* 您可以決定是否顯示圖表圖例：要隱藏它，請取消選中相應選項。 預設情況下，圖例顯示在圖表的右上角。

   圖例也可顯示在圖表頂部，以節省顯示空間。 要執行此操作，請選擇選項 **[!UICONTROL Include in the chart]**

   在 **[!UICONTROL Caption position]** 的子菜單。

   ![](assets/s_ncs_advuser_report_wizard_3d.png)

## 導出分析報告 {#exporting-an-analysis-report}

要從分析報告中導出資料，請按一下下拉清單並選擇所需的輸出格式。

![](assets/s_ncs_user_report_wizard_09.png)

如需詳細資訊，請參閱[此頁面](../../reporting/using/actions-on-reports.md)。

## 重新使用現有報告和分析 {#re-using-existing-reports-and-analyses}

可以使用已儲存在Adobe Campaign的現有報告建立資料的描述性分析報告。 當分析已保存或已建立並配置為通過描述性分析嚮導訪問報告時，可以使用此模式。

要瞭解如何保存描述性分析，請參閱 [保存分析報告](#saving-an-analysis-report)。

要建立描述性分析報告，必須通過工作流轉換或 **[!UICONTROL Tools > Descriptive analysis]** 的子菜單。

1. 選取 **[!UICONTROL Existing analyses and reports]** 並按一下 **[!UICONTROL Next]**。
1. 這允許您訪問可用報告的清單。 選擇要生成的報告。

   ![](assets/s_ncs_user_report_wizard_01.png)

## 存檔分析報告 {#archiving-analysis-reports}

在基於現有分析建立描述性分析時，可以建立存檔以儲存資料並比較報告結果。

要建立歷史記錄，請應用以下步驟：

1. 開啟現有分析或建立新的描述性分析嚮導。
1. 在報告顯示頁面中，按一下按鈕在工具欄中建立歷史記錄，然後按如下所示確認：

   ![](assets/reporting_descriptive_historize_icon.png)

1. 使用存檔訪問按鈕顯示以前的分析。

   ![](assets/reporting_descriptive_historize_access.png)
