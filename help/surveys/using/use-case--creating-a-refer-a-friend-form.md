---
product: campaign
title: 建立參考朋友調查
description: 瞭解建立「參考朋友」表單的步驟
feature: Surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# 使用實例：建立轉介表單{#use-case-creating-a-refer-a-friend-form}

![](../../assets/v7-only.svg)

在此示例中，我們要向資料庫中的收件人提供競爭。 Web表單將包含一個用於輸入答案的部分，另一個用於通過輸入朋友的電子郵件地址來引用朋友。

![](assets/s_ncs_admin_survey_viral_sample_0.png)

使用先前描述的過程建立標識和競爭塊。

要配置和建立引用塊，請應用以下步驟：

1. 建立競爭Web表單，其中包含問題和用於輸入好友聯繫資訊的欄位，如下所示：

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   的 **您的消息** 欄位允許你輸入裁判的資訊。 引用者還必須輸入 **姓氏**。 **名字** 和 **電子郵件**。

   在欄位中輸入的資訊儲存在稱為訪問者表的特定表中。

   >[!NOTE]
   >
   >只要收件人尚未同意，您就無法將其儲存到資料庫中。 它們將暫時儲存在 **遊客** 表格&#x200B;**nms：訪問者**)為病毒式營銷活動設計。 此表定期清除，因為 **清洗** 操作。
   >
   >在本示例中，我們希望目標收件人建議他們參加其推薦人推薦的競爭。 但是，在此郵件中，我們還希望向他們提供我們的一項資訊服務的訂閱。 如果訂閱，則可以將其儲存在資料庫中。

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   與裁判有關的欄位的內容將用於檔案建立指令碼和發送給他們的消息中。

1. 首先建立一個指令碼，將引用者與裁判連接。

   它包含以下說明：

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   在頁面標識塊中輸入的姓、名和電子郵件地址被標識為引用者的姓、名和電子郵件地址。 這些場將重新注入發給裁判的資訊。

   APP5值與Web表單的內部名稱匹配：這些資訊使您能夠找出裁判的來源，即將訪問者連結到根據他們建立的Web表單。

1. 儲存框允許您收集資訊並將其儲存在資料庫中。

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. 然後建立連結到在步驟1中建立的資訊服務的傳遞模板。 將在 **[!UICONTROL Choose scenario]** 的子菜單。

   用於建立推薦聘用消息的傳遞模板包含以下資訊：

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   此模板具有以下特徵：

   * 選擇訪問者表作為目標映射。

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * 裁判的聯繫資訊以及參考者的資訊從訪問台中取出。 使用個性化按鈕插入。

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * 此模板包含到比賽表單的連結和供裁判訂閱新聞簡報的訂閱連結。

      通過個性化塊插入訂閱連結。 預設情況下，它允許您將配置檔案訂閱到 **簡訊** 服務。 可以更改此個性化塊以滿足您的需要，例如，將收件人預訂到其他服務。

   * 內部名稱（此處為「引用者」）將用於消息傳遞指令碼，如下所示。
   >[!NOTE]
   >
   >請參閱 [此頁](../../delivery/using/about-templates.md) 的子菜單。

1. 建立第二個用於傳遞訂閱消息的指令碼。

   ![](assets/s_ncs_admin_survey_viral_sample_7c.png)

   ```
   // Updtate visitor to have a link to the referrer recipient
   ctx.recipient.visitor.@referrerId = ctx.recipient.@id
   ctx.recipient.visitor.@xtkschema = "nms:visitor"
   ctx.recipient.visitor.@_operation = "update" 
   ctx.recipient.visitor.@_key = "@id" 
   xtk.session.Write(ctx.recipient.visitor)
   
   // Send email to friend
   nms.delivery.QueueNotification("referrer",
   <delivery>
   <targets>
     <deliveryTarget>
       <targetPart type='query' exclusion='false' ignoreDeleteStatus='false'>
         <where>
           <condition expr={'@id IN ('+ ctx.recipient.visitor.@id +')' }/>
         </where>
       </targetPart>
      </deliveryTarget>
     </targets>
    </delivery>)
   ```

1. 發佈競爭表單，並向初始目標的收件人發送邀請。 當其中一個邀請朋友時，根據 **推薦服務** 模板。

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   裁判被添加到 **[!UICONTROL Administration > Visitors node]**:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   其配置檔案包含其引用者輸入的資訊。 它根據在表單指令碼中輸入的配置進行儲存。 如果他們決定訂閱新聞簡報，他們將保存在收件人表中。
