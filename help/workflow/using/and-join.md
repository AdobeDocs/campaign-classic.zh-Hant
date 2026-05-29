---
product: campaign
title: 合併連結
description: 合併連結
feature: Workflows
hide: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
TQID: https://experienceleague.adobe.com/L6SmrK6xHkRqZI69OepbB4drLPfrX-cmvi6h6su3LYk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 195
ht-degree: 22%

---

# 合併連結{#and-join}



只有當所有入站轉變啟動時（即所有先前的活動都完成時），聯結才會觸發其出站轉變。 這讓您可以在確保特定活動已完成後再繼續執行工作流程。

例如，您可以在內容建立和傳遞傳送自動化的內容中使用AND-join活動，以確保只有在完成目標查詢和內容更新步驟後才會開始傳遞。 [此區段](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中有專用使用案例

![](assets/and-join-usage.png)

>[!NOTE]
>
>請注意，使用不同目標維度設定的入站轉變無法使用&#x200B;**[!UICONTROL AND-join]**&#x200B;活動連結在一起。

活動的傳出已傳送母體是透過在活動的入站轉變中選擇主集來決定。

傳出轉變只能包含其中一個傳入轉變群體。 如果未設定活動，出站轉變將會隨機選取其中一個入站母體。

>[!CAUTION]
>
>在&#x200B;**AND-join**&#x200B;型別活動的情況下，事件變數會合併，但如果相同的變數定義兩次，則會發生衝突，且值仍未確定。 如需詳細資訊，請參閱[本章節](javascript-scripts-and-templates.md#event-variables)。
