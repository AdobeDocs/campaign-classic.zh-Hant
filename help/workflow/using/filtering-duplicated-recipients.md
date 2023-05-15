---
product: campaign
title: 篩選重複的收件者
description: 了解如何篩選重複的收件者
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 篩選重複的收件者 {#filtering-duplicated-recipients}



在此範例中，我們想篩選在傳送中出現兩次以上的收件者，以便復原重複的設定檔。

若要建立此範例，請套用下列步驟：

1. 拖放 **[!UICONTROL Query]** 活動，然後開啟活動。
1. 按一下 **[!UICONTROL Edit query]** 並將目標和篩選維度設為 **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. 定義下列篩選條件，以定位存在於傳送記錄中的收件者。 選擇 **收件者傳送記錄(broadlog)** 在 **運算式** 欄，選擇 **存在，例如** 在 **運算元** 欄。

   ![](assets/query_recipients_2.png)

1. 定義下列篩選條件以定位您的傳送。 選擇 **[!UICONTROL Internal name]** 在「運算式」欄中， **[!UICONTROL equal to]** （在運算子欄中）。
1. 在值欄中，新增目標傳送的內部名稱。

   ![](assets/query_recipients_3.png)

1. 使用 **[!UICONTROL AND]** 運算子，重複相同的操作以鎖定其他傳送。

   ![](assets/query_recipients_4.png)

您的出站轉變包含傳遞中鎖定的重複收件者。
