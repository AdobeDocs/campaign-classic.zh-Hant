---
product: campaign
title: 資料生命週期
description: 進一步瞭解工作流程中的資料生命週期
feature: Workflows, Data Management
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: f90df5a5e5b3a2317d86ff2919560ded38f44f44
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 5%

---

# 資料生命週期 {#data-life-cycle}



## 工作表 {#work-table}

在工作流程中，從某個活動傳輸到另一個活動的資料會儲存在臨時工作表中。

在適當的轉變上按一下滑鼠右鍵，即可顯示和分析此資料。

![](assets/wf-right-click-analyze.png)

要執行此操作，請選取相關功能表：

* 顯示目標

  此功能表會顯示目標母體上的可用資料以及工作表（**[!UICONTROL Schema]**&#x200B;標籤）的結構。

  ![](assets/wf-right-click-display.png)

  如需詳細資訊，請參閱[工作表和工作流程結構描述](monitoring-workflow-execution.md#worktables-and-workflow-schema)。

* 分析目標

  此功能表可讓您存取描述性分析助理，該助理可以讓您產生轉變資料的統計資料和報告。

  如需詳細資訊，請參閱本[區段](../../reporting/using/using-the-descriptive-analysis-wizard.md)。

在執行工作流程時清除目標資料。 只能存取最後一個工作表。 您可以設定工作流程，讓所有工作表保持可存取狀態：核取工作流程屬性中的&#x200B;**[!UICONTROL Keep the result of interim populations between two executions]**&#x200B;選項。

不過，我們建議您避免在出現大量資料時啟用此選項。

![](assets/wf-purge-data-option.png)

## 目標資料 {#target-data}

儲存在工作流程工作表中的資料可在個人化欄位中存取。

這可讓您使用透過清單收集的資料，或根據傳送中調查的回答收集的資料。 要執行此操作，請使用下列語法：

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)型別個人化元素不適用於目標工作流程。 必須在工作流程中建置傳遞目標，並在傳遞的入站轉變中指定。

如果您想要建立傳遞校樣，需要根據&#x200B;**[!UICONTROL Address substitution]**&#x200B;模式建置校樣目標，才能輸入個人化資料。 如需詳細資訊，請參閱本[區段](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof)。

在下列範例中，我們將收集客戶資訊清單，用於個人化電子郵件中。

應用以下步驟：

1. 建立工作流程以收集資訊，將其與資料庫中已存在的資料進行調解，然後開始傳遞。

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

1. 設定&#x200B;**[!UICONTROL Enrichment]**&#x200B;型別活動，將收集的資料與Adobe Campaign資料庫中已存在的資料進行調解。

   調解金鑰是帳號：

   ![](assets/wf-targetdata-sample-3.png)

1. 然後設定&#x200B;**[!UICONTROL Delivery]**：它是根據範本建立的，收件者是由入站轉變所指定。

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >只有轉換中包含的資料才可用來個人化傳遞。 **targetData**&#x200B;型別個人化欄位僅適用於&#x200B;**[!UICONTROL Delivery]**&#x200B;活動的傳入母體。

1. 在傳遞範本中，使用在工作流程中收集的欄位。

   若要這麼做，請插入&#x200B;**[!UICONTROL Target extension]**&#x200B;型別個人化欄位。

   ![](assets/wf-targetdata-sample-5.png)

   在此處，我們要插入客戶最愛的音樂流派和媒體型別（CD或DVD），如工作流程收集的檔案中所述。

   此外，我們將為熟客卡持有者（即「卡片」值等於1的收件者）新增優惠券。

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData)型別資料是使用與所有個人化欄位相同的特性插入傳遞。 它們也可用於主旨、連結標籤或連結本身。

   傳送給所收集收件者的郵件將包含下列資料：

   ![](assets/wf-targetdata-sample-7.png)
