---
solution: Campaign Classic
product: campaign
title: 合併連結
description: 合併連結
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 6%

---


# 合併連結{#and-join}

只有在激活所有入站轉換（即在所有先前活動完成時）時，連接才會觸發其出站轉換。 這可讓您在繼續執行工作流程之前，先確定某些活動已完成。

例如，您可以在內容建立和傳送傳送自動化的內容中使用AND-join活動，以確保只有在目標查詢和內容更新步驟完成後，才啟動傳送。 [本節](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供專用的使用案例

![](assets/and-join-usage.png)

通過在活動的入站轉變中選擇主集來確定活動的出站發送人口。

出站轉移只能包含其中一個入站轉移人口。 如果未配置活動，則出站轉移將隨機選擇一個入站人口族群。

>[!CAUTION]
>
>對於&#x200B;**AND-join**&#x200B;類型活動，事件變數會合併，但如果相同變數定義兩次，則會發生衝突，且值仍未確定。 如需詳細資訊，請參閱[本章節](../../workflow/using/javascript-scripts-and-templates.md#event-variables)。
