---
solution: Campaign Classic
product: campaign
title: 建立指令碼
description: 瞭解如何透過專屬的使用案例來執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# 建立指令碼{#step-5--creating-the-script}

指令碼會計算針對剩餘人口的傳送內容選擇。 此指令碼會以最高開啟率來恢復傳送的相關資訊，並將內容複製至最終傳送。

## 指令碼{#example-of-a-script}示例

以下指令碼可如同在定位工作流程中使用。 有關詳細資訊，請參閱[實施](#implementation)。

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

有關指令碼的詳細說明，請參閱[指令碼的詳細資訊](#details-of-the-script)。

## 實施{#implementation}

1. 開啟您的&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動。
1. 將[Example of a script](#example-of-a-script)中提供的指令碼複製到&#x200B;**[!UICONTROL JavaScript code]**&#x200B;窗口。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中，輸入指令碼的名稱，例如：

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 關閉&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動。
1. 儲存您的工作流程。

## 指令碼{#details-of-the-script}的詳細資訊

本節詳細說明指令碼的各個部分及其操作模式。

* 指令碼的第一部分是查詢。 **queryDef**&#x200B;命令可讓您從&#x200B;**NmsDelivery**&#x200B;表中恢復通過執行定位工作流建立的傳送，並根據其估計的開啟率對它們進行排序，然後恢復來自具有最高開啟率的傳送的資訊。

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* 複製開啟率最高的傳送。

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 修改複製的傳送的標籤，並將單字&#x200B;**final**&#x200B;添加到該標籤中。

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* 傳送會複製到促銷活動控制面板。

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* 傳送會儲存在資料庫中。

   ```
   // save the delivery in database
   delivery.save()
   ```

* 複製傳送的唯一識別碼會儲存在工作流程變數中。

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## 其他選擇標準{#other-selection-criteria}

上述範例可讓您根據電子郵件的開啟率來選取傳送的內容。 您可以根據其他特定遞送指標來調整：

* 最佳點按吞吐量：`[indicators/@recipientClickRatio]`,
* 最高反應率（開啟電子郵件並點擊訊息）:`[indicators/@reactivity]`,
* 最低投訴率：`[indicators/@refusedRatio]`（對sortDesc屬性使用false值）,
* 最高轉換率：`[indicators/@transactionRatio]`,
* 收到訊息後瀏覽的頁數：`[indicators/@totalWebPage]`,
* 最低取消訂閱率：`[indicators/@optOutRatio]`,
* 事務處理金額：`[indicators/@amount]`。

您現在可以定義最終傳送(請參閱[步驟6:定義最終交貨](../../delivery/using/a-b-testing-uc-final-delivery.md))。
