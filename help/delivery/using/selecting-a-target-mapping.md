---
product: campaign
title: 選擇目標對應
description: 選擇目標對應
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---

# 選擇目標對應{#selecting-a-target-mapping}

預設情況下，傳遞範本目標為&#x200B;**[!UICONTROL Recipients]**。 因此，其目標映射使用&#x200B;**nms:recipient**&#x200B;表的欄位。 Adobe Campaign為您的傳送提供其他目標對應，以根據您的需求使用。

![](assets/delivery_select_mapping.png)

這些對應如下：

| 名稱 | 使用 | 標準結構 |
|---|---|---|
| 收件者 | 傳送給Adobe Campaign資料庫的收件者 | nms:recipient |
| 訪客 | 傳送給已透過反向連結（病毒式行銷）或社交網路(Facebook、Twitter)等收集設定檔的訪客。 | mns:visitor |
| 訂閱 | 傳送給已訂閱資訊服務（例如電子報）的收件者 | nms:subscription |
| 訪客訂閱 | 傳送給已訂閱資訊服務的訪客 | nms:visitorSub |
| 服務 | 發佈至Twitter帳戶或Facebook頁面 | nms:service |
| 運算子 | 傳送至Adobe Campaign運算子 | nms:operator |
| 外部檔案 | 透過包含傳送所需所有資訊的檔案傳送 | 沒有連結的架構，未輸入目標 |

>[!NOTE]
>
>您也可以建立新的目標對應。 此操作為專家用戶保留。 有關詳細資訊，請參閱[配置指南](../../configuration/using/target-mapping.md)。
