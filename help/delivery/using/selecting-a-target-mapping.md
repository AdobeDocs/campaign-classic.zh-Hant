---
product: campaign
title: 選擇目標對應
description: 瞭解如何鎖定對應
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 12%

---

# 選擇目標對應{#selecting-a-target-mapping}



依預設，傳遞範本的目標為 **[!UICONTROL Recipients]**. 因此，其目標對應會使用 **nms：recipient** 表格。 Adobe Campaign為您的傳送提供其他目標對應，以根據您的需求使用。

![](assets/delivery_select_mapping.png)

這些對應如下：

| 名稱 | 使用 | 標準結構描述 |
|---|---|---|
| 收件者 | 傳遞給Adobe Campaign資料庫的收件者 | nms：recipient |
| 訪客 | 向已透過轉介（病毒式行銷）或社交網路(例如Facebook、Twitter)收集設定檔的訪客傳遞。 | mns：visitor |
| 訂閱 | 傳遞給已訂閱資訊服務（例如電子報）的收件者 | nms：subscription |
| 訪客訂閱 | 傳遞給已訂閱資訊服務的訪客 | nms：visitorSub |
| 服務 | 發佈至Twitter帳戶或Facebook頁面 | nms：service |
| 運算子 | 傳遞至Adobe Campaign運運算元 | nms：operator |
| 外部檔案 | 透過包含傳遞所需所有資訊的檔案傳遞 | 沒有連結的結構描述，沒有輸入目標 |

>[!NOTE]
>
>您也可以建立新的目標對應。 這項作業是專為專家使用者保留的。 如需詳細資訊，請參閱[本區段](../../configuration/using/target-mapping.md)。
