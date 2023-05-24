---
product: campaign
title: 建立「推薦朋友」意見調查
description: 瞭解建立「推薦朋友」表單的步驟
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# 使用實例：建立轉介表單{#use-case-creating-a-refer-a-friend-form}



在此範例中，我們想要與資料庫中的收件者競爭。 網路表單中會有一個區段用於輸入答案，另一個區段用於輸入朋友的電子郵件地址來推薦朋友。

![](assets/s_ncs_admin_survey_viral_sample_0.png)

識別與競爭區塊是使用前述程式建立的。

若要設定和建立轉介區塊，請套用下列步驟：

1. 建立競爭網路表單，其中包含問題以及用於輸入朋友聯絡資訊的欄位，如下所示：

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   此 **您的訊息** 欄位可讓您為被推薦者輸入訊息。 反向連結也必須輸入其 **姓氏**， **名字** 和 **電子郵件**.

   在欄位中輸入的資訊會儲存在稱為訪客表格的特定表格中。

   >[!NOTE]
   >
   >只要收件者未表示同意，您就無法將兩者與收件者儲存在資料庫中。 這些檔案會暫時儲存在 **訪客** 表格(**nms：visitor**)專為病毒式行銷活動所設計。 此表格會定期清除，原因如下 **清除** 作業。
   >
   >在此範例中，我們想要鎖定收件者，以建議他們參與反向連結建議的競爭。 不過，在此訊息中，我們也希望向他們提供我們其中一個資訊服務的訂閱。 如果使用者訂閱，則可將其儲存在資料庫中。

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   與被推薦者相關的欄位內容將用於設定檔建立指令碼和傳送給他們的訊息中。

1. 首先，建立指令碼以將反向連結連結至被推薦者。

   它包含下列指示：

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   在頁面識別區塊中輸入的姓氏、名字和電子郵件地址會識別為反向連結的姓氏、名字和電子郵件地址。 這些欄位將重新插入傳送給裁判的訊息內文。

   APP5值符合Web表單的內部名稱：此資訊可讓您找出被推薦者的來源，也就是將訪客連結至根據其建立的Web表單。

1. 儲存方塊可讓您收集資訊並將其儲存在資料庫中。

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. 然後，建立連結至在步驟1中建立的資訊服務的傳遞範本。 它將會選取在 **[!UICONTROL Choose scenario]** 資訊服務的欄位。

   用來建立轉介優惠訊息的傳遞範本包含下列資訊：

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   此範本具有以下特性：

   * 選取訪客表格作為目標對應。

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * 被推薦者的聯絡資訊以及反向連結上的資訊均取自訪客表格。 使用個人化按鈕插入。

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * 此範本包含競爭表格的連結，以及裁判訂閱電子報的訂閱連結。

      訂閱連結會透過個人化區塊插入。 依預設，它可讓您訂閱設定檔至 **電子報** 服務。 您可以變更此個人化區塊以符合您的需求，例如為收件者訂閱不同的服務。

   * 內部名稱（此處為「referrer」）將用於訊息傳遞指令碼，如下所示。
   >[!NOTE]
   >
   >請參閱 [此頁面](../../delivery/using/about-templates.md) 以取得傳遞範本的詳細資訊。

1. 建立用於傳遞訂閱訊息的第二個指令碼。

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

1. 發佈競爭表單，並向初始目標的收件者傳送邀請。 當其中一人邀請朋友時，根據 **推薦優惠** 範本已建立。

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   被推薦者會新增到中的訪客資料夾 **[!UICONTROL Administration > Visitors node]**：

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   其設定檔包含其反向連結輸入的資訊。 它會根據在表單指令碼中輸入的設定進行儲存。 如果他們決定訂閱電子報，則會儲存在收件者表格中。
