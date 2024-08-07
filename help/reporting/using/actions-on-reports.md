---
product: campaign
title: 針對報吿的動作
description: 針對報吿的動作
feature: Reporting, Monitoring
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 3%

---

# 針對報吿的動作{#actions-on-reports}



檢視報表時，工具列可讓您執行特定數量的動作。 下文將詳述這些內容。

![](assets/s_ncs_advuser_report_wizard_2.png)

例如，工具列可讓您在網頁瀏覽器中匯出、列印、封存或顯示報表。

![](assets/s_ncs_advuser_report_wizard_04.png)

## 匯出報告 {#exporting-a-report}

從下拉式清單中選取您要匯出報告的格式。 (.xls、.pdf或.ods)。

![](assets/s_ncs_advuser_report_wizard_06.png)

當報表包含數個頁面時，您需要為每個頁面重複此作業。

您可以設定報表以檢視匯出PDF、Excel或OpenOffice格式的報表。 開啟Adobe Campaign檔案總管並選取相關報表。

匯出選項是透過報告的&#x200B;**[!UICONTROL Page]**&#x200B;活動（在&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中）存取。

變更&#x200B;**[!UICONTROL Paper]**&#x200B;和&#x200B;**[!UICONTROL Margins]**&#x200B;的設定以符合您的需求。 您也可以授權僅以PDF格式匯出頁面。 若要這麼做，請取消勾選&#x200B;**[!UICONTROL Activate OpenOffice/Microsoft Excel export]**&#x200B;選項。

![](assets/s_ncs_advuser_report_wizard_021.png)

### 匯出至Microsoft Excel {#exporting-into-microsoft-excel}

對於預定要匯出至Excel的&#x200B;**[!UICONTROL List with group]**&#x200B;型別報表，適用下列建議和限制：

* 這些報表不得包含任何空白行。

  ![](assets/export_limitations_remove_empty_line.png)

* 清單的圖例必須隱藏。

  ![](assets/export_limitations_hide_label.png)

* 報表不必使用在儲存格層級定義的特定格式。 最好使用&#x200B;**[!UICONTROL Form rendering]**&#x200B;來定義表格中儲存格的格式。 **[!UICONTROL Form rendering]**&#x200B;可以透過&#x200B;**[!UICONTROL Administration > Configuration > Form rendering]**&#x200B;存取。
* 我們不建議插入HTML內容。
* 如果報告包含數個表格、圖表等， 文字元素，它們會一個匯出到另一個之下。
* 您可以在儲存格中強制歸位：此設定將保留在Excel中。 如需詳細資訊，請參閱[本章節](../../reporting/using/creating-a-table.md#defining-cell-format)。

### 延遲匯出 {#postpone-the-export}

例如，您可以延遲匯出報表，以等待非同步呼叫。 若要這麼做，請在頁面的初始化命令檔中輸入下列引數：

```
document.nl_waitBeforeRender = true;
```

若要啟動匯出並開始轉換為PDF，請使用不含任何引數的&#x200B;**document.nl_renderToPdf()**&#x200B;函式。

### 記憶體配置 {#memory-allocation}

匯出某些大型報表時，可能會發生記憶體配置錯誤。

在某些執行個體中，**serverConf.xml**&#x200B;組態檔中指示的JavaScript預設值&#x200B;**maxMB** (**SKMS** （針對裝載的執行個體）)設定為64 MB。 如果您在匯出報表時遇到任何記憶體不足的錯誤，建議將此數字增加到512 MB：

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

若要套用對組態所做的變更，必須重新啟動&#x200B;**nlserver**&#x200B;服務。

若要進一步瞭解&#x200B;**serverConf.xml**&#x200B;檔案，請參閱[本節](../../production/using/configuration-principle.md)。

若要進一步瞭解&#x200B;**nlserver**&#x200B;服務，請參閱[本節](../../production/using/administration.md)。

## 列印報表 {#printing-a-report}

您可以列印報告：若要這樣做，請按一下印表機圖示：這會開啟對話方塊。

為了獲得更好的結果，請編輯瀏覽器列印選項並選取&#x200B;**[!UICONTROL Print background colors and images]**。

![](assets/s_ncs_advuser_report_print_options.png)

## 建立報告封存 {#creating-report-archives}

封存報表可讓您在不同時段建立報表的檢視，例如，顯示指定時段的統計資料。

若要建立封存，請開啟相關報表，然後按一下適當的圖示。

![](assets/s_ncs_advuser_report_wizard_07.png)

若要顯示或隱藏現有的封存，請按一下顯示/隱藏圖示。

![](assets/s_ncs_advuser_report_history_06.png)

封存日期會顯示在顯示/隱藏圖示下方。 按一下封存即可檢視。

![](assets/s_ncs_advuser_report_history_04.png)

您可以刪除報表封存。 若要這麼做，請前往儲存報表的Adobe Campaign節點。 按一下「**[!UICONTROL Archives]**」標籤，選取要刪除的標籤，然後按一下「**[!UICONTROL Delete]**」。

![](assets/s_ncs_advuser_report_history_01.png)
