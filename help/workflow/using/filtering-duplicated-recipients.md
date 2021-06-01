---
product: campaign
title: 篩選重複的收件者
description: 了解如何篩選重複的收件者
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 篩選重複的收件者 {#filtering-duplicated-recipients}

在此範例中，我們想篩選在傳送中出現兩次以上的收件者，以便復原重複的設定檔。

若要建立此範例，請套用下列步驟：

1. 在工作流程中拖放&#x200B;**[!UICONTROL Query]**&#x200B;活動並開啟活動。
1. 按一下&#x200B;**[!UICONTROL Edit query]**，將目標和篩選維度設為&#x200B;**[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 定義下列篩選條件，以定位存在於傳送記錄中的收件者。 在&#x200B;**Expression**&#x200B;欄中選擇&#x200B;**Recipient delivery log(broadlog)**，選擇&#x200B;**存在，如** Operator **欄中的**。

   ![](assets/query_recipients_2.png)

1. 定義下列篩選條件以定位您的傳送。 在「表達式」列中選擇&#x200B;**[!UICONTROL Internal name]**，在「運算子」列選擇&#x200B;**[!UICONTROL equal to]**。
1. 在值欄中，新增目標傳送的內部名稱。

   ![](assets/query_recipients_3.png)

1. 使用&#x200B;**[!UICONTROL AND]**&#x200B;運算子，重複相同的操作以鎖定其他傳送。

   ![](assets/query_recipients_4.png)

您的出站轉變包含傳遞中鎖定的重複收件者。
