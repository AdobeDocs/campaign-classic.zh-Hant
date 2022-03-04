---
product: campaign
title: 資料生命週期
description: 瞭解有關工作流中資料生命週期的詳細資訊
feature: Workflows, Data Management
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 5%

---

# 資料生命週期 {#data-life-cycle}

![](../../assets/common.svg)

## 工作表 {#work-table}

在工作流中，從一個活動傳輸到另一個活動的資料儲存在臨時工作表中。

通過按一下右鍵相應的過渡，可以顯示和分析此資料。

![](assets/wf-right-click-analyze.png)

為此，請選擇相關菜單：

* 顯示目標

   此菜單顯示有關目標填充的可用資料以及工作表的結構(**[!UICONTROL Schema]** )的正平方根。

   ![](assets/wf-right-click-display.png)

   有關此內容的詳細資訊，請參閱 [工作表和工作流架構](monitoring-workflow-execution.md#worktables-and-workflow-schema)。

* 分析目標

   通過此菜單，您可以訪問描述性分析嚮導，該嚮導可以生成有關轉換資料的統計資訊和報告。

   如需詳細資訊，請參閱本[區段](../../reporting/using/using-the-descriptive-analysis-wizard.md)。

目標資料在工作流執行時被清除。 只能訪問最後一個工作表。 您可以配置工作流，以便所有工作表保持可訪問性：檢查 **[!UICONTROL Keep the result of interim populations between two executions]** 的子菜單。

但是，我們建議您避免在大量資料時激活此選項。

![](assets/wf-purge-data-option.png)

## 目標資料 {#target-data}

儲存在工作流工作表中的資料可以在個性化欄位中訪問。

這允許您使用通過清單或基於交付中調查的答案收集的資料。 要執行此操作，請使用以下語法：

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)類型個性化元素不可用於目標工作流。 必須在工作流中生成並在傳遞的入站轉換中指定傳遞目標。

如果要建立交貨憑證，則需要根據 **[!UICONTROL Address substitution]** 模式，以便輸入個性化資料。 如需詳細資訊，請參閱本[區段](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof)。

在以下示例中，我們將收集有關客戶的資訊清單，這些資訊將用於個性化電子郵件中。

應用以下步驟：

1. 建立工作流以收集資訊，將其與資料庫中已有的資料協調，然後啟動傳遞。

   ![](assets/wf-targetdata-sample-1.png)

   在本示例中，檔案內容如下所示：

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   要載入檔案，請應用以下步驟：

   ![](assets/wf-targetdata-sample-2.png)

1. 配置 **[!UICONTROL Enrichment]** 鍵入activity以將收集的資料與Adobe Campaign資料庫中已有的資料進行協調。

   這裡，協調密鑰是帳號：

   ![](assets/wf-targetdata-sample-3.png)

1. 然後配置 **[!UICONTROL Delivery]**:它基於模板建立，收件人由入站轉換指定。

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >只能使用轉換中包含的資料來個性化傳送。 **目標資料** 類型個性化欄位僅可用於 **[!UICONTROL Delivery]** 的子菜單。

1. 在交貨模板中，使用工作流中收集的欄位。

   為此，請插入 **[!UICONTROL Target extension]** 類型個性化欄位。

   ![](assets/wf-targetdata-sample-5.png)

   在此，我們要插入客戶最喜愛的音樂流派和媒體類型（CD或DVD），如工作流收集的檔案中所述。

   作為加號，我們將為會員卡持有者添加優惠券，即「卡」值等於1的收件者。

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData)類型資料使用與所有個性化欄位相同的特徵插入到遞送中。 它們也可用於主題、連結標籤或連結本身。

   發送到收集的收件人的郵件將包含以下資料：

   ![](assets/wf-targetdata-sample-7.png)
