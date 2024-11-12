---
product: campaign
title: 選擇目標對應
description: 瞭解如何鎖定對應
feature: Delivery Templates
hide: true
hidefromtoc: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 446062946b64c9a4d065b6a56d263914cbe628f8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 13%

---

# 選擇目標對應{#selecting-a-target-mapping}

依預設，傳遞範本以&#x200B;**[!UICONTROL Recipients]**&#x200B;為目標。 因此，它們的目標對應使用&#x200B;**nms：recipient**&#x200B;資料表的欄位。 Adobe Campaign為您的傳送提供其他目標對應，以根據您的需求使用。

![](assets/delivery_select_mapping.png)

這些對應如下：

| 名稱 | 使用 | 標準結構描述 |
|---|---|---|
| 收件者 | 傳遞給Adobe Campaign資料庫的收件者 | nms：recipient |
| 訪客 | 例如，透過轉介（病毒式行銷）或社交網路(Facebook， X — 先前稱為Twitter)收集設定檔的訪客。 | mns：visitor |
| 訂閱 | 傳遞給已訂閱資訊服務（例如電子報）的收件者 | nms：subscription |
| 訪客訂閱 | 傳遞給訂閱資訊服務的訪客 | nms：visitorSub |
| 服務 | Publish至X帳戶或Facebook頁面 | nms：service |
| 運算子 | 傳遞給Adobe Campaign操作者 | nms：operator |
| 外部檔案 | 透過包含傳遞所需所有資訊的檔案傳遞 | 沒有連結的結構描述，沒有輸入目標 |

>[!NOTE]
>
>您也可以建立新的目標對應。 這項作業已保留給專家使用者。 如需詳細資訊，請參閱[本區段](../../configuration/using/target-mapping.md)。
