---
product: campaign
title: 中間來源基礎結構的傳入簡訊工作流程活動
description: 中間來源基礎結構的傳入簡訊工作流程活動
feature: Technote, SMS
exl-id: 756039b2-5f57-4dc5-8166-a421206b886b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 5%

---

# 中間來源基礎結構的傳入簡訊工作流程活動 {#inbound-sms-wf}

## 限制 {#limitations}

* 此使用案例僅適用於您從中間來源執行個體收集inSMS資料的行銷執行個體。
* 請勿在中間來源執行個體上實作此使用案例。
* 每個外部中間來源帳戶只有一個自訂工作流程。

## 實施 {#implementation}

1. 將擴充功能新增至行銷執行個體上的`nms:inSMS`結構描述。 擴充功能會將新屬性新增至`nms:inSMS`結構描述，並追蹤來自中間來源執行個體的inSMS記錄主索引鍵。

   ```xml
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. 若要套用對結構描述所做的修改，請啟動資料庫更新輔助程式。 此助理可以透過&#x200B;**工具** > **進階** > **更新資料庫結構**&#x200B;存取。 它會檢查資料庫的實體結構是否符合其邏輯描述，並執行SQL更新指令碼。 [了解更多](../../configuration/using/updating-the-database-structure.md)

1. 停止並備份包含&#x200B;**傳入簡訊活動**&#x200B;的工作流程。

   以下列格式`SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}`備份對應的選項指標。

[進一步瞭解備份](../../production/using/backup.md)

1. （**選擇性**）如果您已在使用排程器活動，請開啟工作流程並按如下方式重新設定：

   1. 從&#x200B;**傳入簡訊**&#x200B;活動的&#x200B;**排程**&#x200B;索引標籤將目前的設定復寫到外部&#x200B;**排程器**&#x200B;活動中。

   1. 停用&#x200B;**傳入SMS**&#x200B;活動的&#x200B;**排程**&#x200B;索引標籤中的目前設定。

      ![](assets/inbound_sms_1.png)

1. 更新&#x200B;**傳入簡訊**&#x200B;自訂指令碼。

   取代下方區塊。 請注意，如果您先前已自訂此程式碼，此指令碼可能會有所不同。

   ```Javascript
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

   請遵循下列先決條件：

   * 輸入`<EXTERNAL_ACCOUNT_ID>`的實值，例如`var iExtAccountId=72733155`。
   * 請務必將下列元素保留在自訂指令碼中：
      * `_operation="insertOrUpdate"`
      * `_key="@midInSMSId,@extAccount-id"`
      * `midInSMSId={smsMessage.id}`
      * `inSms.@["extAccount-id"] = iExtAccountId;{}`

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   
   var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
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

   ```Javascript
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
