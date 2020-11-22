---
solution: Campaign Classic
product: campaign
title: 資料模式的結構
description: 資料模式的結構
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---


# 資料模式的結構{#structure-of-a-data-schema}

資料模式的結構以樹結構的形式顯示。 若要在Adobe Campaign用戶端主控台中以圖形方式檢視它，請選取目標結構並按一下 **[!UICONTROL Structure]** 子標籤。

![](assets/d_ncs_integration_schema_arbo.png)

作為標準，欄位會先顯示（「活動」、「已啟動」等） 按字母順序排列。 接著會出現結構元素（郵遞區號、位置），最後是連結（電子郵件資訊、資料夾等）。

主鍵由紅色鍵標識，外鍵由黃色鍵標識。

根據連結是否屬於表，以圖形方式區分連結。 首先顯示從表開始的表（即表中有外鍵）（電子郵件資訊、資料夾、國家）。 「反向」系列連結（訂閱、訂購等） 的下界。
