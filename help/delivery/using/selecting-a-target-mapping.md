---
product: campaign
title: 選擇目標對應
description: 瞭解如何目標映射
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 10%

---

# 選擇目標對應{#selecting-a-target-mapping}

![](../../assets/common.svg)

預設情況下，交貨模板目標 **[!UICONTROL Recipients]**。 因此，其目標映射使用 **nms：收件人** 的子菜單。 Adobe Campaign為您的交貨提供了其他目標映射，以根據您的需要使用。

![](assets/delivery_select_mapping.png)

這些映射如下：

| 名稱 | 使用 | 標準架構 |
|---|---|---|
| 收件人 | 交付給Adobe Campaign資料庫的收件人 | nms：收件人 |
| 訪問者 | 向通過推薦（病毒式營銷）或社交網路(例如，Facebook、Twitter)收集個人資料的訪客遞送。 | mns：訪問者 |
| 訂閱 | 向訂閱新聞通訊等資訊服務的收件人提供 | nms：訂閱 |
| 訪問者訂閱 | 向訂閱資訊服務的訪問者發送 | nms:visitorSub |
| 服務 | 發佈到Twitter帳戶或Facebook頁 | nms：服務 |
| 運算子 | 交付給Adobe Campaign運營商 | nms：運算子 |
| 外部檔案 | 通過包含交付所需的所有資訊的檔案進行交付 | 沒有連結架構，沒有輸入目標 |

>[!NOTE]
>
>您還可以建立新的目標映射。 此操作保留給專家用戶。 如需詳細資訊，請參閱[本區段](../../configuration/using/target-mapping.md)。
