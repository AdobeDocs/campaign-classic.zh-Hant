---
title: 合併連結
seo-title: 合併連結
description: 合併連結
seo-description: null
page-status-flag: never-activated
uuid: 8234d6cd-0e9b-4187-9ddf-9e1f86aa1b9a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 075206aa-ff7b-4fa8-a05d-14a29fb119ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 5%

---


# 合併連結{#and-join}

只有在激活所有入站轉換（即在所有先前活動完成時）時，連接才會觸發其出站轉換。 這可讓您在繼續執行工作流程之前，先確定某些活動已完成。

例如，您可以在內容建立和傳送傳送自動化的內容中使用AND-join活動，以確保只有在目標查詢和內容更新步驟完成後，才啟動傳送。 本節提供專用的使 [用案例](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

通過在活動的入站轉變中選擇主集來確定活動的出站發送人口。

出站轉移只能包含其中一個入站轉移人口。 如果未配置活動，則出站轉移將隨機選擇一個入站人口族群。

>[!CAUTION]
>
>對於 **AND-join** type活動，會合併事件變數，但如果同一個變數定義兩次，則會發生衝突，且值仍未確定。 有關詳細資訊，請參閱[](../../workflow/using/javascript-scripts-and-templates.md#event-variables)。
