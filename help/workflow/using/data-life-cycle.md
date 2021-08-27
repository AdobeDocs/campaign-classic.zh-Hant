---
product: campaign
title: 資料生命週期
description: 進一步了解工作流程中的資料生命週期
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 5%

---

# 資料生命週期 {#data-life-cycle}

![](../../assets/common.svg)

## 工作表 {#work-table}

在工作流中，從一個活動傳輸到另一個活動的資料儲存在臨時工作表中。

以滑鼠右鍵按一下適當的轉變，即可顯示和分析此資料。

![](assets/wf-right-click-analyze.png)

要執行此操作，請選取相關功能表：

* 顯示目標

   此菜單顯示目標母體上的可用資料以及工作表（**[!UICONTROL Schema]**&#x200B;頁簽）的結構。

   ![](assets/wf-right-click-display.png)

   有關詳細資訊，請參閱[工作表和工作流架構](monitoring-workflow-execution.md#worktables-and-workflow-schema)。

* 分析目標

   此功能表可讓您存取描述性分析精靈，以便產生轉變資料的統計資料和報表。

   如需詳細資訊，請參閱本[區段](../../reporting/using/using-the-descriptive-analysis-wizard.md)。

目標資料會在執行工作流程時清除。 只能訪問最後一個工作表。 您可以配置工作流，以便所有工作表都保持可訪問狀態：檢查工作流屬性中的&#x200B;**[!UICONTROL Keep the result of interim populations between two executions]**&#x200B;選項。

不過，我們建議您避免在有大量資料時啟用此選項。

![](assets/wf-purge-data-option.png)

## 目標資料 {#target-data}

儲存在工作流程工作表中的資料可在個人化欄位中存取。

這可讓您使用透過清單或根據傳送中調查之答案所收集的資料。 若要這麼做，請使用下列語法：

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)類型個人化元素無法用於目標工作流程。傳遞目標必須建置在工作流程中，並在傳遞的入站轉變中指定。

如果您想要建立傳遞校樣，必鬚根據&#x200B;**[!UICONTROL Address substitution]**&#x200B;模式建立校樣目標，才能輸入個人化資料。 如需詳細資訊，請參閱本[區段](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof)。

在下列範例中，我們將收集關於客戶的資訊清單，以用於個人化電子郵件。

應用以下步驟：

1. 建立工作流程以收集資訊，將其與資料庫中已有的資料調解，然後開始傳送。

   ![](assets/wf-targetdata-sample-1.png)

   在我們的範例中，檔案內容如下：

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   若要載入檔案，請套用下列步驟：

   ![](assets/wf-targetdata-sample-2.png)

1. 設定&#x200B;**[!UICONTROL Enrichment]**&#x200B;類型活動，將收集的資料與Adobe Campaign資料庫中已有的資料調解。

   調解金鑰為帳號：

   ![](assets/wf-targetdata-sample-3.png)

1. 然後配置&#x200B;**[!UICONTROL Delivery]**:系統會根據範本建立收件者，並由入站轉變指定收件者。

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >只有轉換中包含的資料才可用於個人化傳送。 **** targetDatatype個人化欄位僅適用於活動的入站母 **[!UICONTROL Delivery]** 體。

1. 在傳遞範本中，使用在工作流程中收集的欄位。

   要執行此操作，請插入&#x200B;**[!UICONTROL Target extension]**&#x200B;鍵入個人化欄位。

   ![](assets/wf-targetdata-sample-5.png)

   在此處，我們要插入客戶最喜愛的音樂類型和媒體類型（CD或DVD），如工作流收集的檔案中所述。

   作為加號，我們將為忠誠卡持有者（即「卡」值等於1的收件者）新增抵用券。

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData)類型資料會使用與所有個人化欄位相同的特性，插入傳遞中。這些標籤也可用於主題、連結標籤或連結本身。

   傳送給收集收件者的訊息將包含下列資料：

   ![](assets/wf-targetdata-sample-7.png)
