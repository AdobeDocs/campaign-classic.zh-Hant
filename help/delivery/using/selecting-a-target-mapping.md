---
title: 選擇目標映射
seo-title: 選擇目標映射
description: 選擇目標映射
seo-description: null
page-status-flag: never-activated
uuid: 29a666a3-2ecc-4732-b068-c93935929771
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: e2c6e273-1640-4f46-a80e-0cecb06e2769
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 選擇目標映射{#selecting-a-target-mapping}

依預設，傳送範本會定位 **[!UICONTROL Recipients]**。 因此，其目標映射使用 **nms:recipient表的欄位** 。 Adobe Campaign會根據您的需求，為您的傳送提供其他目標對應。

![](assets/delivery_select_mapping.png)

這些映射如下：

| 名稱 | 使用 | 標準架構 |
|---|---|---|
| 收件者 | 傳送給Adobe Campaign資料庫的收件者 | nms：接收者 |
| 訪客 | 傳遞給透過反向連結（病毒式行銷）或社交網路（例如Facebook、Twitter）收集的訪客個人檔案。 | mns:visitor |
| 訂閱 | 提供給訂閱資訊服務（例如電子報）的收件者 | nms：訂閱 |
| 訪客訂閱 | 提供給訂閱資訊服務的訪客 | nms:visitorSub |
| 服務 | 發佈至Twitter帳戶或Facebook頁面 | nms:service |
| 營運商 | 傳遞給Adobe Campaign營運商 | nms:operator |
| 外部檔案 | 透過包含傳送所需所有資訊的檔案傳送 | 無連結結構，未輸入目標 |

>[!NOTE]
>
>您也可以建立新的目標對應。 此操作保留給專家用戶。 有關詳細資訊，請參閱「 [Configuration（配置）」指南](../../configuration/using/target-mapping.md)。
