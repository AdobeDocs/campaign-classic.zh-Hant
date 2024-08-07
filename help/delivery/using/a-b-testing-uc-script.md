---
product: campaign
title: 建立指令碼
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# AB測試：建立指令碼 {#step-5--creating-the-script}


系統會透過指令碼，計算預定用於剩餘母體的傳遞內容選擇。 此指令碼會復原有關最高開啟率之傳送的資訊，並將內容複製到最終傳送。

## 指令碼範例 {#example-of-a-script}

以下指令碼可依原樣用於目標定位工作流程。 如需詳細資訊，請參閱[本章節](#implementation)。

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

如需指令碼的詳細說明，請參閱[本節](#details-of-the-script)。

## 實施 {#implementation}

1. 開啟您的&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動。
1. 將[指令碼範例](#example-of-a-script)中提供的指令碼複製到&#x200B;**[!UICONTROL JavaScript code]**&#x200B;視窗中。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中，輸入指令碼的名稱，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 關閉&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動。
1. 儲存您的工作流程。

## 指令碼的詳細資料 {#details-of-the-script}

本節詳細說明指令碼的各個部分及其作業模式。

* 指令碼的第一部分是查詢。 **queryDef**&#x200B;命令可讓您從&#x200B;**NmsDelivery**&#x200B;表格復原透過執行目標工作流程所建立的傳送，並根據其預估開啟率加以排序，然後復原開啟率最高的傳遞中的資訊。

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

* 會複製開啟率最高的傳遞。

  ```
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
  var delivery = nms.delivery.create()
  delivery.Duplicate("nms:delivery|" + winner.@id)
  ```

* 已修改重複傳遞的標籤，且已新增&#x200B;**final**&#x200B;這個字。

  ```
  // append 'final' to the delivery label
  delivery.label = winner.@label + " final"
  ```

* 傳遞會複製到行銷活動控制面板。

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

* 傳遞會儲存在資料庫中。

  ```
  // save the delivery in database
  delivery.save()
  ```

* 重複傳遞的唯一識別碼會儲存在工作流程變數中。

  ```
  // store the new delivery Id in event variables
  vars.deliveryId = delivery.id
  ```

## 其他選取條件 {#other-selection-criteria}

上述範例可讓您根據電子郵件開啟率來選取傳送內容。 您可以調整它，以根據其他傳遞特定指標：

* 最佳點按輸送量： `[indicators/@recipientClickRatio]`，
* 最高反應率（電子郵件開啟及訊息點按）： `[indicators/@reactivity]`，
* 投訴率最低： `[indicators/@refusedRatio]` （使用sortDesc屬性的false值），
* 最高轉換率： `[indicators/@transactionRatio]`，
* 收到訊息後造訪的頁數： `[indicators/@totalWebPage]`，
* 最低取消訂閱率： `[indicators/@optOutRatio]`，
* 交易金額： `[indicators/@amount]`。

您現在可以定義最終傳遞。 [了解更多](a-b-testing-uc-final-delivery.md)。
