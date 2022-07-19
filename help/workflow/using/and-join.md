---
product: campaign
title: AND-join
description: 與連接
feature: Workflows
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---

# 與連接{#and-join}

![](../../assets/v7-only.svg)

僅當激活所有入站轉換（即當完成所有先前活動時）時，連接才會觸發其出站轉換。 這允許您確保在繼續執行工作流之前已完成某些活動。

例如，您可以在內容建立和傳遞發送自動化的上下文中使用與聯接活動，以確保只有目標查詢和內容更新步驟完成後才啟動傳遞。 在中提供了專用的使用案例 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>請注意，配置了不同目標維的入站過渡無法使用 **[!UICONTROL AND-join]** 的子菜單。

通過在活動的入站轉換中選擇主集來確定活動的出站已發送人口。

出站轉換只能包含入站轉換總體之一。 如果未配置該活動，則出站轉換將隨機選擇一個入站總體。

>[!CAUTION]
>
>在 **與連接** 類型活動，將合併事件變數，但如果定義了兩次相同變數，則存在衝突，且值仍未確定。 如需詳細資訊，請參閱[本章節](javascript-scripts-and-templates.md#event-variables)。
