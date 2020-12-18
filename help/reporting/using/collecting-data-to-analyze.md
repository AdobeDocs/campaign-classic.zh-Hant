---
solution: Campaign Classic
product: campaign
title: 收集資料以進行分析
description: 收集資料以進行分析
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 3%

---


# 收集資料以進行分析{#collecting-data-to-analyze}

建立報表時，可直接在報表頁面中選取要使用的資料（如需詳細資訊，請參閱[使用內容](../../reporting/using/using-the-context.md)），或透過一或多個查詢收集。

本練習提供三種不同的方法：

1. 使用資料庫中的資料構建查詢。
1. 處理清單中包含的資料。
1. 使用現有立方中包含的資料。

方法的選擇取決於計算類型、資料量及其耐久性等。 必須仔細檢查這些參數，以避免超出Adobe Campaign資料庫的負載，並最佳化所建立報表的產生與控制。 有關詳細資訊，請參見[此頁面](../../reporting/using/best-practices.md#optimizing-report-creation)。

在所有情況下，資料都會透過&#x200B;**[!UICONTROL Query]**&#x200B;類型活動來收集。

![](assets/reporting_query_edit.png)

當需要使用資料庫中的資料收集或建立報表中的資料時，此資料選擇模式即相關。 在某些情況下，您也可以直接從報表中使用的元素中選取資料。 例如，插入圖表時，您可以直接選擇源資料。 有關詳細資訊，請參閱[使用上下文](../../reporting/using/using-the-context.md)。

## 使用架構{#using-the-data-from-a-schema}中的資料

要使用連結到資料庫方案的資料，請在查詢編輯器中選擇相應的選項，並配置要應用的查詢。

下列範例可讓您在資料庫的設定檔中，收集每個國家／地區的收件者數目。 然後，這些報表可以以表格的形式顯示。

![](assets/reporting_query_from_schema.png)

## 使用導入的清單{#using-an-imported-list}

若要建立報表，您可以使用匯入資料清單中的資料。

要執行此操作，請在查詢框中選擇&#x200B;**[!UICONTROL Use an imported list]**&#x200B;選項並選擇相關清單。

![](assets/reporting_query_from_list.png)

按一下&#x200B;**[!UICONTROL Edit query...]**&#x200B;連結，定義要在此清單中元素間收集的資料，以建立報表。

## 使用立方{#using-a-cube}

可以選擇一個立方來定義查詢。

![](assets/reporting_query_from_cube.png)

立方體可讓您擴充資料庫的探索和分析能力，同時讓一般使用者更容易設定報表和表格：只需選擇一個現有的完全配置的立方，並使用其計算、度量和統計資訊。 有關建立立方的詳細資訊，請參閱[本節](../../reporting/using/about-cubes.md)。

按一下&#x200B;**[!UICONTROL Edit query...]**&#x200B;連結，並選取您要在報表中顯示或使用的指標。

![](assets/reporting_query_from_cube_edit_query.png)

## 查詢{#filtering-options-in-the-queries}中的篩選選項

為避免在整個資料庫上運行查詢，需要過濾資料。

### 簡化的篩選{#simplified-filter}

您可以選取&#x200B;**[!UICONTROL Filter automatically with the context]**&#x200B;選項，讓報表可透過樹狀結構的特定節點（例如清單、收件者或傳送）存取。

**[!UICONTROL Filter with the folder]**&#x200B;選項可讓您指定資料夾，並僅考量其內容。 這可讓您篩選報表資料，僅顯示樹狀結構中其中一個資料夾的資料，如下所示：

![](assets/reporting_control_folder.png)

### 限制收集的{#limiting-the-amount-of-data-collected}資料量

使用結果限制選項配置要通過查詢提取的記錄數：

* **[!UICONTROL Limit to first record]** 要擷取一個結果，
* **[!UICONTROL Size]** 以提取一組記錄。

