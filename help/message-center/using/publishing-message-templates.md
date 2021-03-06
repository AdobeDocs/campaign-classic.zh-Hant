---
product: campaign
title: '發佈訊息範本 '
description: 了解Adobe Campaign Classic中的交易式訊息範本發佈和取消發佈。
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# 發佈訊息範本 {#publishing-template-messages}

![](../../assets/v7-only.svg)

## 範本發佈 {#template-publication}

當 [訊息範本](../../message-center/using/creating-the-message-template.md) 在控制項例項上建立的變數已完成，且 [測試](../../message-center/using/testing-message-templates.md) 您可以發佈。 此程式也會在所有執行執行個體上發佈。

發佈可讓您自動建立 **兩個訊息範本** 執行例項，可讓您傳送連結至的訊息 **即時事件** 和 **批次事件**.

>[!NOTE]
>
>發佈交易式訊息範本時，類型規則也會自動發佈在執行例項上。

>[!IMPORTANT]
>
>每當您對範本進行任何變更時，請務必再次發佈，讓這些變更在交易式訊息傳送期間生效。

1. 在控制執行個體上，前往 **[!UICONTROL Message Center > Transactional message templates]** 樹的資料夾。
1. 選取要在執行執行個體上發佈的範本。
1. 按一下&#x200B;**[!UICONTROL Publish]**。

   ![](assets/messagecenter_publish_model_008.png)

發佈完成後，將應用於批處理和即時類型事件的兩個消息模板都將在生產實例的樹中建立，該樹位於 **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** 檔案夾。

![](assets/messagecenter_deployed_model_001.png)

發佈範本後，如果觸發對應的事件，執行例項將會收到事件，將其連結至交易範本，並傳送對應的交易式訊息給每個收件者。 有關詳細資訊，請參閱 [事件處理](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>如果您將交易式訊息範本的現有欄位（例如寄件者地址）取代為空值，交易式訊息重新發佈後，執行例項上的對應欄位將不會更新。 它仍會包含先前的值。
>
>不過，如果您新增非空白值，則對應欄位在下次發佈後會照常更新。

## 範本取消發佈 {#template-unpublication}

在執行例項上發佈訊息範本後，即可取消發佈。 如需範本發佈程式的詳細資訊，請參閱 [本節](#template-publication).

* 事實上，如果觸發對應事件，仍可呼叫已發佈的範本：如果您不再使用訊息範本，建議取消發佈訊息範本。 這是為了避免錯誤傳送不需要的交易式訊息。

   例如，您發佈了訊息範本，而您只能用於聖誕促銷活動。 在聖誕節期間結束後，您可能會想要取消發佈，並在明年再次發佈。

* 此外，您無法刪除具有 **[!UICONTROL Published]** 狀態。 您必須先取消發佈。

>[!NOTE]
>
>自Campaign 20.2版本開始，即可使用此功能。

若要取消發佈交易式訊息範本，請遵循下列步驟。

1. 在控制執行個體上，前往 **[!UICONTROL Message Center > Transactional message templates]** 樹的資料夾。
1. 選取您要取消發佈的範本。
1. 按一下&#x200B;**[!UICONTROL Unpublish]**。

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. 按一下&#x200B;**[!UICONTROL Start]**。

![](assets/message-center-unpublish.png)

交易式訊息範本狀態會從 **[!UICONTROL Published]** to **[!UICONTROL Being edited]**.

完成取消發佈後：

* 會從每個執行例項中刪除兩個訊息範本（套用至批次和即時類型事件）。

   它們不再出現在 **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** 資料夾(請參閱 [本節](#template-publication))。

* 取消發佈範本後，您就可以從控制執行個體刪除該範本。

   若要這麼做，請從清單中選取它，然後按一下 **[!UICONTROL Delete]** 按鈕。
