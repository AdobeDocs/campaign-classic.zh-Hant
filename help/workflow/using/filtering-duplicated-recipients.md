---
product: campaign
title: 篩選重複的收件者
description: 瞭解如何篩選重複的收件者
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 篩選重複的收件者 {#filtering-duplicated-recipients}



在此範例中，我們要篩選在傳送中出現兩次或更多次的收件者，以復原重複的設定檔。

若要建立此範例，請套用下列步驟：

1. 在工作流程中拖放&#x200B;**[!UICONTROL Query]**&#x200B;活動並開啟活動。
1. 按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;並將目標和篩選維度設定為&#x200B;**[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 定義下列篩選條件，以定位存在於傳遞記錄的收件者。 在&#x200B;**運算式**&#x200B;資料行中選擇&#x200B;**收件者傳遞記錄(broadlog)**，在&#x200B;**運運算元**&#x200B;資料行中選擇&#x200B;**存在，例如**。

   ![](assets/query_recipients_2.png)

1. 定義下列篩選條件來鎖定您的傳送。 在運算式資料行中選擇&#x200B;**[!UICONTROL Internal name]**，在運運算元資料行中選擇&#x200B;**[!UICONTROL equal to]**。
1. 在值欄中，新增目標傳送的內部名稱。

   ![](assets/query_recipients_3.png)

1. 使用&#x200B;**[!UICONTROL AND]**&#x200B;運運算元，重複相同的作業以鎖定其他傳遞。

   ![](assets/query_recipients_4.png)

您的出站轉變包含傳遞中鎖定的重複收件者。
