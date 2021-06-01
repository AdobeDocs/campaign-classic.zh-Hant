---
product: campaign
title: AND-join
description: 合併連結
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---

# 合併連結{#and-join}

只有在啟動所有入站轉變（即完成所有先前的活動）時，連接才會觸發其出站轉變。 這可讓您在繼續執行工作流程之前，確定某些活動已完成。

例如，您可以在內容建立和傳送傳送自動化的內容中使用AND-join活動，以確保只有在目標查詢和內容更新步驟完成後，才會啟動傳送。 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供專用的使用案例

![](assets/and-join-usage.png)

>[!NOTE]
>
>請注意，使用不同目標維度設定的入站轉變無法使用&#x200B;**[!UICONTROL AND-join]**&#x200B;活動連結在一起。

活動的出站已傳送母體，是透過在活動的入站轉變中選擇主要集來決定。

出站轉變只能包含入站轉變母體之一。 如果未設定活動，出站轉變將隨機選取入站母體之一。

>[!CAUTION]
>
>若為&#x200B;**AND-join**&#x200B;類型活動，會合併事件變數，但如果同一個變數定義兩次，則會發生衝突，值仍未確定。 如需詳細資訊，請參閱[本章節](../../workflow/using/javascript-scripts-and-templates.md#event-variables)。
