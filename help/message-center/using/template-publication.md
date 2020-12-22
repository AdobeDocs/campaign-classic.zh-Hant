---
solution: Campaign Classic
product: campaign
title: 範本發佈
description: 事務性消息模板發佈
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 2%

---


# 範本發佈{#template-publication}

當在控制實例上建立的消息模板完成時，可以發佈該消息模板。 此程式也會在所有執行例項上發佈。

Publication可讓您在執行例項上自動建立兩個訊息範本，讓您傳送連結至即時和批次事件的訊息。

>[!NOTE]
>
>發佈交易式訊息範本時，排版規則也會自動發佈在執行例項上。

>[!IMPORTANT]
>
>每當您對範本進行任何變更時，請務必再次發佈範本，讓這些變更在交易訊息傳送期間生效。

1. 在控制實例上，轉至樹的&#x200B;**[!UICONTROL Message Center > Transactional message templates]**&#x200B;資料夾。
1. 選擇要在執行例項上發佈的範本。
1. 按一下 **[!UICONTROL Publish]**。

   ![](assets/messagecenter_publish_model_008.png)

發佈完成後，將在&#x200B;**[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**&#x200B;資料夾的生產實例樹中建立要應用於批處理和即時類型事件的消息模板。

![](assets/messagecenter_deployed_model_001.png)

一旦發佈模板，如果觸發了相應事件，執行實例將接收該事件，將其連結到事務模板，並向每個接收者發送相應的事務消息。

>[!NOTE]
>
>如果用空值替換事務性消息模板的現有欄位（如發件人地址），則在事務性消息再次發佈後，將不更新執行實例上的相應欄位。 它仍會包含上一個值。
>
>不過，如果您新增非空值，則對應欄位會如常在下次發佈後更新。
