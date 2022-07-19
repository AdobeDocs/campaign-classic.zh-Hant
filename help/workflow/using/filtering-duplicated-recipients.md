---
product: campaign
title: 篩選重複的收件者
description: 瞭解如何篩選重複的收件人
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 篩選重複的收件者 {#filtering-duplicated-recipients}

![](../../assets/v7-only.svg)

在本示例中，我們要篩選在傳遞中出現兩次或多次的收件人，以便恢復重複的配置檔案。

要建立此示例，請應用以下步驟：

1. 拖放 **[!UICONTROL Query]** 的子菜單。
1. 按一下 **[!UICONTROL Edit query]** 將目標和篩選維設定為 **[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 為傳遞日誌中存在的目標收件人定義以下篩選條件。 選擇 **收件人交付日誌(broadlog)** 的 **表達式** 列，選擇 **存在** 的 **運算子** 的雙曲餘切值。

   ![](assets/query_recipients_2.png)

1. 定義以下篩選條件以定位交貨。 選擇 **[!UICONTROL Internal name]** 在「表達式」列和 **[!UICONTROL equal to]** 的下界。
1. 在值列中，添加目標傳遞的內部名稱。

   ![](assets/query_recipients_3.png)

1. 與 **[!UICONTROL AND]** 運算子，重複相同的操作以瞄準其他交貨。

   ![](assets/query_recipients_4.png)

您的出站轉移包含交貨中目標的重複收件人。
