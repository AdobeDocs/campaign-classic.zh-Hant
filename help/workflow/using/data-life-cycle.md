---
title: 資料生命週期
description: 進一步瞭解工作流程中的資料生命週期。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# 資料生命週期 {#data-life-cycle}

## 工作表 {#work-table}

在工作流中，從一個活動傳輸到另一個活動的資料儲存在臨時工作表中。

以滑鼠右鍵按一下適當的轉場，即可顯示和分析此資料。

![](assets/wf-right-click-analyze.png)

若要這麼做，請選取相關功能表：

* 顯示目標

   此菜單顯示目標人口的可用資料以及工作表（頁籤）**[!UICONTROL Schema]** 的結構。

   ![](assets/wf-right-click-display.png)

   有關詳細資訊，請參閱工作 [表和工作流模式](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema)。

* 分析目標

   此功能表可讓您存取描述性分析精靈，讓您產生轉場資料的統計資料和報表。

   For more on this, refer to this [section](../../reporting/using/using-the-descriptive-analysis-wizard.md).

當執行工作流時，會清除目標資料。 只有最後一個工作表可以訪問。 您可以配置工作流，以便所有工作表保持可訪問性： 選中工 **[!UICONTROL Keep the result of interim populations between two executions]** 作流屬性中的選項。

不過，我們建議您避免在大量資料時啟用此選項。

![](assets/wf-purge-data-option.png)

## 目標資料 {#target-data}

儲存在工作流程工作表中的資料可在個人化欄位中存取。

這可讓您使用透過清單收集或根據傳送中調查的答案收集的資料。 若要這麼做，請使用下列語法：

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)類型的個人化元素無法用於定位工作流程。 傳送目標必須在工作流程中建立，並在傳送的傳入轉換中指定。

如果您想要建立傳送校樣，則需要根據模式建立校樣目 **[!UICONTROL Address substitution]** 標，以便輸入個人化資料。 For more on this, refer to this [section](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

在下例中，我們將收集客戶相關資訊的清單，以便用於個人化電子郵件。

應用以下步驟：

1. 建立工作流程以收集資訊、將其與資料庫中已有的資料協調，然後開始傳送。

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

1. 設定類 **[!UICONTROL Enrichment]** 型活動，以協調已收集的資料與Adobe Campaign資料庫中已有的資料。

   在這裡，協調密鑰是帳戶號碼：

   ![](assets/wf-targetdata-sample-3.png)

1. 然後設定 **[!UICONTROL Delivery]**: 它是根據模板建立的，而收件者則由入站轉換指定。

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >只有轉換中包含的資料才能用於個人化傳送。 **targetData** type personalization欄位僅適用於活動的傳入 **[!UICONTROL Delivery]** 人口。

1. 在傳送範本中，使用在工作流程中收集的欄位。

   若要這麼做，請插入 **[!UICONTROL Target extension]** 文字個人化欄位。

   ![](assets/wf-targetdata-sample-5.png)

   在此，我們要插入客戶最愛的音樂類型和媒體類型（CD或DVD），如工作流程收集的檔案中所述。

   另外，我們將為忠誠卡持有者（即「卡」值等於1的收件者）新增抵用券。

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData)類型資料會使用與所有個人化欄位相同的特性，插入傳送。 它們也可用於主題、連結標籤或連結本身。

   傳送給收集之收件者的訊息將包含下列資料：

   ![](assets/wf-targetdata-sample-7.png)
