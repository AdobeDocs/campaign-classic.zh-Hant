---
product: campaign
title: 建立指令碼
description: 透過專屬的使用案例了解如何執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 5%

---

# 建立指令碼 {#step-5--creating-the-script}



以剩餘母體為目的地的傳送內容選擇，由指令碼計算。 此指令碼會以最高開啟率來復原有關傳送的資訊，並將內容複製到最終傳送。

## 指令碼範例 {#example-of-a-script}

下列指令碼可如同在目標工作流程中使用。 如需詳細資訊，請參閱[本章節](#implementation)。

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

有關指令碼的詳細說明，請參閱 [本節](#details-of-the-script).

## 實作 {#implementation}

1. 開啟 **[!UICONTROL JavaScript code]** 活動。
1. 複製中提供的指令碼 [指令碼範例](#example-of-a-script) 進入 **[!UICONTROL JavaScript code]** 窗口。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在 **[!UICONTROL Label]** 欄位，輸入指令碼的名稱，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 關閉 **[!UICONTROL JavaScript code]** 活動。
1. 儲存您的工作流程。

## 指令碼的詳細資訊 {#details-of-the-script}

本節詳細說明指令碼的各個部分及其操作模式。

* 指令碼的第一部分是查詢。 此 **queryDef** 命令可讓您從 **NmsDelivery** 表格執行目標工作流程所建立的傳送，並根據其預估開啟率來排序傳送，然後會復原來自開啟率最高之傳送的資訊。

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

* 具有最高開啟率的傳送會重複。

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 已修改重複傳送的標籤，並修改字詞 **fal** 即會新增。

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

* 重複傳送的唯一識別碼會儲存在工作流程變數中。

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## 其他選擇標準 {#other-selection-criteria}

上述範例可讓您根據電子郵件的開啟率來選取傳送的內容。 您可以調整它，以依據其他特定傳送指標：

* 最佳點擊吞吐量： `[indicators/@recipientClickRatio]`,
* 最高反應率（電子郵件開啟和郵件中的點按次數）: `[indicators/@reactivity]`,
* 最低投訴率： `[indicators/@refusedRatio]` （對sortDesc屬性使用false值）,
* 最高轉換率： `[indicators/@transactionRatio]`,
* 接收訊息後瀏覽的頁數： `[indicators/@totalWebPage]`,
* 最低取消訂閱率： `[indicators/@optOutRatio]`,
* 交易金額: `[indicators/@amount]`.

您現在可以定義最終傳送。 [了解更多](a-b-testing-uc-final-delivery.md)。
