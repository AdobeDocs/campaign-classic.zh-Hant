---
solution: Campaign Classic
product: campaign
title: 篩選重複的收件者
description: 瞭解如何篩選複製的收件者
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---


# 篩選重複的收件者 {#filtering-duplicated-recipients}

在此範例中，我們想要篩選在傳送中出現兩次以上的收件者，以便復原複製的描述檔。

若要建立此範例，請套用下列步驟：

1. 在工作流程中拖放&#x200B;**[!UICONTROL Query]**&#x200B;活動並開啟活動。
1. 按一下&#x200B;**[!UICONTROL Edit query]**，將目標和篩選維度設為&#x200B;**[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 定義下列篩選條件，以定位存在於傳送記錄中的收件者。 在&#x200B;**Expression**&#x200B;欄中選擇&#x200B;**Recipient delivery log(broadlog)**，在&#x200B;**Operator**&#x200B;欄中選擇&#x200B;**exist，例如**。

   ![](assets/query_recipients_2.png)

1. 定義下列篩選條件以定位您的傳送。 在「運算式」欄中選擇&#x200B;**[!UICONTROL Internal name]**，在「運算子」欄中選擇&#x200B;**[!UICONTROL equal to]**。
1. 在值欄中，新增目標傳送的內部名稱。

   ![](assets/query_recipients_3.png)

1. 使用&#x200B;**[!UICONTROL AND]**&#x200B;運算子，重複相同的作業以定位其他傳送。

   ![](assets/query_recipients_4.png)

您的對外轉移包含傳送中定位的重複收件者。
