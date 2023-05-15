---
product: campaign
title: 資料方案結構
description: 資料方案結構
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# 資料方案結構{#structure-of-a-data-schema}

資料模式的結構以樹結構的形式顯示。 若要在Adobe Campaign用戶端主控台中以圖形方式檢視，請選取目標架構，然後按一下 **[!UICONTROL Structure]** 頁簽。

![](assets/d_ncs_integration_schema_arbo.png)

依標準，會先顯示欄位（活動、啟動等） 按字母順序排列。 接著會是結構元素（郵遞區號、位置），最後是連結（電子郵件資訊、資料夾等）。

主鍵由紅鍵標識，外鍵由黃色鍵標識。

連結是否屬於表，以圖形方式加以區分。 從表開始的表（即表中有外鍵）將首先顯示（電子郵件資訊、資料夾、國家）。 「反向」收集連結（訂閱、訂購等） 會顯示在結尾。
