---
product: campaign
title: 針對報吿的動作
description: 針對報吿的動作
feature: Reporting
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 4ff86349d6b8966273585bf2a1ea0d785a7e87cb
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 3%

---

# 針對報吿的動作{#actions-on-reports}

![](../../assets/common.svg)

查看報告時，工具欄允許您執行某些操作。 下文詳述。

![](assets/s_ncs_advuser_report_wizard_2.png)

例如，工具欄允許您在Web瀏覽器中導出、打印、存檔或顯示報告。

![](assets/s_ncs_advuser_report_wizard_04.png)

## 導出報告 {#exporting-a-report}

從下拉清單中選擇要將報告導出到的格式。 (.xls、.pdf或.ods)。

![](assets/s_ncs_advuser_report_wizard_06.png)

當報表包含多個頁面時，需要對每個頁面重複該操作。

您可以配置報表，以PDF、Excel或OpenOffice格式導出報表。 開啟Adobe Campaign瀏覽器並選擇相關報告。

通過 **[!UICONTROL Page]** 報告活動， **[!UICONTROL Advanced]** 頁籤。

更改 **[!UICONTROL Paper]** 和 **[!UICONTROL Margins]** 來滿足你的需要。 您也可以僅授權以PDF格式導出頁面。 要執行此操作，請取消選中 **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** 的雙曲餘切值。

![](assets/s_ncs_advuser_report_wizard_021.png)

### 導出到MicrosoftExcel {#exporting-into-microsoft-excel}

對於 **[!UICONTROL List with group]** 類型報告將導出到Excel中，則適用以下建議和限制：

* 這些報表不能包含任何空行。

   ![](assets/export_limitations_remove_empty_line.png)

* 清單的圖例必須隱藏。

   ![](assets/export_limitations_hide_label.png)

* 這些報告不必使用在單元格級別定義的特定格式。 優選使用 **[!UICONTROL Form rendering]** 的子菜單。 的 **[!UICONTROL Form rendering]** 可以通過 **[!UICONTROL Administration > Configuration > Form rendering]**。
* 不建議插入HTML內容。
* 如果報表包含多個表、圖表等。 類型元素，它們將在另一個下方導出。
* 可以強制單元格中的回車符：此配置將保留在Excel中。 如需詳細資訊，請參閱[本章節](../../reporting/using/creating-a-table.md#defining-cell-format)。

### 推遲出口 {#postpone-the-export}

您可以推遲導出報告，例如等待非同步呼叫。 要執行此操作，請在頁面的初始化指令碼中輸入以下參數：

```
document.nl_waitBeforeRender = true;
```

要激活導出並開始轉換為PDF，請使用 **document.nl_renderToPdf()** 函式。

### 記憶體分配 {#memory-allocation}

導出某些大型報告時，可能會出現記憶體分配錯誤。

在某些情況下，預設值 **最大MB** (**SKMS** )中所示的JavaScript **serverConf.xml** 配置檔案設定為64 MB。 如果在導出報告時遇到記憶體不足的錯誤，建議將此數字增加到512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

要應用對配置所做的更改， **nlserver** 需要重新啟動服務。

要瞭解有關 **serverConf.xml** 檔案，請參閱 [此部分](../../production/using/configuration-principle.md)。

要瞭解有關 **nlserver** 服務，請參閱 [此部分](../../production/using/administration.md)。

## 打印報表 {#printing-a-report}

您可以打印報表：要執行此操作，請按一下打印機表徵圖：開啟對話框。

為了獲得更好的結果，請編輯瀏覽器打印選項並選擇 **[!UICONTROL Print background colors and images]**。

![](assets/s_ncs_advuser_report_print_options.png)

## 建立報告存檔 {#creating-report-archives}

通過存檔報表，您可以建立報表在不同時段的視圖，例如顯示給定時段的統計資訊。

要建立存檔，請開啟相關報告，然後按一下相應的表徵圖。

![](assets/s_ncs_advuser_report_wizard_07.png)

要顯示或隱藏現有存檔檔案，請按一下「顯示/隱藏」表徵圖。

![](assets/s_ncs_advuser_report_history_06.png)

存檔日期顯示在「顯示/隱藏」表徵圖下。 按一下存檔以查看。

![](assets/s_ncs_advuser_report_history_04.png)

可以刪除報告存檔。 為此，請轉到儲存報告的Adobe Campaign節點。 按一下 **[!UICONTROL Archives]** 頁籤，選擇要刪除的選項並按一下 **[!UICONTROL Delete]**。

![](assets/s_ncs_advuser_report_history_01.png)
