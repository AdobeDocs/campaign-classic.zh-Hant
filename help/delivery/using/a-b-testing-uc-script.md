---
product: campaign
title: 建立指令碼
description: 瞭解如何通過專用使用案例執行A/B測試
feature: A/B Testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 4%

---

# 建立指令碼 {#step-5--creating-the-script}

![](../../assets/common.svg)

以剩餘填充為目標的傳送內容的選擇由指令碼計算。 此指令碼以最高開啟率恢復有關傳送的資訊，並將內容複製到最終傳送中。

## 指令碼示例 {#example-of-a-script}

以下指令碼可以與目標工作流中一樣使用。 如需詳細資訊，請參閱[本章節](#implementation)。

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

有關指令碼的詳細說明，請參閱 [此部分](#details-of-the-script)。

## 實施 {#implementation}

1. 開啟 **[!UICONTROL JavaScript code]** 的子菜單。
1. 複製中提供的指令碼 [指令碼示例](#example-of-a-script) 到 **[!UICONTROL JavaScript code]** 的子菜單。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在 **[!UICONTROL Label]** 欄位中，輸入指令碼的名稱，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 關閉 **[!UICONTROL JavaScript code]** 的子菜單。
1. 保存工作流。

## 指令碼的詳細資訊 {#details-of-the-script}

本節詳細介紹指令碼的各個部分及其操作模式。

* 指令碼的第一部分是查詢。 的 **查詢定義** 命令，可從 **Nms交付** 將通過執行目標工作流建立的交貨表格，並根據其估計的開啟率對其進行排序，然後恢復來自開啟率最高的交貨的資訊。

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

* 重複開啟率最高的交貨。

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 已修改重複傳遞的標籤，並且 **最後** 的子菜單。

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* 交貨將複製到市場活動控制面板中。

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

* 傳遞將保存在資料庫中。

   ```
   // save the delivery in database
   delivery.save()
   ```

* 重複傳遞的唯一標識符儲存在工作流變數中。

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## 其他選擇標準 {#other-selection-criteria}

上面的示例允許您根據開啟電子郵件的速率來選擇傳遞的內容。 您可以根據其它特定於交付的指標調整它：

* 最佳按一下吞吐量： `[indicators/@recipientClickRatio]`。
* 最高反應率（開啟電子郵件並在郵件中按一下）: `[indicators/@reactivity]`。
* 最低投訴率： `[indicators/@refusedRatio]` （對sortDesc屬性使用false值）,
* 最高轉換率： `[indicators/@transactionRatio]`。
* 接收消息後訪問的頁數： `[indicators/@totalWebPage]`。
* 最低取消訂閱率： `[indicators/@optOutRatio]`。
* 交易記錄金額： `[indicators/@amount]`。

您現在可以定義最終交貨。 [了解更多資訊](a-b-testing-uc-final-delivery.md)。
