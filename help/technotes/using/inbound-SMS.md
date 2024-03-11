---
product: campaign
title: 中間來源基礎結構的傳入簡訊工作流程活動
description: 中間來源基礎結構的傳入簡訊工作流程活動
feature: Technote, SMS
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
source-git-commit: de57e7aec255ab2995d1a758642e6a73cafa91b3
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---

# 中間來源基礎結構的傳入簡訊工作流程活動 {#inbound-sms}

## 限制 {#limitations}

* 此使用案例僅適用於您從中間來源執行個體收集inSMS資料的行銷執行個體。
* 請勿在中間來源執行個體上實作此使用案例。
* 每個外部中間來源帳戶只有一個自訂工作流程。

## 實施 {#implementation}

1. 將擴充功能新增至 `nms:inSMS` 結構描述。 擴充功能會將新屬性新增至 `nms:inSMS` 方案和追蹤來自中間來源執行個體的inSMS記錄主索引鍵。

   ```
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. 若要套用對結構描述所做的修改，請啟動資料庫更新精靈。 此精靈的存取方式為 **工具** > **進階** > **更新資料庫結構**. 它會檢查資料庫的實體結構是否符合其邏輯描述，並執行SQL更新指令碼。 [了解更多](../../configuration/using/updating-the-database-structure.md)

1. 停止並備份包含下列專案的工作流程： **傳入簡訊活動**.

   使用下列格式備份對應的選項指標 `SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}`.

[進一步瞭解備份](../../production/using/backup.md)

1. (**可選**)如果您已在使用排程器活動，請開啟工作流程並按如下方式重新設定：

   1. 複製目前的設定，從 **排程** 的標籤 **傳入簡訊** 活動進入您的外部 **排程器** 活動。

   1. 在中停用目前設定 **排程** 標籤之 **傳入簡訊** 活動。

      ![](assets/inbound_sms_1.png)

1. 更新 **傳入簡訊** 自訂指令碼。

   取代下方區塊。 請注意，如果您先前已自訂此程式碼，此指令碼可能會有所不同。

   ```
   var lastSynchKey = getOption('SMS_MO_INDEX_WKF1105_inSmsUS_smsmidus');
   
   var smsId = application.getNewIds(1);
   
   xtk.session.Write(<inSMS xtkschema="nms:inSMS" _operation="insert"
       id={smsId}
       origin={smsMessage.origin}
       message={smsMessage.message}
       providerId={smsMessage.messageId}/>);
   
   return 2;
   ```

   使用下列新自訂指令碼，根據複合索引鍵更新inSMS資料，結合中間來源記錄的主索引鍵和行銷SMS路由的外部帳戶ID。

   ```
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   // make sure to keep the following elements in the custom script (the rest is optional and custom code can be added): _operation="insertOrUpdate", _key="@midInSMSId,@extAccount-id", midInSMSId={smsMessage.id}, inSms.@["extAccount-id"] = iExtAccountId;, var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
               _key="@midInSMSId,@extAccount-id"
               midInSMSId={smsMessage.id}
               message={smsMessage.message}
               origin={smsMessage.origin}
               providerId={smsMessage.providerId}
               alias={smsMessage.alias}
               messageDate = {smsMessage.messageDate}
               receivalDate = {smsMessage.receivalDate}
               deliveryDate = {smsMessage.deliveryDate}
               largeAccount = {smsMessage.largeAccount}
               countryCode = {smsMessage.countryCode}
               operatorCode = {smsMessage.operatorCode}
               linkedSmsId={smsMessage.linkedSmsId}
               separator = {smsMessage.separator}/>
   inSms.@["extAccount-id"] = iExtAccountId;
   
   xtk.session.Write(inSms);
   
   return 2;
   ```

1. 使用以下指令碼更新傳入SMS進階初始化指令碼。

   指令碼會將主鍵指標重設為24小時前。 工作流程將嘗試在前24小時內重新處理來自中間來源執行個體的所有inSMS資料，並將任何遺失的資料新增到行銷執行個體。

   ```
   // please enter real external account ID to replace <EXTERNAL_ACCOUNT_ID>
   // please enter real pointer option name to replace '<POINTER_OPTION_NAME>'
   // OPTION NAME format: SMS_MO_INDEX_{internal name of the workflow}_inSms_{internal name of the external account to access the mid}
   
   var queryDef = xtk.queryDef.create(
       <queryDef operation="getIfExists" schema="nms:inSMS" lineCount="1">
       <select>
           <node expr="@midInSMSId" alias="@midInSMSId"/>
       </select>
       <where>
           <condition expr="@midInSMSId != 0"/>
           <condition expr={"@created > SubHours(GetDate(), 24)"}/>
           <condition expr={"[@extAccount-id]=<EXTERNAL_ACCOUNT_ID>"}/>
       </where>
       <orderBy>
           <node expr="@midInSMSId"/>
       </orderBy>
       </queryDef>);
   
   var res = parseInt(queryDef.ExecuteQuery().@midInSMSId.toString());
   
   if( !isNaN(res) )
   setOption('<POINTER_OPTION_NAME>', res);
   ```

   >[!WARNING]
   >
   > * 如果數個SMS路由帳戶連結到同一個中間來源執行個體，則每個中間來源執行個體只允許單一工作流程。
   > * 您可以使用任何外部帳戶ID。 外部索引鍵的角色是在涉及不同中間來源伺服器的情況中維護資料協調完整性，在這些情況中，中間來源SMS ID可能在其他中間來源執行個體中相同。
   > * 如果每個中間來源執行個體有多個inSMS工作流程，則可能會發生資料重複，因為中間來源SMS ID會保持不變，而外部帳戶ID會有所不同。

1. 儲存並重新啟動工作流程。


