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
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# 範本取消發佈{#template-unpublication}

在執行例項上發佈訊息範本後，就可以解除發佈。

事實上，已發佈的範本仍可以呼叫。 因此，如果您不再使用訊息範本，建議取消發佈訊息範本。 這是為了避免錯誤地發送不想要的事務性消息。 例如，您發佈了僅用於聖誕促銷活動的訊息範本。 您可能想在聖誕節結束後將其解除發佈，並於明年再次發佈。

此外，您也無法刪除具有狀態的事務性消息 **[!UICONTROL Published]** 模板。 您必須先解除發佈。

要取消發佈事務性消息模板，請執行以下步驟。

1. 在控制實例中，轉至樹 **[!UICONTROL Message Center > Transactional message templates]** 的資料夾。
1. 選取您要取消發佈的範本。
1. 按一下「**[!UICONTROL Unpublish]**」。

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. 按一下「**[!UICONTROL Start]**」。

![](assets/message-center-unpublish.png)

事務性消息模板狀態從更改 **[!UICONTROL Published]** 回到 **[!UICONTROL Being edited]**。

一旦取消發佈完成：

* 兩個消息模板（應用於批處理和即時類型事件）都從每個執行實例中刪除。 它們不再出現在資料夾 **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** 中。

* 一旦取消發佈範本後，您就可視需要從控制例項中刪除範本。 若要這麼做，請從清單中選取它，然後按一 **[!UICONTROL Delete]** 下畫面右上方的按鈕。