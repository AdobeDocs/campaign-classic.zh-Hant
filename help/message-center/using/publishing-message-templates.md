---
product: campaign
title: 發佈訊息範本
description: 瞭解Adobe Campaign Classic中的交易式訊息範本發佈和取消發佈
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# 發佈訊息範本 {#publishing-template-messages}



## 範本發佈 {#template-publication}

當在控制項執行個體上建立的[訊息範本](../../message-center/using/creating-the-message-template.md)完成時，當您已[測試](../../message-center/using/testing-message-templates.md)它之後，您就可以發佈它。 此程式也會將其發佈在所有執行例項上。

出版物可讓您在執行例項上自動建立&#x200B;**兩個訊息範本**，可讓您傳送連結至&#x200B;**即時事件**&#x200B;和&#x200B;**批次事件**&#x200B;的訊息。

>[!NOTE]
>
>發佈異動訊息範本時，執行例項上也會自動發佈型別規則。

>[!IMPORTANT]
>
>無論何時對範本進行任何變更，請務必再次發佈該範本，使這些變更在交易式訊息傳遞期間生效。

1. 在控制項執行個體上，移至樹狀結構的&#x200B;**[!UICONTROL Message Center > Transactional message templates]**&#x200B;資料夾。
1. 選取您要在執行例項上發佈的範本。
1. 按一下&#x200B;**[!UICONTROL Publish]**。

   ![](assets/messagecenter_publish_model_008.png)

發佈完成後，要套用至批次和即時型別事件的訊息範本都會在&#x200B;**[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**&#x200B;資料夾的生產執行個體樹狀結構中建立。

![](assets/messagecenter_deployed_model_001.png)

發佈範本後，如果觸發了相對應的事件，執行執行個體會收到事件、將其連結至交易式範本，並向每個收件者傳送相對應的交易式訊息。 如需詳細資訊，請參閱[事件處理](../../message-center/using/about-event-processing.md)。

>[!NOTE]
>
>如果您將交易式訊息範本的現有欄位（例如傳送者地址）取代為空值，則交易式訊息再次發佈後，執行例項上的對應欄位將不會更新。 它仍會包含先前的值。
>
>不過，如果您新增非空白值，則會在下次發佈後如常更新對應的欄位。

## 範本取消發佈 {#template-unpublication}

在執行例項上發佈訊息範本後，即可將其取消發佈。 如需範本發佈程式的詳細資訊，請參閱[本節](#template-publication)。

* 事實上，如果觸發對應的事件，仍可呼叫已發佈的範本：如果您不再使用訊息範本，建議將其取消發佈。 這是為了避免誤傳不必要的交易式訊息。

  例如，您發佈了一個訊息範本，但僅用於聖誕節行銷活動。 您可能會想要在聖誕節期間結束後取消發佈，並在明年再次發佈。

* 此外，您無法刪除狀態為&#x200B;**[!UICONTROL Published]**&#x200B;的交易式訊息範本。 您必須先取消發佈。

>[!NOTE]
>
>此功能自Campaign第20.2發行版本開始提供。

若要取消發佈異動訊息範本，請遵循下列步驟。

1. 在控制項執行個體上，移至樹狀結構的&#x200B;**[!UICONTROL Message Center > Transactional message templates]**&#x200B;資料夾。
1. 選取您要取消發佈的範本。
1. 按一下&#x200B;**[!UICONTROL Unpublish]**。

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. 按一下&#x200B;**[!UICONTROL Start]**。

![](assets/message-center-unpublish.png)

異動訊息範本狀態從&#x200B;**[!UICONTROL Published]**&#x200B;變更回&#x200B;**[!UICONTROL Being edited]**。

取消發佈完成後：

* 訊息範本（套用至批次和即時型別事件）都會從每個執行例項中刪除。

  它們不再出現在&#x200B;**[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]**&#x200B;資料夾中（請參閱[此區段](#template-publication)）。

* 取消發佈範本後，您可以從控制例項中刪除它。

  若要這麼做，請從清單中選取它，然後按一下畫面右上方的&#x200B;**[!UICONTROL Delete]**&#x200B;按鈕。
