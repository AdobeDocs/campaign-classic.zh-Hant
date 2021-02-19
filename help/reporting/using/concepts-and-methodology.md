---
solution: Campaign Classic
product: campaign
title: 概念和方法
description: 概念和方法
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 1%

---


# 立方體的最佳做法{#concepts-and-methodology}

## 資料綁定{#data-binning}

結合可讓您根據條件將值分組，以簡化資料顯示。 根據您可用的資訊，您可以定義年齡群組、將電子郵件網域群組在一起、限制使用值列舉、明確限制資料顯示並將所有其他資料群組在專用行或欄中，等等。

總的來說，有三種類型的捆綁：

1. 使用手動定義的值範圍。 例如，年齡、平均購物車、已開啟的交貨數等。) 有關詳細資訊，請參閱[定義每個bin](#defining-each-bin)。
1. 動態，視列舉的值而定：只顯示列舉中包含的值，所有其他值都會分組在「其他」中。 有關詳細資訊，請參閱[動態管理bins](#dynamically-managing-bins)。
1. 使用值範圍，將所有其他值分組在一起。 例如，18到25歲，26到59歲，以及其他人。 有關詳細資訊，請參閱[建立值範圍](#creating-value-ranges)。

要啟用綁定，請在建立維時選中相應的框。

![](assets/s_advuser_cube_class_00.png)

您可以手動建立Bin或將其連結到現有枚舉。

Adobe Campaign也提供自動裝訂的助理：值可分成N個組，或根據資料庫中最常用的值分組。

### 定義每個Bin {#defining-each-bin}

要單獨建立每個Bin，請選擇&#x200B;**[!UICONTROL Define each bin]**&#x200B;選項，然後使用表建立各種Bin。

![](assets/s_advuser_cube_class_01.png)

按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕可建立新站，並列出將分組到站中的值。

![](assets/s_advuser_cube_class_02.png)

在下列範例中，語言分為三類：英文／德文／荷蘭文、法文／義大利文／西班牙文和其他文字。

![](assets/s_advuser_cube_class_03.png)

您可以使用SQL掩碼將多個值合併到篩選器中。 要執行此操作，請在&#x200B;**[!UICONTROL Use an SQL mask]**&#x200B;列中檢查&#x200B;**[!UICONTROL Yes]** ，然後輸入要應用於&#x200B;**[!UICONTROL Value or expression]**&#x200B;列的SQL篩選器。

在以下範例中，所有以&#x200B;**yahoo**（yahoo.fr、yahoo.com、yahoo.be等）開頭，或以&#x200B;**ymail**（ymail.com、ymail.eu等）開頭的電子郵件網域 將分組在&#x200B;**YAHOO！標籤下**，以及rocketmail. **comdomain的位** 址。

![](assets/s_advuser_cube_class_03b.png)

### 動態管理Bin {#dynamically-managing-bins}

值可透過枚舉動態管理。 這表示只會顯示枚舉中包含的值。 當枚舉值改變時，立方的內容會自動調整。

要建立此類型的值綁定，請應用以下步驟：

1. 建立新維度並啟用系結。
1. 選擇&#x200B;**[!UICONTROL Dynamically link the values to an enumeration]**&#x200B;選項並選擇匹配枚舉。

   ![](assets/s_advuser_cube_class_04.png)

   每當枚舉值被更新時，匹配的Bin會自動調整。

### 建立值範圍{#creating-value-ranges}

您可以根據所需的間隔，將值分組到範圍中。

要手動定義範圍，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並選擇&#x200B;**[!UICONTROL Define a range]** :

![](assets/s_advuser_cube_class_05.png)

然後指定下限和上限，然後按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以確認。

### 自動生成Bins {#generating-bins-automatically}

您也可以自動產生Bin。 若要這麼做，請按一下&#x200B;**[!UICONTROL Generate bins...]**&#x200B;連結。

![](assets/s_advuser_cube_class_06.png)

您可以：

* 恢復最常用的值

   在下列範例中，將顯示4個最常使用的值，而其他值則會計入「其他」類別並分組。

* 以槽形式生成Bin

   在下列範例中，Adobe Campaign會自動建立4個相同大小的值槽，以顯示資料庫中的值。

在這種情況下，會忽略事實模式中選取的篩選器。

### 枚舉{#enumerations}

為了改善報表的相關性和可讀性，Adobe Campaign可讓您建立特定的列舉，將不同的值重新群組至同一個bin。 這些為綁定而保留的枚舉在立方中引用，然後顯示在報告中。

Adobe Campaign也提供網域列舉功能，讓您顯示資料庫中所有連絡人的電子郵件網域清單，並依ISP重新分組，如下列範例所示：

![](assets/nmx_report_sample.png)

它使用下列範本建立：

![](assets/nmx_enum_domain.png)

要使用此枚舉建立報告，請使用&#x200B;**[!UICONTROL Email domain]**&#x200B;維建立立方。 選擇&#x200B;**[!UICONTROL Enable binning]**&#x200B;選項，然後選擇&#x200B;**[!UICONTROL Dynamically link the values to an enumeration]**。 然後選擇&#x200B;**Domains**&#x200B;枚舉，如上所示。 沒有指定別名的所有值將重新分組到&#x200B;**Others**&#x200B;標籤下。

![](assets/nmx_add_dimension.png)

接著，根據此立方建立報表以顯示值。

您只需要修改列舉即可更新相關報表。 例如，建立&#x200B;**Adobe**&#x200B;值並新增&#x200B;**adobe.com**&#x200B;別名，報表就會在列舉層級自動更新為Adobe值。

![](assets/nmx_add_alias.png)

**[!UICONTROL Domains]**&#x200B;列舉可用來產生顯示網域清單的內建報表。 若要調整這些報表的內容，您可以編輯此清單。

您可以建立保留用於綁定的其他枚舉，並在其他立方中使用它們：所有別名值將重新分組到第一個枚舉頁籤中指定的bin中。

## 計算和使用聚合{#calculating-and-using-aggregates}

可以在聚合中計算最大的資料卷。

在處理大量資料時，聚合非常有用。 系統會根據專用工作流程方塊中定義的設定自動更新資料，將最近收集的資料整合到指標中

集合在每個立方的相關頁籤中定義。

![](assets/s_advuser_cube_agregate_01.png)

>[!NOTE]
>
>用於更新集合計算的工作流可以在集合本身中配置，或者可以通過連結到相關立方的外部工作流來更新集合。

要建立新聚合，請應用以下步驟：

1. 按一下立方的&#x200B;**[!UICONTROL Aggregates]**&#x200B;頁籤，然後按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕。

   ![](assets/s_advuser_cube_agregate_02.png)

1. 輸入匯總的標籤，然後添加要計算的維。

   ![](assets/s_advuser_cube_agregate_03.png)

1. 選擇維和級別。 對每個維和每個級別重複此過程。
1. 按一下&#x200B;**[!UICONTROL Workflow]**&#x200B;頁籤以建立聚合工作流。

   ![](assets/s_advuser_cube_agregate_04.png)

   * **[!UICONTROL Scheduler]**&#x200B;活動可讓您定義計算更新的頻率。 調度程式在[本節](../../workflow/using/scheduler.md)中有詳細說明。
   * **[!UICONTROL Aggregate update]**&#x200B;活動可讓您選擇要套用的更新模式：完整或部分。

      依預設，每次計算時都會執行完整更新。 若要啟用部分更新，請選取相關選項並定義更新條件。

      ![](assets/s_advuser_cube_agregate_05.png)

## 定義測量{#defining-measures}

度量類型在立方的&#x200B;**[!UICONTROL Measures]**&#x200B;頁籤中定義。 您可以計算和、平均值、偏差等。

您可以根據需要建立任意數量的測量：然後，選擇要在表格中顯示或隱藏的度量。 有關詳細資訊，請參閱[顯示度量](#displaying-measures)。

要定義新度量，請應用以下步驟：

1. 按一下度量清單上方的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後選擇要計算的度量類型和公式。

   ![](assets/s_advuser_cube_create_a_measure.png)

1. 如果需要，並根據運算子選擇操作所關心的表達式。

   **[!UICONTROL Advanced selection]**&#x200B;按鈕可讓您建立複雜的計算公式。 如需詳細資訊，請參閱[本章節](../../platform/using/about-queries-in-campaign.md)。

   ![](assets/s_advuser_cube_create_a_measure_01.png)

1. **[!UICONTROL Filter the measure data...]**&#x200B;連結可以限制計算欄位，並僅將其應用於資料庫中的特定資料。

   ![](assets/s_advuser_cube_create_a_measure_02.png)

1. 輸入度量的標籤並添加說明，然後按一下&#x200B;**[!UICONTROL Finish]**&#x200B;建立它。

## 顯示測量{#displaying-measures}

您可以根據需要配置表格中度量的顯示：

* 測量的顯示序列（請參閱[顯示序列](#display-sequence)）,
* 要在報表中顯示／隱藏的資訊（請參閱[設定顯示](#configuring-the-display)）
* 顯示哪些度量：百分比、總數、小數位數等。 （請參閱[更改顯示的測量類型](#changing-the-type-of-measure-displayed)）。

### 顯示序列{#display-sequence}

立方中計算的度量通過&#x200B;**[!UICONTROL Measures]**&#x200B;按鈕進行配置。

移動行以更改顯示順序。 在下列範例中，法文資料會移至清單底部：這表示它將顯示在最後一欄中。

![](assets/s_advuser_cube_in_report_config_04.png)

### 配置顯示{#configuring-the-display}

可針對每個測量或整體分別執行測量、行和列的配置。 特定圖示可讓您存取顯示模式選擇視窗。

* 按一下&#x200B;**[!UICONTROL Edit the configuration of the pivot table]**&#x200B;表徵圖以訪問配置窗口。

   您可以選擇是否顯示度量的標籤以及配置其佈局（行或列）。

![](assets/s_advuser_cube_in_report_config_05.png)

顏色選項可讓您反白標示重要值，以方便閱讀。

![](assets/s_advuser_cube_in_report_config_06.png)

### 更改顯示的測量類型{#changing-the-type-of-measure-displayed}

在每個度量中，可以定義要應用的單位和格式。

![](assets/s_advuser_cube_in_report_config_07.png)

## 共用報表{#sharing-a-report}

設定報表後，您就可以儲存報表，並與其他運算子共用。

要執行此操作，請按一下&#x200B;**[!UICONTROL Show the report properties]**&#x200B;表徵圖並啟用&#x200B;**[!UICONTROL Share this report]**&#x200B;選項。

![](assets/cube_share_option.png)

指定報表所屬的類別及其相關性。 有關詳細資訊，請參閱[本頁](../../reporting/using/configuring-access-to-the-report.md#report-display-context)中的&#x200B;**顯示序列**&#x200B;和&#x200B;**定義過濾選項**&#x200B;部分。

若要確認這些變更，您必須儲存報表。

![](assets/cube_share_confirm.png)

## 建立篩選 {#creating-filters}

您可以建立篩選器，以檢視資料的區段。

操作步驟：

1. 按一下&#x200B;**[!UICONTROL Add a filter]**&#x200B;表徵圖。

   ![](assets/neolap_add_filter.png)

1. 選擇篩選器所關注的維

   ![](assets/neolap_define_filter.png)

1. 選取濾鏡的類型及其精確度等級。

   ![](assets/neolap_ceate_filter.png)

1. 建立篩選器後，篩選器會顯示在報表上方。

   ![](assets/neolap_filter_zone.png)

   按一下篩選以加以編輯。

   按一下交叉點以刪除它。

   您可以視需要合併多個篩選器：都會在這個區域展示。

   ![](assets/neolap_multiple_filters.png)

每次修改篩選（新增、移除、變更）時，都必須重新計算報表。

您也可以根據選取範圍來建立篩選。 若要這麼做，請選取來源儲存格、行和欄，然後按一下&#x200B;**[!UICONTROL Add a filter]**&#x200B;圖示。

要選擇行、列或單元格，請左鍵按一下。 若要取消選取，請再按一下。

![](assets/neolap_create_filter_from_selection.png)

篩選會自動套用，並新增至報表上方的篩選區。

![](assets/neolap_create_filter_display.png)

