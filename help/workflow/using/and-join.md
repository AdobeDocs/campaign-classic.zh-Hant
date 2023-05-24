---
product: campaign
title: AND-join
description: AND-join
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---

# AND-join{#and-join}



只有在所有入站轉變啟動時（即所有先前的活動完成時），聯結才會觸發其出站轉變。 這可讓您在繼續執行工作流程之前，確定特定活動已完成。

例如，您可以在內容建立和傳送自動化的內容中使用AND-join活動，以確保只有在完成目標查詢和內容更新步驟後才會開始傳送。 以下位置提供專屬的使用案例： [本節](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>請注意，使用不同目標維度設定的入站轉變，不能使用 **[!UICONTROL AND-join]** 活動。

活動的傳出已傳送母體取決於在活動的入站轉變中選擇主要集合。

出站轉變只能包含其中一個入站轉變母體。 如果未設定活動，出站轉變將會隨機選取其中一個入站母體。

>[!CAUTION]
>
>若為 **合併連結** 型別活動，事件變數會合併，但如果相同的變數定義兩次，則會發生衝突，且值維持未定。 如需詳細資訊，請參閱[本章節](javascript-scripts-and-templates.md#event-variables)。
