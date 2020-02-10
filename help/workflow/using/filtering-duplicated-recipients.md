---
title: 篩選重複的收件者
description: 瞭解如何篩選複製的收件者
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 篩選重複的收件者 {#filtering-duplicated-recipients}

在此範例中，我們想要篩選在傳送中出現兩次以上的收件者，以便復原複製的描述檔。

若要建立此範例，請套用下列步驟：

1. 在工作流程中拖 **[!UICONTROL Query]** 放活動並開啟活動。
1. 按一 **[!UICONTROL Edit query]** 下並將定位和篩選維度設為 **[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 定義下列篩選條件，以定位存在於傳送記錄中的收件者。 在「 **運算子收件者」欄中選擇「傳送記錄(broadlog)** 」，選擇「運 **算子收件者」欄中存** 在(例如 **「****** OperatorRecipient」)。

   ![](assets/query_recipients_2.png)

1. 定義下列篩選條件以定位您的傳送。 在「運 **[!UICONTROL Internal name]** 算式」欄和「運算子 **[!UICONTROL equal to]** 」欄中選擇。
1. 在值欄中，新增目標傳送的內部名稱。

   ![](assets/query_recipients_3.png)

1. 使用運算 **[!UICONTROL AND]** 子，重複相同的作業以定位其他傳送。

   ![](assets/query_recipients_4.png)

您的對外轉移包含傳送中定位的重複收件者。
