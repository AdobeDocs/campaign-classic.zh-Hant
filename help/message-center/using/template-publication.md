---
title: 範本發佈
seo-title: 範本發佈
description: 範本發佈
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1486e897a125520c51661db3030c62ab380fb173
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# 範本發佈{#template-publication}

在控制實例上建立的消息模板完成後，您可以在所有執行實例上發佈該消息模板。 Publication可讓您在執行例項上自動建立兩個訊息範本，讓您傳送連結至即時和批次事件的訊息。

>[!IMPORTANT]
>
>切記在您對範本進行任何變更時發佈範本，以便這些變更在交易訊息傳送期間生效。

>[!NOTE]
>
>發佈事務性消息模板時，排版規則會自動發佈到執行實例上。

1. 在控制實例中，轉至樹 **[!UICONTROL Message Center > Transactional message templates]** 的資料夾。
1. 選擇要在執行例項上發佈的範本。
1. 按一下「**[!UICONTROL Publish]**」。

   ![](assets/messagecenter_publish_model_008.png)

發佈完成後，將在資料夾的生產實例樹中建立要應用於批處理和即時類型事件的消息模板 **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** 。

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>如果用空值替換事務性消息模板的現有欄位（如發件人地址），則在事務性消息再次發佈後，將不更新執行實例上的相應欄位。 它仍會包含上一個值。 不過，如果您新增非空值，則對應欄位會如常在下次發佈後更新。
